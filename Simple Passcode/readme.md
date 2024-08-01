![image](https://github.com/user-attachments/assets/c712724b-bce2-4371-aeb8-3720f7c76070)

----

`Main` Funtion - simply check user input, and return true or false:

![image](https://github.com/user-attachments/assets/e002df9a-a603-446c-87a1-b98db2f39ebe)

`Check` Function - compare user input with environment variable using sha256:

![image](https://github.com/user-attachments/assets/fb3ee78f-9b47-44af-aaf0-06bb1ba8c952)

`Retrieve Key` Function - generate a key value, that's use to compare with user input:

![image](https://github.com/user-attachments/assets/95e81c3c-73b5-4df2-98bc-01c8aa301c4b)

Our idea is to set breakpoint at the end of `Retrieve Key` Function to get the key value, then copy paste and we successfully cracked it:

![image](https://github.com/user-attachments/assets/a77293fa-3153-4548-9f3b-79c4374269dc)
