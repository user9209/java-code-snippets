# Import key

## Import private key

````
public static PrivateKey convertPrivateKey(byte[] privateKeyBytes) throws Exception {
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


## BC AsymmetricKeyParameter to PKCS8

````
public static byte[] toPKCS8(Ed25519PrivateKeyParameters key) throws Exception {
    return PrivateKeyInfoFactory.createPrivateKeyInfo(key).getEncoded();
}
````

## BC AsymmetricKeyParameter to X509

````
public static byte[] toX509(Ed25519PublicKeyParameters key) throws Exception {
    return SubjectPublicKeyInfoFactory.createSubjectPublicKeyInfo(key).getEncoded();
}
````
