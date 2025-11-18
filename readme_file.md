# Full Stack Portfolio Application

A complete Flask-based web application featuring a modern landing page and comprehensive admin panel for managing projects, client testimonials, contact forms, and newsletter subscriptions.

## 🌟 Features

### Landing Page
- **Hero Section**: Eye-catching introduction with call-to-action
- **Projects Showcase**: Dynamic display of all projects with images and descriptions
- **Client Testimonials**: Rotating display of happy client reviews
- **Contact Form**: Fully functional form for visitor inquiries
- **Newsletter Subscription**: Email collection for marketing campaigns
- **Responsive Design**: Mobile-first approach using Bootstrap 5

### Admin Panel
- **🔐 Secure Authentication**: Login system to protect admin area
- **Dashboard**: Real-time statistics and quick actions
- **Project Management**: Add/delete projects with automatic image cropping
- **Client Management**: Add/delete client testimonials
- **Contact Form Viewer**: Review all submitted inquiries
- **Newsletter Manager**: Track all email subscribers
- **Professional UI**: Clean, modern interface with intuitive navigation
- **Session Management**: Secure logout functionality

### Bonus Features
- ✅ **Image Cropping**: Automatic resizing to 450x350 pixels
- ✅ **SQLAlchemy Integration**: Robust database management
- ✅ **Form Validation**: Client and server-side validation
- ✅ **Flash Messages**: User-friendly success/error notifications
- ✅ **Modern Design**: Gradient backgrounds and smooth animations

## 🛠️ Technology Stack

- **Backend**: Flask 3.0
- **Database**: SQLAlchemy (SQLite/MySQL/PostgreSQL compatible)
- **Frontend**: HTML5, CSS3, Bootstrap 5
- **Image Processing**: Pillow (PIL)
- **Icons**: Font Awesome 6

## 📋 Requirements

```
Flask==3.0.0
Flask-SQLAlchemy==3.1.1
Flask-Migrate==4.0.5
Werkzeug==3.0.1
Pillow==10.1.0
SQLAlchemy==2.0.23
```

## 🚀 Quick Start

### Local Development

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd your-project-folder
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Initialize database**
   ```bash
   python
   >>> from app import app, db
   >>> with app.app_context():
   ...     db.create_all()
   >>> exit()
   ```

5. **Run the application**
   ```bash
   python app.py
   ```

6. **Access the application**
   - Landing Page: http://localhost:5000
   - Admin Panel: http://localhost:5000/admin

## 📁 Project Structure

```
project/
│
├── app.py                      # Main application file
├── requirements.txt            # Python dependencies
├── README.md                   # Documentation
│
├── templates/
│   ├── base.html              # Base template
│   ├── index.html             # Landing page
│   │
│   └── admin/
│       ├── base_admin.html    # Admin base template
│       ├── dashboard.html     # Dashboard
│       ├── projects.html      # Projects listing
│       ├── add_project.html   # Add project form
│       ├── clients.html       # Clients listing
│       ├── add_client.html    # Add client form
│       ├── contacts.html      # Contact submissions
│       └── newsletters.html   # Newsletter subscribers
│
├── static/
│   └── uploads/
│       ├── projects/          # Project images
│       └── clients/           # Client images
│
└── instance/
    └── flipr_project.db       # SQLite database (auto-generated)
```

## 💻 Usage Guide

### Adding a Project

1. Navigate to Admin Panel > Projects
2. Click "Add New Project"
3. Fill in:
   - Project Name
   - Description
   - Upload Image (will be auto-cropped to 450x350)
4. Click "Save Project"

### Adding a Client Testimonial

1. Navigate to Admin Panel > Clients
2. Click "Add New Client"
3. Fill in:
   - Client Name
   - Designation (e.g., CEO, Designer)
   - Testimonial/Description
   - Upload Photo (will be auto-cropped)
4. Click "Save Client"

### Viewing Contact Forms

1. Navigate to Admin Panel > Contact Forms
2. View all submitted inquiries
3. Contact details include: Name, Email, Mobile, City
4. Delete processed inquiries

### Managing Newsletter Subscribers

1. Navigate to Admin Panel > Newsletter
2. View all email subscribers
3. Export emails for marketing campaigns
4. Delete unsubscribed users

## 🌐 Deployment

### PythonAnywhere (Recommended)

See detailed deployment guide in `DEPLOYMENT_GUIDE.md`

**Quick steps:**
1. Create account at pythonanywhere.com
2. Upload code via Git or manual upload
3. Set up virtual environment
4. Configure WSGI file
5. Set static file mappings
6. Reload web app

### Other Platforms

#### Heroku
```bash
# Install Heroku CLI
heroku create your-app-name
git push heroku main
heroku run python -c "from app import app, db; db.create_all()"
```

#### AWS, Azure, Google Cloud
- Use Gunicorn or uWSGI as WSGI server
- Configure nginx for static files
- Set up PostgreSQL/MySQL database
- Use environment variables for configuration

## 🔒 Security Considerations

1. **Change Secret Key**: Update `SECRET_KEY` in production
   ```python
   import secrets
   app.config['SECRET_KEY'] = secrets.token_hex(32)
   ```

2. **Environment Variables**: Use for sensitive data
   ```python
   import os
   app.config['SECRET_KEY'] = os.environ.get('SECRET_KEY')
   ```

3. **Admin Authentication**: Implement login system (not included in basic version)

4. **Input Validation**: All forms include validation

5. **File Upload Security**: Only images accepted, proper sanitization

## 🎨 Customization

### Changing Colors

Edit CSS variables in `templates/base.html`:

```css
:root {
    --primary-color: #2563eb;
    --secondary-color: #1e40af;
    --accent-color: #3b82f6;
}
```

### Logo and Branding

Replace "MyPortfolio" in `templates/base.html`:

```html
<a class="navbar-brand" href="{{ url_for('index') }}">
    <i class="fas fa-rocket me-2"></i>Your Brand Name
</a>
```

### Database Configuration

For MySQL:
```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://user:pass@localhost/dbname'
```

For PostgreSQL:
```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://user:pass@localhost/dbname'
```

## 🐛 Troubleshooting

### Database Errors
```bash
# Reset database
rm instance/flipr_project.db
python
>>> from app import app, db
>>> with app.app_context():
...     db.create_all()
```

### Image Upload Issues
```bash
# Ensure upload folders exist
mkdir -p static/uploads/projects
mkdir -p static/uploads/clients
chmod -R 755 static/uploads
```

### Module Not Found
```bash
pip install -r requirements.txt --force-reinstall
```

## 📸 Screenshots

### Landing Page
- Modern hero section with gradient background
- Project cards with hover effects
- Client testimonial cards
- Elegant contact form
- Newsletter subscription section

### Admin Panel
- Clean dashboard with statistics
- Easy-to-use forms
- Comprehensive data tables
- Professional sidebar navigation

## 🔄 Future Enhancements

- [ ] Admin authentication system
- [ ] Edit functionality for projects/clients
- [ ] Image gallery for projects
- [ ] Email notifications for contact forms
- [ ] Search and filter functionality
- [ ] Pagination for large datasets
- [ ] Export data to CSV/Excel
- [ ] Dark mode toggle
- [ ] Multi-language support
- [ ] Analytics dashboard

## 📝 License

This project is open source and available under the MIT License.

## 👤 Author

Created for full-stack development demonstration

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## ⭐ Show Your Support

Give a ⭐️ if this project helped you!

## 📞 Support

For issues and questions:
- Create an issue in the repository
- Contact: your-email@example.com

---

**Note**: This application is designed for educational and demonstration purposes. For production use, implement proper authentication, security measures, and testing.