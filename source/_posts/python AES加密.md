---
title: 在python中实现AES加密
description: 使用cryptography库的Fernet实现加密
tag: 工具
categories: 工具
top: false

---

# 介绍

在网络通信和数据存储中，保护敏感信息的安全性至关重要。Python中的cryptography库提供了一种强大而简单的方法，通过其Fernet加密算法，可以轻松加密和解密文本信息。本文将介绍如何使用cryptography库的Fernet模块创建一个简单的文本加密工具。

# 安装cryptography库

首先，确保你的Python环境中已经安装了cryptography库。如果未安装，可以使用以下命令进行安装：

```bash
pip install cryptography
```

如果遇到问题可以参考以下的文章：

[安装cryptography报错：Failed building wheel for cryptography-CSDN博客](https://blog.csdn.net/lavender_dream/article/details/109442618)

[pip安装cryptography时出错，怎么解决？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/376354994)

[Python 安装Python Cryptography包失败解决方案|极客教程 (geek-docs.com)

# 编写代码

创建一个Python脚本，我们将在其中使用cryptography库的Fernet来进行文本加密和解密。下面是一个简单的例子：

```python
# 导入必要的库
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from cryptography.hazmat.backends import default_backend
from cryptography.fernet import Fernet

# 生成密钥
def generate_key():
    return Fernet.generate_key()

# 加密文本
def encrypt_text(key, plaintext):
    cipher = Fernet(key)
    encrypted_text = cipher.encrypt(plaintext.encode())
    return encrypted_text

# 解密文本
def decrypt_text(key, ciphertext):
    cipher = Fernet(key)
    decrypted_text = cipher.decrypt(ciphertext).decode()
    return decrypted_text

# 主函数，演示加密和解密
def main():
    # 生成密钥
    key = generate_key()

    # 待加密的文本
    plaintext = "Hello, cryptography!"

    # 加密文本
    ciphertext = encrypt_text(key, plaintext)
    print(f"Encrypted Text: {ciphertext}")

    # 解密文本
    decrypted_text = decrypt_text(key, ciphertext)
    print(f"Decrypted Text: {decrypted_text}")

if __name__ == "__main__":
    main()
```

# 示例

[Github](https://github.com/myncdw/py-AES/releases/tag/py-AES)
