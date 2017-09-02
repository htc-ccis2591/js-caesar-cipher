# HW 1 - Caesar Cipher

The goal of this homework assignment is to create a tool for encrypting and decrypting text using the Caesar Cipher. 

> Note that while there are many ways to implement the Caesar Cipher, you __MUST__ use the method described below for this assignment. 

## Encrypting and Decrypting Text Using a Ciphertext Alphabet
For the purposes of this assignment, we will call unencrypted text “plaintext”, and we will call encrypted text “ciphertext”.

The encryption scheme for this assignment is a simple substitution cipher. The scheme works by replacing each character in the plaintext with the corresponding character in a “ciphertext alphabet”, which is always the same length as the plaintext alphabet.  

For example:
plaintext alphabet:  ABCDEFGHIJKLMNOPQRSTUVWXYZ
ciphertext alphabet: KLMNOPQRSTUVWXYZABCDEFGHIJ

Given the ciphertext alphabet, if we encrypted the string “writing code is cool” it would become “gbsdsxq myno sc myyv”. This is because we replace “w” with “g”, “r” with “b” and so forth. Decryption works exactly the same way, but in reverse. Thus, “myyv” using the above alphabets becomes “cool”.

## Generating a Ciphertext Alphabet from a Key
In your program, rather than having the user specify a ciphertext alphabet directly, you will instead have the user enter a key that will be used to generate the ciphertext alphabet. We will start by setting our ciphertext alphabet equal to the plaintext alphabet. Then, we will move each character to the right by the number of letters specified by the key.  When we get to the end, the letters wrap around. 

So for example, if our key is 3, we will start with:
ciphertext alphabet:  ABCDEFGHIJKLMNOPQRSTUVWXYZ

Then move each letter to the left 3 positions:
ciphertext alphabet:  XYZABCDEFGHIJKLMNOPQRSTUVW

Note that the A is shifted to the right 3 letters, and the last 3 letters of the alphabet (XYZ) have moved to the beginning.

## Program Requirements

### Encrypt & Decrypt Rules
To encrypt or decrypt the text entered by the user, you should use the following rules for each character:

- If it is a letter, replace as described above with a letter of the same case (uppercase or lowercase).
- If it is a space, keep the space.
- If it is anything else, skip it.  It should not appear in the output.

So for example, if we had the alphabets below (key is 16):
plaintext alphabet:  ABCDEFGHIJKLMNOPQRSTUVWXYZ
ciphertext alphabet: KLMNOPQRSTUVWXYZABCDEFGHIJ

And they entered “Writing code is,!;~;;?5555 Cool”, we’d get “Gbsdsxq myno sc Myyv” as output, because we are preserving spaces, but removing any other character not in the alphabet.

### HTML Page
Create an HTML page with a simple form to accept input of a key (numeric 1-25) and a text message (of any length). There should be 3 buttons: Encrypt, Decrypt, & Reset. Also add some basic *instruction* text to the page so that anyone browsing to this will know what it does. Below the form, add a `div` element for the output.

It will be helpful to add id attributes onto the div, buttons, and input controls to easily identify and access them from JavaScript.

### Basic CSS
Use CSS to make the form display nicely. If you want, you can use Bootstrap or another library to help with your display. If not, you will need to write some basic CSS yourself. 

### JS Code
Remember to write good ES6 JavaScript code using best practices discussed in class and in the readings.

#### Get the input values
First, we need to set-up our buttons to get the value of the input controls so that we can use them in the encryption/decryption code. Set up a click handler for each button that will get each of the form fields and log the value to the console. 

Tip: Use the String trim() method to remove any whitespace from the beginning & ending of your input values.

#### Form reset
Setup another click handler to clear out the values on the input fields. You can set the value of the controls in much the same way you get the value, just put the expression on the left side of the equal sign.

For example:
`myElement.value = ""`

Note: If you use a form input type of "reset" you do not need to write code to do this. However for this assignment, I want to see that you are able to set the input field values through your JS code.


#### Encrypt & Decrypt 
Once you are getting your form data, you can now use that to encrypt or decrypt the message.  To do the encryption or decryption, you will need to use arrays following the instructions described below.  I will expect you to create and use functions with input parameters and return values to structure your code.

I reccommend that you begin by creating an array variable for the "plaintext" alphabet, as this should never change. (Be very careful setting this up, as missing a letter or swapping letters will cause incorrect translations!) Then write a function to generate the "ciphertext" alphabet by shifting the letters by the amount specified by the key.

Once you have the plaintext alphabet and the correct ciphertext alphabets, you can start going through the user's message character by character. Find the location of the letter in the plaintext alphabet array, then use the array index to get the appropriate letter from the ciphertext alphabet.


## Helpful Tips 
To get this code working correctly, you'll want to know if a letter is uppercase or lowercase. We learned that a string has a `toUpperCase()` method. We can obviously use this to change a letter (or String) to upperCase, but we can also use it to determine if the letter was upper case or not.

```
let letter = "a";
if (letter === letter.toUpperCase()) {
  console.log("That was an upper case letter!");
} else {
  console.log("That was not an upper case letter!");
}
```

If the letter was upper case, you want the translated letter to also be uppercase.  If not, you will need to use the String `toLowerCase()` method to change the letter to lower case before writing it to the output.  __Remember that you will want an uppercase letter to find the value in the plaintext alphabet.__
