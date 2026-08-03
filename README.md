<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yousra Al-Idrisi | Academic & Education Portfolio</title>
    <style>
        :root {
            --primary-color: #1e293b;
            --accent-color: #2563eb;
            --text-color: #334155;
            --light-bg: #f8fafc;
            --border-color: #e2e8f0;
            --max-width: 900px;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: #ffffff;
            margin: 0;
            padding: 0;
        }

        header {
            border-bottom: 1px solid var(--border-color);
            background-color: #ffffff;
            position: sticky;
            top: 0;
            z-index: 10;
        }

        .nav-container {
            max-width: var(--max-width);
            margin: 0 auto;
            padding: 1rem 1.5rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .site-title {
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--primary-color);
            text-decoration: none;
        }

        nav a {
            color: var(--text-color);
            text-decoration: none;
            margin-left: 1.5rem;
            font-size: 0.95rem;
            font-weight: 500;
        }

        nav a:hover {
            color: var(--accent-color);
        }

        main {
            max-width: var(--max-width);
            margin: 0 auto;
            padding: 2.5rem 1.5rem;
        }

        .profile-section {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 2rem;
            align-items: start;
            margin-bottom: 3rem;
        }

        @media (max-width: 650px) {
            .profile-section {
                grid-template-columns: 1fr;
            }
        }

        h1 {
            font-size: 2.2rem;
            color: var(--primary-color);
            margin-top: 0;
            margin-bottom: 0.5rem;
        }

        .subtitle {
            font-size: 1.1rem;
            color: #64748b;
            margin-bottom: 1rem;
            font-weight: 500;
        }

        .profile-img {
            width: 100%;
            max-width: 220px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            border: 1px solid var(--border-color);
        }

        .links-list {
            list-style: none;
            padding: 0;
            margin: 1.5rem 0;
        }

        .links-list li {
            margin-bottom: 0.4rem;
        }

        .links-list a {
            color: var(--accent-color);
            text-decoration: none;
            font-weight: 500;
        }

        .links-list a:hover {
            text-decoration: underline;
        }

        section {
            margin-bottom: 3rem;
        }

        h2 {
            font-size: 1.4rem;
            color: var(--primary-color);
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 0.4rem;
            margin-bottom: 1.2rem;
        }

        .entry {
            margin-bottom: 1.5rem;
        }

        .entry-header {
            display: flex;
            justify-content: space-between;
            font-weight: 600;
            color: var(--primary-color);
        }

        .entry-sub {
            font-style: italic;
            color: #64748b;
            font-size: 0.95rem;
            margin-bottom: 0.4rem;
        }

        ul.details {
            margin-top: 0.4rem;
            padding-left: 1.2rem;
        }

        ul.details li {
            margin-bottom: 0.3rem;
        }

        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 1rem;
        }

        .card {
            background-color: var(--light-bg);
            border: 1px solid var(--border-color);
            border-radius: 6px;
            padding: 1.2rem;
        }

        .card h3 {
            margin-top: 0;
            font-size: 1.1rem;
            color: var(--primary-color);
        }

        .badge {
            display: inline-block;
            background: #e2e8f0;
            color: #334155;
            font-size: 0.75rem;
            padding: 0.2rem 0.5rem;
            border-radius: 4px;
            font-weight: 600;
            margin-top: 0.5rem;
        }

        footer {
            border-top: 1px solid var(--border-color);
            text-align: center;
            padding: 2rem 0;
            color: #94a3b8;
            font-size: 0.85rem;
        }
    </style>
