def caesar_cipher(text, shift, mode='encrypt'):

    if mode == 'decrypt':
        shift = -shift

    result = ''

    for char in text:
        if char.isalpha():
            # Preserve case (uppercase or lowercase)
            base = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            # Leave non-alphabetic characters unchanged
            result += char

    return result

def main():
    print("Caesar Cipher Program")
    while True:
        mode = input("Choose mode (encrypt/decrypt/exit): ").lower()
        if mode == 'exit':
            print("Exiting the program. Goodbye!")
            break
        elif mode not in ['encrypt', 'decrypt']:
            print("Invalid mode. Please choose 'encrypt', 'decrypt', or 'exit'.")
            continue

        text = input("Enter the text: ")
        while True:
            try:
                shift = int(input("Enter the shift value (integer): "))
                break
            except ValueError:
                print("Please enter a valid integer for the shift value.")

        result = caesar_cipher(text, shift, mode)
        print(f"Result: {result}\n")

if __name__ == "__main__":
    main()
