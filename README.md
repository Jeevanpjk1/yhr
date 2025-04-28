<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Space Exploration | Enormous</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #ff003d;
            --secondary-color: #00f7ff;
            --dark-bg: #0a0a0a;
            --text-light: #ffffff;
            --text-muted: #aaaaaa;
        }

        /* Base Styles */
        body {
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; /* Slightly refined font stack */
            background: var(--dark-bg);
            color: var(--text-light);
            overflow-x: hidden;
        }

        /* Header Navigation */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1rem 1.5rem; /* Adjusted padding */
            z-index: 1000;
            background: rgba(10, 10, 10, 0.8); /* Slightly less opaque */
            backdrop-filter: blur(15px); /* Stronger blur */
            border-bottom: 1px solid rgba(255, 255, 255, 0.1); /* Subtle separator */
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo h1 { /* Added logo class */
            margin: 0;
            font-size: 1.8rem;
            color: var(--primary-color);
            font-weight: bold;
            letter-spacing: 1px;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none; /* Remove default list style */
            padding: 0;
            margin: 0;
        }

        .nav-links a {
            color: var(--text-light);
            text-decoration: none;
            transition: color 0.3s ease, transform 0.3s ease;
            padding: 0.5rem 0;
            position: relative;
        }

        .nav-links a::after { /* Underline effect */
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 0;
            background-color: var(--primary-color);
            transition: width 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--primary-color);
            transform: translateY(-2px); /* Slight lift on hover */
        }
        .nav-links a:hover::after {
            width: 100%;
        }

        /* Hamburger Menu */
        .hamburger {
            display: none;
            cursor: pointer;
            font-size: 1.8rem;
            color: var(--text-light);
            z-index: 1001; /* Ensure it's above nav links on mobile */
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            position: relative;
            overflow: hidden;
            display: flex; /* Use flex for easier content centering */
            align-items: center; /* Vertically center */
            justify-content: flex-start; /* Align content left */
            padding-left: 5%;
        }

        /* Video Background - kept for layering possibility */
        #background-video {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            min-width: 100%;
            min-height: 100%;
            z-index: -2; /* Behind 3D canvas */
            opacity: 0.3; /* Make it subtle if 3D is primary */
            object-fit: cover;
        }

        /* 3D Planet Background Container */
        #planet-bg {
            position: fixed; /* Use fixed to keep it static */
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1; /* Behind content, above video */
            overflow: hidden;
        }

        .hero-content {
           /* position: absolute; */ /* No longer needed with flex */
           /* bottom: 20%; */ /* No longer needed */
           /* left: 5%; */ /* Handled by flex container padding */
            max-width: 650px;
            z-index: 1; /* Ensure it's above background */
            background: rgba(10, 10, 10, 0.5); /* Optional subtle background */
            padding: 2rem;
            border-radius: 10px;
            backdrop-filter: blur(5px);
        }

        .hero h1 {
            font-size: clamp(2.5rem, 6vw, 4.5rem); /* Responsive font size */
            margin: 0 0 1rem 0;
            line-height: 1.1;
            color: var(--text-light);
            text-shadow: 2px 2px 10px rgba(0,0,0,0.5);
        }
        .hero p { /* Added subtitle paragraph */
            font-size: 1.1rem;
            color: var(--text-muted);
            margin-bottom: 1.5rem;
        }

        /* Sections */
        .section {
            padding: 5rem 2rem; /* Increased padding */
            max-width: 1200px;
            margin: 0 auto;
            position: relative; /* Needed for z-index */
            z-index: 1; /* Ensure sections are above fixed background */
        }

        .section h2 {
            font-size: clamp(2rem, 5vw, 3rem); /* Responsive */
            color: var(--primary-color);
            margin-bottom: 3rem; /* Increased margin */
            text-align: center; /* Center section titles */
        }

        /* Technology Grid */
        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); /* Wider cards */
            gap: 2.5rem; /* Increased gap */
        }

        .tech-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px; /* Smoother corners */
            padding: 2rem;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            backdrop-filter: blur(5px); /* Glassmorphism touch */
        }

        .tech-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 30px rgba(0, 247, 255, 0.1); /* Secondary color glow */
        }

        .tech-card i {
            color: var(--secondary-color); /* Use secondary color for icons */
            margin-bottom: 1rem;
        }
        .tech-card h3 {
            color: var(--text-light);
            margin-bottom: 0.5rem;
        }
         .tech-card p {
            color: var(--text-muted);
            font-size: 0.95rem;
         }

        /* Contact Form */
        .contact-form {
            max-width: 700px; /* Wider form */
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05); /* Form background */
            padding: 2.5rem;
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        input, textarea {
            width: 100%;
            padding: 1rem; /* More padding */
            background: rgba(0,0,0,0.3); /* Darker input background */
            border: 1px solid rgba(255, 255, 255, 0.2); /* Subtle border */
            color: var(--text-light);
            border-radius: 8px; /* Rounded inputs */
            font-size: 1rem;
            box-sizing: border-box; /* Include padding in width */
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }
        input:focus, textarea:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 15px rgba(255, 0, 61, 0.3); /* Glow on focus */
        }

        textarea {
            resize: vertical; /* Allow vertical resize only */
        }

        /* General Button Style */
        .btn {
            background-color: var(--primary-color);
            color: var(--text-light);
            border: none;
            padding: 1rem 2rem;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 50px; /* Pill shape */
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .btn:hover {
            background-color: #e00036; /* Darker shade on hover */
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255, 0, 61, 0.4);
        }
        .btn:active {
             transform: translateY(-1px);
             box-shadow: 0 2px 10px rgba(255, 0, 61, 0.3);
        }


        /* Footer */
        footer {
            background: #000;
            padding: 3rem 2rem; /* More padding */
            text-align: center;
            position: relative;
            z-index: 1;
            border-top: 1px solid rgba(255, 255, 255, 0.1); /* Subtle separator */
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-bottom: 1.5rem; /* More space */
        }

        .social-links a {
            color: var(--text-muted); /* Muted color */
            font-size: 1.8rem; /* Larger icons */
            transition: color 0.3s ease, transform 0.3s ease;
        }

        .social-links a:hover {
            color: var(--primary-color);
            transform: scale(1.2); /* Scale up on hover */
        }
        footer p {
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        /* Scroll Animation Styles */
        .hidden {
            opacity: 0;
            transform: translateY(50px);
            transition: opacity 0.8s ease-out, transform 0.8s ease-out;
            will-change: opacity, transform; /* Performance hint */
        }
        .visible {
            opacity: 1;
            transform: translateY(0);
        }


        /* Mobile Styles */
        @media (max-width: 768px) {
             header {
                padding: 1rem;
                background: rgba(10, 10, 10, 0.95); /* More solid on mobile */
             }
            .nav-links {
                display: none; /* Hide by default */
                position: absolute;
                top: 100%;
                left: 0;
                right: 0;
                background: var(--dark-bg);
                padding: 2rem 1rem; /* More padding */
                flex-direction: column;
                text-align: center;
                border-top: 1px solid rgba(255, 255, 255, 0.1);
                gap: 1.5rem; /* More space between links */
            }

            .nav-links.active {
                display: flex; /* Show when active */
            }

            .hamburger {
                display: block; /* Show hamburger */
            }

            .hero {
                padding-left: 2rem; /* Adjust padding */
                padding-right: 2rem;
                 justify-content: center; /* Center content on mobile */
                 text-align: center;
            }
            .hero-content {
                padding: 1.5rem;
            }

            .section {
                padding: 3rem 1rem;
            }
             .tech-grid {
                grid-template-columns: 1fr; /* Stack cards on mobile */
             }
             .contact-form {
                 padding: 1.5rem;
             }
        }
    </style>
</head>
<body>
<!-- 3D Planet Background -->
<div id="planet-bg"></div>

<!-- Header -->
<header>
    <nav>
        <div class="logo"><h1>ENORMOUS</h1></div>
        <ul class="nav-links"> <!-- Changed to ul for semantics -->
            <li><a href="index.html">Home</a></li>
            <li><a href="galaxies.html">Galaxies</a></li>
            <li><a href="universe.html">Universe</a></li>
            <li><a href="#missions">Missions</a></li>
            <li><a href="#technology">Technology</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        <div class="hamburger">☰</div>
    </nav>
</header>

<!-- Hero Section with Self-Hosted Video -->
<section class="hero">
    <!-- Video can act as a fallback or subtle layer -->
    <video autoplay muted loop playsinline id="background-video">
        <!-- ===== IMPORTANT: REPLACE 'your-video.mp4' with your actual video file ===== -->
        <source src="your-video.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <div class="hero-content">
        <h1>Pioneering The Cosmos</h1>
        <p>Join Enormous on our journey to unravel the mysteries of the universe and push the boundaries of exploration.</p>
        <a href="#about" class="btn">Learn More</a>
    </div>
</section>

<!-- Missions Section (Example - Add Content) -->
<section id="missions" class="section hidden">
    <h2>Current Missions</h2>
    <p style="text-align: center; color: var(--text-muted); margin-bottom: 3rem;">Exploring the frontiers of space, one mission at a time.</p>
    <!-- Add mission details here -->
    <div style="text-align:center; padding: 2rem; background: rgba(255,255,255,0.05); border-radius: 10px;">Mission content placeholder</div>
</section>

<!-- Technology Section -->
<section id="technology" class="section hidden">
    <h2>Our Technology</h2>
    <div class="tech-grid">
        <div class="tech-card hidden">
            <i class="fas fa-rocket fa-3x"></i>
            <h3>Advanced Propulsion</h3>
            <p>Developing next-generation ion thrusters and fusion concepts for faster, efficient deep space travel.</p>
        </div>
        <div class="tech-card hidden">
            <i class="fas fa-satellite-dish fa-3x"></i> <!-- Changed icon -->
            <h3>Quantum Comms</h3>
            <p>High-throughput, secure communication networks spanning interplanetary distances using quantum entanglement.</p>
        </div>
        <div class="tech-card hidden">
            <i class="fas fa-microscope fa-3x"></i>
            <h3>Exo-Life Detection</h3>
            <p>Sophisticated sensor suites designed to detect biosignatures on distant exoplanets and moons.</p>
        </div>
        <div class="tech-card hidden">
            <i class="fas fa-cubes fa-3x"></i>
            <h3>Modular Habitats</h3>
            <p>Expandable and self-sustaining habitat modules for long-duration missions and off-world settlements.</p>
        </div>
    </div>
</section>

<!-- About Section -->
<section id="about" class="section hidden">
    <h2>About Enormous</h2>
    <p style="text-align: center; color: var(--text-muted); max-width: 800px; margin: 0 auto 2rem auto;">
        Founded with a vision for humanity's future among the stars, Enormous Space Technologies is dedicated to making interstellar exploration a reality. We combine cutting-edge engineering with sustainable practices to develop technologies that are both groundbreaking and responsible. Our multidisciplinary team of scientists, engineers, and visionaries works tirelessly to overcome the challenges of space travel and unlock the secrets held within the cosmos.
    </p>
</section>

<!-- Contact Section -->
<section id="contact" class="section hidden">
    <h2>Get In Touch</h2>
    <p style="text-align: center; color: var(--text-muted); margin-bottom: 2rem;">Have questions, ideas, or partnership inquiries? Reach out to us.</p>
    <form class="contact-form" id="contactForm"> <!-- Added ID for potential JS -->
        <div class="form-group">
            <input type="text" id="name" placeholder="Your Name" required>
        </div>
        <div class="form-group">
            <input type="email" id="email" placeholder="Your Email" required>
        </div>
        <div class="form-group">
            <textarea id="message" rows="6" placeholder="Your Message" required></textarea> <!-- Increased rows -->
        </div>
        <div style="text-align: center;"> <!-- Center button -->
            <button type="submit" class="btn">Send Message</button>
        </div>
    </form>
</section>

<!-- Footer -->
<footer>
    <div class="social-links">
        <a href="#" aria-label="Twitter"><i class="fab fa-twitter"></i></a>
        <a href="#" aria-label="Facebook"><i class="fab fa-facebook-f"></i></a> <!-- Use -f for brand icon -->
        <a href="#" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
        <a href="#" aria-label="LinkedIn"><i class="fab fa-linkedin-in"></i></a> <!-- Use -in for brand icon -->
    </div>
    <p>© 2025 Enormous Space Technologies. All rights reserved.</p>
</footer>

<!-- === JAVASCRIPT === -->
<script>
    // --- Hamburger Menu Toggle ---
    const hamburger = document.querySelector('.hamburger');
    const navLinks = document.querySelector('.nav-links');

    hamburger.addEventListener('click', () => {
        navLinks.classList.toggle('active');
        // Optional: Change hamburger icon to 'X' when open
        hamburger.textContent = navLinks.classList.contains('active') ? '✕' : '☰';
    });

    // Close menu when a link is clicked
    document.querySelectorAll('.nav-links a').forEach(link => {
        link.addEventListener('click', () => {
            if (navLinks.classList.contains('active')) {
                 navLinks.classList.remove('active');
                 hamburger.textContent = '☰';
            }
        });
    });

    // --- Smooth Scroll ---
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function(e) {
            const href = this.getAttribute('href');
            // Ensure it's a valid internal link and not just '#'
            if (href && href.startsWith('#') && href.length > 1) {
                e.preventDefault();
                const targetElement = document.querySelector(href);
                if (targetElement) {
                    // Calculate offset needed for fixed header
                    const headerOffset = document.querySelector('header').offsetHeight + 20; // Add extra space
                    const elementPosition = targetElement.getBoundingClientRect().top;
                    const offsetPosition = elementPosition + window.pageYOffset - headerOffset;

                    window.scrollTo({
                        top: offsetPosition,
                        behavior: 'smooth'
                    });
                }
            }
            // Close mobile nav if open after clicking
            if (navLinks.classList.contains('active')) {
                 navLinks.classList.remove('active');
                 hamburger.textContent = '☰';
            }
        });
    });

     // --- Scroll Reveal Animation ---
     const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('visible');
                // Optional: Stop observing once visible to save resources
                // observer.unobserve(entry.target);
            } else {
                 // Optional: Remove class if you want animation to replay on scroll up
                 // entry.target.classList.remove('visible');
            }
        });
    }, {
        rootMargin: '0px', // Default
        threshold: 0.1 // Trigger when 10% of the element is visible
    });

    // Observe all elements with the 'hidden' class
    document.querySelectorAll('.hidden').forEach(el => observer.observe(el));

    // --- Contact Form (Basic Console Log) ---
    // For a real site, you'd use Fetch API to send data to a server/backend service
    const contactForm = document.getElementById('contactForm');
    if (contactForm) {
        contactForm.addEventListener('submit', (e) => {
            e.preventDefault(); // Prevent default page reload
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const message = document.getElementById('message').value;
            console.log('Form Submitted:', { name, email, message });
            alert('Thank you for your message! (Check console for data)'); // User feedback
            contactForm.reset(); // Clear the form
        });
    }