</head>
<body>

    <header>
        <div class="nav-container">
            <a href="#" class="site-title">Yousra Al-Idrisi</a>
            <nav>
                <a href="#about">About</a>
                <a href="#research">Research</a>
                <a href="#teaching">Teaching</a>
                <a href="#academy">Academy</a>
            </nav>
        </div>
    </header>

    <main>
        <div class="profile-section" id="about">
            <div>
                <h1>Yousra Al-Idrisi</h1>
                <div class="subtitle">Pure Mathematician & Educator</div>
                <p>
                    I hold an M.A. in Mathematics from the <strong>University of California, Santa Cruz</strong> and a B.A. in Mathematics from the <strong>University of California, Berkeley</strong>.
                </p>
                <p>
                    My academic work focuses on geometric group theory, low-dimensional topology, and non-positive curvature geometry. Beyond research, I am dedicated to university mathematics education, course curriculum development, and 1:1 private instruction through <strong>Math With Yousra Academy</strong>.
                </p>

                <ul class="links-list">
                    <li><strong>Email:</strong> <a href="mailto:mathwithyousra.academy@gmail.com">mathwithyousra.academy@gmail.com</a></li>
                    <li><strong>Curriculum Vitae:</strong> <a href="CV.pdf" target="_blank">Download CV (PDF)</a></li>
                    <li><strong>LinkedIn:</strong> <a href="https://www.linkedin.com/in/yousra-al-idrisi-14950a316/" target="_blank">linkedin.com/in/yousra-al-idrisi</a></li>
                </ul>
            </div>
            <div>
                <img src="profile.jpg" alt="Yousra Al-Idrisi" class="profile-img" onerror="this.style.display='none'">
            </div>
        </div>

        <section id="research">
            <h2>Research Interests & Thesis</h2>
            <p>
                <strong>Research Interests:</strong> Geometric group theory and low-dimensional topology, including non-positive curvature, hyperbolic manifolds, Artin and Coxeter groups, random groups, and knot/link invariants.
            </p>

            <div class="entry">
                <div class="entry-header">
                    <span>Master's Thesis: Geometry of Nonpositive Curvature and the Flat Subspace Theorem</span>
                    <span>2025 – 2026</span>
                </div>
                <div class="entry-sub">University of California, Santa Cruz (Advisor: Jiayin Pan)</div>
                <ul class="details">
                    <li>Developed a self-contained proof of the Gromoll–Wolf Flat Subspace Theorem for solvable groups acting on nonpositively curved spaces.</li>
                    <li>Constructed comparison geometry foundations including Rauch's comparison theorem, Cartan–Hadamard theorem, and geodesic rigidity bounds.</li>
                </ul>
            </div>
        </section>

        <section id="teaching">
            <h2>Teaching & Academic Mentorship</h2>
            <div class="entry">
                <div class="entry-header">
                    <span>Teaching Assistant</span>
                    <span>Sep 2022 – Present</span>
                </div>
                <div class="entry-sub">University of California, Santa Cruz</div>
                <ul class="details">
                    <li><strong>Courses Taught:</strong> MATH 23B (Vector Calculus II), MATH 23A (Vector Calculus I), MATH 21 (Linear Algebra), MATH 19B (Calculus for STEM), MATH 16B (Calculus for Life Sciences), MATH 11A/B, MATH 3 (Precalculus).</li>
                    <li>Designed original quizzes, practice exams, problem sets, and discussion activities aimed at strengthening conceptual rigor and addressing student misconceptions.</li>
                </ul>
            </div>
        </section>

        <section id="academy">
            <h2>Math With Yousra Academy</h2>
            <p>
                Providing high-yield, university-aligned instruction and specialized private tutoring for advanced secondary and university students.
            </p>

            <div class="card-grid">
                <div class="card">
                    <h3>1:1 Private Instruction</h3>
                    <p>Tailored coaching in AP Calculus AB/BC, Multivariable Calculus, Linear Algebra, Differential Equations, and Introduction to Proofs.</p>
                    <span class="badge">In-Person & Remote</span>
                </div>
                <div class="card">
                    <h3>Curriculum & Courseware</h3>
                    <p>Canvas-structured online video modules, exam preparation guides, and structured mathematical problem sets built from university standards.</p>
                    <span class="badge">Academy Platform</span>
                </div>
            </div>
        </section>

    </main>

    <footer>
        &copy; Yousra Al-Idrisi. All rights reserved.
    </footer>

</body>
</html>
