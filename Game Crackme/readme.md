![image](https://github.com/user-attachments/assets/ce5f66f1-9e9f-48ae-9fd8-b5ce4f175dcc)

----
We have a file packed with UPX:

![image](https://github.com/user-attachments/assets/466e2bd7-cd9e-4c0b-90c1-e9dff14ae8ed)

Using `upx` to directly unpack the file. Or do it manual:

Finding tail of unpacking stub:

![image](https://github.com/user-attachments/assets/0a07d7e0-014e-47aa-bef9-92a3c45719bc)

Open the file with `x32dbg`, set breakpoint at that tail address (challenge file needs `D3DX9_43.dll` to run perfectly in my case):

![image](https://github.com/user-attachments/assets/9b97776f-e359-45e4-a00c-58bb9ce1ccf1)
![image](https://github.com/user-attachments/assets/c6d916bc-856a-4349-83f0-4b6a6c819148)

go to breakpoint we just set:
![image](https://github.com/user-attachments/assets/69515760-754c-4dc3-bb38-ceee6cd34efa)

Then step over to go to next instruction (probably OEP):

![image](https://github.com/user-attachments/assets/de2d6836-80e3-4a57-bc3d-d4be9fee6181)

Dumping process, fixing IAT with `Scylla`:

+ Fixing IAT and get imports:

  ![image](https://github.com/user-attachments/assets/c8b447e0-bacb-45e6-9068-546f204b5374)

  ![image](https://github.com/user-attachments/assets/88dfb5ca-b77f-4097-976d-dab5317eebbb)

+ Fixing dump:

  ![image](https://github.com/user-attachments/assets/f9324e50-559e-4a12-b644-a7de157f3b5f)

After that, we have the unpacked exe file.

First running prompts the cd check message:

![image](https://github.com/user-attachments/assets/b61d0744-ce5c-4708-9338-5bf5d3525e88)

Load into IDA, the graph presents that this one jump to previous windows prompt if zero flag is 1:

![image](https://github.com/user-attachments/assets/8d72c099-b8bc-4b28-a347-ee6d787fbd7c)

![image](https://github.com/user-attachments/assets/83657b2c-e79c-40bf-a8e4-d8578c0b1979)

So i managed to change `JZ` opcode to `JNZ` opcode (74 to 75), then the file is going to change its execution flow (jump to another branch, that creates some winGUI or something):

![image](https://github.com/user-attachments/assets/cd0e0757-ef42-48fd-99c6-fccc541e3712)

Patched then execute the new one, we completely cracked it:

![image](https://github.com/user-attachments/assets/fa95e61c-853c-40fc-9de5-16ee38e3f1e7)


