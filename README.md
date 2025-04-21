# Infix to Postfix Conversion using Stack

## 📌 Aim
To write a Python program that converts a given **infix expression** to its **postfix form** using a stack, based on operator precedence and associativity rules. The input expression will only contain the operators `^` and `*`. A **dictionary** is used to store precedence, and a **set** is used to store the operators.

---

## 🛠 Procedure
1. Define the set of valid operators: `^`, `*`, `(`, and `)`.
2. Define a dictionary to hold the precedence of the operators. Higher numbers indicate higher precedence.
3. Traverse each character in the infix expression.
4. If the character is an operand (not in operators set), add it to the output.
5. If the character is '(', push it onto the stack.
6. If the character is ')', pop from the stack to output until '(' is found.
7. If the character is an operator:
   - While the stack is not empty and the operator on the top of the stack has greater or equal precedence, pop it to output.
   - Push the current operator onto the stack.
8. After the expression is completely scanned, pop all remaining operators from the stack to the output.

---

## 💻 Program
```python
# Infix to Postfix conversion using stack, dictionary, and set

Operators = set(['*', '^', '(', ')'])
Priority = {'*': 1, '^': 2}

def infixToPostfix(expression):
    stack = []
    output = ''
    for char in expression:
        if char not in Operators:
            output += char
        elif char == "(":
            stack.append(char)
        elif char == ")":
            while stack and stack[-1] != '(': 
                output += stack.pop()
            stack.pop()  # remove '('
        else:
            while stack and stack[-1] != '(' and Priority[char] <= Priority.get(stack[-1], 0):
                output += stack.pop()
            stack.append(char)

    while stack:
        output += stack.pop()
    return output

expression = input("Enter infix expression: ")
print(f"infix notation:  {expression}")
print("postfix notation: ", infixToPostfix(expression))

---

##OutPut
![image](https://github.com/user-attachments/assets/5092b0b4-eaa2-4bf9-a300-8f191aee9afd)

---

##Reslt
Thus, the program was successfully created and executed to convert infix to postfix notation.



