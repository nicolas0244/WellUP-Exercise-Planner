# ExercisePlan - Exercise Planning & Management App

Welcome to **ExercisePlan**, your personal workout planning and management companion! This app helps you track your exercise routines, plan weekly workouts, and connect with an AI assistant powered by n8n.

## Features

✨ **Comprehensive Workout Management**
- Plan and schedule workouts by type (Cardio, Strength, Flexibility, Sports, Other)
- Track duration, calories burned, and intensity levels
- Add personal notes to each workout
- View workouts organized by week

📊 **Weekly Dashboard**
- Real-time workout statistics (workouts this week, total minutes, calories burned)
- Weekly calendar overview with workout indicators
- Exercise type breakdown showing your activity distribution
- Quick stats at a glance

💬 **AI Assistant Integration**
- Chat with an AI-powered workout assistant
- Get personalized workout recommendations
- Ask questions about your exercise routine
- Connected to n8n for intelligent responses

📱 **Mobile-First Design**
- Fully responsive interface
- Touch-friendly buttons and controls
- Fast and smooth interactions
- Dark mode support

## Getting Started

### 1. Open the App
Simply open `index.html` in your web browser. No installation required!

### 2. Create Your First Workout
- Click "Get Started" on the welcome screen
- Click the "+ Add Workout" button
- Fill in your workout details:
  - **Name**: Give your workout a title (e.g., "Morning Run")
  - **Type**: Choose from Cardio, Strength, Flexibility, Sports, or Other
  - **Date & Time**: Set when your workout is scheduled
  - **Duration**: How many minutes will you exercise?
  - **Intensity**: Light, Moderate, or Intense
  - **Estimated Calories**: How many calories will you burn?
  - **Notes**: Optional details about your workout

### 3. Track Your Workouts
- Check off completed workouts
- View your weekly progress on the calendar
- Monitor your total minutes and calories burned
- See your exercise type distribution

### 4. Connect to N8N Chat (Optional)

To enable the AI assistant chat feature:

#### Step 1: Set Up N8N Webhook
1. Go to your n8n instance (e.g., `https://your-n8n-domain.com`)
2. Create a new workflow
3. Add a **Webhook** trigger node with:
   - Method: `POST`
   - Path: `/exercise-chat` (or your preferred path)
   - Authentication: Disable for now (or add basic auth)

#### Step 2: Add AI Logic
4. After the webhook, add your preferred AI node:
   - **OpenAI Node** for ChatGPT integration
   - **Anthropic Node** for Claude
   - **Local LLM** for self-hosted solutions

5. Configure your AI node to:
   - Use the incoming message from the webhook
   - Include context about the user's workouts
   - Generate helpful responses about exercise

#### Step 3: Update Webhook URL
6. Copy your webhook URL from n8n
7. Open `js/app.js` in your code editor
8. Find this line (around line 20):
   ```javascript
   N8N_WEBHOOK_URL: 'https://your-n8n-instance.com/webhook/exercise-chat',
   ```
9. Replace with your actual webhook URL:
   ```javascript
   N8N_WEBHOOK_URL: 'https://your-n8n.com/webhook/exercise-chat',
   ```

#### Step 4: Test the Chat
10. Reload your app in the browser
11. Click the 💬 chat button in the header
12. Type a message and send
13. Your n8n workflow should respond!

### Example N8N Workflow

Here's a simple example workflow configuration:

1. **Webhook Trigger** → Receives POST with: message, workouts, stats, timestamp
2. **OpenAI Node** → Takes the message and generates a response
3. **Return Response** → Sends back the AI response

Sample Webhook Response Format:
```json
{
  "reply": "Great! You've had 3 workouts this week with a total of 240 minutes. Keep up the excellent work! Consider adding a flexibility session to balance out your routine.",
  "message": "Great! You've had 3 workouts this week with a total of 240 minutes. Keep up the excellent work! Consider adding a flexibility session to balance out your routine."
}
```

## Data Storage

All your workouts are automatically saved to your browser's **LocalStorage**. This means:
- ✅ Your data persists between sessions
- ✅ No server needed - everything stays on your device
- ⚠️ Data is local to your browser (not synced across devices)
- 💡 Clear browser data will remove your workouts

## Tips for Best Results

1. **Be Consistent**: Log your workouts regularly for better tracking
2. **Set Realistic Goals**: Start with manageable workout schedules
3. **Use Notes**: Add details about how you felt or modifications you made
4. **Review Weekly**: Check your calendar to spot patterns and plan better
5. **Chat with AI**: Ask the assistant for personalized advice based on your routine

## Troubleshooting

### Chat not responding?
- Check that your n8n webhook URL is correct in `js/app.js`
- Verify your n8n workflow is active and running
- Check browser console (F12 → Console tab) for error messages

### Workouts not saving?
- Make sure LocalStorage is enabled in your browser
- Check that you're not in private/incognito mode
- Try clearing cache and reloading

### UI looks strange?
- Make sure all files are in the correct folder structure:
  ```
  PolyPulse/
  ├── index.html
  ├── css/
  │   └── styles.css
  ├── js/
  │   └── app.js
  └── assets/ (if needed)
  ```

## Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Files Overview

- **index.html**: Main app structure and UI
- **css/styles.css**: All styling with responsive design
- **js/app.js**: App logic, storage management, and n8n integration

## Privacy & Security

- All workout data is stored locally on your device
- No data is sent to any server unless you enable the chat feature
- Chat messages are sent to your n8n instance (ensure you trust it)
- For production use, add authentication to your n8n webhook

## Future Enhancements

Planned features:
- Export workouts to PDF/CSV
- Social sharing of achievements
- Advanced analytics and insights
- Custom workout templates
- Integration with fitness trackers
- Mobile app version

## Support & Feedback

Have questions or suggestions? Feel free to modify and extend the app!

---

**Stay active, stay healthy! 💪**
