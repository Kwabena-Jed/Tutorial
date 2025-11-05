Perfect 👏 you’ve done an excellent job so far — you now have a professional **two-layer navbar** structure (top info bar + main navbar).

Now let’s take the next step:
You want the **main navbar to be centered** with **equal spacing (margins)** on both sides — so it doesn’t stretch edge-to-edge across the screen.

We’ll achieve this using a **container** and **max-width layout technique**, which is a standard best practice for web design.

---

## ✅ Updated HTML

*(No structure change — we’ll only wrap the navbar sections in a container for centering.)*

```html
<!-- ===== Top Info Bar ===== -->
<div class="topbar">
  <div class="container">
    <div class="topbar-left">
      <span><i class="fa fa-mobile"></i> Mobile: +233 246 692 516</span>
      <span><i class="fa fa-envelope"></i> teamgracesc@gmail.com</span>
    </div>
    <div class="topbar-right">
      <a href="#"><i class="fa-brands fa-x-twitter"></i></a>
      <a href="#"><i class="fa-brands fa-facebook-f"></i></a>
      <a href="#"><i class="fa-brands fa-tiktok"></i></a>
      <a href="#"><i class="fa-brands fa-instagram"></i></a>
      <a href="#"><i class="fa-brands fa-youtube"></i></a>
    </div>
  </div>
</div>

<!-- ===== Main Navigation Bar ===== -->
<div class="nav-wrapper">
  <div class="topnav">
    <div class="nav-left">
      <a href="login.html" class="logo">Welcome Page</a>
    </div>

    <div class="nav-center">
      <a href="index.html" class="active">Home</a>
      <a href="about.html">About</a>
      <a href="contact.html">Contact</a>
      <a href="#">Services</a>
    </div>

    <div class="nav-right">
      <form class="search-form">
        <input type="text" placeholder="Search..." />
        <button type="submit"><i class="fa fa-search"></i></button>
      </form>
    </div>

    <a href="javascript:void(0);" class="icon" onclick="toggleMenu()">
      <i class="fa fa-bars"></i>
    </a>
  </div>
</div>
```

---

## ✅ Updated CSS

We’ll introduce a `.container` and `.nav-wrapper` class for layout control.

```css
/* General reset */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

/* ===== Shared Container ===== */
.container {
  max-width: 1200px;
  margin: 0 auto;       /* centers horizontally */
  padding: 0 20px;      /* adds space from screen edges */
}

/* ===== Top Info Bar ===== */
.topbar {
  background-color: #f7f7f7;
  border-bottom: 1px solid #ddd;
  font-size: 14px;
  color: #333;
}

.topbar .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 6px 0;
  flex-wrap: wrap;
}

.topbar-left span {
  margin-right: 15px;
  display: inline-flex;
  align-items: center;
  gap: 5px;
}

.topbar-right a {
  color: #162938;
  margin-left: 10px;
  text-decoration: none;
  font-size: 16px;
  transition: color 0.3s ease;
}

.topbar-right a:hover {
  color: #00bcd4;
}

/* ===== Main Nav Wrapper ===== */
.nav-wrapper {
  background-color: #162938;
}

/* ===== Main Navigation Bar ===== */
.topnav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-top: 2px solid rgba(255, 255, 255, 0.2); /* faint border line */
  padding: 12px 0;
  position: relative;
  max-width: 1200px; /* centers navbar contents */
  margin: 0 auto;
  width: 100%;
  flex-wrap: wrap;
}

/* Left section */
.nav-left .logo {
  color: white;
  text-decoration: none;
  font-weight: 600;
  font-size: 18px;
}

/* Center section (links) */
.nav-center {
  display: flex;
  gap: 25px;
}

.nav-center a {
  color: white;
  text-decoration: none;
  font-size: 17px;
  padding: 8px 10px;
  transition: color 0.3s ease;
}

.nav-center a:hover {
  color: #00bcd4;
}

.nav-center a.active {
  color: #00bcd4;
  font-weight: 600;
}

/* Right section (search bar) */
.nav-right {
  display: flex;
  align-items: center;
}

.search-form {
  display: flex;
  align-items: center;
  background: white;
  border-radius: 25px;
  overflow: hidden;
}

.search-form input {
  border: none;
  outline: none;
  padding: 8px 12px;
  font-size: 14px;
  width: 140px;
}

.search-form button {
  border: none;
  background-color: #00bcd4;
  color: white;
  padding: 8px 12px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.search-form button:hover {
  background-color: #0097a7;
}

/* Hamburger icon */
.icon {
  display: none;
  color: white;
  font-size: 22px;
  cursor: pointer;
  position: absolute;
  right: 20px;
  top: 15px;
}

/* ===== Responsive Design ===== */
@media screen and (max-width: 768px) {
  .topbar .container {
    flex-direction: column;
    text-align: center;
    font-size: 13px;
  }

  .topbar-left span {
    display: block;
    margin-bottom: 4px;
  }

  .topnav {
    flex-direction: column;
    align-items: flex-start;
    padding: 10px 20px;
  }

  .nav-center,
  .nav-right {
    display: none;
    flex-direction: column;
    width: 100%;
    background-color: #162938;
    text-align: center;
    padding: 10px 0;
  }

  .topnav.responsive .nav-center,
  .topnav.responsive .nav-right {
    display: flex;
  }

  .icon {
    display: block;
  }

  .search-form {
    justify-content: center;
    width: 80%;
    margin: 0 auto;
  }
}
```

---

## ✅ JavaScript

(unchanged)

```html
<script>
function toggleMenu() {
  const nav = document.querySelector('.topnav');
  nav.classList.toggle('responsive');
}
</script>
```

---

## ✅ Font Awesome (for icons)

Add this in your `<head>` if you haven’t already:

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
```

---

### 💡 What’s New

* Added `.container` to **center content and add left/right spacing**.
* `.nav-wrapper` ensures the navbar background still spans the full width.
* Navbar content (Welcome Page, links, search bar) now sits beautifully **in the middle** of the page.
* Responsive design remains perfectly functional.

---

Would you like me to make the navbar **slightly sticky** (fixed at top when scrolling)? It’s a great touch for user navigation.
