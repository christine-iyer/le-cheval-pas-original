# Working on the file. 


# Cocktail Database Application

A modern web application for managing cocktail recipes with a MongoDB database backend and a beautiful, responsive frontend.

## Features

- **CRUD Operations**: Create, Read, Update, and Delete cocktail recipes
- **Search Functionality**: Search cocktails by name, ingredients, recipe, or comments
- **Modern UI**: Beautiful, responsive design with smooth animations
- **MongoDB Database**: Persistent data storage with automatic initialization
- **RESTful API**: Clean API endpoints for all operations
- **Form Validation**: Client-side and server-side validation
- **Real-time Updates**: Instant UI updates after operations

## Tech Stack

- **Backend**: Node.js, Express.js, MongoDB, Mongoose
- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Styling**: Custom CSS with responsive design
- **Icons**: Font Awesome
- **Fonts**: Inter (Google Fonts)

## Installation & Setup

### For New Developers (Git Workflow)

1. **Clone the repository**:
   ```bash
   git clone https://github.com/christine-iyer/le-cheval-pas-original.git
   cd le-cheval-pas-original
   ```

2. **Create your feature branch**:
   ```bash
   git checkout -b your-feature-branch-name
   ```

3. **Install dependencies**:
   ```bash
   npm install
   ```

4. **Set up MongoDB**:
   - **Option A - Local MongoDB**: 
     ```bash
     # Install MongoDB (macOS with Homebrew)
     brew install mongodb-community
     
     # Start MongoDB service
     brew services start mongodb-community
     ```
   
   - **Option B - MongoDB Atlas** (Cloud):
     - Create a `.env` file in the project root
     - Add your connection string: `MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/mongoLaura`

5. **Start the application**:
   ```bash
   npm start        # Production mode (port 4000)
   npm run dev      # Development mode with nodemon
   ```

6. **Open your browser** and navigate to:
   ```
   http://localhost:4000
   ```

### Development Workflow

1. **Make your changes** on your feature branch
2. **Test locally** to ensure everything works
3. **Commit your changes**:
   ```bash
   git add .
   git commit -m "Descriptive commit message"
   ```
4. **Push your branch**:
   ```bash
   git push origin your-feature-branch-name
   ```
5. **Create a Pull Request** on GitHub for code review

## Database Configuration

### MongoDB Setup
- **Default Local**: `mongodb://localhost:27017/mongoLaura`
- **Production**: Set `MONGO_URI` environment variable in `.env` file
- **Auto-initialization**: Imports default cocktails from `allCocktails.js` on first run

### Environment Variables
Create a `.env` file in the project root (optional for local development):
```
MONGO_URI=mongodb://localhost:27017/mongoLaura
PORT=4000
CLOUDINARY_CLOUD_NAME=dqjhgnivi
CLOUDINARY_UPLOAD_PRESET=cocktail_uploads
```

## Database Schema (Mongoose)

The application uses a MongoDB collection `cocktails` with the following schema:

```js
{
  theCock:      { type: String, required: true },
  theIngredients: { type: String, required: true },
  theRecipe:    { type: String, required: true },
  theJpeg:      { type: String },
  theComment:   { type: String },
  created_at:   { type: Date, default: Date.now }
}
```

## API Endpoints

- `GET /api/cocktails` - Get all cocktails
- `GET /api/cocktails/:id` - Get a specific cocktail
- `POST /api/cocktails` - Create a new cocktail
- `PUT /api/cocktails/:id` - Update an existing cocktail
- `DELETE /api/cocktails/:id` - Delete a cocktail
- `POST /api/upload` - Upload an image (returns file path)

## Usage

### Adding a New Cocktail

1. Fill out the form on the left side of the application
2. Required fields: Cocktail Name, Ingredients, Recipe
3. Optional fields: Image URL, Comments
4. Click "Save Cocktail"

### Editing a Cocktail

1. Click the "Edit" button on any cocktail card
2. The form will be populated with the cocktail's data
3. Make your changes
4. Click "Save Cocktail" or "Cancel" to abort

### Deleting a Cocktail

1. Click the "Delete" button on any cocktail card
2. Confirm the deletion in the modal dialog

### Searching Cocktails

1. Use the search box in the top-right of the cocktails section
2. Search works across cocktail names, ingredients, recipes, and comments
3. Results update in real-time as you type

## File Structure

```
mongoLauraCloudinary/
├── server.js              # Main server file with Express and MongoDB/Mongoose
├── package.json           # Node.js dependencies and scripts
├── allCocktails.js        # Original cocktail data (imported automatically)
├── cocktails.db           # Legacy SQLite database (unused)
├── cocktails.sqbpro       # SQLite Pro project file
├── .env                   # Environment variables (create this file)
├── public/                # Frontend files
│   ├── index.html         # Main HTML page
│   ├── style.css          # CSS styling
│   ├── script.js          # Frontend JavaScript
│   └── uploads/           # Local image upload directory
└── README.md              # This file
```

## Initial Data

The application automatically imports the initial cocktails from `allCocktails.js` when the database is first created:

- **Hot Rüuski**: Vodka, Peat Moss, Pine Tar
- **Cold Soul**: Vodka, Ice, Herbs

## Development

### Adding New Features

1. **Backend**: Modify `server.js` to add new API endpoints
2. **Frontend**: Update `public/script.js` for new functionality
3. **Styling**: Modify `public/style.css` for UI changes

### Database Modifications

To modify the database schema:

1. Update the Mongoose schema in `server.js`
2. Remove or update existing documents as needed
3. Restart the application

## Troubleshooting

### Common Issues

1. **Port already in use**: Stop the process using port 4000 or change the port in `server.js`
2. **MongoDB connection errors**: 
   - Make sure MongoDB is running locally: `brew services start mongodb-community`
   - Or update your `MONGO_URI` for Atlas/cloud in `.env` file
3. **CORS issues**: The server includes CORS middleware for cross-origin requests
4. **Image upload issues**: Check `public/uploads/` directory permissions
5. **Cloudinary errors**: Verify upload preset `cocktail_uploads` is configured

### Development Commands
```bash
# Check if MongoDB is running
brew services list | grep mongodb

# Check database connection
mongosh mongoLaura --eval "db.cocktails.find()"

# Clear uploaded images
rm -rf public/uploads/*

# Install nodemon for development
npm install -g nodemon
```

### Logs

Check the console output for:

- Database connection status
- API request logs
- Error messages

## Browser Compatibility

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Contributing

### Git Workflow
1. **Fork the repository** (if external contributor)
2. **Clone and create feature branch**:
   ```bash
   git clone https://github.com/christine-iyer/le-cheval-pas-original.git
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** following the coding patterns in the codebase
4. **Test thoroughly** - run both `npm start` and `npm run dev`
5. **Commit with descriptive messages**:
   ```bash
   git add .
   git commit -m "feat: add new cocktail search functionality"
   ```
6. **Push and create Pull Request**:
   ```bash
   git push origin feature/your-feature-name
   ```

### Code Style
- Follow existing patterns in the codebase
- Use MongoDB with Mongoose (not SQLite)
- Maintain the unique field naming convention (`theCock`, `theIngredients`, etc.)
- Test both local file upload and Cloudinary integration

---

**Enjoy managing your cocktail recipes! 🍸**
