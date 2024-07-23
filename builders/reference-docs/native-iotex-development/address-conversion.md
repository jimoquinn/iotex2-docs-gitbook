# Address Conversion

The IoTeX blockchain supports two distinct address formats: the IoTeX "native" format (addresses that start with "`io1...`") and the Ethereum-compatible format (starting with "`0x`". This page provides an overview of these formats, their purposes, and links to relevant documentation for developers and tools for conversion.

{% hint style="success" %}
[⇒ Go to the IoTeX Address converter](https://iotexscan.io/address-convert)
{% endhint %}

## IoTeX "Native" `io` Address Format

The IoTeX "native" address format is characterized by addresses that start with "`io1`". This format was introduced to ensure a transaction was happening on the IoTeX blockchain. An example of an IoTeX native address is:

```
io1qyqszqgpqyqszqgpqyqszqgpqyqszqgpqyqszq
```

## Ethereum-Compatible `0x` Address Format

IoTeX also supports Ethereum-compatible addresses that start with "`0x`". These addresses follow the standard Ethereum format, making it easier for developers and users to interact with IoTeX using familiar tools and conventions. An example of an Ethereum-compatible address on IoTeX is:

```
0x1234567890abcdef1234567890abcdef12345678
```

## Address Conversion

To facilitate seamless interaction between these two formats, IoTeX provides tools and commands to convert addresses:

* **IoTeX Address Converter Tool**: This online tool allows users to easily convert between IoTeX native and Ethereum-compatible addresses. [⇒ IoTeX Address Converter](https://iotexscan.io/address-convert)
*   **ioctl CLI Command**: The `ioctl` command-line client includes a command to convert addresses. This is particularly useful for developers who prefer working in a terminal environment. To convert an address using `ioctl`, use the following command:

    ```css
    ioctl account ethaddr {io_address | 0x_address}
    ```

## Account Cryptography Documentation

Refer to the [Account Cryptography Documentation](account-cryptography.md) for more in-depth information on IoTeX account cryptography and how native addresses are generated and managed on the IoTeX blockchain.
