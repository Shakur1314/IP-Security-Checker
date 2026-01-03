# IP-Security-Checker
A visual IP address security checker built with p5.js that provides location information and security analysis for IP addresses.

Features

Real-time IP address lookup and analysis
Location information display (Country, City, Region, Timezone)
Network information (ASN, Organization)
Security classification (Private, Hosting, Standard)
Visual security indicators
Demo mode with pre-loaded IP addresses
Clean, cybersecurity-themed interface

Demo
Try these pre-loaded IP addresses:

8.8.8.8 - Google DNS
1.1.1.1 - Cloudflare DNS
208.67.222.222 - OpenDNS
9.9.9.9 - Quad9
192.168.1.1 - Private Network IP

Screenshots
The tool displays:

IP address input field
Location details (country, city, region, timezone)
Network information (ASN, organization)
Security analysis with color-coded indicators
Visual security level indicator

Installation
Prerequisites

Web browser with JavaScript enabled
p5.js library (included via CDN)

Setup

Clone the repository:

bashgit clone https://github.com/yourusername/ip-security-checker.git
cd ip-security-checker

Open index.html in your web browser

Or use a local server:
bashpython -m http.server 8000
# Then navigate to http://localhost:8000
Usage

Enter an IP address in the input field
Click "Check IP Security" button
View the security analysis results

Understanding Security Levels

PRIVATE (Blue) - Local network IP addresses (192.168.x.x, 10.x.x.x)
HOSTING (Orange) - Data center or hosting provider IPs (potentially used for proxies/VPNs)
STANDARD (Green) - Regular residential or ISP addresses

File Structure
ip-security-checker/
│
├── index.html          # Main HTML file
├── sketch.js           # p5.js sketch with IP checker logic
├── README.md           # This file
└── LICENSE             # License file
How It Works
Demo Mode
The application includes a mock IP database with pre-configured entries for common DNS servers and private IPs. This allows the tool to work without requiring an external API.
IP Classification

Private IPs: Detected using common private IP ranges
Hosting IPs: Identified by ASN and organization data
Standard IPs: Regular residential or business connections

Data Display
The tool shows:

Geographic location information
Network ownership details
Security risk assessment
Visual color-coded indicators

Technical Details
Built With

p5.js - Creative coding library
Vanilla JavaScript
HTML5 Canvas

Key Functions

setup() - Initialize canvas and UI elements
draw() - Render the interface
checkIPSecurity() - Validate and lookup IP address
displayIPInfo() - Render IP information on canvas
drawSecurityIndicator() - Display visual security level

Customization
Adding More Demo IPs
Edit the ipDatabase object in sketch.js:
javascriptconst ipDatabase = {
  'YOUR_IP_HERE': {
    ip: 'YOUR_IP_HERE',
    country_name: 'Country Name',
    country: 'CC',
    city: 'City Name',
    region: 'Region',
    timezone: 'Timezone',
    asn: 'AS12345',
    org: 'Organization Name',
    type: 'standard' // or 'hosting' or 'private'
  }
};
Changing Colors
Modify the color values in the code:

Background: background(30, 30, 50)
Accent color: fill(0, 255, 150)
Security indicators: Modify in drawSecurityIndicator()

Future Enhancements

 Integration with real IP geolocation APIs (ipapi, ipinfo.io)
 VPN/Proxy detection
 Threat intelligence integration
 Export results to JSON/CSV
 IP reputation scoring
 Historical lookup data
 Bulk IP checking
 Dark/Light theme toggle

API Integration (Optional)
To integrate with a real IP geolocation API, modify the checkIPSecurity() function:
javascriptasync function checkIPSecurity() {
  let ip = ipInput.value().trim();
  
  try {
    let response = await fetch(`https://ipapi.co/${ip}/json/`);
    ipData = await response.json();
    statusText = '✓ Security check complete for ' + ip;
  } catch (error) {
    statusText = '✗ Error checking IP: ' + error.message;
  }
}
Note: Most IP APIs require registration and API keys.
Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

Fork the project
Create your feature branch (git checkout -b feature/AmazingFeature)
Commit your changes (git commit -m 'Add some AmazingFeature')
Push to the branch (git push origin feature/AmazingFeature)
Open a Pull Request

License
This project is licensed under the MIT License - see the LICENSE file for details.
Acknowledgments

Built with p5.js
Inspired by cybersecurity threat intelligence tools
Demo IP data sourced from public DNS providers

Disclaimer
This tool is for educational and research purposes only. The demo mode uses simulated data for unknown IP addresses. For production use, integrate with a legitimate IP geolocation service.
