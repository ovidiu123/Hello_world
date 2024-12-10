# DES Algorithm: Calculating **L1**

**Author**: Lupan Ovidiu  
**Group**: FAF-223  

This project implements a key step in the DES (Data Encryption Standard) algorithm: calculating **L1**, the first 32 bits of the binary representation of an 8-character message.

---

## Features

### Key Highlights:
1. **Message Input**:
   - Allows manual input of an 8-character message.
   - Provides an option to generate a random 8-character alphanumeric message.

2. **Binary Representation**:
   - Converts the message into its binary equivalent using **8-bit ASCII encoding**.
   - Displays the binary string and its length in bits.

3. **L1 Calculation**:
   - Extracts the first 32 bits from the binary representation.
   - Displays **L1** in:
     - Binary
     - Hexadecimal
     - Text formats

---

## How It Works

### Step 1: Message Input

The program offers two options:
1. **Manual Input**: User inputs a message with exactly 8 characters.
2. **Random Message Generation**: Generates a random 8-character string composed of letters and digits.

### Step 2: Binary Conversion

The message is converted into binary using **ASCII encoding**, where each character is represented as an 8-bit binary string.  
**Example**:
- Input: `A1B2C3D4`
- Binary: `0100000100110001010000100011001001000011010000110011010000110100`

### Step 3: L1 Extraction

The first 32 bits of the binary string are extracted as **L1**.  
**Example**:
- Binary: `01000001001100010100001000110010`
- Hexadecimal: `0x41314232`
- Text: `A1B2`

---

## Code Implementation

```python
import random
import string


def generate_random_message():
    return ''.join(random.choices(string.ascii_letters + string.digits, k=8))


def text_to_binary(text):
    binary_message = ''.join([format(ord(char), '08b') for char in text])
    return binary_message


def print_binary_representation(binary_message):
    print("\nReprezentare binara:")
    print(f"Bit string: {binary_message}")
    print(f"Lungimea: {len(binary_message)} bits")


def calculate_l1(binary_message):
    if len(binary_message) != 64:
        raise ValueError("Input must be exactly 64 bits long")

    l1 = binary_message[:32]
    return l1


print("Algoritmul DES - Calcularea L1")
print("1. Introdu un mesaj manual")
print("2. Genereaza un mesaj aleatoriu")

choice = input("Introdu alegerea ta (1/2): ").strip()

if choice == '1':
    while True:
        message = input("Introdu un mesaj cu lungimea de 8 caractere: ").strip()
        if len(message) == 8:
            break
        print("Mesajul trebuie sa aiba lungimea de 8 caractere! ")
else:
    message = generate_random_message()
    print(f"Mesajul generat: {message}")

message_binary = text_to_binary(message)

print_binary_representation(message_binary)

l1 = calculate_l1(message_binary)

print("\nCalcularea L1:")
print(f"L1 (primii 32 bits): {l1}")
print(f"L1 in Hex: 0x{int(l1, 2):08X}")

l1_text = ''.join([chr(int(l1[i:i + 8], 2)) for i in range(0, 32, 8)])
print(f"L1 in Text: {l1_text}")
