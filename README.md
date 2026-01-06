# Social Media Sentiment Tracker

A powerful web application for tracking and analyzing brand sentiment across social media platforms. Built with React, TypeScript, and Tailwind CSS, this tool helps businesses monitor public perception, manage reputation, and make data-driven decisions.

## Features

### 🎯 Core Capabilities

- **Real-Time Monitoring**: Track brand mentions, keywords, and hashtags across multiple social platforms
- **Sentiment Classification**: Automatically categorize mentions as positive, negative, or neutral using NLP
- **Multi-Platform Support**: Integration structure for X (Twitter), Facebook, and Instagram
- **Interactive Dashboard**: Centralized interface with customizable sentiment metrics visualization
- **Trend Analysis**: Display sentiment data over time to identify patterns
- **Alerts & Notifications**: Automated alerts for sentiment changes and volume spikes
- **Reporting & Export**: Generate and export comprehensive reports in CSV and JSON formats

### 📊 Dashboard Components

- **Sentiment Overview Cards**: Real-time statistics with positive, negative, and neutral breakdowns
- **Trend Charts**: Interactive line charts showing sentiment changes over time
- **Recent Mentions Feed**: Live feed of social media mentions with sentiment badges
- **Alert Panel**: Configurable alerts for sentiment drops and volume spikes

### ⚙️ Configuration

- Custom keyword and hashtag tracking
- Platform selection (Twitter, Facebook, Instagram)
- Alert threshold configuration
- Customizable monitoring preferences

## Technology Stack

- **Frontend Framework**: React 18 with TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **Charts**: Recharts
- **Routing**: React Router
- **HTTP Client**: Axios
- **Date Utilities**: date-fns

## Project Structure

```
social-media-sentiment-tracker/
├── src/
│   ├── components/          # Reusable UI components
│   │   ├── AlertsPanel.tsx
│   │   ├── MentionList.tsx
│   │   ├── SentimentChart.tsx
│   │   └── SentimentStatsCard.tsx
│   ├── pages/              # Page components
│   │   ├── Dashboard.tsx
│   │   └── Settings.tsx
│   ├── services/           # API and business logic
│   │   ├── sentimentService.ts
│   │   └── socialMediaService.ts
│   ├── types/              # TypeScript type definitions
│   │   └── index.ts
│   ├── utils/              # Utility functions
│   │   ├── exportUtils.ts
│   │   └── mockData.ts
│   ├── App.tsx            # Main app component
│   ├── main.tsx           # Entry point
│   └── index.css          # Global styles
├── public/                # Static assets
├── index.html            # HTML template
├── package.json          # Dependencies
├── tsconfig.json         # TypeScript config
├── tailwind.config.js    # Tailwind CSS config
├── vite.config.ts        # Vite config
└── README.md            # This file
```

## Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm, yarn, or pnpm

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd social-media-sentiment-tracker
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

### Build for Production

```bash
npm run build
```

The production-ready files will be in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## API Integration Guide

The application currently uses mock data for demonstration purposes. To integrate with real social media APIs:

### Twitter/X Integration

1. Sign up for Twitter API access at https://developer.twitter.com/
2. Obtain your API credentials (API Key, API Secret, Bearer Token)
3. Update `src/services/socialMediaService.ts`:

```typescript
async fetchTwitterMentions(keywords: string[]): Promise<Mention[]> {
  const response = await axios.get('https://api.twitter.com/2/tweets/search/recent', {
    params: { 
      query: keywords.join(' OR '),
      max_results: 100 
    },
    headers: { 
      Authorization: `Bearer ${process.env.VITE_TWITTER_BEARER_TOKEN}` 
    }
  });
  // Process and return mentions
}
```

### Facebook Integration

1. Create a Facebook App at https://developers.facebook.com/
2. Obtain an Access Token
3. Update the `fetchFacebookMentions` method with Facebook Graph API calls

### Instagram Integration

1. Set up Instagram Basic Display API or Instagram Graph API
2. Obtain necessary credentials
3. Update the `fetchInstagramMentions` method accordingly

### Environment Variables

Create a `.env` file in the root directory:

```env
VITE_TWITTER_BEARER_TOKEN=your_twitter_token
VITE_FACEBOOK_ACCESS_TOKEN=your_facebook_token
VITE_INSTAGRAM_ACCESS_TOKEN=your_instagram_token
VITE_API_BASE_URL=your_backend_api_url
```

## Sentiment Analysis

The application includes a basic keyword-based sentiment analyzer in `src/services/sentimentService.ts`. For production use, consider integrating advanced NLP services:

### Recommended NLP Services

1. **Google Cloud Natural Language API**
   - Comprehensive sentiment analysis
   - Entity recognition
   - Multilingual support

2. **Azure Text Analytics**
   - Sentiment scoring
   - Key phrase extraction
   - Language detection

3. **AWS Comprehend**
   - Real-time sentiment analysis
   - Entity and key phrase detection
   - Custom classification

4. **Hugging Face Transformers**
   - Self-hosted models
   - Fine-tunable for specific domains
   - No API costs

Example integration with Google Cloud:

```typescript
import { LanguageServiceClient } from '@google-cloud/language';

const client = new LanguageServiceClient();

async analyzeSentiment(text: string) {
  const document = {
    content: text,
    type: 'PLAIN_TEXT',
  };
  
  const [result] = await client.analyzeSentiment({ document });
  const sentiment = result.documentSentiment;
  
  return {
    score: sentiment.score,
    magnitude: sentiment.magnitude
  };
}
```

## Customization

### Adding New Social Platforms

1. Update the `Platform` type in `src/types/index.ts`
2. Add a new fetch method in `src/services/socialMediaService.ts`
3. Update the platform selection UI in `src/pages/Settings.tsx`

### Customizing Charts

Modify `src/components/SentimentChart.tsx` to customize chart appearance, add new visualizations, or change data presentation.

### Adding Export Formats

Extend `src/utils/exportUtils.ts` to add support for PDF, Excel, or other export formats.

## Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

### Code Style

The project uses TypeScript strict mode and follows React best practices. Tailwind CSS is used for styling with a consistent design system.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License.

## Support

For issues, questions, or contributions, please open an issue on the GitHub repository.

## Roadmap

- [ ] Real-time WebSocket updates
- [ ] Advanced NLP integration
- [ ] Multi-language support
- [ ] Competitor comparison analytics
- [ ] Email notification system
- [ ] Mobile responsive improvements
- [ ] Dark mode support
- [ ] Advanced filtering and search
- [ ] Historical data analysis
- [ ] Custom report templates

## Acknowledgments

- Built with [Vite](https://vitejs.dev/)
- UI components styled with [Tailwind CSS](https://tailwindcss.com/)
- Charts powered by [Recharts](https://recharts.org/)
- Icons and design inspiration from modern SaaS applications
