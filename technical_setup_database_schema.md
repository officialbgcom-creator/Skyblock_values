---
title: BG SKYBLOCK Technical Architecture & Database Schema
---

## 1. Database Schema (Supabase/Prisma)

### Table: `categories`
- `id`: UUID (Primary Key)
- `name`: String (e.g., "Armor Sets")
- `slug`: String (Unique)
- `order`: Integer
- `icon`: String (Lucide icon name)

### Table: `items`
- `id`: UUID (Primary Key)
- `category_id`: UUID (Foreign Key -> categories.id)
- `name`: String
- `rarity`: Enum (Common, Uncommon, Rare, Epic, Legendary, Mythic)
- `market_value`: String (e.g., "50M - 60M")
- `image_url`: String (Storage link)
- `is_favorite`: Boolean
- `attributes`: JSONB (Dynamic key-value pairs: {"Defense": 100, "Ability": "Leap"})

### Table: `roles`
- `discord_id`: String (Primary Key)
- `role_type`: Enum (Super Admin, Editor, Helper, User)
- `assigned_by`: String (Discord ID)

### Table: `feedback`
- `id`: UUID (Primary Key)
- `user_id`: String (Discord ID)
- `type`: Enum (Bug, Suggestion, General)
- `description`: Text
- `status`: Enum (Pending, Reviewed, Integrated)
- `webhook_sent`: Boolean

## 2. Environment Variables (`.env.local`)

```env
NEXT_PUBLIC_DISCORD_CLIENT_ID=your_id
DISCORD_CLIENT_SECRET=your_secret
DISCORD_REDIRECT_URI=http://localhost:3000/api/auth/callback/discord
DISCORD_WEBHOOK_URL=your_webhook_url
DATABASE_URL=postgresql://...
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
SUPABASE_SERVICE_ROLE_KEY=your_key
```

## 3. Discord Activity / iFrame Handling
The app is built using standard Next.js routing. To embed in Discord:
1. Provide the deployment URL as the Activities source.
2. Ensure `X-Frame-Options` and `Content-Security-Policy` allow embedding from `discord.com`.
3. Use `next-auth` Discord Provider for seamless OAuth2 within the iFrame.