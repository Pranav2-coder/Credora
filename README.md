<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pranav | Advanced Portfolio</title>
  <style>
    :root {
      --primary: #8e2de2;
      --secondary: #4a00e0;
      --bg: #0f0f0f;
      --text: #ffffff;
      --accent: #ff6ec4;
    }* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  scroll-behavior: smooth;
}

body {
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(to right, #0f0f0f, #1a1a1a);
  color: var(--text);
  line-height: 1.6;
}

header {
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  padding: 3rem 1rem;
  text-align: center;
  position: relative;
}

header h1 {
  font-size: 3rem;
  margin-bottom: 0.5rem;
}

header p {
  font-size: 1.2rem;
  color: #e0e0e0;
}

nav {
  display: flex;
  justify-content: center;
  gap: 2rem;
  background: #111;
  padding: 1rem;
  position: sticky;
  top: 0;
  z-index: 1000;
}

nav a {
  color: var(--text);
  text-decoration: none;
  font-weight: bold;
  transition: 0.3s;
}

nav a:hover {
  color: var(--accent);
}

section {
  padding: 6rem 2rem;
  max-width: 1000px;
  margin: auto;
}

section h2 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: var(--accent);
  position: relative;
}

section h2::after {
  content: '';
  width: 50px;
  height: 4px;
  background: var(--accent);
  display: block;
  margin-top: 0.5rem;
}

.projects .project {
  background: #1e1e1e;
  margin: 2rem 0;
  padding: 2rem;
  border-left: 5px solid var(--accent);
  border-radius: 12px;
  box-shadow: 0 0 15px rgba(255, 110, 196, 0.3);
  transition: transform 0.3s;
}

.projects .project:hover {
  transform: translateY(-5px);
}

.project h3 {
  margin-bottom: 0.5rem;
}

.project p {
  color: #ccc;
}

#contact p {
  margin: 0.5rem 0;
}

footer {
  background: #111;
  color: #888;
  text-align: center;
  padding: 3rem 1rem;
}

@media (max-width: 768px) {
  header h1 {
    font-size: 2.2rem;
  }

  section h2 {
    font-size: 2rem;
  }
}

  </style>
</head>
<body>
  <header>
    <h1>Pranav's Portfolio</h1>
    <p>Engineer | Developer | Innovator</p>
  </header>  <nav>
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </nav>  <section id="home">
    <h2>Welcome</h2>
    <p>Welcome to my portfolio. I’m Pranav, passionate about building intelligent IoT systems, modern web applications, and scalable cloud solutions. My goal is to blend creativity and code to solve real-world problems.</p>
  </section>  <section id="about">
    <h2>About Me</h2>
    <p>I am currently pursuing engineering and have a deep interest in the intersection of software and hardware. Whether it’s a smart road divider or a full-stack learning platform, I enjoy the challenge of making things that matter.</p>
  </section>  <section id="projects" class="projects">
    <h2>Projects</h2><div class="project">
  <h3>Smart Road Divider</h3>
  <p>IoT-based dynamic lane management system using sensors and microcontrollers for real-time traffic optimization and road safety improvements.</p>
</div>

<div class="project">
  <h3>Startup Website</h3>
  <p>Developed a fast, responsive website for a startup with animated components, custom branding, and mobile-first design using HTML5, CSS3, and JS.</p>
</div>

<div class="project">
  <h3>E-Learning Website</h3>
  <p>Created an online education platform with interactive course listings, smooth navigation, and responsive layout for all screen sizes.</p>
</div>

  </section>  <section id="contact">
    <h2>Contact</h2>
    <p>Email: paratepranav29@gmail.com</p>
    <p>LinkedIn: https://www.linkedin.com/in/pranav-parate-6a4255365?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app </p>
    <p>GitHub:https://github.com/Pranav2-coder </p>
  </section>  <footer>
    <p> Designed with passion and precision.</p>
  </footer>
</body>
</html> 