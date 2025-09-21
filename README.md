# 🗺️ Telegram Bot + Flask API for Managing Places Database
This project combines a **Telegram bot** powered by [PyTelegramBotAPI](https://pypi.org/project/pyTelegramBotAPI/) and a **REST API using Flask** to manage a list of places stored in a SQLite database. Additionally, it uses the **Geoapify Places API** to automatically fetch tourist locations.

## 📋 Features
- **Telegram Bot**:
  - Search for places by **name** (`/place_by_name`) or **address** (`/place_by_address`).
  - Retrieve a list of places by **category** (`/list_places`).
  - Add (`/add_place`), update (`/update_place`), and delete (`/delete_place`) records.
  - Automatically load tourist spots on startup.
- **Flask REST API**:
  - `POST /add_place` — Add a new place.
  - `GET /place_by_name/<name>` — Get address by name.
  - `GET /place_by_address/<address>` — Get name by address.
  - `GET /list_places/<category>` — List places by category.
  - `PUT /update_place/<name>` — Update address by name.
  - `DELETE /delete_place/<name>` — Delete place by name.
- **SQLite Database** (`places.db`):
  - Automatically created on the first run.
  - Stores name, category, and address.

## 🛠️ Tech Stack
- [Python 3.8+](https://www.python.org/)  
- [Flask](https://flask.palletsprojects.com/) — Web server and REST API.  
- [PyTelegramBotAPI (telebot)](https://pypi.org/project/PyTelegramBotAPI/) — Telegram Bot API wrapper.  
- [Requests](https://pypi.org/project/requests/) — For HTTP requests to Geoapify API.  
- [SQLite3](https://www.sqlite.org/) — Built-in database.  
- [Geoapify Places API](https://www.geoapify.com/) — Tourist places data provider.

## 🚀 Installation and Run

1. **Install dependencies**
```bash
pip install -r requirements.txt
```
2. **Configure environment variables**  
Create a `.env` file or replace values in the code:  
- `BOT_API_KEY` — Telegram bot token from [BotFather](https://t.me/BotFather).  
- `GeoApiKey` — Geoapify API key.  
- Optionally adjust `Latitude`, `Longitude`, and `Radius`.
3. **Run the application**
```bash
python PlaceFinder.py
```
Bot will start polling Telegram API, and Flask server will be available at:
```
http://localhost:5000
```

## 📡 API Request Examples
### Add a place
```bash
curl -X POST http://localhost:5000/add_place \
-H "Content-Type: application/json" \
-d '{"name": "Park", "category": "tourism", "address": "Central St"}'
```
### Get place by name
```bash
curl http://localhost:5000/place_by_name/Park
```
### List places by category
```bash
curl http://localhost:5000/list_places/tourism
```
### Update a place
```bash
curl -X PUT http://localhost:5000/update_place/Park \
-H "Content-Type: application/json" \
-d '{"address": "New Central St"}'
```
### Delete a place
```bash
curl -X DELETE http://localhost:5000/delete_place/Park
```

## 🤖 Using the Telegram Bot
1. Find your bot in Telegram using the name you set up in **BotFather**.  
2. Commands:  
   - `/start` — Display bot features.  
   - `/place_by_name` — Search address by place name.  
   - `/place_by_address` — Search place name by address.  
   - `/list_places` — List places by category.  
   - `/add_place` — Add a new place.  
   - `/update_place` — Update place address.  
   - `/delete_place` — Delete a place.  

## 📜 License
This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.
