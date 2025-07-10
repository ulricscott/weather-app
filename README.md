# 🌤 Weather App (Ruby on Rails)

A simple, containerized Ruby on Rails application that fetches real-time weather data from the OpenWeatherMap API based on user-submitted addresses.

> ⚡️ Built to be open source — contributions and forks welcome!

---

## 🔍 Features

- Input an address via a web form
- Retrieve and display:
  - Current temperature (°C)
  - Min/Max temperature (°C)
  - Humidity
  - Wind speed (km/h)
- Displays if the response is cached
- Rails 7 app with Hotwire support
- Dockerized for easy development and deployment
- GitHub Actions for CI/CD

---

## 🧰 Tech Stack

- **Ruby on Rails** 7
- **OpenWeatherMap API**
- **Docker**
- **Hotwire/Turbo**
- **GitHub Actions** for CI
- Optional: Kamal deploy hooks scaffolded

---

## 🚀 Getting Started

### Prerequisites

- Ruby (if running natively)
- Docker & Docker Compose (recommended)
- OpenWeatherMap API key

---

### 🔧 Local Development (Docker Recommended)

1. **Clone the repository**

```bash
git clone https://github.com/uscott-dev/weather_app.git
cd weather_app
```

2. **Set up environment**

Create a `.env` file or configure environment variables for your OpenWeatherMap API key.

```env
WEATHER_API_KEY=your-api-key-here
```

3. **Run using Docker**

```bash
docker-compose build
docker-compose up
```

App will be available at [http://localhost:3000](http://localhost:3000)

---

## 🧑‍💻 Manual Setup (without Docker)

1. **Install dependencies**

```bash
bundle install
yarn install
```

2. **Set your API key**

Edit `app/controllers/weather_controller.rb` and set:

```ruby
API_KEY = ENV["WEATHER_API_KEY"] || "your-api-key-here"
```

3. **Run the server**

```bash
rails server
```

---

## 🌐 Usage

### Home Page

- Form at `/` allows users to input an address.

### Weather Display

- Submitting the form queries OpenWeatherMap and redirects to `/weather` displaying:
  - Temp (converted from Kelvin to Celsius)
  - Humidity
  - Wind speed (m/s → km/h)
  - Whether data is served from cache

If the API key is missing:

```erb
Please make sure you've updated your "api-key" in controllers/weather_controller.rb
```

---

## 📦 Project Structure Highlights

```
app/
├── controllers/
│   └── weather_controller.rb
├── views/
│   └── weather/
│       ├── index.html.erb
│       └── show.html.erb
config/
├── routes.rb         # Defines root and /weather routes
Dockerfile            # Rails production-ready Dockerfile
docker-compose.yml    # Development environment
.github/
└── workflows/ci.yml  # GitHub Actions CI pipeline
```

---

## 🔮 Future Improvements

- [ ] Add unit and integration tests (RSpec or Minitest)
- [ ] Integrate geocoding for better location accuracy
- [ ] Add map view with coordinates
- [ ] Enable multi-language support
- [ ] UI styling with Tailwind or Bootstrap
- [ ] Improve error handling and validations
- [ ] Store API responses in Redis for better caching
- [ ] Add search history per user (with Devise or session-based storage)
- [ ] Deploy to a free platform like Render, Fly.io, or Railway
- [ ] Convert temperature units (Celsius ⇄ Fahrenheit)

Have ideas? [Open an issue](https://github.com/uscott-dev/weather_app/issues) or submit a PR!

---

## ⚙️ Deployment

This project includes:

- `.kamal/` folder for deployment hooks
- GitHub Actions (`ci.yml`) for CI

You can integrate this with platforms like:

- Fly.io
- Render
- Railway
- Heroku (Docker or native)

---

## 🤝 Contributing

This app was built to be **open source** — feel free to fork, contribute, or use it as a starter project. Whether you’re fixing typos, writing tests, or adding new features, all contributions are welcome!

---

## 📜 License

MIT License © 2025 [Ulric Scott](https://github.com/ulricscott)

---

## 🌐 Credits

Powered by the [OpenWeatherMap API](https://openweathermap.org/api).
