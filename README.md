# IP-Security-Checker

![IP Security Checker](ip%20security%20checker.png)

A visual IP address security checker built with p5.js. Enter any IP address to get location details, network ownership, and a security classification — all rendered in a cybersecurity-themed interface.

> **Note:** The tool runs in demo mode by default using a built-in IP database. For live lookups, see the API integration section below.

---

## Features

- Real-time IP address lookup and analysis
- Location information (country, city, region, timezone)
- Network details (ASN, organization)
- Security classification with color-coded indicators: Private, Hosting, or Standard
- Demo mode with pre-loaded IP addresses
- Clean, dark cybersecurity-themed interface

---

## Screenshots

**Input view — enter any IP to begin:**

![Input Screen](ip%20security%20checker.png)

**Results view — security analysis output:**

![Results Screen](ip%20security%20checker%202.png)

---

## Demo IPs

| IP Address | Description |
|---|---|
| `8.8.8.8` | Google DNS |
| `1.1.1.1` | Cloudflare DNS |
| `208.67.222.222` | OpenDNS |
| `9.9.9.9` | Quad9 |
| `192.168.1.1` | Private Network IP |

---

## Security Levels

| Level | Color | Meaning |
|---|---|---|
| PRIVATE | Blue | Local network IP (e.g. 192.168.x.x, 10.x.x.x) |
| HOSTING | Orange | Data center or hosting provider — potentially a proxy or VPN |
| STANDARD | Green | Regular residential or ISP address |

---

## Installation

**Prerequisites:** A web browser with JavaScript enabled. No build tools required.

```bash
git clone https://github.com/yourusername/ip-security-checker.git
cd ip-security-checker
```

Open `index.html` directly in your browser, or serve it locally:

```bash
python -m http.server 8000
# Navigate to http://localhost:8000
```

---

## Usage

1. Enter an IP address in the input field
2. Click **Check IP Security**
3. View the location, network, and security analysis results

---

## File Structure

```
ip-security-checker/
├── index.html      # Main HTML file
├── sketch.js       # p5.js sketch with IP checker logic
├── README.md       # This file
└── LICENSE
```

---

## Customization

### Adding More Demo IPs

Edit the `ipDatabase` object in `sketch.js`:

```javascript
const ipDatabase = {
  'YOUR_IP_HERE': {
    ip: 'YOUR_IP_HERE',
    country_name: 'Country Name',
    country: 'CC',
    city: 'City Name',
    region: 'Region',
    timezone: 'Timezone',
    asn: 'AS12345',
    org: 'Organization Name',
    type: 'standard' // 'hosting' or 'private'
  }
};
```

### API Integration (Optional)

To use live data instead of demo mode, modify `checkIPSecurity()` in `sketch.js`:

```javascript
async function checkIPSecurity() {
  let ip = ipInput.value().trim();
  try {
    let response = await fetch(`https://ipapi.co/${ip}/json/`);
    ipData = await response.json();
    statusText = '✓ Security check complete for ' + ip;
  } catch (error) {
    statusText = '✗ Error checking IP: ' + error.message;
  }
}
```

> Most IP geolocation APIs require registration and an API key.

---

## Built With

- [p5.js](https://p5js.org/) — Creative coding library
- Vanilla JavaScript
- HTML5 Canvas

---

## Contributing

Pull requests are welcome.

```bash
git checkout -b feature/your-feature
git commit -m 'Add your feature'
git push origin feature/your-feature
```

Then open a Pull Request.

---

## License

MIT License — see the `LICENSE` file for details.

---

## Disclaimer

This tool is for educational and research purposes only. Demo mode uses simulated data. For production use, integrate with a legitimate IP geolocation service.
