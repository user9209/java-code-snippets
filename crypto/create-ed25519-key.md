# Ed25519

`keysize = 255`

see

````
KeyPairGenerator keyPairGenerator = KeyPairGenerator.getInstance("Ed25519");
keyPairGenerator.initialize(255,new SecureRandom());
KeyPair keyPair = keyPairGenerator.generateKeyPair();

PrivateKey privateKey = keyPair.getPrivate();
PublicKey publicKey = keyPair.getPublic();
````
