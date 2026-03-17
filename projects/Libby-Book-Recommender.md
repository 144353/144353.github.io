
An interactive React-based AI librarian application that helps users discover Chinese books through natural conversation. The app uses Google Gemini function calling to understand reader preferences, search the NLB Libby catalog, and present tailored book recommendations in a warm bilingual interface.

The project combines conversational AI, dynamic recommendation logic, pinyin support, and a visually rich reading-focused UI to create a more human and engaging book discovery experience.

---

## Features

- Conversational AI librarian powered by Google Gemini
- Personalized book recommendation flow based on user interests and reading mood
- Integration with the NLB Libby catalog
- Function calling workflow for controlled recommendation generation
- Chinese text display with pinyin annotations
- Bilingual responses in Simplified Chinese and English
- Context-aware suggestion chips for follow-up prompts
- Animated chat and recommendation UI
- Direct links to search recommended books on Libby

---

## Project Workflow

The application follows this general flow:

1. The user chats with the AI librarian about reading interests, mood, or preferred genres.
2. The AI gathers enough context through natural conversation.
3. When ready, the model calls the `searchLibby` function to search for relevant books.
4. Matching books are processed and filtered.
5. The model selects the best three options and calls `showRecommendations`.
6. The UI displays the recommendations in a separate recommendation panel.
7. The user can continue the conversation, ask for more details, or request a different set of books.

---

## Technical Implementation

### Core Technologies

- React for the frontend application
- TypeScript for type safety
- Google Gemini API via `@google/genai`
- Tailwind CSS for utility-first styling
- Motion for animations
- Lucide React for icons
- `pinyin-pro` for Chinese pinyin rendering

---

## AI Behavior Design

The Gemini system instruction is carefully designed to make the AI behave like a warm and thoughtful librarian. It is instructed to:

- communicate in Simplified Chinese
- provide English translation below each Chinese reply
- ask only one question at a time
- understand the user’s mood and reading habits before recommending
- avoid recommending books until enough context is gathered
- use the Libby search tool before showing recommendations
- recommend only books that were actually found

This prompt design is central to the quality of the user experience.

---

## Example User Experience

A typical user journey might look like this:

1. The app greets the user as an AI librarian.
2. The user says they feel stressed and want something light to read.
3. The AI asks one follow-up question about reading preferences.
4. After enough context, the AI searches Libby for matching Chinese books.
5. Three personalized recommendations appear in the recommendation panel.
6. The user clicks through to Libby or continues chatting for more options.

---

## Strengths of the Project

- Blends conversational AI with a real library catalog
- Uses function calling to make recommendations more reliable
- Creates a thoughtful, reader-centered interaction model
- Supports Chinese readers with pinyin and bilingual explanations
- Presents recommendations in a polished and engaging interface

---

## Current Limitations

- Recommendation quality depends on the external Libby catalog response
- Search is only as strong as the simplified query cleaning logic
- No authentication or user account system
- Recommendations are session-based and not persisted
- The app currently relies on prompt engineering rather than a separate ranking model

---

## Future Improvements

- Save reading history and user preferences
- Add book cover thumbnails from live catalog data
- Support more advanced recommendation filtering
- Include borrowing availability or library branch availability
- Add multilingual toggle options
- Persist conversations across sessions
- Introduce user profiles and personalized recommendation memory

---

## Libraries and Tools

- React
- TypeScript
- `@google/genai`
- `lucide-react`
- `motion`
- `pinyin-pro`
- Tailwind CSS
- OverDrive / Libby API

---

## Data Sources and Services

- Google Gemini API for conversational reasoning and function calling
- NLB Libby / OverDrive API for searchable Chinese book catalog data

---

## Conclusion

This project is a strong example of how conversational AI can be combined with real library infrastructure to create a more personal and accessible book discovery experience. Rather than functioning as a generic chatbot, the application is designed around the role of a thoughtful librarian, using structured tool calls and UI design to make book recommendations feel grounded, relevant, and human-centered.