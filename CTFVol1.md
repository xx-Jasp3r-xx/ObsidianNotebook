# CTF Collection Volume 1

1. no explanation necessary

2. decode base64
	+ `echo -n "VEhNe2p1NTdfZDNjMGQzXzdoM19iNDUzfQ==" | base64 -d`
	
3. given picture, find flag (hint was metadata)
	+ `exiftool findme.jpg`
	
4. given picture, find flag (hint was steghide)
	+ `steghide extract -sf Extinction.jpg`
	
5. highlighted the text question and flag was there

6. scan QR code for flag
	+ we can use this [online QR code reader](https://pageloot.com/qr-code-scanner/#upload)

7. given a binary file
	+ `strings hello.hello | grep -i thm`
	+ `r2 hello.hello then iz`
	
8. decode base58
	+ `sudo apt-get install base58`
	+ `echo -n "3agrSy1CewF9v8ukcSkPSYm3oKUoByUpKG4L" | base58 -d`
	
9. given a rot cipher (below is rot23, rot19, rot14, and rot7)
	+ `echo "MAF{atbe_max_vtxltk}" | tr 'd-za-cD-ZA-C' 'a-zA-Z'`
	+ `echo "MAF{atbe_max_vtxltk}" | tr 'h-za-gH-ZA-G' 'a-zA-Z'`
	+ `echo "MAF{atbe_max_vtxltk}" | tr 'm-za-lM-ZA-L' 'a-zA-Z'`
	+ `echo "MAF{atbe_max_vtxltk}" | tr 't-za-sT-ZA-S' 'a-zA-Z'`
	
10. highlighted the text and inspected the HTML code where the flag was located

11. given a corrupted png file. had to fix file header to be png (89 50 4E 47 0D 0A 1A 0A)
	+ `vim spoil.png` 
	+ `:%!xxd -p`
	+ `16x > shift + insert > :s/ //g`
	+ `:%!xxd -p -r`
	+ we can also use **hexedit**
	
12. flag hidden in TryHackMe reddit account
	+ this [new room](https://www.reddit.com/r/tryhackme/comments/eizxaq/new_room_coming_soon/) had the flag
	
13. given a binaryfuck cipher
	+ put the cipher in [decoder](https://www.dcode.fr/brainfuck-language)
	+ might need to add space before [ and after .
	+ another decoder can be found [here](https://www.splitbrain.org/services/ook)
	
14. given two strings that we need to XOR
	+ put the strings in the [XOR calculator](http://xor.pw/)
	+ `a = hex(int(s1, 16) ^ int(s2, 16))[2:]`
	+ `print(bytes.fromhex(a).decode('utf-8'))`
	+ we can install `pwntools` for python
	+ `pip install pwntools`
	+ `unhex(s1)` and `unhex(s2)` then `xor(s1, s2)`
	+ binary in python is bin(0b)

15. given a file was told to binwalk it
	+ `binwalk -e hell.jpg`

16. given a file that was all dark
	+ used [stego online tool](https://aperisolve.fr/)

17. given a QR code
	+ QR sends you to a soundcloud link which plays the text needed for the flag
	+ use [online tool](https://pageloot.com/qr-code-scanner/#upload) to read QR code

18. was told to go back in time to a particular website
	+ used [Waybackmachine](https://archive.org/web/)

19. given a cipher text with a key (hint was vigenere cipher)
	+ used [decoder online](https://www.dcode.fr/vigenere-cipher)
	
20. was told to decode cipher text (hint dec > hex > ascii)
	+ `python -c "print(hex(581695969015253365094191591547859387620042736036246486373595515576333693))" | xxd -p -r`
	+ `x=$(printf "%x" <decimal>); echo $((0x$x)) | xxd -p -r`

21. given a pcap file
	+ opened in Wireshark and found it in HTTP protocol
	+ we can also look at file > export HTTP object
	+ we can follow the HTTP stream too