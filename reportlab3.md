# Vigenère Cipher (Romanian Alphabet Implementation)

Author: **Lupan Ovidiu**  
Group: **FAF-223**

This project implements the Vigenère Cipher, adapted for the Romanian alphabet. It handles encryption and decryption of messages using a keyword, supporting special Romanian characters like **Ă, Â, Î, Ș, and Ț**.

---

## Features

1. **Custom Romanian Alphabet Support**:
   - Includes Romanian-specific characters: **Ă, Â, Î, Ș, and Ț**.
   - Ensures compatibility with Romanian language text.

2. **Encryption and Decryption**:
   - Encrypts a plaintext message using the Vigenère algorithm.
   - Decrypts ciphertext to restore the original message.

3. **Input Validation**:
   - Ensures that the message contains only valid Romanian characters.
   - Enforces a minimum keyword length of 7 characters for security.

4. **Key Automation**:
   - Dynamically repeats or truncates the keyword to match the message length.

5. **Ease of Use**:
   - Simple interface for choosing between encryption and decryption.

---

## How It Works

1. **Validation**:
   - The message is validated against the Romanian alphabet. If invalid characters are present, an error message is shown.

2. **Key Generation**:
   - The keyword is repeated or truncated to ensure it matches the message length.

3. **Encryption**:
   - Each character of the message is shifted by the corresponding character of the keyword within the Romanian alphabet.

4. **Decryption**:
   - Each character of the ciphertext is reversed by subtracting the keyword's character value.

---

## Code Implementation

```python
def is_valid_message(message):
    valid_chars = set("AĂÂBCDEFGHIÎJKLMNOPQRSȘTȚUVWXYZ")
    return all(char in valid_chars for char in message)

def prepare_message(message):
    message = message.replace(" ", "").upper()
    return ''.join(filter(lambda char: char in "AĂÂBCDEFGHIÎJKLMNOPQRSȘTȚUVWXYZ", message))

def generate_key(msg, key):
    key = list(key)
    if len(msg) == len(key):
        return key
    else:
        for i in range(len(msg) - len(key)):
            key.append(key[i % len(key)])
    return "".join(key)

def encrypt_vigenere(msg, key):
    encrypted_text = []
    key = generate_key(msg, key)
    alphabet = "AĂÂBCDEFGHIÎJKLMNOPQRSȘTȚUVWXYZ"
    for i in range(len(msg)):
        char = msg[i]
        if char in alphabet:
            encrypted_index = (alphabet.index(char) + alphabet.index(key[i])) % len(alphabet)
            encrypted_char = alphabet[encrypted_index]
        else:
            encrypted_char = char
        encrypted_text.append(encrypted_char)
    return "".join(encrypted_text)

def decrypt_vigenere(msg, key):
    decrypted_text = []
    key = generate_key(msg, key)
    alphabet = "AĂÂBCDEFGHIÎJKLMNOPQRSȘTȚUVWXYZ"
    for i in range(len(msg)):
        char = msg[i]
        if char in alphabet:
            decrypted_index = (alphabet.index(char) - alphabet.index(key[i]) + len(alphabet)) % len(alphabet)
            decrypted_char = alphabet[decrypted_index]
        else:
            decrypted_char = char
        decrypted_text.append(decrypted_char)
    return "".join(decrypted_text)

def main():
    choice = int(input("Alege operația: 1 - Criptare, 2 - Decriptare: "))
    key = input("Introduceți cheia (minim 7 caractere): ").upper()

    while len(key) < 7:
        key = input("Cheia trebuie să aibă cel puțin 7 caractere. Introduceți din nou cheia: ").upper()

    message = input("Introduceți mesajul: ")
    message = prepare_message(message)

    if not is_valid_message(message):
        print("Mesajul conține caractere nepermise. Folosiți doar A-Z, Â, Ș, Ț, Î, Ă.")
        return

    key = generate_key(message, key)

    if choice == 1:
        encrypted_text = encrypt_vigenere(message, key)
        print("Mesajul criptat:", encrypted_text)
    elif choice == 2:
        decrypted_text = decrypt_vigenere(message, key)
        print("Mesajul decriptat:", decrypted_text)
    else:
        print("Alegere invalidă.")

if __name__ == "__main__":
    main()
