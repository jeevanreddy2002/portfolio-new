/*
==============================================
PORTFOLIO WEBSITE JAVASCRIPT
Author: Jeevan Reddy Arlagadda
==============================================
*/

// Wait for DOM to be fully loaded
document.addEventListener('DOMContentLoaded', function() {
    // Theme toggle functionality
    const themeToggle = document.getElementById('themeToggle');
    const rootElement = document.documentElement;
    
    // Check for saved theme preference
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme === 'light') {
        rootElement.classList.add('light-theme');
    }
    
    // Toggle theme when button is clicked
    themeToggle.addEventListener('click', function() {
        rootElement.classList.toggle('light-theme');
        
        // Save theme preference
        if (rootElement.classList.contains('light-theme')) {
            localStorage.setItem('theme', 'light');
        } else {
            localStorage.setItem('theme', 'dark');
        }
    });
    // Initialize AOS animation library
    AOS.init({
        duration: 1000,
        once: false,
        mirror: true
    });

    // Initialize Typed.js for typing animation
    const options = {
        strings: [
            'Python Developer',
            'Machine Learning Engineer',
            'AWS Certified Professional',
            'Backend Developer'
        ],
        typeSpeed: 50,
        backSpeed: 30,
        backDelay: 2000,
        loop: true
    };
    
    const typed = new Typed('.typing-text', options);

    // Navigation menu toggle for mobile
    const hamburger = document.querySelector('.hamburger');
    const navMenu = document.querySelector('.nav-menu');
    
    hamburger.addEventListener('click', () => {
        hamburger.classList.toggle('active');
        navMenu.classList.toggle('active');
    });
    
    // Close mobile menu when clicking a nav link
    document.querySelectorAll('.nav-link').forEach(link => {
        link.addEventListener('click', () => {
            hamburger.classList.remove('active');
            navMenu.classList.remove('active');
        });
    });
    
    // Navbar scroll effect
    const navbar = document.querySelector('.navbar');
    
    window.addEventListener('scroll', () => {
        if (window.scrollY > 50) {
            navbar.classList.add('scrolled');
        } else {
            navbar.classList.remove('scrolled');
        }
    });
    
    // Smooth scrolling for navigation links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function(e) {
            e.preventDefault();
            
            const targetId = this.getAttribute('href');
            if (targetId === '#') return;
            
            const targetElement = document.querySelector(targetId);
            if (targetElement) {
                window.scrollTo({
                    top: targetElement.offsetTop - 80,
                    behavior: 'smooth'
                });
            }
        });
    });
    
    // Tech stack category filtering
    const categoryTabs = document.querySelectorAll('.category-tab');
    const techTiles = document.querySelectorAll('.tech-tile');
    
    categoryTabs.forEach(tab => {
        tab.addEventListener('click', () => {
            // Remove active class from all tabs
            categoryTabs.forEach(t => t.classList.remove('active'));
            
            // Add active class to clicked tab
            tab.classList.add('active');
            
            const category = tab.getAttribute('data-category');
            
            // Show/hide tech tiles based on category
            techTiles.forEach(tile => {
                if (category === 'all' || tile.getAttribute('data-category') === category) {
                    tile.style.display = 'block';
                    
                    // Add animation
                    setTimeout(() => {
                        tile.style.opacity = '1';
                        tile.style.transform = 'translateY(0)';
                    }, 100);
                } else {
                    tile.style.opacity = '0';
                    tile.style.transform = 'translateY(20px)';
                    
                    setTimeout(() => {
                        tile.style.display = 'none';
                    }, 300);
                }
            });
        });
    });
    
    // Hover effects for tech tiles
    techTiles.forEach(tile => {
        tile.addEventListener('mouseenter', () => {
            tile.querySelector('i').classList.add('fa-beat');
        });
        
        tile.addEventListener('mouseleave', () => {
            tile.querySelector('i').classList.remove('fa-beat');
        });
    });
    
    // Project card hover effects
    const projectCards = document.querySelectorAll('.project-card');
    
    projectCards.forEach(card => {
        card.addEventListener('mouseenter', () => {
            card.style.transform = 'translateY(-10px)';
        });
        
        card.addEventListener('mouseleave', () => {
            card.style.transform = 'translateY(0)';
        });
    });
    
    // Terminal typing effect
    const terminalLines = document.querySelectorAll('.terminal-body p');
    let lineIndex = 0;
    
    function typeTerminalLine() {
        if (lineIndex < terminalLines.length) {
            const line = terminalLines[lineIndex];
            line.style.display = 'block';
            
            // Simulate typing effect
            const text = line.textContent;
            line.textContent = '';
            let charIndex = 0;
            
            function typeChar() {
                if (charIndex < text.length) {
                    line.textContent += text.charAt(charIndex);
                    charIndex++;
                    setTimeout(typeChar, Math.random() * 50 + 20);
                } else {
                    lineIndex++;
                    setTimeout(typeTerminalLine, 500);
                }
            }
            
            typeChar();
        }
    }
    
    // Hide terminal lines initially
    terminalLines.forEach(line => {
        line.style.display = 'none';
    });
    
    // Start terminal typing effect when about section is in view
    const aboutSection = document.querySelector('#about');
    
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                setTimeout(typeTerminalLine, 500);
                observer.unobserve(entry.target);
            }
        });
    }, { threshold: 0.5 });
    
    observer.observe(aboutSection);
    
    // Section reveal animations on scroll
    const sections = document.querySelectorAll('.section');
    
    const revealSection = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('section-visible');
            }
        });
    }, { threshold: 0.2 });
    
    sections.forEach(section => {
        revealSection.observe(section);
    });
    
    // Download CV functionality
    const downloadButtons = document.querySelectorAll('.download-cv');
    
    downloadButtons.forEach(button => {
        button.addEventListener('click', function(e) {
            e.preventDefault();
            
            // Direct link to the resume file
            window.location.href = 'assets/Jeevan_Reddy_Arlagadda_Resume.docx';
        });
    });
    
    // Contact form submission
    const contactForm = document.getElementById('contactForm');
    
    if (contactForm) {
        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            // Get form data
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const subject = document.getElementById('subject').value;
            const message = document.getElementById('message').value;
            
            // Normally would send this data to a server
            // For demo purposes, just show an alert
            alert(`Thank you ${name} for your message! I'll get back to you soon.`);
            
            // Reset form
            contactForm.reset();
        });
    }
    
    // Add parallax effect to home section
    const homeSection = document.querySelector('.home-section');
    
    window.addEventListener('scroll', () => {
        const scrollPosition = window.scrollY;
        if (scrollPosition < window.innerHeight) {
            homeSection.style.backgroundPositionY = `${scrollPosition * 0.5}px`;
        }
    });
    
    // Add glitch effect to code container
    const codeContainer = document.querySelector('.code-container');
    
    if (codeContainer) {
        setInterval(() => {
            codeContainer.classList.add('glitch');
            
            setTimeout(() => {
                codeContainer.classList.remove('glitch');
            }, 200);
        }, 5000);
    }
    
    // Add active class to current section in navigation
    const sections2 = document.querySelectorAll('section');
    const navLinks = document.querySelectorAll('.nav-link');
    
    window.addEventListener('scroll', () => {
        let current = '';
        
        sections2.forEach(section => {
            const sectionTop = section.offsetTop;
            const sectionHeight = section.clientHeight;
            
            if (window.scrollY >= sectionTop - 200) {
                current = section.getAttribute('id');
            }
        });
        
        navLinks.forEach(link => {
            link.classList.remove('active');
            if (link.getAttribute('href') === `#${current}`) {
                link.classList.add('active');
            }
        });
    });
});
