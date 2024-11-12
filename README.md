1.Run the code on visual studio or Github code space 


from flask import Flask
import os
from datetime import datetime
import pytz
import subprocess

app = Flask(__name__)

@app.route('/')
def htop():
    name = "Abilash A"  
    username = os.environ.get("USER", "Default User")  
    ist_time = datetime.now(pytz.timezone("Asia/Kolkata")).strftime('%Y-%m-%d %H:%M:%S %Z')
    top_output = subprocess.getoutput('top -b -n 1')


    return f"""
    <h1>System Information</h1>
    <p><strong>Name:</strong> {name}</p>
    <p><strong>Username:</strong> {username}</p>
    <p><strong>Server Time (IST):</strong> {ist_time}</p>
    <pre>{top_output}</pre>
    """

if __name__ == '__main__':
    app.run()
