#  SQL injection demonstration  

SQL injection is a vulnerability in websites that do not have proper input validation, which allows user input to be taken as SQL code.

---

## **1=1 is always true**
- If input is not sanitized the input it could be abused by the following:
- A typical username field of " User " could be changed to " User' OR '1'='1 "
- The SQL database will read this as:
- SELECT * FROM users WHERE username = 'admin' OR '1'='1' AND password = 'password'

-  This will return true because because '1'='1' is always true so the condition becomes true.

  
  ![1=1 Screenshot](/1=1SQLi.png)


## **-- comment**
- A typical username field of " User " could be changed to " User'-- "
- SELECT * FROM users WHERE username = 'admin -- AND password = 'password'

- This will return true because it ignores the rest of the condition after the comment requesting the password
- since the username = your input it will return true.

  
  ![-- Screenshot](/--SQLi.png)

## **How to spot?**
- You can check a website to see if it vulnerable to SQL injection by attempting SQL code in a input box
- By using the following user input, "  username'   "
- The website responds with an error, "Syntax error: Encountered "aaa" at line 1, column 67."
- Based on this response you can see that proper sanitization has not occurred making this website vulnerable to SQL injection.

  
  ![-- Screenshot](/SQLCheck.png)

## **Prevention**
- Use a safe API which avoids using the interpreter completely.
- Server side input validation
- If you have to use query with user input escape any special characters so they cannot be treated as SQL commands.
