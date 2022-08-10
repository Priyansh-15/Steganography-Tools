# Project Name : Steganography-Tools
# Made By - Priyansh Sharma

## Project Demo Implementation Video :

https://user-images.githubusercontent.com/77832407/183821992-df55c835-ae41-4cd8-8253-6cbe7881eaf8.mp4


* Steganography is the art of hiding the fact that communication is taking place, by hiding information in other information. 
* This project hides the message with in the image, text file, audio file and video file. In this project, the sender selects a cover file (image, text, audio or video) with secret text and hide it into the cover file by using different efficient algorithm and generate a stego file of same format as our cover file (image, text, audio or video). Then the stego file is sent to the destination with the help of private or public communication networks. On the other side i.e. receiver, the receiver downloads the stego file and by using the appropriate decoding algorithm retrieves the secret text that is hidden in the stego file.

![1](https://user-images.githubusercontent.com/77832407/152796278-a60d3042-a6cd-442d-96e0-7f5a8b11f3ed.jpg)

# Image Steganography ( Hiding TEXT in IMAGE ) :
* Using ***Least Significant Bit Insertion*** we overwrite the LSB bit of actual image with the bit of text message character. At the end of text message we push a delimiter to the message string as a checkpoint useful in decoding function. We encode data in order of Red, then Green and then Blue pixel for the entire message.

# Text Steganography ( Hiding TEXT in TEXT ) :
* In Unicode, there are specific zero-width characters (ZWC). We used four ZWCs for hiding the Secret Message through the Cover Text.

![image](https://user-images.githubusercontent.com/77832407/152797497-54ad8d79-9375-4c8a-9b7a-2b3586303d47.png)

* We get its ascii value and it is incremented or decremented based on if ascii value between 32 and 64 , it is incremented by 48(ascii value for 0) else it is decremented by 48
* Then xor the the obtained value with 170(binary equivalent-10101010) 
* Convert the obtained number from first two step to its binary equivalent then add "0011" if it earlier belonged to ascii value between 32 and 64 else add "0110" making it 12       bit for each character.
* With the final binary equivalent we also 111111111111 as delimiter to find the end of message 
* Now from 12 bit representing each character every 2 bit is replaced with equivalent ZWCs according to the table. Each character is hidden after a word in the cover text.


# Audio Steganography ( Hiding TEXT in AUDIO ) :
* For encoding we have modified the LSB Algorithm, for that we take each frame byte of the converting it to 8 bit format then check for the 4th LSB and see if it matches with the secret message bit. If yes change the 2nd LSB to 0 using logical AND operator between each frame byte and 253(11111101). Else we change the 2nd LSB to 1  using logical AND operation with 253 and then logical OR to change it to 1 and now add secret message bit in LSB for achieving that use logical AND operation between each frame byte of carrier audio and a binary number of 254 (11111110). Then logical OR operation between modified carrier byte and the next bit (0 or 1) from the secret message which resets the LSB of carrier byte.

# Video Steganography ( Hiding TEXT in Video ) :
* In video steganography we have used combination of cryptography and Steganography. We encode the message through two parts
* We convert plaintext to cipher text for doing so we have used RC4 Encryption Algorithm. ***RC4 is a stream cipher and variable-length key algorithm***. This algorithm encrypts one byte at a time. It has two major parts for encryption and decryption:-
* ***KSA(Key-Scheduling Algorithm)***- A list S of length 256 is made and  the entries of S are set equal to the values from 0 to 255 in ascending order. We ask user for a key and convert it to its equivalent ascii code. S[] is a permutation of 0,1,2....255, now a variable j is assigned as   j=(j+S[i]+key[i%key_length) mod 256 and swap S(i) with S(j)  and accordingly we get new permutation for the whole keystream according to the key.
* ***PRGA(Pseudo random generation Algorithm (Stream Generation))*** -  Now we take input length of plaintext and initiate loop to generate a keystream byte  of equal length. For this we initiate i=0, j=0 now increment i by 1 and mod with 256. Now we add S[i] to j amd mod of it with 256 ,again swap the values. At last step take store keystreambytes which matches as S[(S[i]+S[j]) mod 256] to finally get key stream of length same as plaintext. 
* Now we xor the plaintext with keystream to get the final cipher.



***With Further Development In this Project " Steganography Tools", This Project Can be used by Indian army, RAW, Police and Intelligence agency for Special Emergency operation.***
