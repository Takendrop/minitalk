# minitalk

**minitalk** is a project that involves creating a simple communication program between a client and a server using UNIX signals. The communication is achieved by sending strings from the client to the server, which then displays the received strings. The project is designed to test your understanding of inter-process communication (IPC) and signal handling in UNIX systems.

## Project Overview

The project consists of two programs: a **client** and a **server**.

- **Server**: The server must be started first. Upon launch, it will print its Process ID (PID), which is used by the client to send messages.
- **Client**: The client takes two parameters:
  1. The server's PID.
  2. The string to send to the server.

The client sends the provided string to the server using UNIX signals (`SIGUSR1` and `SIGUSR2`). The server receives the string and prints it out. The server should be able to handle multiple strings from different clients sequentially without needing to restart.

### Key Requirements

- The server must display the received string quickly. For instance, taking 1 second to display 100 characters is considered too slow.
- Communication between the client and server must only use UNIX signals (`SIGUSR1` and `SIGUSR2`).
- The server must be able to handle messages from several clients in a row without restarting.

## Allowed Functions

You are allowed to use the following functions to implement the mandatory part of the project:

- `write`
- `ft_printf` (or any equivalent function that you coded)
- `signal`
- `sigemptyset`
- `sigaddset`
- `sigaction`
- `kill`
- `getpid`
- `malloc`
- `free`
- `pause`
- `sleep`
- `usleep`
- `exit`

## Project Requirements

- **Executable Names**: The executables must be named `client` and `server`.
- **Makefile**: You must provide a Makefile that compiles the source files without relinking. The Makefile must include the rules: `$(NAME)`, `all`, `clean`, `fclean`, and `re`.
- **Memory Management**: Your programs must be free of memory leaks. Properly free all dynamically allocated memory.
- **Error Handling**: Your programs should handle errors thoroughly and must not crash unexpectedly (e.g., segmentation fault, bus error, double free, etc.).
- **Global Variables**: You are allowed one global variable per program (one for the client and one for the server), but its use must be justified.

## Implementation Details

- **Client**: The client converts the string into a series of signals (using `SIGUSR1` and `SIGUSR2`) based on the binary representation of each character in the string. It then sends these signals to the server process identified by the provided PID.
- **Server**: The server listens for signals, reconstructs the string from the received signals, and prints the string once it has been fully received.

## Bonus Part

For the bonus part of the project, you can implement additional features:

- **Message Acknowledgment**: The server sends a signal back to the client to acknowledge the receipt of each message.
- **Unicode Support**: Implement support for Unicode characters, allowing the client to send and the server to correctly display Unicode strings.

## How to Run

### Server

First, start the server, which will print its PID:

./server

### Client

Once the server is running, you can use the client to send a message to the server:

./client [server_pid] "Your message here"

Replace [server_pid] with the PID of the running server and "Your message here" with the string you wish to send.

## Conclusion

The **minitalk** project provides a hands-on approach to learning about process communication and signal handling in UNIX. It challenges you to create a reliable and efficient communication system using only basic UNIX signals, while also emphasizing the importance of proper memory management and error handling.
