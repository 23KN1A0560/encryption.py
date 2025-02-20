# encryption.py
About 🔐 Secure Data Hiding in Images using Steganography | AICTE &amp; IBM SkillsBuild Internship Project. This Python-based tool hides secret messages in images using OpenCV &amp; PyQt6, with password-protected decryption. Secure, user-friendly &amp; efficient for cybersecurity. Future scope: multi-format support, AES encryption &amp; web/mobile integration![idi mypic jpg](https://github.com/user-attachments/assets/a851c3ac-a729-46ab-ad81-214054aaac22)
import cv2
import os

def main():
    img = cv2.imread("mypic.jpg")  # Replace with the correct image path
    if img is None:
        print("Error: Image not found.")
        return

    msg = input("Enter secret message: ")
    password = input("Enter a passcode: ")

    # Check if the message can fit in the image
    if len(msg) > img.size // 3:
        print("Error: Message is too long to fit in the image.")
        return

    # Encoding the message
    for i in range(len(msg)):
        n, m, z = divmod(i, img.shape[1]), i % img.shape[1], i % 3
        img[n, m, z] = ord(msg[i])

    cv2.imwrite("stegano.png", img)
    os.startfile("stegano.png")  # Use 'os.startfile' for Windows

if __name__ == "__main__":
    main()