</script>

<!-- Three.js Library -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<!-- Optional: OrbitControls for manual rotation/zoom -->
<!-- <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js"></script> -->

<script>
    // --- Advanced Three.js Background ---
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 2000); // Increased far plane
    const renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true }); // Alpha true for transparent background
    renderer.setSize(window.innerWidth, window.innerHeight);
    document.getElementById('planet-bg').appendChild(renderer.domElement);

    const textureLoader = new THREE.TextureLoader();

    // --- Planet ---
    // ===== IMPORTANT: Replace these placeholder URLs with actual high-res texture URLs =====
    const earthTexture = textureLoader.load('https://example.com/path/to/earth_day_high_res.jpg'); // Color map
    const earthBumpMap = textureLoader.load('https://example.com/path/to/earth_bump_map.jpg'); // Bump map for mountains/terrain
    const earthSpecularMap = textureLoader.load('https://example.com/path/to/earth_specular_map.jpg'); // Specular map for water shininess

    const planetGeometry = new THREE.SphereGeometry(2.5, 64, 64); // Slightly larger planet
    const planetMaterial = new THREE.MeshStandardMaterial({
        map: earthTexture,
        bumpMap: earthBumpMap,
        bumpScale: 0.05, // Adjust bump intensity
        roughnessMap: earthSpecularMap, // Using specular as roughness (invert if needed)
        metalness: 0.4, // Adjust metalness
        roughness: 0.7 // Adjust roughness
    });
    const planet = new THREE.Mesh(planetGeometry, planetMaterial);
    scene.add(planet);

    // --- Clouds ---
    const cloudTexture = textureLoader.load('https://example.com/path/to/earth_clouds_high_res.png'); // Use PNG with transparency
    const cloudGeometry = new THREE.SphereGeometry(2.55, 64, 64); // Slightly larger than planet
    const cloudMaterial = new THREE.MeshPhongMaterial({ // Phong for transparency/specular highlights
        map: cloudTexture,
        transparent: true,
        opacity: 0.8, // Adjust cloud opacity
        depthWrite: false // Prevent rendering issues with transparency
    });
    const clouds = new THREE.Mesh(cloudGeometry, cloudMaterial);
    scene.add(clouds);


    // --- Starfield ---
    const starGeometry = new THREE.BufferGeometry();
    const starCount = 10000;
    const posArray = new Float32Array(starCount * 3); // x, y, z for each star

    for(let i = 0; i < starCount * 3; i++) {
        // Assign random positions within a large sphere radius
        posArray[i] = (Math.random() - 0.5) * 1000; // Spread stars out further
    }

    starGeometry.setAttribute('position', new THREE.BufferAttribute(posArray, 3));
    const starMaterial = new THREE.PointsMaterial({
        size: 0.25, // Adjust star size
        color: 0xffffff,
        transparent: true,
        opacity: 0.8,
        blending: THREE.AdditiveBlending // Brighter where stars overlap
    });
    const starMesh = new THREE.Points(starGeometry, starMaterial);
    scene.add(starMesh);


    // --- Lighting ---
    const ambientLight = new THREE.AmbientLight(0xffffff, 0.2); // Soft ambient light
    scene.add(ambientLight);

    const directionalLight = new THREE.DirectionalLight(0xffffff, 1.0); // Simulates sunlight
    directionalLight.position.set(5, 3, 5); // Position the light source
    scene.add(directionalLight);

    // --- Camera Position ---
    camera.position.z = 6;


    // --- Optional: Orbit Controls ---
    // Uncomment the script tag above and this section for manual controls
    // const controls = new THREE.OrbitControls(camera, renderer.domElement);
    // controls.enableDamping = true; // Smooths movement
    // controls.dampingFactor = 0.05;
    // controls.screenSpacePanning = false;
    // controls.minDistance = 4; // Prevent zooming too close
    // controls.maxDistance = 20; // Prevent zooming too far

    // --- Mouse Interaction (Subtle Parallax) ---
    let mouseX = 0, mouseY = 0;
    let targetX = 0, targetY = 0;
    const windowHalfX = window.innerWidth / 2;
    const windowHalfY = window.innerHeight / 2;

    function onDocumentMouseMove(event) {
        mouseX = (event.clientX - windowHalfX);
        mouseY = (event.clientY - windowHalfY);
    }
    document.addEventListener('mousemove', onDocumentMouseMove);

    // --- Scroll Interaction ---
    let lastScrollY = window.pageYOffset;
    function updateCameraOnScroll() {
        const scrollY = window.pageYOffset;
        // Example: Rotate planet based on scroll direction/amount
        planet.rotation.y += (scrollY - lastScrollY) * 0.0005;
        clouds.rotation.y += (scrollY - lastScrollY) * 0.0003; // Slightly different cloud rotation
        // Example: Move camera slightly Z based on scroll
        // camera.position.z = 6 + scrollY * 0.001;
        lastScrollY = scrollY;
    }
    window.addEventListener('scroll', updateCameraOnScroll);


    // --- Animation Loop ---
    const clock = new THREE.Clock(); // For consistent animation speed

    function animate() {
        requestAnimationFrame(animate);
        const elapsedTime = clock.getElapsedTime();

        // Subtle continuous rotation
        planet.rotation.y += 0.0005;
        clouds.rotation.y += 0.0008; // Clouds rotate slightly faster

        // Starfield subtle movement (optional)
        // starMesh.rotation.y -= 0.0001;

        // Update mouse parallax effect smoothly
        targetX = mouseX * 0.001;
        targetY = mouseY * 0.001;
        const parallaxFactor = 0.05; // How much smoothing
        scene.rotation.y += parallaxFactor * (targetX - scene.rotation.y);
        scene.rotation.x += parallaxFactor * (targetY - scene.rotation.x);


        // Update OrbitControls if enabled
        // controls.update();

        renderer.render(scene, camera);
    }
    animate();


    // --- Responsive Resize ---
    window.addEventListener('resize', () => {
        // Update camera aspect ratio
        camera.aspect = window.innerWidth / window.innerHeight;
        camera.updateProjectionMatrix();

        // Update renderer size
        renderer.setSize(window.innerWidth, window.innerHeight);

        // Update mouse parallax calculation reference points
        windowHalfX = window.innerWidth / 2;
        windowHalfY = window.innerHeight / 2;
    });

</script>

</body>
</html>
