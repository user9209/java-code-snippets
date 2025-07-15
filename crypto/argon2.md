# Argon2 java 21

## String Password

```
public static byte[] getKey(String password) {
        int iterations = 2;
        int memLimit = 66536;
        int hashLength = 32;
        int parallelism = 1;

        Argon2Parameters.Builder builder = new Argon2Parameters.Builder(Argon2Parameters.ARGON2_id)
                .withVersion(Argon2Parameters.ARGON2_VERSION_13)
                .withIterations(iterations)
                .withMemoryAsKB(memLimit)
                .withParallelism(parallelism);
                //.withSalt(salt);

        Argon2BytesGenerator generate = new Argon2BytesGenerator();
        generate.init(builder.build());
        byte[] result = new byte[hashLength];
        generate.generateBytes(password.getBytes(StandardCharsets.UTF_8), result, 0, result.length);
        eraseString(password);
        return result;
    }
```

## char[] Password

```
    public static byte[] getKey(char[] password) {
        int iterations = 2;
        int memLimit = 66536;
        int hashLength = 32;
        int parallelism = 1;

        Argon2Parameters.Builder builder = new Argon2Parameters.Builder(Argon2Parameters.ARGON2_id)
                .withVersion(Argon2Parameters.ARGON2_VERSION_13)
                .withIterations(iterations)
                .withMemoryAsKB(memLimit)
                .withParallelism(parallelism);
        //.withSalt(salt);

        Argon2BytesGenerator generate = new Argon2BytesGenerator();
        generate.init(builder.build());
        byte[] result = new byte[hashLength];
        generate.generateBytes(password, result, 0, result.length);
        Arrays.fill(password, '\0');
        return result;
    }
```

## Secure Erase of String Password

```
    public static void eraseString(String target) {
        try {
            MethodHandles.Lookup lookup = MethodHandles.privateLookupIn(String.class, MethodHandles.lookup());
            VarHandle valueField = lookup.findVarHandle(String.class, "value", byte[].class);

            byte[] value = (byte[]) valueField.get(target);
            Arrays.fill(value, (byte) 0); // Overwrite
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
```

### Gradle

```
tasks.withType(JavaExec).configureEach {
    jvmArgs += [
        '--add-opens', 'java.base/java.lang=ALL-UNNAMED'
    ]
}
```


## Secure Erase of String Password V2

```
    public static void eraseString2(String target) {
        try {
            Field valueField = String.class.getDeclaredField("value");
            valueField.setAccessible(true);

            byte[] value = (byte[]) valueField.get(target);
            Arrays.fill(value, (byte) 0); // Overwrite
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
```

### Gradle

```
tasks.withType(JavaExec).configureEach {
    jvmArgs += [
        '--add-opens', 'java.base/java.lang=ALL-UNNAMED'
    ]
}
```
