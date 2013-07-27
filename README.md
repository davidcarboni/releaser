
Cryptolite
----------


### What is it?

Cryptolite is a wrapper for the Java Cryptography Extension, providing simple, "right" cryptography and bypassing all the options. It's "lite" as in "easy to use", not as in "less powerful". It's similar to Jasypt, (http://www.jasypt.org/) but provides even less options - if any. This means Cryptolite can do serious cryptography in just half a dozen classes and a tiny number of API methods. 

Cryptolite doesn't do any cryptography itself. Instead it relies on the well known open source BouncyCastle JCE provider to do the heavy lifting. The API is focused explicitly on providing the things developers need, especially webapp developers - hashing passwords, generating random IDs, encrypting Strings and Files, digital signatures and key exchange. No options means under the covers it just does what's most appropriate - and if necessary pragmatic - enabling you to use cryptography without having to understand it in depth. For example, did you know that using AES in ECB mode is a bad idea? Neither did I when I started, so I wrote Cryptolite to take care of it. (http://www.codinghorror.com/blog/2009/05/why-isnt-my-encryption-encrypting.html)


### Why release it?

There are two reasons: the first is to share what we believe to be a valuable by-product of WorkDocx with the community, (inspired by 37signals: http://37signals.com/svn/posts/1620-sell-your-by-products) and the second is to provide transparency for WorkDocx users as to how we are looking after their data.

The Cryptolite library was developed to provide security for the WorkDocx software-as-a-service website (http://workdocx.com/) and is the result of many hours of research and coding work I've done to keep our users safe online. Putting it into the public domain allows anyone using WorkDocx the opportunity to see how we do cryptography. It also means that if we've missed anything there's no hiding it, so if you do spot something you're not happy with, let us know (support@workdocx.com or @WorkdocxSupport) as we'll be keen to fix it.

For the community, the hope is that this will make it such a no-brainer to use good cryptography that more and more people will get it right by default. Keeping it small and opening the source code makes it easy to see how to make use of the JCE in ways not provided for by Cryptolite, so do let us know if you'd like to feed something back in.


### Thanks go to..

Much of the inspiration for the algorithms, modes and parameters comes from http://www.daemonology.net/blog/2009-06-11-cryptographic-right-answers.html. Additional research is from good old Wikipedia, as well as a bunch of other sites offering advice, including Coding Horror, above. JCE bootstrapping is from Beginning Cryptography With Java (http://www.wrox.com/WileyCDA/WroxTitle/Beginning-Cryptography-with-Java.productCd-0764596330.html), and many thanks go to the guys at BouncyCastle for their JCE provider (http://www.bouncycastle.org/).


### Licensing:

This library is released under the LGPL, like many other libraries, which means you are free to use it in commercial products. The main requirement is that you distribute the source code of this library (including any modifications) with your application. It doesn't impose obligations on your own code. See http://stackoverflow.com/questions/919549/lgpl-licensed-library for a good summary.

If you have any questions, feel free to contact me via developers@workdocx.com, @WorkdocxDev or find me on GitHub at https://github.com/davidcarboni.

David Carboni
http://workdocx.com/
