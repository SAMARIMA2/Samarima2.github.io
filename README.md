
// Directory Structure
// project-root/
// ├── server.js
// ├── views/
// │   ├── index.ejs
// │   ├── about.ejs
// │   ├── contact.ejs
// ├── public/
// │   ├── css/
// │   │   └── styles.css
// ├── package.json

// server.js
const express = require('express');
const path = require('path');
const app = express();

// Set view engine to EJS
app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

// Serve static files
app.use(express.static(path.join(__dirname, 'public')));

// Routes
app.get('/', (req, res) => {
  res.render('index', {
    title: 'Megalinks Consolidated Investment Ltd',
    instagramLink: 'https://www.instagram.com/megalinks_consolidated/profilecard/?igsh=MWpiNmk3ejZtcHl3bQ=='
  });
});

app.get('/about', (req, res) => {
  res.render('about', { title: 'About Us' });
});

app.get('/contact', (req, res) => {
  res.render('contact', {
    title: 'Contact Us',
    contactInfo: {
      email: 'info@megalinks.com',
      phone: '+234-XXX-XXXX-XXX',
      address: 'Crown Luxury City Asaba, Nigeria.'
    }
  });
});

// Start server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});

/* index.ejs */
<!-- views/index.ejs -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><%= title %></title>
    <link rel="stylesheet" href="/css/styles.css">
</head>
<body>
    <header>
        <h1>Welcome to Megalinks Consolidated Investment Ltd</h1>
        <p>Building Wealth, Unlocking Potential in Real Estate Networking</p>
    </header>
    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/contact">Contact</a>
    </nav>
    <section>
        <p>Follow us on Instagram: <a href="<%= instagramLink %>" target="_blank">Megalinks Consolidated</a></p>
    </section>
    <footer>
        <p>&copy; 2024 Megalinks Consolidated Investment Ltd</p>
    </footer>
</body>
</html>

/* about.ejs */
<!-- views/about.ejs -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><%= title %></title>
    <link rel="stylesheet" href="/css/styles.css">
</head>
<body>
    <header>
        <h1>About Us</h1>
    </header>
    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/contact">Contact</a>
    </nav>
    <section>
        <p>About Megalinks Consolidated Investment Ltd...</p>
    </section>
    <footer>
        <p>&copy; 2024 Megalinks Consolidated Investment Ltd</p>
    </footer>
</body>
</html>

/* contact.ejs */
<!-- views/contact.ejs -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><%= title %></title>
    <link rel="stylesheet" href="/css/styles.css">
</head>
<body>
    <header>
        <h1>Contact Us</h1>
    </header>
    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/contact">Contact</a>
    </nav>
    <section>
        <p>Email: <%= contactInfo.email %></p>
        <p>Phone: <%= contactInfo.phone %></p>
        <p>Address: <%= contactInfo.address %></p>
    </section>
    <footer>
        <p>&copy; 2024 Megalinks Consolidated Investment Ltd</p>
    </footer>
</body>
</html>

/* styles.css */
/* public/css/styles.css */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #0056a8;
    color: #fff;
}
header {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 1rem 0;
}
nav {
    background: #f4f4f4;
    padding: 0.5rem 0;
    text-align: center;
}
nav a {
    margin: 0 15px;
    color: #333;
    text-decoration: none;
}
footer {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 1rem 0;
}
