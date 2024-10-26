<h1>Keystroke Recorder</h1>


Overview
The Keystroke Recorder is a simple keylogger implemented in Python, designed to capture and log keystrokes on a target system. It demonstrates basic keystroke recording functionality and includes the capability to send logged data to a remote server for analysis. This project is intended for educational purposes to help understand keylogging techniques and the importance of cybersecurity.

**Disclaimer**: Unauthorized access to another person's computer is illegal and unethical. Use this project responsibly and only on systems you have permission to test.

**Features**
-Records keystrokes in real-time.
-Saves keystrokes to a log file.
-Sends logs to a specified remote server.
-Uses an environment variable for configurable log filenames.

**Technologies Used**
-Python
-pynput for keyboard event handling
-requests for sending data to a server
-logging for logging captured keystrokes

**Example Usage**
Upon running, the keylogger will start capturing keystrokes immediately.
The keystrokes will be logged in a text file specified by the KEY_LOG_FILENAME environment variable or default to a timestamped filename.

**Important Notes**
Ensure you have permission to run this software on the target system.
Misuse of this keylogger can result in legal consequences.

**Contributions**
Contributions are welcome! If you'd like to contribute to this project, please fork the repository and submit a pull request.

**License**
Project licensed under **MIT license**
see the LICENSE file for details.

**Acknowledgments**
This project is for educational purposes only and aims to demonstrate the concept of keylogging in a responsible manner.


