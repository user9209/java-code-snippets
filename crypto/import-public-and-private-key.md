# Import key

## Import private key

````
public static PublicKey convertPublicKey(byte[] privateKeyBytes) throws Exception {
    KeySpec keySpec = new PKCS8EncodedKeySpec(privateKeyBytes);
    KeyFactory keyFactory = KeyFactory.getInstance("Ed25519", "BC");
    return keyFactory.generatePrivate(keySpec);
}
````

## Import public key

````
public static PublicKey convertPublicKey(byte[] publiceKeyBytes) throws Exception {
    KeySpec keySpec = new X509EncodedKeySpec(publiceKeyBytes);
    KeyFactory keyFactory = KeyFactory.getInstance("Ed25519", "BC");
    return keyFactory.generatePublic(keySpec);
}
````
