# Telegram Shop Bot in Google Colab

This README explains how to set up and run the Telegram Shop Bot in Google Colab. The bot allows users to view products, send their address, place orders, and identify items from images. Follow the steps below to configure and run the bot in a Colab notebook.

## Requirements

- **Google Colab**: This setup is designed for Google Colab and may not work locally.
- **Telegram Bot Token**: Obtain a bot token from [BotFather](https://core.telegram.org/bots#botfather).
- **YOLOv8 Model**: Download the `yolov8n.pt` model.

## Setup and Installation

1. **Open Google Colab**:
   - Go to [Google Colab](https://colab.research.google.com/) and open a new notebook.

2. **Install Required Libraries**:
   - Run the following command in the first cell to install dependencies:
     ```python
     !pip install pyTelegramBotAPI requests Pillow ultralytics
     ```

3. **Download the YOLOv8 Model**:
   - Run this code in a new cell to download the `yolov8n.pt` model:
     ```python
     from ultralytics import YOLO

     # Download YOLOv8 model
     YOLO('yolov8n.pt')
     ```

## Setting Up the Bot Code

1. **Paste the Bot Code**:
   - Copy and paste the Telegram bot code (from `main.py`) into a new cell. Make sure to replace the `TOKEN` placeholder with your actual Telegram bot token.

2. **Modify Code for Colab Compatibility**:
   - In the last part of the code, replace `bot.polling()` with the following to ensure it runs within the Colab environment:
     ```python
     import time
     from threading import Thread

     def run_bot():
         bot.infinity_polling(timeout=10, long_polling_timeout=5)

     # Start bot in a new thread
     Thread(target=run_bot).start()
     ```

3. **Start the Bot**:
   - Run the cell containing the bot code. This will initialize and start the bot in Google Colab. Note that Colab sessions may time out if they’re idle.

## Using the Bot

- **Interact with the Bot**: Go to Telegram and send commands/messages to your bot as per the features you have defined (e.g., `/list` to see products, "Address: [your address]" to save the shipping address, and sending photos to recognize items).
- **Keep Colab Session Active**: To avoid Colab’s idle timeout, interact regularly with the notebook, or consider using **Google Colab Pro** for longer runtime sessions.

## Troubleshooting

- **YOLO Model Issues**: Ensure the `yolov8n.pt` model is successfully downloaded in your Colab environment.
- **Colab Session Timeout**: Colab sessions are temporary and will eventually time out. Keep the notebook active or use Colab Pro for extended usage.

## Contributing

Feel free to contribute, report bugs, or request features by opening a Pull Request or submitting an Issue.

## License

MIT License
