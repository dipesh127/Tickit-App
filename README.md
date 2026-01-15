# My Tickit App

## Overview

My Tickit is a cutting-edge event management and ticketing platform designed to simplify the way events are organized and experienced. It provides a seamless interface for event organizers to manage ticket sales, track attendance, and communicate with participants in real-time. Also known as "Ticketr - Real-time Event Ticketing Platform," this application leverages modern technologies to deliver a responsive, secure, and user-friendly experience.

## Features

### For Event Attendees

- **Real-time Ticket Availability Tracking**: Stay updated on ticket stock without page refreshes.
- **Smart Queuing System**: Join virtual queues with live position updates to secure your spot.
- **Time-Limited Ticket Offers**: Take advantage of flash sales and limited-time promotions.
- **Mobile-Friendly Ticket Management**: Access and manage tickets on any device.
- **Secure Payment Processing**: Integrated with Stripe for safe and quick transactions.
- **Digital Tickets with QR Codes**: Easy check-in at events using scannable QR codes.
- **Automatic Refunds**: Get instant refunds for cancelled events without hassle.

### For Event Organizers

- **Direct Payments via Stripe Connect**: Receive payouts directly to your account.
- **Real-time Sales Monitoring**: Track ticket sales and revenue as they happen.
- **Automated Queue Management**: Handle high-demand events with built-in queue controls.
- **Event Analytics and Tracking**: Gain insights into attendance, sales, and engagement.
- **Automatic Ticket Recycling**: Re-release unsold or returned tickets automatically.
- **Customizable Ticket Limits**: Set per-user purchase limits to prevent scalping.
- **Event Cancellation with Automatic Refunds**: Cancel events effortlessly with one-click refunds.
- **Bulk Refund Processing**: Manage refunds for multiple tickets at once.

### Technical Features

- **Real-time Updates**: Powered by Convex for instant synchronization across users.
- **Authentication**: Secure user management with Clerk.
- **Payment Processing**: Robust integration with Stripe Connect for seamless transactions.
- **Server-Side and Client-Side Rendering**: Optimized performance with Next.js.
- **Modern UI**: Built with Tailwind CSS and shadcn/ui for a clean, accessible design.
- **Responsive Design**: Works flawlessly on desktop, tablet, and mobile.
- **Rate Limiting**: Prevents abuse on queue joins and purchases.
- **Automated Fraud Prevention**: Built-in checks to ensure secure operations.
- **Toast Notifications**: Real-time feedback for user actions.

### UI/UX Features

- **Instant Feedback**: Toast notifications keep users informed of every action.
- **Consistent Design System**: Utilizes shadcn/ui for uniform, accessible components.
- **Fully Accessible**: Adheres to WCAG standards for inclusivity.
- **Animated Transitions**: Smooth animations enhance the user experience.
- **Loading States and Animations**: Clear indicators during data fetches.
- **Micro-Interactions**: Subtle animations for buttons and forms to boost engagement.

## Technologies Used

| Category         | Technology     | Purpose                             |
| ---------------- | -------------- | ----------------------------------- |
| Framework        | Next.js 14     | Full-stack web application          |
| Database/Backend | Convex         | Real-time database and queries      |
| Authentication   | Clerk          | User authentication and management  |
| Payments         | Stripe Connect | Secure payment processing           |
| Styling          | Tailwind CSS   | Utility-first CSS framework         |
| UI Components    | shadcn/ui      | Accessible, customizable components |

## Prerequisites

Before setting up the project, ensure you have the following:

- **Node.js**: Version 18 or higher
- **Package Manager**: npm or yarn
- **Stripe Account**: For payment processing (with Stripe Connect enabled)
- **Clerk Account**: For authentication
- **Convex Account**: For real-time database

## Installation

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/dipesh127/My-Tickit-App.git
   cd My-Tickit-App
   ```

2. **Install Dependencies**:

   ```bash
   npm install
   # Or if using yarn:
   # yarn install
   ```

3. **Set Up Environment Variables**:
   Create a `.env.local` file in the root directory and add the following:

   ```
   NEXT_PUBLIC_CONVEX_URL=your_convex_url
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_key
   CLERK_SECRET_KEY=your_clerk_secret
   STRIPE_SECRET_KEY=your_stripe_secret
   STRIPE_WEBHOOK_SECRET=your_webhook_secret
   NEXT_PUBLIC_APP_URL=http://localhost:3000
   ```

   Replace placeholders with your actual values from the respective services.

4. **Start the Development Server**:
   ```bash
   npm run dev
   ```
   The app will be available at `http://localhost:3000`.

