# 🇺🇸 American Small Businesses Directory

<div align="center">

**A modern, authenticated business directory platform built with React and Supabase**

[🌐 Live Demo](https://kaatbailey.github.io/SupabaseDirectory/) • [📖 Documentation](#-features) • [🔐 Admin Panel](https://kaatbailey.github.io/SupabaseDirectory/admin-authenticated.html)

![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-3ECF8E?style=flat-square&logo=supabase&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![Status](https://img.shields.io/badge/Status-Live-success?style=flat-square)
![Businesses](https://img.shields.io/badge/Businesses-67+-blue?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

</div>

---

## 🎯 Quick Overview

A **production-ready business directory** showcasing 67+ American family-owned businesses. This full-stack application demonstrates modern web development practices with secure authentication, real-time data synchronization, and a beautiful responsive UI.

### Key Highlights

- 🔍 **Smart Search & Filtering** - Real-time search across business names, descriptions, and categories
- 🔐 **Secure Admin Dashboard** - JWT authentication with Row Level Security (RLS)
- ⚡ **Real-time Updates** - Instant data synchronization via Supabase subscriptions
- 📱 **Fully Responsive** - Optimized for desktop, tablet, and mobile devices
- 🎨 **Modern UI/UX** - Gradient backgrounds, smooth animations, and intuitive design

> 👉 **[Try the live demo →](https://kaatbailey.github.io/SupabaseDirectory/)**

---

## ✨ Features

### 🌐 Public Features
- **Smart Search** - Real-time search across all business data
- **Category Filtering** - Filter by 15+ industry categories (Agriculture, Fashion, Food & Wellness, etc.)
- **Responsive Design** - Seamless experience on all devices
- **Real-time Data** - Instant updates from Supabase database
- **Direct Contact** - Links to business owners' X/Twitter profiles
- **Modern UI** - Gradient backgrounds, card-based layout, smooth animations

### 🔐 Admin Features
- **Secure Authentication** - Email/password login via Supabase Auth
- **Full CRUD Operations** - Create, Read, Update, Delete business listings
- **Emoji Picker** - Visual icon selector for business categories
- **Multi-Admin Support** - Multiple authenticated users can manage content
- **Search & Filter** - Quickly find businesses to edit
- **Data Export** - Download all business data as JSON
- **Auto-refresh** - Stay synced with latest database changes

---

## 🛠️ Tech Stack

### Frontend
- **React 18** - Component-based UI library
- **Tailwind CSS** - Utility-first CSS framework for styling
- **Babel Standalone** - JSX transformation in browser

### Backend & Database
- **Supabase** - PostgreSQL database with real-time subscriptions
- **Supabase Auth** - Secure authentication system
- **Row Level Security (RLS)** - Database-level access control

### Deployment
- **GitHub Pages** - Static site hosting
- **Custom Domain Ready** - Easy to configure

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     GitHub Pages                        │
│  ┌──────────────────┐      ┌──────────────────────┐   │
│  │ Public Directory │      │  Admin Dashboard     │   │
│  │   (Read Only)    │      │ (Auth Required)      │   │
│  └────────┬─────────┘      └──────────┬───────────┘   │
└───────────┼────────────────────────────┼───────────────┘
            │                            │
            └────────────┬───────────────┘
                         │ HTTPS/WSS
                         ▼
            ┌────────────────────────────┐
            │    Supabase Backend        │
            │ ┌────────────────────────┐ │
            │ │   PostgreSQL Database  │ │
            │ │  - businesses table    │ │
            │ │  - RLS policies        │ │
            │ └────────────────────────┘ │
            │ ┌────────────────────────┐ │
            │ │   Authentication       │ │
            │ │  - JWT tokens          │ │
            │ │  - User management     │ │
            │ └────────────────────────┘ │
            │ ┌────────────────────────┐ │
            │ │   Real-time Engine     │ │
            │ │  - WebSocket updates   │ │
            │ └────────────────────────┘ │
            └────────────────────────────┘
```

---

## 🚀 Quick Start

### For Public Viewing
Simply visit the live site:
```
https://kaatbailey.github.io/SupabaseDirectory/
```

### For Admin Access
1. Navigate to the admin panel
2. Login with authorized credentials
3. Manage business listings with full CRUD capabilities

### Local Development
```bash
# Clone the repository
git clone https://github.com/kaatbailey/SupabaseDirectory.git

# Open index.html in your browser
# No build process needed - runs directly in browser!
```

---

## 📊 Database Schema

```sql
CREATE TABLE businesses (
  id BIGSERIAL PRIMARY KEY,
  created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  name TEXT NOT NULL,
  description TEXT NOT NULL,
  icon TEXT NOT NULL,
  category TEXT NOT NULL,
  owners TEXT[] NOT NULL
);

-- Indexes for performance
CREATE INDEX idx_businesses_created_at ON businesses(created_at DESC);
CREATE INDEX idx_businesses_category ON businesses(category);
```

### Security Policies (Row Level Security)

```sql
-- Public can read all businesses
CREATE POLICY "Public read access" ON businesses
  FOR SELECT USING (true);

-- Only authenticated users can insert
CREATE POLICY "Authenticated insert" ON businesses
  FOR INSERT WITH CHECK (auth.role() = 'authenticated');

-- Only authenticated users can update
CREATE POLICY "Authenticated update" ON businesses
  FOR UPDATE USING (auth.role() = 'authenticated');

-- Only authenticated users can delete
CREATE POLICY "Authenticated delete" ON businesses
  FOR DELETE USING (auth.role() = 'authenticated');
```

---

## 🔒 Security Features

- ✅ **Row Level Security (RLS)** enabled on all database tables
- ✅ **JWT Authentication** for admin access
- ✅ **HTTPS** enforced via GitHub Pages
- ✅ **Secure credential management** via environment variables
- ✅ **No sensitive data** exposed in client code
- ✅ **Database-level access control** prevents unauthorized writes

---

## 📈 Project Stats

| Metric | Value |
|--------|-------|
| **Total Businesses** | 67+ |
| **Categories** | 15 |
| **Response Time** | <100ms |
| **Mobile Score** | 100% Responsive |
| **Authentication** | Supabase Auth |
| **Database** | PostgreSQL |

---

## 🎯 Use Cases

- 📋 **Business Directory** - Showcase American small businesses
- 🛍️ **Product Discovery** - Help customers find artisan products
- 🤝 **Community Building** - Connect entrepreneurs and supporters
- 🇺🇸 **Support Local** - Promote USA-made products
- 📊 **Content Management** - Secure admin portal for updates

---

## 🌟 Key Technical Achievements

### Real-time Synchronization
Utilizes Supabase's real-time subscriptions to instantly reflect database changes across all connected clients.

### Scalable Authentication
Implements industry-standard JWT authentication with refresh tokens and secure password hashing via Supabase Auth.

### Responsive Design System
Built with Tailwind CSS utility classes for consistent, maintainable styling across all screen sizes.

### Database Security
Leverages PostgreSQL Row Level Security to enforce access control at the database layer, not just the application layer.

---

## 🤝 Contributing

While this is a personal portfolio project, suggestions and feedback are welcome!

### How to Contribute
1. Open an issue to discuss proposed changes
2. Fork the repository
3. Create a feature branch
4. Submit a pull request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Kathy Bailey**

- 🌐 Portfolio: [kaatbailey.github.io](https://kaatbailey.github.io)
- 💼 GitHub: [@kaatbailey](https://github.com/kaatbailey)
- 📧 Email: baileykaat@gmail.com

---

## 🙏 Acknowledgments

- Business owners and entrepreneurs featured in the directory
- Supabase team for excellent backend infrastructure
- Open source community for React and Tailwind CSS
- American small business community

---

## 📚 Related Projects

Interested in more full-stack applications? Check out my other work:
- [Portfolio Website](https://kaatbailey.github.io)
- More projects coming soon!

---

## 🔮 Future Enhancements

- [ ] **User Reviews** - Allow customers to rate and review businesses
- [ ] **Map Integration** - Display business locations on interactive map
- [ ] **Advanced Search** - Filters for location, price range, etc.
- [ ] **Business Analytics** - Dashboard for business owners
- [ ] **Email Notifications** - Alerts for new listings
- [ ] **Social Sharing** - Share businesses on social media
- [ ] **API Documentation** - Public API for third-party integrations
- [ ] **Mobile App** - React Native mobile application

---

<div align="center">

## ⭐ Star this repo if you find it helpful!

**[View Live Demo](https://kaatbailey.github.io/SupabaseDirectory/)** | **[Report Bug](https://github.com/kaatbailey/SupabaseDirectory/issues)** | **[Request Feature](https://github.com/kaatbailey/SupabaseDirectory/issues)**

Made with ❤️ by [Kathy Bailey](https://github.com/kaatbailey)

</div>
