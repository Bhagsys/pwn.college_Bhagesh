#Citadel CTF

## 01 Zahard's Welcome
flag was in the discord under the rules channel 

## 02 The Social Network
first part was in the user citadweller's instagram accout where the second part was in the same user's X account 

## 03 Omniscent Flag Metadata
using exiftool we get the image's metadata which reveals that there is another image hidden within then using binwalk we optained the hidden flag which contained the flag

## 04 track 8
using pachinko's latest album's 8th track as the key for a vigenere cipher on the ciphertext we are told to use pachinko as the key on the flag portion to get the flag 

## 05 test of sweetness
a website which askes us to become admin inspecting the web page and then change user cookie to admin and u get the flag

## 06 rotten apple
a string was encrypted with tow rotation ciphers i.e; ROT13 and ROT47 to get the flag

## 07 randomly accessed memories
flag is split into 3 parts with each parts placed in commits decoding each piece using b64 decoding 

## 08 selected ambident work
opening the .wav file then opening it and viewing it as a spectrogram we we citadel followed by long streaks these streaks are morse code decoding with gives us the full flag

## 09 the robots trail
first we opened the source code to find the clue to go to the robots.txt endpoint following which we get another pathfile which leads to another and finally flag is found at a secrect .txt file

## 10 rotting in the deep 
a flag was converted to a number with its digits encrypted. applying a ROT-3 cipher we were able to decrypt the flag

## 11 coco conjecture
we uploaded the pdf to chatgpt where it self wrote an algorithm to get us the flag

## 12 schlagenheim
the .wav file is converted into a MIDI file by the clues and opening the file through garageband we get the entire flag

## 13 xor slide
we sent it simply to chatgpt along with a screenshot of the challenge where it decoded and gave us the flag

## 14 the sound of music
following the username citadweller again but this time through 3 different music rating/streaming websites we get 3 parts of the flag

## 15 echos and pings
given it to chatgpt where it told us an jpg image is hiding within it a subsequent prompt then revealed the image with the flag

## 16 the ripper
running the hash through chatgpt we found that reversing fake_flag() was the answer to the flag
