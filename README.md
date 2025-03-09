# MQTT Weather Data Storage & Visualization

This project is designed to collect temperature and humidity data from an MQTT broker, store it in an SQLite database, and provide real-time visualization with 5-minute averaging.

## Features

- Live data collection from an MQTT broker
- Storage of data in an SQLite database
- Real-time visualization of temperature and humidity
- Automatic 5-minute averaging of sensor data
- Historical data access with customizable time ranges
- Fully responsive design for both desktop and mobile devices

## Technical Architecture

### Backend
- Built with Node.js and Express
- Uses an MQTT client to gather data
- SQLite for database storage
- Socket.io for real-time data updates

### Frontend
- HTML, CSS, and JavaScript
- Chart.js for interactive data visualization
- Socket.io client for real-time updates
- Responsive UI for optimal user experience

## Installation

### Prerequisites
- Node.js (v14 or higher)
- npm (v6 or higher)

### Setup

1. Clone the repository:
   ```sh
   git clone https://github.com/Mugisha-Samuella/mqtt-weather-app.git
   cd mqtt-weather-app
   ```

2. Install dependencies:
   ```sh
   npm install
   ```

3. Start the application:
   ```sh
   npm start
   ```

4. Open `http://localhost:3000` to view the dashboard.

## Database Structure

The project uses an SQLite database with these tables:

### weather_data
Stores raw MQTT sensor data:
- `id`: Primary key
- `topic`: MQTT topic
- `value`: Numeric value
- `timestamp`: Time of data reception

### weather_averages
Stores processed 5-minute average values:
- `id`: Primary key
- `temperature`: Average temperature
- `humidity`: Average humidity
- `timestamp`: Time of calculation

## MQTT Configuration

The application connects to an MQTT broker at `ws://157.173.101.159:9001` and subscribes to:
- `/work_group_01/room_temp/temperature` (temperature readings)
- `/work_group_01/room_temp/humidity` (humidity readings)

## API Endpoints

- `GET /api/latest` - Retrieves the most recent temperature and humidity values.
- `GET /api/history?hours=24` - Fetches historical 5-minute average data for a specified time range.

## Development

For development mode with automatic restarts on file changes:
```sh
npm run dev
```

## Customization

### Changing MQTT Broker
To connect to a different MQTT broker, update the connection URL in `app.js`:
```javascript
const mqttClient = mqtt.connect('ws://your-broker-url:port');
```

### Adjusting Chart Settings
Modify the chart configurations in `index.html` to customize data visualization.

## License
MIT

## Author
Samuella Mugisha

