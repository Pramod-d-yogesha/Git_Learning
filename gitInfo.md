# What is Git? How is it different from other version control systems?

Git is a **distributed version control system (DVCS)** that helps developers track changes in their codebase, collaborate with others, and manage project history efficiently. Unlike traditional **centralized version control systems (CVCS)**, Git allows every user to have a full copy of the repository, including its entire history, on their local machine.

This design provides more flexibility, faster performance, and better data safety.

![image](https://github.com/user-attachments/assets/6f45bb8d-42c9-48cd-bd29-ac6e81d00b3f)

## Key differences between CVCS and DVCS

| #  | Topic       | Centralized VCS (CVCS)                                      | Distributed VCS (DVCS)                                    |
|----|------------|--------------------------------------------------------------|-----------------------------------------------------------|
| 1  | Cloning    | Only specific files or folders are checked out.              | The entire repository (full history) is cloned.            |
| 2  | History    | No commit history/logs are available locally.                | Full commit history/logs are available locally.            |
| 3  | Online use | Always requires an internet connection for any operation.    | Only needs internet for pushing and pulling; commits work offline. |
| 4  | Backup     | No local backup; data loss if the central server fails.      | Local copy serves as a full backup.                        |
| 5  | Speed      | Slower because every action communicates with the server.    | Faster because most actions happen locally.                |
