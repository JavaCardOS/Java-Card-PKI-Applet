# Java-Card-PKI-Applet
An open source Java/Java Card implementation of the ISO7816 and related PKI standards. 

INTRODUCTION
============

This is the current release of the Java Card PKI host API and application. For more details see http://javacardsign.sourceforge.net.

REQUIREMENTS
============

To run the host application you need Java Runtime Environment 1.6. To load the applet to a Java Card smart card you need a Java Card and
Global Platform compliant applet loader, e.g. pyApduTool from http://javacardos.com/javacardforum/viewtopic.php?f=3&t=38
Whatever card you use it needs to support the following Java Card API/crypto:

  ALG_RSA_SHA_PKCS1, ALG_RSA_NOPAD, ALG_SHA, ALG_SECURE_RANDOM,
  TYPE_RSA_CRT_PRIVATE, LENGTH_RSA_1024.
  
SOURCE CODE, LICENSE
====================

The source code is released under LGPL and is currently only available from the sourceforge SVN repository.

The libraries that we use are released under respective licenses described in the "lib" folder.

Discussion
=======

Have doubts? You can visit [Here](http://javacardos.com/javacardforum/viewforum.php?f=34) to ask and discuss.


USAGE INSTRUCTIONS 
=================

Creating a PKI card
-------------------

1. Unpack the release file
2. To load the applet to the card use your applet loader program (e.g. pyApduTool) to load applet.cap to the card and install it.
3.Run the host application: 
    To run the host application go to the "lib" folder in your terminal/prompt window and type.  
    java -jar pkihost.jar
    Or you can simply run either pkihost.sh or pkihost.bat depending on your operating system.
4. Remove and insert card to connect again.
5. Fill in the data in the first tab (Private Init). The PUC has to be 16 bytes long. Setting the historical bytes of the ATR is optional. You need to load the four certificates and three private keys. You can use the ones provided in the "files" folder. Then click "Initialize Applet".
   All the required data will be written to the applet.
6. Go to user administration panel. Here you can set a new user PIN.  It has to be between 4 and 20 digits long. Click "Set PIN", you will be asked to enter your PUC. Here you can also perform user PIN verification with the card at any time. 
     
     The applet is already to be used (personalised), you can reading out this PKI card.
 
 Read out a PKI card and use the PKI card
----------------------
1. Run the host application
2. Insert the PKI card into the reader (contact interface).
3. In the certificates tab you can load all the certificates from the card. This is necessary to perform cryptographics operations later on. The user certificates in our PKI applet are protected by a PIN, you will be asked for one.
4.  In the "Decrypt" tab you can decrypt any data. You enter the cipher text (or create it with "Encrypt text..."/"Encrypt file...", the  card's decryption certificate key will be used for encryption).
   Then press the Decrypt button. You will be asked for a PIN and the  card will decrypt the data, which will appear in the "Result" box.
5.  The "Signature & Authentication" tab works in a similar way. Data to be signed or encrypted is entered in a corresponding box. The  signing/encryption algorithm can be configured with the radio  buttons. The Sign button will do the required cryptograhic operation on the card after asking for the PIN. The result will appear in the "Signature" box. Here you can also verify the signature with using the card's certificate. Just press Verify.
6. The "Challenge" tab can be used at any point to prompt the PKI card  for a challenge. This challenge can be used as a data to be signed  in the signature tab. 
  
  You can visit "http://javacardos.com/javacardforum/viewforum.php?f=34" to get more informations.
