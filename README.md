# Mini House Café · ミニハウス カフェ
Website for **Mini House Café**, a family restaurant in Myoko, Niigata, Japan. It serves Filipino, Indian and taco dishes, and its coffee is Philippine Barako and Arabica only. Guests aged 65 and over get free coffee.
> 〒944-0047 新潟県妙高市白山町1丁目5-19 · +81-090-8657-2010 · mini.cafe2026@gmail.com
## Features
- **8 languages**: Japanese and English are the main languages, plus Spanish, Chinese, Hindi, Portuguese, Tagalog and Korean. The site opens in the visitor's browser language and remembers their choice.
- **Menu with pickup ordering**: category tabs, a cart, and payment at the counter. Free coffee for guests 65+ is taken off the order automatically. Alcohol is dine-in only.
- **Table reservations**: booking times follow breakfast, lunch and dinner hours, and each time slot takes up to 40 guests.
- **Event booking**: birthdays, debuts, reunions and company parties, with an option to book the café's own live band.
- **About Us, coffee, gallery and contact sections**, with an embedded Google Map, directions and opening hours.
## Tech stack
| Part      | Technology |
|-----------|------------|
| Frontend  | React, Tailwind CSS, shadcn/ui, Framer Motion, Lenis smooth scroll |
| Backend   | FastAPI (Python) |
| Database  | MongoDB |
## Project structure
```
backend/
  server.py            # API + menu data (MENU list, prices in yen)
frontend/
  public/              # logo.png, favicon.png, index.html
  src/
    App.js             # page layout
    lib/site.js        # contact info, address, hours, map, currency
    i18n/              # translations: ja, en, es, zh, hi, pt, tl, ko
    components/site/   # Hero, Story, Menu, Coffee, Events, Reserve, Visit, Footer…
    context/           # cart
```
## API
| Method | Endpoint            | Purpose |
|--------|---------------------|---------|
| GET    | `/api/menu`         | Menu items and reservation time slots |
| POST   | `/api/orders`       | Place a pickup order (prices are calculated on the server) |
| POST   | `/api/reservations` | Request a table |
| POST   | `/api/events`       | Request an event, with or without the band |
## Run locally
Backend:
```bash
cd backend
pip install -r requirements.txt
# create backend/.env with MONGO_URL, DB_NAME, CORS_ORIGINS
uvicorn server:app --host 0.0.0.0 --port 8001
```
Frontend:
```bash
cd frontend
yarn install
# create frontend/.env with REACT_APP_BACKEND_URL=http://localhost:8001
yarn start
```
## Common edits
- **Menu items and prices**: `MENU` in `backend/server.py`
- **Address, phone, email, hours**: `frontend/src/lib/site.js`
- **Text in any language**: `frontend/src/i18n/<language>.js`
- **Logo**: `frontend/public/logo.png`, `logo192.png`, `favicon.png`
---
© Mini House Café · Kain na tayo · さあ、いただきましょう
