# vpc-visual

An animated, beginner-friendly AWS VPC diagram that explains a virtual network as Ravi's gated housing society. Built with plain HTML, CSS, JavaScript, and inline SVG: no build step and no JavaScript dependencies.

## Moving objects

| Packet / icon | What it means |
| --- | --- |
| ✉️ Envelope | A visitor's request entering through the Internet Gateway |
| 💾 Floppy disk | Application data moving between web, app, and database tiers |
| 🔁 Repeat arrows | Database replication to the live copy in Zone B |
| 📦 Package | A software update going out through NAT and the Internet Gateway |
| 👿 Devil | An intruder attempting to reach private resources and being blocked |
| 🔒 Lock | The office's encrypted VPN connection to the private network |
| 🤝 Handshake | The private connection to a partner VPC through peering |

## The 9 steps

1. **VPC** — Ravi's fenced plot inside an AWS Cloud region, with CIDR `10.0.0.0/16`.
2. **Availability Zones** — Two separate buildings in the same region.
3. **Subnets** — Gold public areas and purple private areas in both zones.
4. **Internet Gateway** — The main gate, internet, visitors, route table, and first request envelope.
5. **Load Balancer** — A receptionist shares requests between web servers in both zones.
6. **App & Database** — Web-to-app-to-database flow plus a live database copy and replication path.
7. **NAT Gateway** — Private resources can request outbound software updates without being directly exposed to incoming internet traffic.
8. **Security** — Security Group door guards, subnet Network ACL gate guards, and a blocked intruder.
9. **VPN & Peering** — A secret office tunnel and a private road to a partner VPC.

Click a step to reveal that step and everything before it. Use **Auto-play** to advance every five seconds or **Reset** to return to step 1. The diagram stage stays dark in either page theme so its color coding remains clear.

## Run locally

1. Install Python 3 if it is not already installed.
2. Open a terminal in the `vpc-visual` folder.
3. Run:

   ```bash
   python3 -m http.server 8000
   ```
4. Open <http://localhost:8000> in your browser. (On Windows, `python -m http.server 8000` may be the command available.)

You can also open `index.html` directly, but a local server is recommended for consistent browser behavior.

## Host on GitHub Pages

1. Create a GitHub repository named `vpc-visual`, then upload the contents of this folder to the repository's `main` branch. Keep `index.html` in the repository root.
2. Open the repository **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select branch **main** and folder **/ (root)**, then click **Save**.
5. Wait for the Pages deployment to finish. The site link appears in the same Pages settings area, usually `https://YOUR-USERNAME.github.io/vpc-visual/`.

## Project structure

```text
vpc-visual/
├── index.html       # Page structure and accessible controls
├── css/
│   └── style.css    # Layout, responsive design, themes, and focus styles
├── js/
│   └── app.js       # Step content, inline SVG diagram, packets, and interactions
├── .nojekyll        # Tells GitHub Pages not to run Jekyll processing
├── LICENSE          # MIT license; replace YOUR NAME if desired
└── README.md        # Project guide
```

## Customise text and colours

- **Step text:** Edit the `steps` array near the top of `js/app.js`. Each item has `title`, `subtitle`, `plain`, `technical`, and `watch` values.
- **Diagram elements:** The inline SVG and its `layer(...)` blocks in `js/app.js` define the diagram. Each numbered layer is revealed when that step is selected.
- **Page colours:** Change the CSS custom properties in `:root` at the top of `css/style.css` (for example `--blue`, `--teal`, `--gold`, `--purple`, `--red`, and `--green`). The SVG stage has its own dark background and SVG-specific colors in `js/app.js`.
- **Creator name:** Replace `Dhruv Sonawane` in `index.html` if you ever need to change the attribution. The MIT license's `YOUR NAME` placeholder is intentionally left as requested.
- **Timing:** Change the `5000` value in `js/app.js` to adjust auto-play interval in milliseconds.

## Notes

This is an educational visualization, not an AWS deployment template. Real VPC routing, security, and high availability require careful configuration and validation. The Google Fonts stylesheet uses Bricolage Grotesque with system fallbacks; if offline, the page uses a local system font. Motion respects `prefers-reduced-motion`.
