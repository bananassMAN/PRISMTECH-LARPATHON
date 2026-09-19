# LuminaLanes

LuminaLanes is a dynamic Li-Fi beam scheduling and load-balancing digital twin for a smart library environment. It models a ceiling grid of access points, clustered users at study tables, and moving obstacles in the aisles. The simulation shows how optical wireless coverage can be maintained through proactive handovers, predictive sensing, and cascading load redistribution.

## Overview

The project demonstrates three core behaviors:

- Load balancing across access points when one cell reaches its capacity threshold
- Predictive threat detection for moving obstacles before they physically block a beam
- Automatic handover logic that transitions between green, orange, and red connection states

The experience is presented in a polished browser dashboard, with a separate Python implementation for a real-time Pygame simulation.

## Project Files

- `index.html` — main dashboard and UI shell for the digital twin
- `app.js` — core simulation logic, entity models, access-point logic, rendering loop, and UI interactions
- `styles.css` — visual styling, theme system, panels, range controls, and animation behavior
- `main.py` — standalone Python/Pygame implementation of the same Li-Fi simulation concept

## Features

- 3x2 access-point ceiling layout
- Multi-user capacity management with per-AP limits
- User clustering around study tables
- Moving aisle obstacles with forward warning zones
- Proactive orange-state handovers before blockage occurs
- Red-state failure handling when physical obstruction persists
- Event log for handovers, load balancing, and drops
- Dark/light theme support and audio chime feedback
- Interactive dashboard with Home, Load Balancing, and Predictive Sensing views

## How the simulation works

The system models users as devices connected to nearby access points. Each access point can serve a limited number of users, and the algorithm tries to assign each user to the nearest available connection with a clean line of sight.

When a moving obstacle enters a predicted warning zone:

1. The system marks the affected beam as threatened (orange)
2. It initiates a proactive handover before the link is physically disrupted
3. If the candidate AP is unavailable or blocked, the connection can drop to a red failure state

This creates a visual digital twin of adaptive optical wireless behavior under realistic indoor interference conditions.

## Run the web version

From the project folder:

```bash
cd LuminaLanes
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/index.html
```

You can also open `index.html` directly in a browser, though using a local web server is recommended.

## Run the Python version

```bash
cd LuminaLanes
python main.py
```

If `pygame` is not installed, the script will attempt to install it automatically.

## Notes

This project is designed as a concept demo and visualization rather than a production networking stack. It is best suited for understanding the motion, capacity, and handover behavior of Li-Fi systems in dense indoor spaces.

## Suggested next improvements

- Parameter tuning for AP capacity and handover thresholds
- More realistic signal attenuation and beam geometry
- Additional user mobility patterns and path planning
- Metrics dashboard for throughput, load, and failure rates
- Exportable simulation logs for analysis
