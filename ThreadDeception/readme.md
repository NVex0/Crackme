![image](https://github.com/user-attachments/assets/4df6a874-7eeb-4bae-92da-373c62376e43)

Bypass some antidebug shit:

### 1.

![image](https://github.com/user-attachments/assets/ef0903ab-dc89-47eb-8d8d-47cdf902cef5)

- `JZ` to `JNZ`

### 2.
![image](https://github.com/user-attachments/assets/3c6b707c-e5f5-4dd7-a2c5-e14db366a522)

- `JNZ` to `JZ`

### 3.
![image](https://github.com/user-attachments/assets/99d3e977-150b-4d8b-a3bb-aae4846e2598)

- Assume that this function did some window's title check antidebug:

  ![image](https://github.com/user-attachments/assets/77dda3ce-523f-41b8-919f-6c071034ff82)

  NOPed it:

  ![image](https://github.com/user-attachments/assets/13288bf7-a5f7-4401-91d0-ce7a31631d20)

We can run debugger on the program smoothly now.

- It creates a new child process with the same name:

  ![image](https://github.com/user-attachments/assets/cabb7b51-d6f1-47d9-861b-1ae7b6d4ec91)
  
  ![image](https://github.com/user-attachments/assets/34be4f67-bf8a-460c-a9a3-17e893e8ab80)

  ![image](https://github.com/user-attachments/assets/bff9f4d1-e873-44be-8d60-68ca790f3512)

- Allocates new memory in previous created process, then write the input in it:

  ![image](https://github.com/user-attachments/assets/08504f3e-d844-495b-84eb-303d72632feb)

  ![image](https://github.com/user-attachments/assets/29b978e0-da62-40b0-a01a-4a648b122991)

  ![image](https://github.com/user-attachments/assets/44e833a4-f58e-4d96-adac-b76e72d73762)

- Create new thread with take our input as its parameter:

  ![image](https://github.com/user-attachments/assets/c79bd60e-eed1-4816-854f-f7365b3539a2)

- Go on to the function processing from CreateRemoteThread calling convention:

  + Doing hex decode, then a xoring:
 
    ![image](https://github.com/user-attachments/assets/8d4a71d7-e3d9-47c8-8aef-0fb001e0415c)

    ![image](https://github.com/user-attachments/assets/6b1ba5f4-dcac-47b0-9faa-0e3048eccdf0)

    which lead us to the correct password:

    ![image](https://github.com/user-attachments/assets/4192e642-ea67-4663-aa0c-a955c5a20e2f)

    And the correct message notification.

  
