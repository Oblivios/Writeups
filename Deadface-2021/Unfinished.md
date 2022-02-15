## Unfinished - *Programming*

### - Description -

> There seems to be something wrong with this code. Can you figure
out how to make it return the flag? Modify the code to show the flag. 
Submit the flag as: flag{flag-goes-here}.

**Code**

```py
def get_flag():
    flag = '666c61677b30682d6c6f6f6b2d612d466c61477d'
    return u(flag).decode('utf-8')

print(f'The flag is: ')
```

### - Solution -

This one is easy, we have to call the function `get_flag()`

So we have to modify the last line:

`print(f'The flag is: {get_flag()}')`

Here's a picture of the code and the result:

![Code&Result](https://user-images.githubusercontent.com/68814228/137643160-ba40bd55-d2d9-4949-8b94-1faac5dd8b1a.png)
