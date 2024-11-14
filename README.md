Code Documentation: Structure, AI Tools, and Security Considerations
1. Code Structure Outline
HTML (index.html):
Container: Includes elements to start speech input and select the target language for translation.
Buttons:
startButton: Starts the speech input process.
speakButton: Speaks the translated text (shown only after a successful translation).
Transcripts Section:
originalText: Displays the recognized speech in its original language.
translatedText: Displays the translated text.
Language Selection:
Dropdown menu with supported languages.
JavaScript (script.js):
Variables: Stores elements related to the UI and speech recognition/translation process.
Speech Recognition:
Uses Google Cloud’s Speech-to-Text API (webkitSpeechRecognition) for speech recognition.
recognition.onresult: Extracts text from recognized speech and sends it for translation.
recognition.onerror: Handles any errors in speech recognition.
DeepL Translation:
translateText function: Sends the recognized text to DeepL's API for translation to the selected language.
Speech Synthesis:
speakButton: Uses the Web Speech API (SpeechSynthesisUtterance) to read aloud the translated text in the selected language.
CSS (style.css):
Global Styling: Basic layout, colours, and text styling for a consistent UI.
Container: Styles the main container for alignment and layout adjustments.
Button and Select Styling: Consistent colours, padding, and hover effects.
Responsive Design: Media queries to adjust layout on smaller screens.

<br>

2. AI Tools Used
Google Cloud Speech-to-Text (Speech Recognition):
Enables real-time speech-to-text transcription.
The code uses webkitSpeechRecognition, enabling speech recognition directly in the browser.
DeepL Translation API:
Translates recognized text into the target language.
The translateText function sends a POST request to DeepL's translation service.
Web Speech API (Speech Synthesis):
Provides speech synthesis to read aloud the translated text in the specified language.
Adjusts the pronunciation based on the selected language, enhancing accuracy for each language's unique sounds.

<br>

3. Security Considerations
API Key Management:
DeepL API Key: Ensure that the API key is stored securely and not hard-coded directly in client-side code. A safer approach would be to use a server-side proxy or environment variables to retrieve the API key dynamically.
Exposed API Key Risk: Having the API key directly in JavaScript makes it accessible to anyone viewing the page source, risking abuse. Moving the translation logic to a server or backend can mitigate this issue.
CORS Policies:
If moving API calls to a backend, configure appropriate Cross-Origin Resource Sharing (CORS) policies to restrict unauthorised access to API endpoints.
User Data Privacy:
Speech input data is sensitive. Ensure that the audio data and resulting text are handled securely and not stored unnecessarily.
The app should provide clear information to users on how their data is processed (e.g., a privacy notice).
Error Handling and Feedback:
Include informative error messages for network issues, translation errors, and API-related failures.
Implement user feedback (e.g., error messages for unsupported browsers) to enhance the user experience and security.
Cross-Browser Compatibility:
webkitSpeechRecognition is only supported in Chrome-based browsers. For unsupported browsers, inform users or provide alternatives.
Rate Limiting and API Quotas:
If the app usage scales, enforce rate limiting and monitor API quotas to avoid exceeding free-tier limits, especially on the DeepL API.
