# MarketForge — Telegram Mini App

Магазин на базе Telegram Mini App + Supabase + Vercel.

---

## Деплой на Vercel

### 1. Залить на GitHub
```bash
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/ВАШ_ЮЗЕР/ВАШ_РЕПО.git
git push -u origin main
```

### 2. Подключить Vercel
1. Зайти на [vercel.com](https://vercel.com) → **Add New Project**
2. Выбрать репозиторий с GitHub
3. Framework Preset: **Vite**
4. В разделе **Environment Variables** добавить:

| Переменная | Значение |
|---|---|
| `VITE_SUPABASE_URL` | `https://dhazezwjaqlqmnacgnim.supabase.co` |
| `VITE_SUPABASE_PROJECT_ID` | `dhazezwjaqlqmnacgnim` |
| `VITE_SUPABASE_PUBLISHABLE_KEY` | Anon key из Supabase Dashboard |

5. Нажать **Deploy**

> `.env` файл **не коммитится** в репозиторий (он в `.gitignore`). Все переменные вводятся в Vercel Dashboard.

---

## Настройка напоминаний о корзине

Подробная инструкция: [CART_REMINDER_SETUP.md](./CART_REMINDER_SETUP.md)

Кратко:
1. Выполнить SQL миграцию `supabase/migrations/20260226200000_cart_sessions.sql`
2. Задеплоить Edge Functions: `sync-cart` и `cart-reminder`
3. Создать Cron Job с расписанием `*/2 * * * *`

---

## Стек
- React 18 + TypeScript + Vite
- Supabase (БД + Edge Functions + Auth)
- Telegram Mini App SDK
- Tailwind CSS + shadcn/ui
