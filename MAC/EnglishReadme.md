[![Chinese](https://img.shields.io/badge/Chinese-README-red)](README.md)

# Chapter 6: Message Authentication Code

In cryptography, message authentication code (English: Message authentication code, abbreviated as MAC), also translated as message authentication code, file message authentication code, message authentication code, information authentication code, is a small piece of information generated after a specific algorithm , check the integrity of a certain message, and perform identity verification. It can be used to check whether the content of a message has been changed during delivery, whether by accident or deliberate attack. At the same time, it can be used as the identity verification of the message source to confirm the source of the message.

### 1. Introduction to message authentication code

Message authentication actually generates a redundant information on the message itself - MAC message authentication code. The message authentication code is generated by using the key to generate a new data block for the message to be authenticated and encrypting the data block. It is unique and one-to-one corresponding to the information to be protected. Therefore, the integrity of the message can be effectively protected. As well as realizing the non-repudiation and non-forgery of the sender’s messages.

#### 1. MAC function

The Message Authentication Code (MAC) function is a public function of the message and key. It generates a fixed-length value and uses this value as the authentication code. The MAC function is defined in the following form: MAC = Ck(M), where M is a variable-length message, K is the key shared by both sender and receiver, and C(k)M is a fixed-length authentication code.

##### 1.1. The security requirements of the MAC function are as follows

- If the attacker knows M and Ck(M), it is computationally infeasible for him to construct a message M1 that satisfies Ck(M1)=Ck(M).
- Ck(M) should be uniformly distributed, that is, for any randomly selected messages M and M1, the probability of Ck(M1)=Ck(M) is 2^-n, where n is the bit length of the MAC.
- Suppose M1 is a known transformation of M, that is, M1=f(M). For example: f can represent reversing one or more bits of M, then the probability of Ck(M1)=Ck(M) is 2^ -n.
 
The first requirement prevents an attacker from crafting new messages that match a given MAC. The second requirement is to prevent brute force attacks based on chosen plaintext. The last requirement is that the authentication algorithm should not be weaker for some parts or bits of the message than for other parts or bits.

The current status quo is that people prefer to use Hash functions to design message authentication codes. Regarding Hash functions, please read the chapters related to one-way hash functions. The reason is that the Hash function has the following characteristics:

- Generally, the software execution speed of Hash functions like MD5, SHA-1, Blake2 is faster than block cipher algorithms such as DES and AES.
- Exploitable password hash function code library.
- There are no export restrictions on cryptographic hash functions from the United States or other countries, but there are export restrictions on even symmetric block ciphers for Mac.

The Hash function does not rely on keys, so it cannot be used directly with MAC. Many solutions have been proposed to add keys to Hash functions, including UMAC and HMAC. Among them, HMAC is currently the most popular solution. It is selected as the method that must be used to implement MAC in IP security solutions, and HMAC is also used in other Internet protocols, such as Secure Socket Protocol SSL. Below we will introduce several commonly used message authentication code algorithms.



### 2. HMAC algorithm

#### 1. Introduction to HMAC algorithm

The HMAC algorithm is a message authentication method based on Hash function and key proposed by H.krawcyzk, M.Bellare, R.Canetti in 1996. The message authentication that HMAC can provide includes two aspects:

- Message integrity authentication: It can prove that the message content has not been modified during the transmission process.
- Source identity authentication: Because the communicating parties share the authentication key, the receiving party can authenticate that the source that sent the data is consistent with the claim, that is, it can reliably confirm that the received message is consistent with the sent message.

The design goals of the HMAC algorithm given in RFC20 are as follows:

- Use the existing Hash function directly without modification. In particular, it is easy to get the faster Hash function and its code on the software for free.
- If a faster or more secure Hash function is found or needed, it should be easy to replace the original embedded Hash function.
- The original performance of the Hash function should be maintained and its performance should not be reduced excessively.
- The use and handling of keys should be simple.
- If the strength of the embedded Hash function is known, it is entirely possible to know how strong the authentication mechanism is against cryptanalysis.

Let H be the HASH function embedded in the HMAC algorithm, M be the message acted on by HMAC, group M into groups, the length of each group is b; K is the key, the length of which is less than or equal to b, let K+ be the sufficient length less than b. Fill with 0
is a b-bit long result. ipad = 00110110 (hexadecimal number 36) repeats the result b/8 times, opad=01011100 (hexadecimal number 5C) repeats the result b/8 times. The HMAC algorithm is described as follows:
.：
     ![.：
](https://github.com/guoshijiang/cryptography/blob/master/img/mac001.png)


That is the following steps:
- Add 0 after the key K to create a string of length b.
- Execute the XOR operation between the b-length string generated in the previous step and ipad.
- Fill the data stream of message M into the result string of the second step.
- Use H to act on the data stream generated in step 3.
- Execute the XOR operation between the b-word long string generated in the first step and opad.
- Then fill the result of step 4 into the result of step 5.
- Use H to act on the data stream generated in step 6 and output the final result.

The construction of the HMAC algorithm takes into account the flaws of the HASH function, which increases the difficulty of the attack to a certain extent.


The key of the HMAC algorithm can be of any length. When the key length is longer than the group length of the Hash curve function, a Hash operation is performed on the key, and its digest is used as the key used by HMAC. However, when the key length is smaller than the length of the Hash value output by the Hash function, the security of the HMAC algorithm will be reduced. Therefore, the recommended minimum length of the key is the length of the Hash value output by the embedded Hash function. Keys whose length is greater than the length of the hash value output by the Hash function are acceptable, but the additional length does not significantly improve the security of the HMAC algorithm. In addition, the key must be randomly selected (or use a strong pseudo-random generation method based on random seeds), and updated periodically. Periodically updating keys is a basic security measure to deal with potential flaws in functions and keys, and can reduce the harm caused by leaked keys.


#### 2. Security of HMAC

The construction of the HMAC algorithm takes into account the defects of the Hash function. It corrects the defects of the Hash function through secondary Hash operations, and the value range of the Hash function is not reduced under the action of the key. The designers of HMAC considered the attack costs of different attack models. Considering that offline attacks are easier to complete than online attacks, the key was also used in the secondary Hash operation when constructing HMAC to strengthen the resistance to offline attacks.


The security of the HMAC algorithm depends on the security of the embedded HASH function. Currently, the most powerful attack on the HMAC algorithm is based on the collision attack on the HASH function. If a birthday attack is used, without changing the key of the HMAC algorithm, for a HASH function with an embedded output digest length of n bits, it is necessary to calculate digests for approximately 2^n/2 messages to find a collision. This is computationally infeasible. Therefore, under existing conditions, birthday attacks are basically infeasible to the HMAC algorithm, unless the embedded HASH function has serious flaws and conflicts. Since the MD5 and SHA-1 algorithms have been cracked, you must be careful when choosing to embed a Hash function, and never choose an algorithm that has been cracked.


At the same time, the security of HMAC also relies on the key. The security of the key depends on the length and randomness of the key. When using HMAC for message authentication, you should choose a random key or a key generated using a cryptographic pseudo-random sequence generator. The length of the key cannot be less than the length of the HASH value output by the HASH function. A secure key negotiation mechanism must be adopted, the key must be updated as frequently as possible, and the key must be well protected. These are essential elements for maintaining HMAC message authentication security. If the attacker cannot crack the key, even if the attacker finds a collision of the HASH function, he cannot forge the message to conduct an effective attack on HMAC message authentication. Therefore, on the premise of ensuring key security, HMAC message authentication is more secure than simply using the HASH function for message authentication.


### 3. UMAC algorithm



### 4. Summary