## Setup Guides

### Setting Up Clerk

1. Sign up or log in to [Clerk](https://clerk.com).
2. Create a new application.
3. Configure your authentication providers (e.g., Email, Google).
4. Set up allowed redirect URLs (e.g., `http://localhost:3000` for development).
5. Copy the Publishable Key and Secret Key to your `.env.local` file.

### Setting Up Convex

1. Sign up or log in to [Convex](https://www.convex.dev).
2. Create a new project.
3. Install the Convex CLI globally:
   ```bash
   npm install -g convex
   ```
   Or use npx for one-time use.
4. Initialize Convex in your project:
   ```bash
   npx convex init
   ```
5. Copy the deployment URL from the Convex dashboard and add it to `.env.local` as `NEXT_PUBLIC_CONVEX_URL`.
6. Start the Convex development server (run in a separate terminal):
   ```bash
   npx convex dev
   ```
   Keep this running alongside your Next.js dev server.

### Setting Up Stripe

1. Sign up or log in to [Stripe](https://stripe.com).
2. Enable Stripe Connect in your dashboard.
3. Configure your payment settings and products.
4. Add your Secret Key and Webhook Secret to `.env.local`.

#### Setting Up Stripe Webhooks for Local Development

1. Install the Stripe CLI:
   - **macOS**: `brew install stripe/stripe-cli/stripe`
   - **Windows (with Scoop)**: `scoop install stripe`
   - **Linux**: Download from [Stripe CLI releases](https://github.com/stripe/stripe-cli/releases) and follow installation steps.
2. Log in to Stripe CLI:
   ```bash
   stripe login
   ```
3. Forward webhooks to your local server:
   ```bash
   stripe listen --forward-to localhost:3000/api/webhooks/stripe
   ```
4. Copy the generated webhook signing secret (starts with `whsec_`) and add it to `.env.local` as `STRIPE_WEBHOOK_SECRET`.
5. Keep the CLI running during development and testing.

## Usage

1. **Run the Servers**:

   - Start Next.js: `npm run dev`
   - Start Convex: `npx convex dev` (in another terminal)
   - Start Stripe webhook listener: `stripe listen --forward-to localhost:3000/api/webhooks/stripe` (in another terminal)

2. **Access the Application**:

   - Open `http://localhost:3000` in your browser.
   - Sign up or log in using Clerk authentication.

3. **For Attendees**:

   - Browse upcoming events.
   - Join queues for high-demand tickets.
   - Purchase tickets securely.

4. **For Organizers**:
   - Create and manage events.
   - Monitor sales and analytics in real-time.
   - Handle refunds and cancellations.

Refer to the in-app guides or documentation for advanced features.

## Project Structure

```
My-Tickit-App/
├── app/                 # Next.js app directory (pages, components, etc.)
├── components/          # Reusable UI components using shadcn/ui
├── lib/                 # Utilities, Convex queries, Stripe integrations
├── public/              # Static assets
├── .env.local           # Environment variables (gitignored)
├── next.config.js       # Next.js configuration
├── tailwind.config.js   # Tailwind CSS configuration
├── package.json         # Dependencies and scripts
└── README.md            # This file
```

(Note: Exact structure may vary; explore the repo for details.)

## Contributing

Contributions are welcome! To get started:

1. **Fork the Repository**: Create your own copy on GitHub.
2. **Create a Feature Branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make Your Changes**: Implement and test your feature.
4. **Commit Changes**:
   ```bash
   git commit -m "Add your feature description"
   ```
5. **Push to the Branch**:
   ```bash
   git push origin feature/your-feature-name
   ```
6. **Open a Pull Request**: Describe your changes and submit for review.

Please ensure code follows existing patterns, includes tests where applicable, and updates documentation.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details. (If no LICENSE file exists, consider adding one.)

## Contact

For questions, issues, or feedback:

- **Repository Issues**: Open a new issue on [GitHub](https://github.com/dipesh127/My-Tickit-App/issues).
- **Author**: Rajesh Chauhan – [GitHub Profile](https://github.com/dipesh127).

Thank you for your interest in My Tickit App! 🚀
