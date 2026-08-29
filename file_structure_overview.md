# Project Structure: BG Skyblock Community App

```text
/
├── app/
│   ├── layout.tsx             # Root layout with global styles & providers
│   ├── page.tsx               # Landing Page (Hero Showcase)
│   ├── categories/
│   │   └── page.tsx           # Category Grid View
│   ├── category/
│   │   └── [slug]/
│   │       └── page.tsx       # Item Catalog & Dynamic Value View
│   ├── admin/
│   │   └── dashboard/
│   │       └── page.tsx       # Admin Portal & Role Management
│   ├── api/
│   │   ├── auth/[...nextauth]/route.ts  # Discord OAuth2 configuration
│   │   ├── feedback/route.ts            # Discord Webhook integration
│   │   └── items/route.ts               # CRUD operations for catalog
│   └── globals.css            # Tailwind & custom animations
├── components/
│   ├── ui/
│   │   ├── Card.tsx           # Glassmorphic card system
│   │   ├── Button.tsx         # Spring-animated buttons
│   │   └── Badge.tsx          # Rarity-glow badges
│   ├── Header.tsx             # Sticky nav with shimmering logo
│   ├── SideNavBar.tsx         # Desktop sidebar navigation
│   ├── Footer.tsx             # Community footer
│   ├── ItemCard.tsx           # Floating animator & detail engine
│   ├── BackgroundShader.tsx   # WebGL/Three.js cosmic background
│   └── FeedbackModal.tsx      # Discord integrated form
├── lib/
│   ├── prisma.ts              # Database client
│   └── discord.ts             # Webhook & OAuth helpers
├── prisma/
│   └── schema.prisma          # Database models (Categories, Items, Roles)
├── public/                    # Static assets (logos, fallback images)
├── .env.local                 # Configuration template
├── next.config.mjs            # Next.js configuration
├── package.json               # Dependencies
└── tailwind.config.ts         # Theme & Animation configuration
```