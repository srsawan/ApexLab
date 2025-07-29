<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Adaptive Performance in Complex Systems Lab - Clemson University</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --clemson-orange: #F66733;
            --clemson-purple: #522D80;
            --clemson-gray: #f9f9f9;
            --text-dark: #2c3e50;
            --text-light: #7f8c8d;
            --white: #ffffff;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --shadow-hover: 0 8px 25px rgba(0, 0, 0, 0.15);
        }

        body {
            font-family: 'Georgia', serif;
            line-height: 1.6;
            color: var(--text-dark);
            background-color: var(--white);
        }

        /* Header & Navigation */
        header {
            background: var(--white);
            box-shadow: var(--shadow);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 70px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--clemson-purple);
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--clemson-orange), var(--clemson-purple));
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-dark);
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
            padding: 5px 0;
        }

        .nav-links a:hover,
        .nav-links a.active {
            color: var(--clemson-orange);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 0;
            background-color: var(--clemson-orange);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after,
        .nav-links a.active::after {
            width: 100%;
        }

        .mobile-menu {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--clemson-purple);
            cursor: pointer;
        }

        /* Container */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, var(--clemson-purple) 0%, var(--clemson-orange) 100%);
            color: white;
            padding: 120px 0 80px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="50" r="1" fill="white" opacity="0.1"/></svg>');
            animation: float 20s linear infinite;
        }

        @keyframes float {
            0% { transform: translateY(0px); }
            100% { transform: translateY(-100px); }
        }

        .hero-content {
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-size: 3.5rem;
            font-weight: bold;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .hero-tagline {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            opacity: 0.9;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 12px 24px;
            border-radius: 25px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
            border: none;
            font-size: 1rem;
        }

        .btn-primary {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 2px solid rgba(255, 255, 255, 0.3);
        }

        .btn-primary:hover {
            background: white;
            color: var(--clemson-purple);
            transform: translateY(-2px);
            box-shadow: var(--shadow-hover);
        }

        .btn-secondary {
            background: transparent;
            color: white;
            border: 2px solid white;
        }

        .btn-secondary:hover {
            background: white;
            color: var(--clemson-orange);
        }

        /* Main Content */
        main {
            margin-top: 70px;
        }

        section {
            padding: 60px 0;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: var(--clemson-purple);
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            width: 60px;
            height: 4px;
            background: linear-gradient(90deg, var(--clemson-orange), var(--clemson-purple));
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        /* Page Content */
        .page {
            display: none;
            min-height: 70vh;
        }

        .page.active {
            display: block;
        }

        /* Home Page Specific */
        .home-intro {
            background: var(--clemson-gray);
            text-align: center;
        }

        .home-intro p {
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto;
            color: var(--text-light);
        }

        .explore-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .explore-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            text-align: center;
            cursor: pointer;
            border: 3px solid transparent;
        }

        .explore-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-hover);
            border-color: var(--clemson-orange);
        }

        .explore-card i {
            font-size: 3rem;
            color: var(--clemson-orange);
            margin-bottom: 1rem;
        }

        .explore-card h3 {
            color: var(--clemson-purple);
            margin-bottom: 1rem;
        }

        /* News Ticker */
        .news-ticker {
            background: var(--clemson-purple);
            color: white;
            padding: 15px 0;
            overflow: hidden;
            position: relative;
        }

        .ticker-content {
            display: flex;
            animation: scroll 30s linear infinite;
            white-space: nowrap;
        }

        .ticker-item {
            padding-right: 50px;
            font-weight: 500;
        }

        @keyframes scroll {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }

        /* People Grid */
        .people-filters {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 8px 16px;
            background: transparent;
            border: 2px solid var(--clemson-orange);
            color: var(--clemson-orange);
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .filter-btn.active,
        .filter-btn:hover {
            background: var(--clemson-orange);
            color: white;
        }

        .people-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }

        .person-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            text-align: center;
        }

        .person-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-hover);
        }

        .person-photo {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, var(--clemson-orange), var(--clemson-purple));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: white;
        }

        .person-info {
            padding: 1.5rem;
        }

        .person-name {
            font-size: 1.3rem;
            font-weight: bold;
            color: var(--clemson-purple);
            margin-bottom: 0.5rem;
        }

        .person-role {
            color: var(--clemson-orange);
            font-weight: 600;
            margin-bottom: 1rem;
        }

        .person-links {
            display: flex;
            justify-content: center;
            gap: 1rem;
        }

        .person-links a {
            color: var(--text-light);
            font-size: 1.2rem;
            transition: color 0.3s ease;
        }

        .person-links a:hover {
            color: var(--clemson-orange);
        }

        /* Research Areas Grid */
        .research-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .research-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            position: relative;
            border-top: 4px solid var(--clemson-orange);
        }

        .research-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-hover);
        }

        .research-icon {
            padding: 2rem 2rem 1rem;
            text-align: center;
        }

        .research-icon i {
            font-size: 3rem;
            color: var(--clemson-purple);
        }

        .research-content {
            padding: 0 2rem 2rem;
        }

        .research-card h3 {
            color: var(--clemson-purple);
            margin-bottom: 1rem;
            text-align: center;
        }

        /* Publications */
        .publications-controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .search-box {
            padding: 10px 15px;
            border: 2px solid #ddd;
            border-radius: 25px;
            width: 300px;
            font-size: 1rem;
        }

        .search-box:focus {
            outline: none;
            border-color: var(--clemson-orange);
        }

        .publication-item {
            background: white;
            padding: 1.5rem;
            margin-bottom: 1rem;
            border-radius: 10px;
            box-shadow: var(--shadow);
            border-left: 4px solid var(--clemson-orange);
            transition: all 0.3s ease;
        }

        .publication-item:hover {
            transform: translateX(5px);
            box-shadow: var(--shadow-hover);
        }

        .pub-title {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--clemson-purple);
            margin-bottom: 0.5rem;
        }

        .pub-authors {
            color: var(--text-light);
            margin-bottom: 0.5rem;
        }

        .pub-venue {
            color: var(--clemson-orange);
            font-weight: 600;
            margin-bottom: 1rem;
        }

        /* News Timeline */
        .timeline {
            position: relative;
            padding-left: 2rem;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 15px;
            top: 0;
            bottom: 0;
            width: 2px;
            background: var(--clemson-orange);
        }

        .timeline-item {
            position: relative;
            background: white;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border-radius: 10px;
            box-shadow: var(--shadow);
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -27px;
            top: 20px;
            width: 12px;
            height: 12px;
            background: var(--clemson-orange);
            border-radius: 50%;
            border: 3px solid white;
        }

        .timeline-date {
            color: var(--clemson-purple);
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        /* Contact Form */
        .contact-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: start;
        }

        .contact-info {
            background: var(--clemson-gray);
            padding: 2rem;
            border-radius: 15px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .contact-item i {
            color: var(--clemson-orange);
            font-size: 1.2rem;
            width: 20px;
        }

        .contact-form {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: var(--shadow);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--clemson-purple);
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--clemson-orange);
        }

        .form-group textarea {
            height: 120px;
            resize: vertical;
        }

        /* Footer */
        footer {
            background: var(--clemson-purple);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }

        /* Mobile Responsiveness */
        @media (max-width: 768px) {
            .mobile-menu {
                display: block;
            }

            .nav-links {
                display: none;
                position: absolute;
                top: 100%;
                left: 0;
                width: 100%;
                background: white;
                flex-direction: column;
                padding: 1rem 0;
                box-shadow: var(--shadow);
            }

            .nav-links.active {
                display: flex;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero-tagline {
                font-size: 1.1rem;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .contact-grid {
                grid-template-columns: 1fr;
            }

            .publications-controls {
                flex-direction: column;
            }

            .search-box {
                width: 100%;
            }

            .explore-cards {
                grid-template-columns: 1fr;
            }

            .people-grid {
                grid-template-columns: 1fr;
            }

            .research-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Smooth animations */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">
                <div class="logo-icon">
                    <i class="fas fa-flask"></i>
                </div>
                <div>
                    <div>APCSL</div>
                    <small style="font-size: 0.8rem; color: var(--text-light);">Clemson University</small>
                </div>
            </div>
            <ul class="nav-links">
                <li><a href="#" class="nav-link active" data-page="home">Home</a></li>
                <li><a href="#" class="nav-link" data-page="about">About</a></li>
                <li><a href="#" class="nav-link" data-page="people">People</a></li>
                <li><a href="#" class="nav-link" data-page="research">Research</a></li>
                <li><a href="#" class="nav-link" data-page="publications">Publications</a></li>
                <li><a href="#" class="nav-link" data-page="news">News & Events</a></li>
                <li><a href="#" class="nav-link" data-page="join">Join Us</a></li>
                <li><a href="#" class="nav-link" data-page="contact">Contact</a></li>
            </ul>
            <button class="mobile-menu">
                <i class="fas fa-bars"></i>
            </button>
        </nav>
    </header>

    <main>
        <!-- HOME PAGE -->
        <div id="home" class="page active">
            <section class="hero">
                <div class="container">
                    <div class="hero-content">
                        <h1>Adaptive Performance in Complex Systems Lab</h1>
                        <p class="hero-tagline">Advancing resilient performance through innovative research in sociotechnical systems at Clemson University</p>
                        <div class="cta-buttons">
                            <a href="#" class="btn btn-primary" data-page="research">
                                <i class="fas fa-microscope"></i>
                                Explore Our Research
                            </a>
                            <a href="#" class="btn btn-secondary" data-page="publications">
                                <i class="fas fa-file-alt"></i>
                                View Publications
                            </a>
                        </div>
                    </div>
                </div>
            </section>

            <div class="news-ticker">
                <div class="container">
                    <div class="ticker-content">
                        <span class="ticker-item">🎉 New NSF grant awarded for healthcare resilience research</span>
                        <span class="ticker-item">📚 Latest paper published in Human Factors journal</span>
                        <span class="ticker-item">🎓 Congratulations to our PhD graduate Dr. Sarah Johnson</span>
                        <span class="ticker-item">🏆 Best paper award at HFES 2024 conference</span>
                    </div>
                </div>
            </div>

            <section class="home-intro">
                <div class="container">
                    <h2 class="section-title">Our Mission</h2>
                    <p>Our research involves methods to learn about evolving patterns of adaptation in complex sociotechnical systems, such as healthcare and education. Actionable insights from such learning are used to inform the design of policies, workflows, and interfaces for resilient performance.</p>
                    
                    <div class="explore-cards">
                        <div class="explore-card" data-page="research">
                            <i class="fas fa-hospital"></i>
                            <h3>Healthcare Systems</h3>
                            <p>Investigating adaptive performance in healthcare environments to improve patient safety and care delivery.</p>
                        </div>
                        <div class="explore-card" data-page="research">
                            <i class="fas fa-shield-alt"></i>
                            <h3>Resilience Engineering</h3>
                            <p>Developing frameworks to enhance system resilience and recovery from disruptions.</p>
                        </div>
                        <div class="explore-card" data-page="research">
                            <i class="fas fa-brain"></i>
                            <h3>Cognitive Systems</h3>
                            <p>Exploring human-system interactions and decision-making processes in complex environments.</p>
                        </div>
                        <div class="explore-card" data-page="research">
                            <i class="fas fa-cogs"></i>
                            <h3>Adaptive Design</h3>
                            <p>Creating design principles for systems that adapt dynamically to changing requirements.</p>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- ABOUT PAGE -->
        <div id="about" class="page">
            <section>
                <div class="container">
                    <h2 class="section-title">About the Lab</h2>
                    <div class="research-grid">
                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-university"></i>
                            </div>
                            <div class="research-content">
                                <h3>Clemson Affiliation</h3>
                                <p>Part of Clemson University's Industrial Engineering Department, we leverage the university's strong engineering tradition and innovative research environment to advance our understanding of complex systems.</p>
                            </div>
                        </div>
                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-eye"></i>
                            </div>
                            <div class="research-content">
                                <h3>Our Vision</h3>
                                <p>To be a leading research lab in understanding and designing adaptive performance in complex sociotechnical systems, contributing to safer and more effective healthcare and educational environments.</p>
                            </div>
                        </div>
                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-handshake"></i>
                            </div>
                            <div class="research-content">
                                <h3>Collaborations</h3>
                                <p>We work closely with healthcare institutions, educational organizations, and industry partners to translate research findings into practical applications that improve system performance.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- PEOPLE PAGE -->
        <div id="people" class="page">
            <section>
                <div class="container">
                    <h2 class="section-title">Our Team</h2>
                    
                    <div class="people-filters">
                        <button class="filter-btn active" data-filter="all">All</button>
                        <button class="filter-btn" data-filter="pi">Principal Investigator</button>
                        <button class="filter-btn" data-filter="phd">PhD Students</button>
                        <button class="filter-btn" data-filter="ms">MS Students</button>
                        <button class="filter-btn" data-filter="collaborators">Collaborators</button>
                    </div>

                    <div class="people-grid">
                        <div class="person-card" data-role="pi">
                            <div class="person-photo">
                                <i class="fas fa-user"></i>
                            </div>
                            <div class="person-info">
                                <div class="person-name">Dr. Sudeep Hegde</div>
                                <div class="person-role">Principal Investigator</div>
                                <p>Associate Professor specializing in complex systems engineering, healthcare informatics, and resilience engineering.</p>
                                <div class="person-links">
                                    <a href="mailto:shegde@clemson.edu"><i class="fas fa-envelope"></i></a>
                                    <a href="#"><i class="fab fa-linkedin"></i></a>
                                    <a href="#"><i class="fas fa-globe"></i></a>
                                </div>
                            </div>
                        </div>

                        <div class="person-card" data-role="phd">
                            <div class="person-photo">
                                <i class="fas fa-user-graduate"></i>
                            </div>
                            <div class="person-info">
                                <div class="person-name">PhD Student 1</div>
                                <div class="person-role">PhD Student</div>
                                <p>Research focus: Healthcare system resilience and adaptive interfaces.</p>
                                <div class="person-links">
                                    <a href="#"><i class="fas fa-envelope"></i></a>
                                    <a href="#"><i class="fab fa-linkedin"></i></a>
                                </div>
                            </div>
                        </div>

                        <div class="person-card" data-role="ms">
                            <div class="person-photo">
                                <i class="fas fa-user-graduate"></i>
                            </div>
                            <div class="person-info">
                                <div class="person-name">MS Student 1</div>
                                <div class="person-role">MS Student</div>
                                <p>Research focus: Cognitive workload assessment in complex systems.</p>
                                <div class="person-links">
                                    <a href="#"><i class="fas fa-envelope"></i></a>
                                    <a href="#"><i class="fab fa-linkedin"></i></a>
                                </div>
                            </div>
                        </div>

                        <div class="person-card" data-role="collaborators">
                            <div class="person-photo">
                                <i class="fas fa-users"></i>
                            </div>
                            <div class="person-info">
                                <div class="person-name">Dr. Collaborator</div>
                                <div class="person-role">External Collaborator</div>
                                <p>Healthcare Systems Researcher at Medical University.</p>
                                <div class="person-links">
                                    <a href="#"><i class="fas fa-envelope"></i></a>
                                    <a href="#"><i class="fab fa-linkedin"></i></a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- RESEARCH PAGE -->
        <div id="research" class="page">
            <section>
                <div class="container">
                    <h2 class="section-title">Research Areas</h2>
                    <div class="research-grid">
                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-hospital-alt"></i>
                            </div>
                            <div class="research-content">
                                <h3>Healthcare Systems</h3>
                                <p>Investigating adaptive performance in healthcare environments, focusing on patient safety, workflow optimization, and technology integration to improve care delivery and outcomes. Our research includes studies on emergency department operations, surgical team coordination, and health information systems.</p>
                                <a href="#" class="btn btn-primary" style="margin-top: 1rem;">View Publications</a>
                            </div>
                        </div>
                        
                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-shield-alt"></i>
                            </div>
                            <div class="research-content">
                                <h3>Resilience Engineering</h3>
                                <p>Developing frameworks and methodologies to enhance system resilience, enabling organizations to maintain performance under varying conditions and recover from disruptions. We focus on proactive resilience strategies and adaptive capacity building.</p>
                                <a href="#" class="btn btn-primary" style="margin-top: 1rem;">View Publications</a>
                            </div>
                        </div>
                        
                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-brain"></i>
                            </div>
                            <div class="research-content">
                                <h3>Cognitive Systems Engineering</h3>
                                <p>Exploring human-system interactions, cognitive workload, and decision-making processes to design more effective and user-friendly complex systems. Our work includes cognitive task analysis, situation awareness studies, and human-automation interaction research.</p>
                                <a href="#" class="btn btn-primary" style="margin-top: 1rem;">View Publications</a>
                            </div>
                        </div>
                        
                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-cogs"></i>
                            </div>
                            <div class="research-content">
                                <h3>Design for Adaptive Performance</h3>
                                <p>Creating design principles and tools that enable systems to adapt dynamically to changing requirements while maintaining optimal performance levels. We develop adaptive interfaces, flexible workflows, and intelligent support systems.</p>
                                <a href="#" class="btn btn-primary" style="margin-top: 1rem;">View Publications</a>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- PUBLICATIONS PAGE -->
        <div id="publications" class="page">
            <section>
                <div class="container">
                    <h2 class="section-title">Publications</h2>
                    
                    <div class="publications-controls">
                        <input type="text" placeholder="Search publications..." class="search-box" id="pub-search">
                        <div>
                            <button class="btn btn-primary">
                                <i class="fas fa-download"></i>
                                Export BibTeX
                            </button>
                            <button class="btn btn-secondary">
                                <i class="fab fa-google"></i>
                                Google Scholar
                            </button>
                        </div>
                    </div>

                    <div class="publications-list">
                        <div class="publication-item">
                            <div class="pub-title">Adaptive Performance Measurement in Healthcare Teams: A Multi-Method Approach</div>
                            <div class="pub-authors">Hegde, S., Johnson, M., Smith, K.</div>
                            <div class="pub-venue">Human Factors, 2024</div>
                            <p>This study presents a comprehensive framework for measuring adaptive performance in healthcare teams, incorporating physiological, behavioral, and cognitive indicators.</p>
                        </div>

                        <div class="publication-item">
                            <div class="pub-title">Resilience Patterns in Emergency Department Operations During Crisis Events</div>
                            <div class="pub-authors">Chen, L., Hegde, S., Williams, R.</div>
                            <div class="pub-venue">Applied Ergonomics, 2023</div>
                            <p>An analysis of how emergency departments adapt their operations during high-stress crisis events, identifying key resilience factors.</p>
                        </div>

                        <div class="publication-item">
                            <div class="pub-title">Cognitive Load Assessment in Complex Sociotechnical Systems</div>
                            <div class="pub-authors">Hegde, S., Davis, A.</div>
                            <div class="pub-venue">Proceedings of HFES 2023</div>
                            <p>A novel approach to real-time cognitive load assessment using multimodal sensors in complex work environments.</p>
                        </div>

                        <div class="publication-item">
                            <div class="pub-title">Design Principles for Adaptive User Interfaces in Healthcare Information Systems</div>
                            <div class="pub-authors">Rodriguez, P., Hegde, S., Thompson, J.</div>
                            <div class="pub-venue">International Journal of Medical Informatics, 2023</div>
                            <p>Evidence-based design principles for creating adaptive interfaces that respond to user context and workload in healthcare settings.</p>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- NEWS & EVENTS PAGE -->
        <div id="news" class="page">
            <section>
                <div class="container">
                    <h2 class="section-title">News & Events</h2>
                    
                    <div class="timeline">
                        <div class="timeline-item">
                            <div class="timeline-date">December 2024</div>
                            <h3>NSF Grant Award</h3>
                            <p>Our lab received a $500,000 NSF grant to study adaptive performance in healthcare systems during emergency situations. This three-year project will involve collaboration with local hospitals and emergency services.</p>
                        </div>

                        <div class="timeline-item">
                            <div class="timeline-date">November 2024</div>
                            <h3>Best Paper Award at HFES 2024</h3>
                            <p>Dr. Hegde and team received the Best Paper Award at the Human Factors and Ergonomics Society Annual Meeting for their work on "Real-time Cognitive Load Assessment in Complex Systems."</p>
                        </div>

                        <div class="timeline-item">
                            <div class="timeline-date">October 2024</div>
                            <h3>PhD Defense Success</h3>
                            <p>Congratulations to Dr. Sarah Johnson on successfully defending her dissertation titled "Adaptive Interfaces for Emergency Medical Decision Support Systems." She will be joining Microsoft Research as a postdoc.</p>
                        </div>

                        <div class="timeline-item">
                            <div class="timeline-date">September 2024</div>
                            <h3>Invited Keynote at ResEng 2024</h3>
                            <p>Dr. Hegde delivered a keynote presentation on "The Future of Resilience Engineering in Healthcare" at the International Conference on Resilience Engineering in Copenhagen, Denmark.</p>
                        </div>

                        <div class="timeline-item">
                            <div class="timeline-date">August 2024</div>
                            <h3>New Lab Members</h3>
                            <p>We welcome three new graduate students to our lab: Maria Rodriguez (PhD), James Chen (MS), and Alex Thompson (MS). They will be working on projects related to adaptive performance measurement and cognitive systems engineering.</p>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- JOIN US PAGE -->
        <div id="join" class="page">
            <section>
                <div class="container">
                    <h2 class="section-title">Join Our Team</h2>
                    
                    <div class="research-grid">
                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-graduation-cap"></i>
                            </div>
                            <div class="research-content">
                                <h3>PhD Positions</h3>
                                <p>We are seeking motivated PhD students with backgrounds in Industrial Engineering, Human Factors, Computer Science, or related fields. Full funding available through research assistantships.</p>
                                <ul style="text-align: left; margin: 1rem 0;">
                                    <li>Strong analytical and programming skills</li>
                                    <li>Interest in human factors and complex systems</li>
                                    <li>Research experience preferred</li>
                                </ul>
                                <a href="https://www.clemson.edu/graduate/" class="btn btn-primary">Apply to Clemson</a>
                            </div>
                        </div>

                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-user-graduate"></i>
                            </div>
                            <div class="research-content">
                                <h3>MS Positions</h3>
                                <p>Master's students can join our lab for thesis or non-thesis tracks. We offer hands-on research experience and mentorship in cutting-edge projects.</p>
                                <ul style="text-align: left; margin: 1rem 0;">
                                    <li>Background in engineering or related field</li>
                                    <li>Programming experience (Python, R, MATLAB)</li>
                                    <li>Strong communication skills</li>
                                </ul>
                                <a href="https://www.clemson.edu/graduate/" class="btn btn-primary">Apply to Clemson</a>
                            </div>
                        </div>

                        <div class="research-card">
                            <div class="research-icon">
                                <i class="fas fa-flask"></i>
                            </div>
                            <div class="research-content">
                                <h3>Undergraduate Research</h3>
                                <p>Undergraduate students can participate in research through independent study courses, summer research programs, or volunteer positions.</p>
                                <ul style="text-align: left; margin: 1rem 0;">
                                    <li>Junior or Senior standing</li>
                                    <li>GPA of 3.0 or higher</li>
                                    <li>Commitment of at least one semester</li>
                                </ul>
                                <a href="#" class="btn btn-primary" data-page="contact">Contact Us</a>
                            </div>
                        </div>
                    </div>

                    <div style="background: var(--clemson-gray); padding: 2rem; border-radius: 15px; margin-top: 2rem;">
                        <h3 style="color: var(--clemson-purple); text-align: center; margin-bottom: 1rem;">What Our Students Say</h3>
                        <div class="research-grid">
                            <div style="background: white; padding: 1.5rem; border-radius: 10px; text-align: center;">
                                <p style="font-style: italic; margin-bottom: 1rem;">"Working in Dr. Hegde's lab has been an incredible experience. The research is cutting-edge and highly relevant to real-world problems."</p>
                                <strong>- Sarah J., PhD Graduate</strong>
                            </div>
                            <div style="background: white; padding: 1.5rem; border-radius: 10px; text-align: center;">
                                <p style="font-style: italic; margin-bottom: 1rem;">"The mentorship and collaborative environment helped me develop both technical and professional skills."</p>
                                <strong>- Michael L., MS Student</strong>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- CONTACT PAGE -->
        <div id="contact" class="page">
            <section>
                <div class="container">
                    <h2 class="section-title">Contact Us</h2>
                    
                    <div class="contact-grid">
                        <div class="contact-info">
                            <h3 style="color: var(--clemson-purple); margin-bottom: 1.5rem;">Get in Touch</h3>
                            
                            <div class="contact-item">
                                <i class="fas fa-user"></i>
                                <div>
                                    <strong>Dr. Sudeep Hegde</strong><br>
                                    Principal Investigator
                                </div>
                            </div>

                            <div class="contact-item">
                                <i class="fas fa-envelope"></i>
                                <div>shegde@clemson.edu</div>
                            </div>

                            <div class="contact-item">
                                <i class="fas fa-phone"></i>
                                <div>(864) 656-XXXX</div>
                            </div>

                            <div class="contact-item">
                                <i class="fas fa-map-marker-alt"></i>
                                <div>
                                    Freeman Hall, Room XXX<br>
                                    Clemson University<br>
                                    Clemson, SC 29634
                                </div>
                            </div>

                            <div class="contact-item">
                                <i class="fas fa-building"></i>
                                <div>
                                    Department of Industrial Engineering<br>
                                    Clemson University
                                </div>
                            </div>
                        </div>

                        <div class="contact-form">
                            <h3 style="color: var(--clemson-purple); margin-bottom: 1.5rem;">Send us a Message</h3>
                            <form>
                                <div class="form-group">
                                    <label for="name">Name</label>
                                    <input type="text" id="name" name="name" required>
                                </div>

                                <div class="form-group">
                                    <label for="email">Email</label>
                                    <input type="email" id="email" name="email" required>
                                </div>

                                <div class="form-group">
                                    <label for="subject">Subject</label>
                                    <input type="text" id="subject" name="subject" required>
                                </div>

                                <div class="form-group">
                                    <label for="message">Message</label>
                                    <textarea id="message" name="message" required></textarea>
                                </div>

                                <button type="submit" class="btn btn-primary" style="width: 100%;">
                                    <i class="fas fa-paper-plane"></i>
                                    Send Message
                                </button>
                            </form>
                        </div>
                    </div>

                    <div style="margin-top: 3rem; text-align: center;">
                        <h3 style="color: var(--clemson-purple); margin-bottom: 1rem;">Visit Our Campus</h3>
                        <div style="background: #ddd; height: 300px; border-radius: 15px; display: flex; align-items: center; justify-content: center; color: #666;">
                            <div>
                                <i class="fas fa-map" style="font-size: 3rem; margin-bottom: 1rem;"></i>
                                <p>Interactive Google Maps would be embedded here</p>
                                <p>Showing Clemson University campus and Freeman Hall location</p>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </div>
    </main>

    <footer>
        <div class="container">
            <p>&copy; 2025 Adaptive Performance in Complex Systems Lab | Clemson University | Department of Industrial Engineering</p>
            <p style="margin-top: 0.5rem; opacity: 0.8;">
                <a href="#" style="color: white; margin: 0 10px;">Privacy Policy</a>
                <a href="#" style="color: white; margin: 0 10px;">Accessibility</a>
                <a href="https://www.clemson.edu" style="color: white; margin: 0 10px;">Clemson University</a>
            </p>
        </div>
    </footer>

    <script>
        // Navigation functionality
        const navLinks = document.querySelectorAll('.nav-link');
        const pages = document.querySelectorAll('.page');
        const mobileMenu = document.querySelector('.mobile-menu');
        const navLinksContainer = document.querySelector('.nav-links');

        // Handle navigation
        function showPage(pageId) {
            pages.forEach(page => page.classList.remove('active'));
            navLinks.forEach(link => link.classList.remove('active'));
            
            document.getElementById(pageId).classList.add('active');
            document.querySelector(`[data-page="${pageId}"]`).classList.add('active');
        }

        navLinks.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const pageId = link.getAttribute('data-page');
                showPage(pageId);
            });
        });

        // Handle explore cards and other page navigation buttons
        document.addEventListener('click', (e) => {
            if (e.target.closest('[data-page]') && !e.target.closest('.nav-link')) {
                e.preventDefault();
                const pageId = e.target.closest('[data-page]').getAttribute('data-page');
                showPage(pageId);
            }
        });

        // Mobile menu toggle
        mobileMenu.addEventListener('click', () => {
            navLinksContainer.classList.toggle('active');
        });

        // People filter functionality
        const filterBtns = document.querySelectorAll('.filter-btn');
        const personCards = document.querySelectorAll('.person-card');

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                filterBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                
                const filter = btn.getAttribute('data-filter');
                
                personCards.forEach(card => {
                    if (filter === 'all' || card.getAttribute('data-role') === filter) {
                        card.style.display = 'block';
                    } else {
                        card.style.display = 'none';
                    }
                });
            });
        });

        // Publications search
        const pubSearch = document.getElementById('pub-search');
        const publicationItems = document.querySelectorAll('.publication-item');

        if (pubSearch) {
            pubSearch.addEventListener('input', (e) => {
                const searchTerm = e.target.value.toLowerCase();
                
                publicationItems.forEach(item => {
                    const text = item.textContent.toLowerCase();
                    if (text.includes(searchTerm)) {
                        item.style.display = 'block';
                    } else {
                        item.style.display = 'none';
                    }
                });
            });
        }

        // Smooth scroll for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Header background change on scroll
        window.addEventListener('scroll', function() {
            const header = document.querySelector('header');
            if (window.scrollY > 50) {
                header.style.boxShadow = '0 2px 20px rgba(0, 0, 0, 0.15)';
            } else {
                header.style.boxShadow = '0 4px 6px rgba(0, 0, 0, 0.1)';
            }
        });

        // Contact form submission
        const contactForm = document.querySelector('.contact-form form');
        if (contactForm) {
            contactForm.addEventListener('submit', (e) => {
                e.preventDefault();
                alert('Thank you for your message! We will get back to you soon.');
                contactForm.reset();
            });
        }

        // Intersection Observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        // Observe elements for animation
        document.querySelectorAll('.research-card, .person-card, .publication-item, .timeline-item').forEach(el => {
            el.classList.add('fade-in');
            observer.observe(el);
        });
    </script>
</body>
</html>
