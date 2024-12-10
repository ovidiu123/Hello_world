# Caesar Cipher Encryption/Decryption Script

Author: **Lupan Ovidiu**  
Group: **FAF-223**

This project implements a simple **Caesar Cipher** for encrypting and decrypting messages using a shift key. The script allows users to:
- Encrypt a message by shifting characters forward in the alphabet.
- Decrypt a message by shifting characters backward in the alphabet.

---

## Features

1. **Encrypt Messages**: Converts plaintext into a secure cryptogram using a user-defined shift key.
2. **Decrypt Messages**: Deciphers a cryptogram back into readable plaintext using the same key.
3. **Validation**:
   - Ensures the user inputs a valid choice (encrypt or decrypt).
   - Validates the shift key to be within the range of 1–25.
4. **Alphabet Handling**: Operates exclusively on uppercase English letters (A–Z).

---

## How It Works

1. **Encryption Logic**:
   - For each character in the message, find its position in the alphabet.
   - Shift the position forward by the key value (modulo 26 for wraparound).
   - Append the shifted character to the encrypted message.

2. **Decryption Logic**:
   - For each character in the cryptogram, find its position in the alphabet.
   - Shift the position backward by the key value (modulo 26 for wraparound).
   - Append the shifted character to the decrypted message.

---

## Code Implementation

```python
def encrypt(key, message, alphabet):
    encrypted_message = ""
    for ch in message:
        if ch in alphabet:
            pos = alphabet.index(ch)
            new_pos = (pos + key) % 26
            encrypted_message += alphabet[new_pos]
    return encrypted_message


def decrypt(key, message, alphabet):
    decrypted_message = ""
    for ch in message:
        if ch in alphabet:
            pos = alphabet.index(ch)
            new_pos = (pos - key) % 26
            decrypted_message += alphabet[new_pos]
    return decrypted_message


alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

while True:
    choice = input("Do you want to encrypt a message, or decrypt it? E/D\n").upper().strip().replace(" ", "")
    if choice == "E" or choice == "D":
        break
    else:
        print("Invalid choice. Please choose either encryption: E, or decryption: D.")

while True:
    key = int(input("Enter your key (1-25): "))
    if 1 <= key <= 25:
        break
    else:
        print("Invalid key. Please enter a key between 1 and 25.")

if choice == "E":
    message = input("Enter your message for encryption\n").upper().replace(" ", "").strip()
    result = encrypt(key, message, alphabet)
    print(f"Encrypted message: {result}")
else:
    message = input("Enter your cryptogram for decryption\n").upper().replace(" ", "").strip()
    result = decrypt(key, message, alphabet)
    print(f"Decrypted message: {result}")
