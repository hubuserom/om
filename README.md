# om
this is my first Git repository
first project repository .index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Music School of Delhi</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Reset and Base Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #87CEEB; /* Sky Blue */
            --secondary: #000000; /* Black */
            --accent: #FFFFFF; /* White */
        }

        body {
            color: var(--secondary);
            overflow-x: hidden;
            position: relative;
        }

        #musicCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: #000;
        }

        /* Navigation */
        nav {
            background-color: rgba(135, 206, 235, 0.9);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--secondary);
            text-decoration: none;
            display: flex;
            align-items: center;
        }

        .logo i {
            margin-right: 0.5rem;
            color: var(--secondary);
        }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li {
            margin-left: 2rem;
        }

        .nav-links a {
            color: var(--secondary);
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1rem;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-links a:hover {
            color: var(--accent);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 0;
            background-color: var(--accent);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .hamburger {
            display: none;
            cursor: pointer;
        }

        .hamburger div {
            width: 25px;
            height: 3px;
            background-color: var(--secondary);
            margin: 5px;
            transition: all 0.3s ease;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: rgba(0, 0, 0, 0.5);
            color: var(--accent);
            padding: 80px 2rem 2rem;
            position: relative;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(rgba(135, 206, 235, 0.3), rgba(135, 206, 235, 0.3));
            z-index: -1;
        }

        .hero-content {
            max-width: 1200px;
            margin: 0 auto;
            animation: fadeIn 1.5s ease;
            position: relative;
            z-index: 1;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        .hero p.intro {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            line-height: 1.6;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            text-shadow: 1px 1px 2px rgba(182, 166, 166, 0.5);
        }

        /* Video Carousel - Updated Styles */
        .video-carousel {
            width: 100%;
            position: relative;
            overflow: hidden;
            height: 0;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            background: #000;
        }

        .video-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 300%;
            height: 100%;
            display: flex;
            transition: transform 0.5s ease;
        }

        .video-item {
            position: relative;
            width: 33.333%;
            height: 100%;
            overflow: hidden;
        }

        .video-item iframe {
            width: 100%;
            height: 100%;
            border: none;
            opacity: 0.7;
            transition: opacity 0.3s ease;
        }

        .video-item.active iframe {
            opacity: 1;
        }

        .video-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .video-item.active .video-overlay {
            opacity: 0;
            pointer-events: none;
        }

        .play-icon {
            font-size: 4rem;
            color: #FF0000;
            opacity: 0.8;
            transition: all 0.3s ease;
            margin-bottom: 15px;
        }

        .watch-youtube {
            color: white;
            background: rgba(0, 0, 0, 0.7);
            padding: 8px 15px;
            border-radius: 4px;
            font-size: 0.9rem;
            text-decoration: none;
            position: absolute;
            bottom: 20px;
            right: 20px;
            z-index: 30;
        }

        .carousel-controls {
            position: absolute;
            top: 50%;
            width: 100%;
            display: flex;
            justify-content: space-between;
            transform: translateY(-50%);
            z-index: 10;
        }

        .carousel-btn {
            background: rgba(255, 255, 255, 0.7);
            color: #333;
            border: none;
            padding: 1rem;
            cursor: pointer;
            font-size: 1.5rem;
            transition: all 0.3s ease;
            z-index: 20;
        }

        .carousel-btn:hover {
            background: rgba(255, 255, 255, 0.9);
        }

        .carousel-dots {
            position: absolute;
            bottom: 20px;
            left: 0;
            right: 0;
            display: flex;
            justify-content: center;
            z-index: 10;
        }

        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.5);
            margin: 0 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .dot.active {
            background: #FF0000;
            transform: scale(1.2);
        }

        /* Rotating Circles Section */
        .levels-container {
            display: flex;
            justify-content: center;
            gap: 3rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
        }

        .level-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 0 15px;
        }

        .level-circle {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: rgba(0, 0, 0, 0.3);
            border: 2px solid var(--primary);
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            animation: rotate 15s linear infinite;
            box-shadow: 0 0 15px rgba(135, 206, 235, 0.5);
        }

        .level-circle img {
            width: 60px;
            height: 60px;
            object-fit: contain;
            animation: rotateReverse 15s linear infinite;
        }

        .level-label {
            text-align: center;
            margin-top: 15px;
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--accent);
            text-shadow: 0 0 5px rgba(0,0,0,0.7);
        }

        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes rotateReverse {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(-360deg); }
        }

        /* About Section */
        .about-section {
            background-color: rgba(65, 62, 62, 0.5);
            padding: 2rem;
            border-radius: 10px;
            margin: 2rem auto;
            max-width: 1000px;
            text-align: left;
            color: var(--accent);
        }

        .about-section p {
            line-height: 1.8;
            margin-bottom: 1rem;
            text-align: justify;
            text-shadow: 0 0 5px rgba(0,0,0,0.3);
        }

        /* Button */
        .btn {
            display: inline-block;
            background-color: var(--secondary);
            color: var(--accent);
            padding: 0.8rem 2rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            border: 2px solid var(--secondary);
            margin-bottom: 2rem;
        }

        .btn:hover {
            background-color: transparent;
            color: var(--secondary);
            background-color: var(--accent);
        }

        /* Footer */
        footer {
            background-color: rgba(0, 0, 0, 0.8);
            color: var(--accent);
            padding: 3rem 2rem;
            text-align: center;
            position: relative;
        }

        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
            z-index: 1;
        }

        .social-icons {
            margin-bottom: 1.5rem;
        }

        .social-icons a {
            color: var(--accent);
            font-size: 1.5rem;
            margin: 0 0.5rem;
            transition: color 0.3s ease;
        }

        .social-icons a:hover {
            color: var(--primary);
        }

        .footer-links {
            display: flex;
            list-style: none;
            margin-bottom: 1.5rem;
            flex-wrap: wrap;
            justify-content: center;
        }

        .footer-links li {
            margin: 0 1rem;
        }

        .footer-links a {
            color: var(--accent);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: var(--primary);
        }

        .copyright {
            font-size: 0.9rem;
            opacity: 0.8;
        }

        /* Animations */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive Design */
        @media screen and (max-width: 768px) {
            .nav-links {
                position: absolute;
                right: 0;
                top: 80px;
                background-color: rgba(135, 206, 235, 0.95);
                width: 100%;
                flex-direction: column;
                align-items: center;
                padding: 1rem 0;
                clip-path: circle(0px at 90% -10%);
                transition: all 0.5s ease-out;
                pointer-events: none;
            }

            .nav-links.active {
                clip-path: circle(1000px at 90% -10%);
                pointer-events: all;
            }

            .nav-links li {
                margin: 1rem 0;
            }

            .hamburger {
                display: block;
            }

            .hamburger.active div:nth-child(1) {
                transform: rotate(-45deg) translate(-5px, 6px);
            }

            .hamburger.active div:nth-child(2) {
                opacity: 0;
            }

            .hamburger.active div:nth-child(3) {
                transform: rotate(45deg) translate(-5px, -6px);
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p.intro {
                font-size: 1rem;
            }

            .levels-container {
                gap: 1.5rem;
            }

            .level-circle {
                width: 100px;
                height: 100px;
            }

            .level-circle img {
                width: 50px;
                height: 50px;
            }

            .level-label {
                font-size: 1rem;
            }

            .about-section {
                padding: 1.5rem;
            }

            .play-icon {
                font-size: 3rem;
            }
        }

        @media screen and (max-width: 480px) {
            .hero h1 {
                font-size: 2rem;
            }

            .levels-container {
                flex-direction: column;
                gap: 1rem;
            }

            .level-item {
                margin: 10px 0;
            }

            .btn {
                padding: 0.6rem 1.5rem;
            }

            .footer-links {
                flex-direction: column;
            }

            .footer-links li {
                margin: 0.5rem 0;
            }

            .play-icon {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Particle Background Canvas -->
    <canvas id="musicCanvas"></canvas>

    <!-- Navigation -->
    <nav>
        <img src="MUSIC-removebg-preview.png" alt="Music Image" style="width: 100px; height: auto;">
        <ul class="nav-links">
            <li><a href="index.html">Home</a></li>
            <li><a href="about.html">About</a></li>
            <li><a href="courses.html">Courses</a></li>
            <li><a href="contact.html">Contact</a></li>
            <li><a href="branch.html">branch</a></li>
            <li><a href="reviews.html">Reviews</a></li>
        </ul>
        <div class="hamburger">
            <div></div>
            <div></div>
            <div></div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1>Welcome to Music School of Delhi</h1>
            <p class="intro">Discover your musical potential with our expert instructors and world-class facilities. Join us on a journey of creativity and excellence in music education.</p>
            <a href="courses.html" class="btn">Explore Courses</a>
        </div>
    </section>

    <!-- Video Carousel - Updated Section -->
    <div class="video-carousel">
        <div class="video-container" id="videoContainer">
            <div class="video-item active">
                <iframe id="video1" src="https://www.youtube.com/embed/jgqu4Ax3TNc?enablejsapi=1&rel=0&showinfo=0" allowfullscreen></iframe>
                <div class="video-overlay" data-video="video1">
                    <i class="fas fa-play play-icon"></i>
                    <a href="https://www.youtube.com/watch?v=jgqu4Ax3TNc" target="_blank" class="watch-youtube">Watch on YouTube</a>
                </div>
            </div>
            <div class="video-item">
                <iframe id="video2" src="https://www.youtube.com/embed/rxPmk6lxvVU?enablejsapi=1&rel=0&showinfo=0" allowfullscreen></iframe>
                <div class="video-overlay" data-video="video2">
                    <i class="fas fa-play play-icon"></i>
                    <a href="https://www.youtube.com/watch?v=rxPmk6lxvVU" target="_blank" class="watch-youtube">Watch on YouTube</a>
                </div>
            </div>
            <div class="video-item">
                <iframe id="video3" src="https://www.youtube.com/embed/Zt0TjtxA-10?enablejsapi=1&rel=0&showinfo=0" allowfullscreen></iframe>
                <div class="video-overlay" data-video="video3">
                    <i class="fas fa-play play-icon"></i>
                    <a href="https://www.youtube.com/watch?v=Zt0TjtxA-10" target="_blank" class="watch-youtube">Watch on YouTube</a>
                </div>
            </div>
        </div>
        <div class="carousel-controls">
            <button class="carousel-btn" id="prevBtn"><i class="fas fa-chevron-left"></i></button>
            <button class="carousel-btn" id="nextBtn"><i class="fas fa-chevron-right"></i></button>
        </div>
        <div class="carousel-dots">
            <div class="dot active" data-index="0"></div>
            <div class="dot" data-index="1"></div>
            <div class="dot" data-index="2"></div>
        </div>
    </div>

    <!-- About Section with Rotating Circles -->
    <section class="hero">
        <div class="hero-content">
            <!-- Rotating Circles -->
            <div class="levels-container">
                <div class="level-item">
                    <div class="level-circle">
                        <img src="https://cdn-icons-png.flaticon.com/512/3209/3209100.png" alt="Beginner Music Notes">
                    </div>
                    <div class="level-label">Beginner</div>
                </div>
                <div class="level-item">
                    <div class="level-circle">
                        <img src="https://cdn-icons-png.flaticon.com/512/3659/3659899.png" alt="Intermediate Music Notes">
                    </div>
                    <div class="level-label">Intermediate</div>
                </div>
                <div class="level-item">
                    <div class="level-circle">
                        <img src="https://cdn-icons-png.flaticon.com/512/2720/2720552.png" alt="Advanced Music Notes">
                    </div>
                    <div class="level-label">Advanced</div>
                </div>
            </div>

            <div class="about-section">
               <p>Established in 2003, the Music School of Delhi has grown to become one of India's most respected and renowned music institutions. With over two decades of experience, the school is committed to nurturing aspiring musicians and turning them into skilled professionals. Believing that everyone has the potential to learn music, the school provides an encouraging environment focused on both artistic and personal growth.

                We offer a wide range of beginner and intermediate courses in instruments such as guitar, piano, and tabla, along with professional vocal singing programs. Our curriculum is carefully designed to meet global standards, ensuring our students receive a world-class education. In addition to regular classes, we also conduct workshops that boost confidence and teach essential industry skills.</p> 
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="social-icons">
                <a href="#"><i class="fab fa-facebook"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-youtube"></i></a>
            </div>
            <ul class="footer-links">
                <li><a href="index.html">Home</a></li>
                <li><a href="about.html">About</a></li>
                <li><a href="courses.html">Courses</a></li>
                <li><a href="contact.html">Contact</a></li>
                <li><a href="reviews.html">Reviews</a></li>
            </ul>
            <p class="copyright">&copy; 2023 Music School of Delhi. All Rights Reserved.</p>
        </div>
    </footer>

    <script>
        // Mobile Navigation
        const hamburger = document.querySelector('.hamburger');
        const navLinks = document.querySelector('.nav-links');

        hamburger.addEventListener('click', () => {
            navLinks.classList.toggle('active');
            hamburger.classList.toggle('active');
        });

        // Close mobile menu when clicking on a link
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                navLinks.classList.remove('active');
                hamburger.classList.remove('active');
            });
        });

        // Navbar scroll effect
        window.addEventListener('scroll', () => {
            const nav = document.querySelector('nav');
            if (window.scrollY > 50) {
                nav.style.padding = '0.5rem 2rem';
                nav.style.boxShadow = '0 4px 12px rgba(0, 0, 0, 0.1)';
            } else {
                nav.style.padding = '1rem 2rem';
                nav.style.boxShadow = '0 2px 10px rgba(0, 0, 0, 0.1)';
            }
        });

        // Video Carousel - Updated JavaScript
        const videoContainer = document.getElementById('videoContainer');
        const prevBtn = document.getElementById('prevBtn');
        const nextBtn = document.getElementById('nextBtn');
        const dots = document.querySelectorAll('.dot');
        const videoItems = document.querySelectorAll('.video-item');
        const videoOverlays = document.querySelectorAll('.video-overlay');
        let currentIndex = 0;
        let autoSlideInterval;
        let isAnyVideoPlaying = false;

        let ytPlayers = {};
        let playerReadyCount = 0;
        const totalVideos = videoItems.length;

        function updateCarousel() {
            videoContainer.style.transform = `translateX(-${currentIndex * 33.333}%)`;
            videoItems.forEach((item, index) => {
                item.classList.toggle('active', index === currentIndex);
            });
            dots.forEach((dot, index) => {
                dot.classList.toggle('active', index === currentIndex);
            });
        }

        function goToSlide(index) {
            if (isAnyVideoPlaying) return;
            currentIndex = index;
            updateCarousel();
            resetAutoSlide();
        }

        function nextSlide() {
            if (isAnyVideoPlaying) return;
            currentIndex = (currentIndex + 1) % videoItems.length;
            updateCarousel();
            resetAutoSlide();
        }

        function prevSlide() {
            if (isAnyVideoPlaying) return;
            currentIndex = (currentIndex - 1 + videoItems.length) % videoItems.length;
            updateCarousel();
            resetAutoSlide();
        }

        function startAutoSlide() {
            if (isAnyVideoPlaying) return;
            clearInterval(autoSlideInterval);
            autoSlideInterval = setInterval(() => {
                if (!isAnyVideoPlaying) nextSlide();
            }, 5000);
        }

        function resetAutoSlide() {
            if (isAnyVideoPlaying) return;
            clearInterval(autoSlideInterval);
            startAutoSlide();
        }

        function playVideo(videoId) {
            if (ytPlayers[videoId]) {
                ytPlayers[videoId].playVideo();
            }
        }

        window.onYouTubeIframeAPIReady = function () {
            videoItems.forEach((item) => {
                const iframe = item.querySelector('iframe');
                const videoId = iframe.id;
                ytPlayers[videoId] = new YT.Player(videoId, {
                    events: {
                        'onReady': onPlayerReady,
                        'onStateChange': onPlayerStateChange
                    }
                });
            });
        };

        function onPlayerReady(event) {
            playerReadyCount++;
            if (playerReadyCount === totalVideos) {
                updateCarousel();
                startAutoSlide();
            }
        }

        function onPlayerStateChange(event) {
            const videoId = event.target.getIframe().id;
            const overlay = document.querySelector(`.video-overlay[data-video="${videoId}"]`);

            if (event.data === YT.PlayerState.PLAYING) {
                isAnyVideoPlaying = true;
                clearInterval(autoSlideInterval);
                if (overlay) {
                    overlay.style.opacity = '0';
                    overlay.style.pointerEvents = 'none';
                }
            } else if (event.data === YT.PlayerState.ENDED || event.data === YT.PlayerState.PAUSED) {
                isAnyVideoPlaying = false;
                if (overlay) {
                    overlay.style.opacity = '1';
                    overlay.style.pointerEvents = 'auto';
                }
                const carousel = document.querySelector('.video-carousel');
                if (!carousel.matches(':hover')) {
                    startAutoSlide();
                }
            }
        }

        nextBtn.addEventListener('click', () => {
            if (!isAnyVideoPlaying) nextSlide();
        });

        prevBtn.addEventListener('click', () => {
            if (!isAnyVideoPlaying) prevSlide();
        });

        dots.forEach(dot => {
            dot.addEventListener('click', () => {
                if (!isAnyVideoPlaying) {
                    const index = parseInt(dot.getAttribute('data-index'));
                    goToSlide(index);
                }
            });
        });

        videoOverlays.forEach(overlay => {
            overlay.addEventListener('click', (e) => {
                if (e.target.tagName === 'A') return;
                const videoId = overlay.getAttribute('data-video');
                const item = overlay.closest('.video-item');
                const index = Array.from(videoItems).indexOf(item);
                if (index !== currentIndex) {
                    currentIndex = index;
                    updateCarousel();
                }
                playVideo(videoId);
            });
        });

        const tag = document.createElement('script');
        tag.src = "https://www.youtube.com/iframe_api";
        document.head.appendChild(tag);

        // Pause auto slide on hover
        const carousel = document.querySelector('.video-carousel');
        carousel.addEventListener('mouseenter', () => clearInterval(autoSlideInterval));
        carousel.addEventListener('mouseleave', () => {
            if (!isAnyVideoPlaying) startAutoSlide();
        });

        // Particle Background
        const canvas = document.getElementById('musicCanvas');
        const ctx = canvas.getContext('2d');
        
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        
        // Music symbols
        const symbols = ['♪', '♫', '♩', '♬', '♭', '♯'];
        const particles = [];
        const mouse = { x: null, y: null };
        
        // Particle class
        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = 15 + Math.random() * 10;
                this.symbol = symbols[Math.floor(Math.random() * symbols.length)];
                this.speedX = Math.random() * 2 - 1;
                this.speedY = Math.random() * 2 - 1;
                this.opacity = 0.5 + Math.random() * 0.5;
            }
            
            update() {
                // Move away from mouse
                if (mouse.x && mouse.y) {
                    const dx = mouse.x - this.x;
                    const dy = mouse.y - this.y;
                    const distance = Math.sqrt(dx * dx + dy * dy);
                    
                    if (distance < 150) {
                        this.x -= dx / 15;
                        this.y -= dy / 15;
                    }
                }
                
                // Movement
                this.x += this.speedX;
                this.y += this.speedY;
                
                // Boundary check
                if (this.x < 0 || this.x > canvas.width) this.speedX *= -1;
                if (this.y < 0 || this.y > canvas.height) this.speedY *= -1;
            }
            
            draw() {
                ctx.font = `${this.size}px Arial`;
                ctx.fillStyle = `rgba(135, 206, 235, ${this.opacity})`;
                ctx.fillText(this.symbol, this.x, this.y);
            }
        }
        
        // Create particles
        for (let i = 0; i < 40; i++) {
            particles.push(new Particle());
        }
        
        // Track mouse position
        window.addEventListener('mousemove', (e) => {
            mouse.x = e.x;
            mouse.y = e.y;
        });
        
        // Animation loop
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            // Draw connections
            for (let a = 0; a < particles.length; a++) {
                for (let b = a; b < particles.length; b++) {
                    const dx = particles[a].x - particles[b].x;
                    const dy = particles[a].y - particles[b].y;
                    const distance = Math.sqrt(dx * dx + dy * dy);
                    
                    if (distance < 150) {
                        ctx.strokeStyle = `rgba(135, 206, 235, ${0.3 - distance/500})`;
                        ctx.lineWidth = 1;
                        ctx.beginPath();
                        ctx.moveTo(particles[a].x, particles[a].y);
                        ctx.lineTo(particles[b].x, particles[b].y);
                        ctx.stroke();
                    }
                }
                particles[a].update();
                particles[a].draw();
            }
            
            requestAnimationFrame(animate);
        }
        
        // Handle window resize
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
        
        // Start animation
        animate();
    </script>
</body>
</html>
