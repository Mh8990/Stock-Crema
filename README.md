# CREMA + Stock System (Combined)

## Folder
- `crema-site/` : Website tempahan CREMA (WhatsApp checkout) + emit order JSON to Stock System
- `stock-system/` : Sistem stok (multi-admin sync) menggunakan Supabase (realtime)

## Cara Link
1. Deploy `stock-system/` (Netlify / Vercel / hosting static).
2. Dalam `crema-site/index.html`, cari `STOCK_APP_URL` dan isi domain stock system anda.
3. Bila customer klik **Hantar Pesanan**, CREMA akan:
   - simpan order JSON dalam `localStorage` key: `crema_new_order`
   - hantar `postMessage` (jika stock system dibuka dari tab yang sama / opener)
   - terus buka WhatsApp (fungsi asal tak diubah)

## Multi Admin Sync
Stock system already uses Supabase realtime (`postgres_changes`) so semua admin akan nampak order yang sama.

## Sound Notification
Stock system akan bunyi 'ding' bila order baru masuk (dari Supabase realtime, postMessage atau localStorage).

## Supabase
Edit `stock-system/index.html`:
- `SUPABASE_URL`
- `SUPABASE_ANON_KEY`

Then run SQL in `stock-system/supabase_setup.sql`.

