# Monoalphabetic Cipher Decryption Tool

Author: **Lupan Ovidiu**  
Group: **FAF-223**

This project provides an interactive decryption tool for monoalphabetic ciphers using frequency analysis. The application is built with **PyQt5** for the GUI and leverages **matplotlib** for visualizing frequency distributions. It facilitates analyzing encrypted text and performing manual substitutions to decrypt messages effectively.

---

## Features

1. **Frequency Analysis**:
   - Computes the frequency of each letter in the encrypted message.
   - Displays frequencies alongside standard English letter frequencies for comparison.

2. **Interactive Substitution**:
   - Allows users to manually map encrypted letters to decrypted letters via a GUI table.
   - Provides a real-time preview of the decrypted message.

3. **Graphical Visualization**:
   - Generates a bar chart comparing the encrypted message's letter frequencies with standard English frequencies.

4. **User-Friendly Interface**:
   - Easy-to-use GUI with clear input, output, and decryption tools.
   - Tables for frequency analysis and substitution mappings.

---

## Code Explanation

### **Key Components**

1. **Frequency Analysis**:
   - Computes the percentage frequency of letters in the encrypted message.
   - Compares these frequencies with pre-defined English letter frequencies for decryption hints.

2. **Substitution Mapping**:
   - Users input decrypted letters for each encrypted letter in an interactive table.
   - Updates the preview of the decrypted message dynamically.

3. **Visualization**:
   - Uses matplotlib to create a bar chart for visual comparison of letter frequencies.

4. **GUI**:
   - Built with PyQt5, featuring widgets for input, output, tables, and buttons for actions.

---

## Code

```python
import string
import sys
from collections import Counter
import matplotlib.pyplot as plt
from PyQt5.QtWidgets import QApplication, QMainWindow, QVBoxLayout, QWidget, QLabel, QTextEdit, QPushButton, \
    QTableWidget, QTableWidgetItem

# English letter frequencies
english_frequencies = {
    'a': 8.167, 'b': 1.492, 'c': 2.782, 'd': 4.253, 'e': 12.702,
    'f': 2.228, 'g': 2.015, 'h': 6.094, 'i': 6.966, 'j': 0.153,
    'k': 0.772, 'l': 4.025, 'm': 2.406, 'n': 6.749, 'o': 7.507,
    'p': 1.929, 'q': 0.095, 'r': 5.987, 's': 6.327, 't': 9.056,
    'u': 2.758, 'v': 0.978, 'w': 2.360, 'x': 0.150, 'y': 1.974,
    'z': 0.074
}

class MonoalphabeticCipherApp(QMainWindow):
    def __init__(self):
        super().__init__()
        # GUI initialization and layout setup
        ...

    def show_frequency_analysis(self):
        # Analyze and visualize frequencies
        ...

    def update_decryption(self):
        # Update decrypted message based on mappings
        ...

if __name__ == '__main__':
    app = QApplication(sys.argv)
    window = MonoalphabeticCipherApp()
    window.show()
    sys.exit(app.exec_())
