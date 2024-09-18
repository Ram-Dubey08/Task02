# Task02: Build a Chatbot Using python
import tkinter as tk
from tkinter import scrolledtext
import random

class Chatbot:
    def __init__(self, root):
        self.root = root
        self.root.title("Chatbot")

        self.text_area = scrolledtext.ScrolledText(root, width=50, height=20)
        self.text_area.pack(padx=10, pady=10)

        self.input_field = tk.Entry(root, width=50)
        self.input_field.pack(padx=10, pady=10)

        self.send_button = tk.Button(root, text="Send", command=self.send_message)
        self.send_button.pack(padx=10, pady=10)

    def send_message(self):
        user_input = self.input_field.get()
        self.input_field.delete(0, tk.END)
        self.text_area.insert(tk.END, f"User: {user_input}\n")
        response = self.chatbot_response(user_input)
        self.text_area.insert(tk.END, f"Chatbot: {response}\n")

    def chatbot_response(self, user_input):
        responses = [
            "Hello! How can I help you today? ",
            "What's on your mind? ",
            "I'm here to assist you. What do you need? ",
            "How can I assist you? ",
            "What can I help you with? ",
        ]
        return random.choice(responses)

if __name__ == "__main__":
    root = tk.Tk()
    app = Chatbot(root)
    root.mainloop()
