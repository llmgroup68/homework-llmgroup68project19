# homework-llmgroup68project19
project19:forge a signature to pretend that you are Satoshi
实现方式：Python

成员：李丽敏-202100460130（仅一人一组）

实验概述：
  一：ECDSA
       
      ECDSA是一种基于椭圆曲线密码学的数字签名算法。它可用于验证数据的完整性和真实性，并确保数据的未被篡改。CDSA基于椭圆曲线上的离散对数问题，利用椭圆曲线上点的运算性质来实现数字签名。它由三个主要步骤组成：密钥生成、签名和验签。
    
  密钥生成：
      选择一个椭圆曲线和一个基点（公共参数）。
       
      随机生成一个私钥（通常为一个大整数），并计算对应的公钥。
    
  签名：
       
      选择一个随机数k
       
      使用私钥和消息的哈希值计算签名，包括两个部分：r （r = (k * G).x mod n）和 s（s = (k^-1 * (hash + r * privateKey)) mod n）。
    
  验签：
       
     使用公钥、消息的哈希值和签名进行验证，检查签名是否有效。
       
     验证的过程包括：计算w = s^-1 mod n，计算u1 = (hash * w) mod n，计算u2 = (r * w) mod n，计算验证点V = (u1 * G + u2 * publicKey)。
     如果验证点V的x坐标与r相等，则说明签名有效，否则签名无效。
二：实验过程
    在实验中，首先实现实现了ECDSA（椭圆曲线数字签名算法）的签名和验证功能。
    
   1：定义了椭圆曲线参数p、a、b以及基点G的x坐标和y坐标。辅助函数，包括求最大公约数、扩展欧几里得算法、求逆元、模幂运算等。实现了将整数转换为字节数组的函数int_to_bytes()和将字节数组转换为整数的函数bytes_to_int()。定义了要签名的消息msg。（关键代码如下）

![image](https://github.com/llmgroup68/homework-llmgroup68project19/assets/138642474/b2cda55d-4d7c-476e-bbdf-cf5ecf3b0061)

   2：然后我们实现了ECDSA签名函数ECDSA_sign(msg)，其中使用了随机数k和哈希函数SHA-1来生成签名。使用了哈希函数SHA-1来计算消息的哈希值，并根据公式验证签名的有效性。
调用ECDSA_verif_sign()函数对给定的消息msg和签名(r, s)进行验证，返回验证结果。

![image](https://github.com/llmgroup68/homework-llmgroup68project19/assets/138642474/ace6a11f-ae11-490e-bb64-416d097850a3)

   3：最后，实现了伪造签名的函数forge_sign()，该函数生成了随机数u和v，并根据这些随机数计算出伪造的签名(r, s, e)。实现了验证伪造签名的函数verify(r, s, e)，该函数根据公式验证伪造签名的有效性。

   ![image](https://github.com/llmgroup68/homework-llmgroup68project19/assets/138642474/84d3e9dd-4110-4cbc-92e1-710c0c249ffe)

   运行结果如下：

   ![image](https://github.com/llmgroup68/homework-llmgroup68project19/assets/138642474/db1f866a-2b47-4c8b-8243-ea2383f57694)




