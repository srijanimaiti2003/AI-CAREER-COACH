# 🚀 AI Career Coach - Full Stack Application

A comprehensive AI-powered career coaching platform that helps professionals enhance their careers through personalized guidance, interview preparation, resume building, and industry insights.

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Environment Variables](#-environment-variables)
- [Database Setup](#-database-setup)
- [Running the Application](#-running-the-application)
- [Core Functionality](#-core-functionality)
- [API Routes](#-api-routes)
- [HR Interview Preparation](#-hr-interview-preparation)
- [Contributing](#-contributing)
- [License](#-license)

## 🌟 Features

### 🤖 AI-Powered Career Guidance
- Personalized career advice using Google Gemini AI
- Smart recommendations based on user profile and industry trends
- Automated industry insights generation

### 📝 Smart Resume Builder
- ATS-optimized resume creation
- Real-time resume scoring and feedback
- Markdown-based resume editing with live preview
- PDF export functionality

### 💼 Interview Preparation
- Role-specific mock interviews
- Instant AI feedback on performance
- Practice questions for technical and behavioral interviews
- Performance tracking with detailed analytics

### 📊 Industry Insights & Analytics
- Real-time salary data and market trends
- Industry growth analysis
- Skill demand forecasting
- Performance dashboards with charts

### ✉️ AI Cover Letter Generator
- Customized cover letters for specific job applications
- Company and role-specific content generation
- Multiple templates and formats

### 🎯 User Onboarding & Profiles
- Comprehensive user profiling system
- Skill assessment and experience tracking
- Industry-specific onboarding flow

## 🛠 Tech Stack

### Frontend
- **Next.js 15** - React framework with App Router
- **React 19** - UI library with latest features
- **Tailwind CSS** - Utility-first CSS framework
- **shadcn/ui** - Modern UI component library
- **Radix UI** - Accessible component primitives
- **Lucide React** - Beautiful icon library
- **React Hook Form** - Form management with validation
- **Zod** - TypeScript-first schema validation

### Backend & Database
- **Prisma** - Next-generation ORM
- **PostgreSQL** - Primary database (via Neon DB)
- **Neon DB** - Serverless PostgreSQL platform

### Authentication & User Management
- **Clerk** - Complete authentication solution
- **@clerk/nextjs** - Next.js integration
- **@clerk/themes** - Customizable UI themes

### AI & Machine Learning
- **Google Gemini AI** - Advanced language model
- **@google/generative-ai** - Official Google AI SDK

### Background Jobs & Scheduling
- **Inngest** - Background job processing
- **Cron Jobs** - Automated industry insights updates

### UI Components & Libraries
- **React Markdown** - Markdown rendering
- **MDX Editor** - Rich markdown editing
- **Recharts** - Data visualization and charts
- **React Spinners** - Loading components
- **Sonner** - Toast notifications
- **html2pdf.js** - PDF generation
- **Date-fns** - Date manipulation utilities

### Development Tools
- **ESLint** - Code linting and formatting
- **PostCSS** - CSS processing
- **Turbopack** - Fast bundler (Next.js)

### Styling & Animation
- **Tailwind CSS Animate** - Animation utilities
- **Class Variance Authority** - Component variants
- **clsx & tailwind-merge** - Conditional classes

## 📁 Project Structure

```
ai-career-coach/
├── app/                          # Next.js App Router
│   ├── (auth)/                  # Authentication pages
│   │   ├── sign-in/
│   │   └── sign-up/
│   ├── (main)/                  # Main application pages
│   │   ├── dashboard/           # User dashboard
│   │   ├── interview/           # Interview preparation
│   │   ├── resume/              # Resume builder
│   │   ├── ai-cover-letter/     # Cover letter generator
│   │   └── onboarding/          # User onboarding
│   ├── api/                     # API routes
│   │   └── inngest/             # Background job handlers
│   ├── globals.css              # Global styles
│   ├── layout.js               # Root layout
│   └── page.js                 # Landing page
├── components/                  # Reusable components
│   ├── ui/                     # shadcn/ui components
│   ├── header.jsx              # Navigation header
│   ├── hero.jsx                # Landing page hero
│   └── theme-provider.jsx      # Theme management
├── lib/                        # Utility libraries
│   ├── inngest/                # Background job functions
│   ├── prisma.js               # Database client
│   ├── utils.js                # General utilities
│   └── checkUser.js            # User validation
├── actions/                    # Server actions
│   ├── user.js                 # User operations
│   ├── resume.js               # Resume operations
│   ├── cover-letter.js         # Cover letter operations
│   ├── interview.js            # Interview operations
│   └── dashboard.js            # Dashboard data
├── data/                       # Static data
│   ├── features.js             # Feature descriptions
│   ├── faqs.js                 # FAQ content
│   ├── testimonial.js          # User testimonials
│   └── industries.js           # Industry data
├── hooks/                      # Custom React hooks
│   └── use-fetch.js            # Data fetching hook
├── prisma/                     # Database schema & migrations
│   ├── schema.prisma           # Database models
│   └── migrations/             # Database migrations
└── public/                     # Static assets
    ├── logo.png
    └── banner images
```

## 📋 Prerequisites

Before running this application, make sure you have:

- **Node.js** (v18 or higher)
- **npm** or **yarn** package manager
- **PostgreSQL** database (or Neon DB account)
- **Clerk** account for authentication
- **Google AI Studio** account for Gemini API

## 🚀 Installation

1. **Clone the repository:**
```bash
git clone <your-repo-url>
cd ai-career-coach
```

2. **Install dependencies:**
```bash
npm install
# or
yarn install
```

3. **Generate Prisma client:**
```bash
npx prisma generate
```

## 🔑 Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
# Database Configuration
DATABASE_URL="your_neon_db_connection_string"

# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY="your_clerk_publishable_key"
CLERK_SECRET_KEY="your_clerk_secret_key"

# Clerk Routing Configuration
NEXT_PUBLIC_CLERK_SIGN_IN_URL="/sign-in"
NEXT_PUBLIC_CLERK_SIGN_UP_URL="/sign-up"
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL="/onboarding"
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL="/onboarding"

# Google AI Configuration
GEMINI_API_KEY="your_google_ai_api_key"
```

### Environment Setup Guide:

1. **Database URL**: Get from [Neon Console](https://console.neon.tech/)
2. **Clerk Keys**: Get from [Clerk Dashboard](https://dashboard.clerk.com/)
3. **Gemini API Key**: Get from [Google AI Studio](https://makersuite.google.com/)

## 🗄️ Database Setup

1. **Push the schema to your database:**
```bash
npx prisma db push
```

2. **View your database (optional):**
```bash
npx prisma studio
```

## 🏃‍♂️ Running the Application

### Development Mode
```bash
npm run dev
# or with Turbopack (faster)
npm run dev --turbo
```

### Production Build
```bash
npm run build
npm start
```

### Other Commands
```bash
npm run lint          # Run ESLint
npx prisma generate   # Regenerate Prisma client
```

The application will be available at `http://localhost:3000`

## 🔧 Core Functionality

### Database Models

The application uses the following main models:

- **User**: User profiles with authentication integration
- **Assessment**: Interview performance tracking
- **Resume**: User resume data and ATS scoring
- **CoverLetter**: Generated cover letters for applications
- **IndustryInsight**: Market data and trends (auto-updated via cron jobs)

### Background Jobs

- **Industry Insights Generation**: Weekly automated updates using Inngest
- **Performance Analytics**: User progress tracking
- **AI Content Generation**: Resume feedback and cover letter creation

### Authentication Flow

1. User signs up/signs in via Clerk
2. Redirected to onboarding for profile setup
3. Access to main dashboard and features
4. Persistent session management

## 🛣️ API Routes

- `/api/inngest` - Background job handler for industry insights
- Server actions handle most data operations:
  - `actions/user.js` - User profile management
  - `actions/resume.js` - Resume CRUD operations
  - `actions/interview.js` - Assessment handling
  - `actions/cover-letter.js` - Cover letter generation

## 🎯 HR Interview Preparation

Preparing for an HR interview about this project? Check out our comprehensive [HR Interview Preparation Guide](./HR_INTERVIEW_PREP.md)!

This guide includes:
- 📝 Ready-to-use elevator pitches (30s and 60s versions)
- 💡 In-depth feature explanations with talking points
- 🛠 Technical stack justifications for every technology choice
- 🏗 Architecture and design decisions with detailed rationale
- 💪 6 major challenges with STAR-formatted responses
- 🎯 10+ common HR questions with comprehensive answers
- 💼 Behavioral questions and interview strategies
- 📊 Tips, preparation strategies, and common pitfalls to avoid

Perfect for discussing this project confidently in technical and HR interviews!

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Built with ❤️ using Next.js, Prisma, Clerk, and Google AI**
