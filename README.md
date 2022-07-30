# impl-sm2
  sm2算法是一种椭圆曲线公钥密码算法，比RSA算法更加安全高效。包括公钥加密、数字签名、密钥协商三部分。
  
  数字签名算法的签名生成部分使用随机密钥k作为公私钥对的基础。如果使用两个相同的k在不同的消息上生成两个签名，会导致签名私钥的泄露。尽管k被要求是随机得，但人们还是在无意中可能使用相同的k。
  
  为了避免这个漏洞，RFC 6979中定义了k的确定性初始化以及确定性的数字签名生成过程，即签署相同的交易将产生相同的k值，签署不同的交易将产生不同的k值。并且此类签名与标准数字签名算法（DSA）和椭圆曲线数字签名算法（ECDSA）兼容。关于RFC中定义的k的生成过程可见参考文献[2]。
  
  本次实验实现了使用gmssl库实现了sm2中的数字签名算法。因为对于RFC 6979文档中生成k的算法描述存在一些疑惑，所以尝试实现k的生成并未成功。
  
  实验参数选取：
  
  素数p：
  
  FFFFFFFEFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000FFFFFFFFFFFFFFFF
  
  系数a:
  
  FFFFFFFEFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000FFFFFFFFFFFFFFFC
  
  系数b:
  
  28E9FA9E9D9F5E344D5A9E4BCF6509A7F39789F515AB8F92DDBCBD414D940E93
  
  基点G：
  
  x=32c4ae2c1f1981195f9904466a39c9948fe30bbff2660be1715a4589334c74c7
  
  y=bc3736a2f4f6779c59bdcee36b692153d0a9877cc62a474002df32e52139f0a0
  
  阶n：
  
  FFFFFFFEFFFFFFFFFFFFFFFFFFFFFFFF7203DF6B21C6052B53BBF40939D54123
  
  待签名消息：message
  
  私钥：
  
  00B9AB0B828FF68872F21A837FC303668428DEA11DCD1B24429D0C99E24EED83D5

  公钥：
  
B9C9A6E04E9C91F7BA880429273747D7EF5DDEB0BB2FF6317EB00BEF331A83081A6994B8993F3F5D6EADDDB81872266C87C018FB4162F5AF347B483E24620207

  实验结果：
  
  图中16进制字符串是签名结果，“pass”是验签结果。
  
  <img width="398" alt="image" src="https://user-images.githubusercontent.com/110089380/181922430-d7a15040-781b-42c1-a4e6-e2b72f11b9f8.png">

  参考文献：
  
  [1]http://www.gmbz.org.cn/main/viewfile/20180108023346264349.html

  [2]https://rfc2cn.com/rfc6979.html

  [3]https://blog.csdn.net/wcc19840827/article/details/106634927
 
