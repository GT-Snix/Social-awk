# 📱 Social-awk - A Social Media Application

A full-stack social media platform built with FastAPI backend and Streamlit frontend, featuring user authentication, media uploads, and a real-time feed.

## 🎯 Features

- **User Authentication**: Secure JWT-based authentication with email and password
- **User Registration**: Easy sign-up process
- **Media Sharing**: Upload images and videos with captions
- **Social Feed**: View posts from all users in chronological order
- **Post Management**: Delete your own posts
- **Media Hosting**: Integrated with ImageKit for reliable media storage and transformation
- **Text Overlays**: Captions displayed as overlays on media

## 🏗️ Architecture

### Backend
- **Framework**: FastAPI
- **Database**: SQLite with async support (aiosqlite)
- **Authentication**: FastAPI-Users with JWT tokens
- **Media Storage**: ImageKit
- **ORM**: SQLAlchemy with async support

### Frontend
- **Framework**: Streamlit
- **API Client**: Requests library

## 📋 Prerequisites

- Python 3.13+
- UV package manager (recommended) or pip
- ImageKit account (for media hosting)
- OpenAI API key (optional, for future features)

## 🚀 Getting Started

### Installation

1. **Clone the repository**
   ```bash
   cd negma
   ```

2. **Install dependencies**
   ```bash
   uv sync
   ```
   Or with pip:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   
   Create a `.env` file in the `negma` directory:
   ```env
   IMAGEKIT_PRIVATE_KEY=your_private_key
   IMAGEKIT_PUBLIC_KEY=your_public_key
   IMAGEKIT_URL=https://ik.imagekit.io/your_endpoint
   OPENAI_API_KEY=your_openai_key (optional)
   ```

4. **Run the backend**
   ```bash
   python main.py
   ```
   The API will be available at `http://localhost:8000`

5. **In a new terminal, run the frontend**
   ```bash
   streamlit run frontend.py
   ```
   Open your browser to the Streamlit URL (typically `http://localhost:8501`)

## 📁 Project Structure

```
negma/
├── app/
│   ├── app.py          # FastAPI application and routes
│   ├── db.py           # Database models and session management
│   ├── users.py        # Authentication and user management
│   ├── images.py       # ImageKit integration
│   └── schemas.py      # Pydantic schemas
├── frontend.py         # Streamlit UI
├── main.py            # Application entry point
├── pyproject.toml     # Project dependencies
└── .env               # Environment variables (local)
```

## 🔑 API Endpoints

### Authentication
- `POST /auth/register` - Register a new user
- `POST /auth/jwt/login` - Login with email and password
- `POST /auth/forgot-password` - Request password reset
- `POST /auth/verify` - Verify email

### Users
- `GET /users/me` - Get current user info
- `GET /users/{user_id}` - Get user by ID
- `PATCH /users/{user_id}` - Update user profile

### Posts
- `POST /upload` - Upload media and create a post
- `GET /feed` - Get all posts in feed
- `DELETE /posts/{post_id}` - Delete a post

## 🔐 Security Notes

- ⚠️ Change the `SECRET` in `app/users.py` before deploying to production
- Store API keys securely in environment variables (never commit `.env` files)
- JWT tokens expire after 1 hour (configurable in `app/users.py`)

## 🛠️ Development

### Running Tests
```bash
pytest
```

### Database
- Database file: `test.db`
- Automatically created on first run
- Uses SQLite with async support for development

## 📦 Dependencies

See `pyproject.toml` for full dependency list, including:
- FastAPI & Uvicorn
- SQLModel & SQLAlchemy
- FastAPI-Users
- ImageKit
- Streamlit
- Python-dotenv

## 🐛 Troubleshooting

**Connection refused on localhost:8000**
- Ensure backend is running: `python main.py`

**ImageKit upload errors**
- Verify your ImageKit credentials in `.env`
- Check that public/private keys are correctly set

**Database locked errors**
- Delete `test.db` and restart to reset database

## 📝 License

This project is part of the Degraft workspace.
