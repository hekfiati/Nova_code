# Nova Code

Integrated storefront and API for Deb Lucky Fashion Jewelries.

## Project layout

- `backend/` — Django REST API, catalog media import command, and order/payment
  endpoints.
- `frontend/` — React + Vite storefront. The app lives in `frontend/client/`.

The frontend uses the Django API for catalog and checkout features. Contact
messages open in WhatsApp and do not require a backend endpoint.

## Run locally

Start the backend in one terminal from `backend/`:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver 8000
```

Start the storefront in another terminal from the repository root:

```powershell
npm install
npm run dev
```

The Vite development server proxies `/api` requests to
`http://localhost:8000`. See `frontend/client/README.md` for storefront
configuration and `backend/DEPLOYMENT.md` for backend deployment details.

## Configuration

- Copy `backend/.env.example` to `backend/.env` and configure the backend
  settings required for payments, email, and deployment.
- Copy `frontend/client/.env.example` to `frontend/client/.env.local`.
- Set `VITE_WHATSAPP_NUMBER` to the real business number before launch:
  digits only, including country code, without a local leading zero. The
  placeholder is for development only. Restart Vite after changing it and
  rebuild production deployments.

## Product images

Initial product images are tracked in `backend/catalog/initial_product_images/`.
The backend's runtime `media/` directory is intentionally not included. From
`backend/`, run `python manage.py import_frontend_product_images` to initialize
product media when needed.
