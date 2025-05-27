# bad_script.py

import os
import sqlite3
import threading
import json

USERNAME = "admin"
PASSWORD = "123456"  # Hardcoded credentials (bad)

def connect_to_db():
    conn = sqlite3.connect("app.db")
    return conn

def run_query(query):
    conn = connect_to_db()
    cursor = conn.cursor()
    try:
        cursor.execute(query)  # SQL injection risk
        results = cursor.fetchall()
        return results
    except:
        pass
    conn.close()

def risky_eval():
    user_input = input("Enter something: ")
    eval("print(" + user_input + ")")  # Unsafe use of eval()

def thread_starter():
    for i in range(5):
        t = threading.Thread(target=run_query, args=(f"SELECT * FROM users WHERE id = {i}",))
        t.run()  # Incorrect usage — should be `t.start()`

def long_function(a, b):
    x = a + b
    if x > 5:
        if x < 10:
            if x != 7:
                print("weird range")
            else:
                print("seven")
        else:
            print("ten or more")
    else:
        print("five or less")

    unused = 42

    return None

def main():
    run_query("SELECT * FROM users WHERE username = '%s'" % USERNAME)
    risky_eval()
    thread_starter()
    long_function(3, 4)

main()
