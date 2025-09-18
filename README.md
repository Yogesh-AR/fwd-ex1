# EX01 Developing a Simple Webserver
## Date:17/09/25

## AIM:
To develop a simple webserver to serve html pages and display the list of protocols in TCP/IP Protocol Suite.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Import the necessary modules.

### Step 5:
Define a custom request handler.

### Step 6:
Start an HTTP server on a specific port.

### Step 7:
Run the Python script to serve web pages.

### Step 8:
Serve the HTML pages.

### Step 9:
Start the server script and check for errors.

### Step 10:
Open a browser and navigate to http://127.0.0.1:8000 (or the assigned port).

## PROGRAM:

from http.server import HTTPServer, BaseHTTPRequestHandler
content = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>TCP/IP Protocols Overview</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            padding: 20px;
        }
        table {
            width: 90%;
            margin: auto;
            border-collapse: collapse;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        caption {
            font-size: 1.8em;
            margin-bottom: 15px;
            font-weight: bold;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 12px 15px;
        }
        th {
            background-color: #007BFF;
            color: white;
            text-align: left;
        }
        tbody tr:nth-child(even) {
            background-color: #f2f2f2;
        }
        tbody tr:hover {
            background-color: #e0f7fa;
        }
    </style>
</head>
<body>
    <table>
        <caption>Common TCP/IP Protocols</caption>
        <thead>
            <tr>
                <th>Protocol</th>
                <th>Function</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>TCP</td>
                <td>Provides reliable and ordered delivery of data between devices in a network.</td>
            </tr>
            <tr>
                <td>IP</td>
                <td>Manages addressing and packet routing to ensure data reaches the correct destination.</td>
            </tr>
            <tr>
                <td>UDP</td>
                <td>Allows faster but less reliable communication without establishing a connection.</td>
            </tr>
            <tr>
                <td>HTTP</td>
                <td>Used to transfer web pages and content over the internet.</td>
            </tr>
            <tr>
                <td>HTTPS</td>
                <td>Secure version of HTTP that encrypts communication using SSL/TLS.</td>
            </tr>
            <tr>
                <td>FTP</td>
                <td>Enables file transfers between systems on a network.</td>
            </tr>
            <tr>
                <td>SMTP</td>
                <td>Used to send and route email messages between servers.</td>
            </tr>
            <tr>
                <td>DNS</td>
                <td>Translates human-readable domain names into machine-readable IP addresses.</td>
            </tr>
        </tbody>
    </table>
</body>
</html>
"""
class myhandler(BaseHTTPRequestHandler):
    def do_GET(self):
        print("request received")
        self.send_response(200)
        self.send_header('content-type', 'text/html; charset=utf-8')
        self.end_headers()
        self.wfile.write(content.encode())
server_address = ('',8000)
httpd = HTTPServer(server_address,myhandler)
print("my webserver is running...")
httpd.serve_forever()

## OUTPUT:

![alt text](<Screenshot 2025-09-17 113724.png>)
![alt text](<Screenshot 2025-09-17 114022.png>)

## RESULT:
The program for implementing simple webserver is executed successfully.

