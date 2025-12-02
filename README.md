<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Berita Sekolahku - Portal Informasi SMA NUSANTARA</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
    
    <!-- Internal CSS -->
    <style>
        /* --- VARIABEL WARNA & GLOBAL --- */
        :root {
            --primary-color: #0f3056;      /* Biru Tua */
            --secondary-color: #0d402d;    /* Hijau Tua */
            --accent-color: #c19f55;       /* Emas */
            --light-color: #fefefe;        /* Putih */
            --background-color: #f4f4f4;   /* Abu-abu Sangat Muda untuk kontras */
            --text-color: #333;
            --dark-text-color: #ddd;
            --shadow: 0 4px 15px rgba(0,0,0,0.1);
            --font-family: 'Poppins', sans-serif;
            --font-family-heading: 'Playfair Display', serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-family);
            line-height: 1.6;
            color: var(--text-color);
            background-color: var(--background-color);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* --- HEADER --- */
        header {
            background: var(--light-color);
            box-shadow: var(--shadow);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        header .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            text-decoration: none;
            color: var(--primary-color);
            font-weight: 700;
            font-size: 1.2rem;
        }

        .logo img {
            width: 80px;
            height: auto;
            margin-right: 10px;
            border-radius: 50%;
            border: 2px solid var(--accent-color);
        }

        nav ul {
            list-style: none;
            display: flex;
        }

        nav ul li {
            margin-left: 20px;
        }

        nav ul li a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 600;
            transition: color 0.3s ease;
            position: relative;
        }

        nav ul li a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background-color: var(--accent-color);
            transition: width 0.3s ease;
        }

        nav ul li a:hover, nav ul li a.active {
            color: var(--primary-color);
        }

        nav ul li a:hover::after {
            width: 100%;
        }

        /* --- PAGE SECTIONS --- */
        .page-section {
            display: none; /* Sembunyikan semua halaman secara default */
            padding: 20px 0;
        }

        .page-section.active {
            display: block; /* Tampilkan halaman yang aktif */
        }

        /* --- HERO SECTION --- */
        .hero {
            background: linear-gradient(to right, rgba(15,48,86,0.85), rgba(15,48,86,0.7)), url('https://images.unsplash.com/photo-1523050854058-8df90110c9f1?q=80&w=2070&auto=format&fit=crop') no-repeat center center/cover;
            color: var(--light-color);
            padding: 100px 0;
            margin-bottom: 40px;
        }

        .hero .container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            align-items: center;
        }

        .hero-content .badge {
            background: var(--accent-color);
            color: var(--primary-color);
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 15px;
        }

        .hero h1 {
            font-family: var(--font-family-heading);
            font-size: 3rem;
            margin-bottom: 20px;
            line-height: 1.2;
        }

        .hero p {
            font-size: 1.1rem;
            margin-bottom: 30px;
            opacity: 0.9;
        }

        .btn {
            padding: 12px 25px;
            text-decoration: none;
            border-radius: 5px;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-block;
        }

        .btn-primary {
            background: var(--accent-color);
            color: var(--primary-color);
        }

        .btn-primary:hover {
            background: #b08d40;
            transform: translateY(-2px);
            box-shadow: 0 5px 10px rgba(0,0,0,0.2);
        }

        .hero-image img {
            width: 100%;
            border-radius: 10px;
            box-shadow: var(--shadow);
        }

        /* --- SEARCH & CATEGORY SECTION --- */
        .search-section, .category-section {
            margin-bottom: 30px;
        }

        .search-bar {
            display: flex;
            max-width: 600px;
            margin: 0 auto;
        }

        .search-bar input {
            flex-grow: 1;
            padding: 12px 15px;
            border: 2px solid var(--light-color);
            border-radius: 5px 0 0 5px;
            font-family: var(--font-family);
            font-size: 1rem;
        }

        .search-bar button {
            padding: 12px 20px;
            background: var(--primary-color);
            color: var(--light-color);
            border: none;
            border-radius: 0 5px 5px 0;
            cursor: pointer;
            font-family: var(--font-family);
            font-weight: 600;
            transition: background-color 0.3s ease;
        }

        .search-bar button:hover {
            background: #0a2145;
        }

        .category-filter {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 10px 20px;
            background: var(--light-color);
            border: 2px solid var(--light-color);
            border-radius: 25px;
            cursor: pointer;
            font-family: var(--font-family);
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .filter-btn.active, .filter-btn:hover {
            background: var(--primary-color);
            color: var(--light-color);
            border-color: var(--primary-color);
        }

        /* --- NEWS SECTION --- */
        .news-section h2 {
            font-family: var(--font-family-heading);
            text-align: center;
            margin-bottom: 40px;
            font-size: 2.5rem;
            color: var(--primary-color);
        }

        .news-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .news-card {
            background: var(--light-color);
            border-radius: 10px;
            box-shadow: var(--shadow);
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
            display: flex;
            flex-direction: column;
        }

        .news-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        }

        .news-card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .news-card-content {
            padding: 20px;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }

        .news-card-content .meta {
            font-size: 0.8rem;
            color: #777;
            margin-bottom: 10px;
        }

        .news-card-content .meta .category {
            background: var(--secondary-color);
            color: var(--light-color);
            padding: 3px 8px;
            border-radius: 3px;
            font-weight: 600;
        }

        .news-card-content h3 {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--primary-color);
        }

        .news-card-content p {
            font-size: 0.9rem;
            color: #555;
            flex-grow: 1;
        }

        /* --- TIMELINE PPDB SECTION --- */
        .timeline-section {
            padding: 60px 0;
        }
        .timeline-section h2 {
            font-family: var(--font-family-heading);
            text-align: center;
            font-size: 2.5rem;
            color: var(--primary-color);
            margin-bottom: 50px;
        }
        .timeline {
            position: relative;
            max-width: 800px;
            margin: 0 auto;
        }
        .timeline::after {
            content: '';
            position: absolute;
            width: 6px;
            background-color: var(--primary-color);
            top: 0;
            bottom: 0;
            left: 50%;
            margin-left: -3px;
            border-radius: 3px;
        }
        .timeline-container {
            padding: 10px 40px;
            position: relative;
            background-color: inherit;
            width: 50%;
        }
        .timeline-container::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            right: -10px;
            background-color: var(--accent-color);
            border: 4px solid var(--primary-color);
            top: 25px;
            border-radius: 50%;
            z-index: 1;
        }
        .timeline-left {
            left: 0;
        }
        .timeline-right {
            left: 50%;
        }
        .timeline-right::after {
            left: -10px;
        }
        .timeline-content {
            padding: 20px 30px;
            background-color: var(--light-color);
            position: relative;
            border-radius: 10px;
            box-shadow: var(--shadow);
        }
        .timeline-content h3 {
            color: var(--primary-color);
            margin-top: 0;
            margin-bottom: 10px;
        }
        .timeline-content p {
            margin-bottom: 0;
        }
        .timeline-content .date {
            font-weight: bold;
            color: var(--secondary-color);
            display: block;
            margin-bottom: 10px;
        }
        
        /* --- MODAL --- */
        .modal {
            display: none;
            position: fixed;
            z-index: 2000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0,0,0,0.7);
            animation: fadeIn 0.3s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .modal-content {
            background-color: var(--light-color);
            margin: 5% auto;
            padding: 30px;
            border-radius: 10px;
            width: 90%;
            max-width: 800px; /* Lebih kecil untuk modal PPDB */
            position: relative;
            animation: slideIn 0.4s;
            text-align: center;
        }

        @keyframes slideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .close-btn {
            color: #aaa;
            position: absolute;
            top: 15px;
            right: 25px;
            font-size: 35px;
            font-weight: bold;
            cursor: pointer;
            transition: color 0.3s;
        }

        .close-btn:hover {
            color: var(--text-color);
        }
        
        /* Style untuk Modal Berita */
        #newsModal .modal-content {
            max-width: 800px;
            text-align: left;
        }

        #newsModal .modal-content img {
            width: 100%;
            height: 400px;
            object-fit: cover;
            border-radius: 5px;
            margin-bottom: 20px;
        }

        #newsModal .modal-content .meta-info {
            margin-bottom: 15px;
            font-size: 0.9rem;
            color: #777;
        }

        #newsModal .modal-content .meta-info span {
            margin-right: 15px;
        }

        #newsModal .modal-content .meta-info #modalCategory {
            background: var(--secondary-color);
            color: var(--light-color);
            padding: 3px 8px;
            border-radius: 3px;
            font-weight: 600;
        }
        
        /* Style untuk Indentasi Paragraf dan Penulis */
        #newsModal .modal-content .article-body p {
            text-align: justify;
            text-indent: 1.5cm; /* Menjorok ke dalam 1.5cm */
            margin-bottom: 1em; /* Jarak antar paragraf */
        }

        #newsModal .modal-content .author {
            margin-top: 2em;
            text-align: right;
            font-style: italic;
            font-weight: 600;
            color: var(--primary-color);
        }

        /* --- FOOTER --- */
        footer {
            background: var(--primary-color);
            color: var(--dark-text-color);
            padding: 50px 0 20px;
            margin-top: 60px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }

        .footer-section h3 {
            margin-bottom: 15px;
            color: var(--accent-color);
        }

        .footer-section p, .footer-section a {
            color: var(--dark-text-color);
            text-decoration: none;
            display: block;
            margin-bottom: 5px;
            transition: color 0.3s;
        }

        .footer-section a:hover {
            color: var(--light-color);
        }

        .social-links a {
            display: inline-block;
            margin-right: 15px;
        }

        .footer-bottom {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 0.9rem;
        }

        /* --- RESPONSIVE DESIGN --- */
        @media screen and (max-width: 768px) {
            header .container {
                flex-direction: column;
            }
            
            nav ul {
                margin-top: 15px;
            }

            .hero .container {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .hero h1 {
                font-size: 2rem;
            }

            .hero-image {
                order: -1;
            }

            .modal-content {
                width: 95%;
                padding: 20px;
                margin: 10% auto;
            }

            /* Indentasi paragraf tetap aktif di layar kecil untuk memenuhi permintaan */
            #newsModal .modal-content .article-body p {
                text-indent: 1.5cm;
            }
            
            /* Timeline Responsif */
            .timeline::after {
                left: 31px;
            }
            .timeline-container {
                width: 100%;
                padding-left: 70px;
                padding-right: 25px;
            }
            .timeline-container::before {
                left: 60px;
                border: medium solid var(--light-color);
                border-width: 10px 10px 10px 0;
                border-color: transparent var(--light-color) transparent transparent;
            }
            .timeline-left::after, .timeline-right::after {
                left: 21px;
            }
            .timeline-right {
                left: 0%;
            }
        }
    </style>
</head>
<body>

    <header>
        <div class="container">
            <a href="#" class="logo">
                <img src="logo.jpg" alt="Logo Sekolah">
                <span>SMA NUSANTARA</span>
            </a>
            <nav>
                <ul>
                    <li><a href="#" id="berandaLink" class="active">Beranda</a></li>
                    <li><a href="#" id="ppdbLink">PPDB</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <main>
        <!-- Halaman Beranda -->
        <section id="berandaPage" class="page-section active">
            <!-- Hero Section -->
            <section class="hero">
                <div class="container">
                    <div class="hero-content">
                        <span class="badge">Berita Nusantara</span>
                        <h1>Berprestasi, Berkarakter, Berdaya Saing Global</h1>
                        <p>SMA Nusantara merupakan sekolah swasta yang berkomitmen menyediakan pendidikan berkualitas melalui program Reguler dan International Class Program (ICP). Dengan lingkungan belajar yang nyaman, tenaga pendidik kompeten, serta kurikulum yang dirancang untuk mengembangkan karakter dan kemampuan abad 21, kami membimbing siswa menjadi pribadi yang unggul, percaya diri, dan siap bersaing di tingkat nasional maupun internasional.</p>
                        <a href="#" class="btn btn-primary" data-id="1">Pilihan Hari Ini</a>
                    </div>
                    <div class="hero-image">
                        <img src="hero.jpg" alt="Hero Image">
                    </div>
                </div>
            </section>

            <!-- Search Bar -->
            <section class="search-section">
                <div class="container">
                    <div class="search-bar">
                        <input type="text" id="searchInput" placeholder="Cari berita...">
                        <button id="searchButton">Cari</button>
                    </div>
                </div>
            </section>

            <!-- Category Filter -->
            <section class="category-section">
                <div class="container">
                    <div class="category-filter">
                        <button class="filter-btn active" data-category="semua">semua</button>
                        <button class="filter-btn" data-category="Karya Sastra">Seni Rupa</button>
                        <button class="filter-btn" data-category="Karya Sastra">Karya Sastra</button>
                        <button class="filter-btn" data-category="Karya Ilmiah">Karya Ilmiah</button>
                        <button class="filter-btn" data-category="Eksperimen Kreatif">Eksperimen Kreatif</button>
                    </div>
                </div>
            </section>

            <!-- News Grid -->
            <section class="news-section">
                <div class="container">
                    <h2>Berita Terkini</h2>
                    <div class="news-grid" id="newsGrid">
                        <!-- Berita akan dimuat di sini oleh JavaScript -->
                    </div>
                </div>
            </section>
        </section>

        <!-- Halaman Timeline PPDB -->
        <section id="ppdbPage" class="page-section">
            <div class="timeline-section">
                <div class="container">
                    <h2>Timeline PPDB 2025/2026</h2>
                    <div class="timeline">
                        <div class="timeline-container timeline-left">
                            <div class="timeline-content">
                                <span class="date">1 - 31 Mei 2025</span>
                                <h3>Pembukaan Pendaftaran Online</h3>
                                <p>Calon siswa dapat melakukan pendaftaran secara online melalui website resmi PPDB. Pastikan semua dokumen persyaratan sudah dipersiapkan.</p>
                            </div>
                        </div>
                        <div class="timeline-container timeline-right">
                            <div class="timeline-content">
                                <span class="date">3 - 5 Juni 2025</span>
                                <h3>Seleksi Administrasi dan Wawancara</h3>
                                <p>Panitia akan melakukan verifikasi dokumen yang telah diunggah oleh calon siswa. Hasil seleksi akan diumumkan pada tahap berikutnya.</p>
                            </div>
                        </div>
                        <div class="timeline-container timeline-left">
                            <div class="timeline-content">
                                <span class="date">10 Juni 2025</span>
                                <h3>Pengumuman Hasil Seleksi</h3>
                                <p>Pengumuman calon siswa yang diterima akan ditayangkan di website PPDB dan di papan pengumuman sekolah.</p>
                            </div>
                        </div>
                        <div class="timeline-container timeline-right">
                            <div class="timeline-content">
                                <span class="date">11 - 14 Juni 2025</span>
                                <h3>Daftar Ulang</h3>
                                <p>Calon siswa yang diterima wajib melakukan daftar ulang dengan melengkapi berkas dan membayar biaya pendaftaran ulang sesuai ketentuan.</p>
                            </div>
                        </div>
                        <div class="timeline-container timeline-left">
                            <div class="timeline-content">
                                <span class="date">15 Juli 2025</span>
                                <h3>Hari Pertama Masuk Sekolah</h3>
                                <p>Selamat datang kepada siswa baru! Kegiatan awal tahun ajaran akan dimulai dengan masa orientasi siswa.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- Modal for News Detail -->
    <div id="newsModal" class="modal">
        <div class="modal-content">
            <span class="close-btn news-close-btn">&times;</span>
            <img id="modalImage" src="" alt="">
            <h2 id="modalTitle"></h2>
            <div class="meta-info">
                <span id="modalCategory"></span>
                <span id="modalDate"></span>
            </div>
            <div id="modalBody" class="article-body">
                <!-- Konten berita akan dimuat di sini -->
            </div>
            <div id="modalAuthor" class="author">
                <!-- Nama penulis akan dimuat di sini -->
            </div>
        </div>
    </div>

    <!-- Modal for PPDB -->
    <div id="ppdbModal" class="modal">
        <div class="modal-content">
            <span class="close-btn ppdb-close-btn">&times;</span>
            <h2>Pendaftaran Peserta Didik Baru</h2>
            <p>Pendaftaran untuk tahun ajaran 2025/2026 belum dibuka. Silakan lihat timeline perkiraan untuk informasi lebih lanjut.</p>
            <a href="#" id="timelineLink" class="btn btn-primary">Lihat Timeline</a>
        </div>
    </div>

    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>SMA NUSANTARA</h3>
                    <p>Berprestasi, Berkarakter, Berdaya Saing Global</p>
                </div>
                <div class="footer-section">
                    <h3>Kontak</h3>
                    <p>Jl. Pendidikan No. 1, Kota Malang</p>
                    <p>Email: info@smanusantara.sch.id</p>
                    <p>Telepon: (021) 37465</p>
                </div>
                <div class="footer-section">
                    <h3>Ikuti Kami</h3>
                    <div class="social-links">
                        <a href="#">Facebook</a>
                        <a href="#">Instagram</a>
                        <a href="#">Twitter</a>
                    </div>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; SMA NUSANTARA 1999</p>
            </div>
        </div>
    </footer>

    <!-- Internal JavaScript -->
    <script>
        document.addEventListener('DOMContentLoaded', () => {

            // Data Berita dengan teks lengkap 5 paragraf dan nama penulis
            const newsData = [
                {
                    id: 1,
                    category: 'Karya Seni',
                    title: 'Berita - Pameran Seni dan Inovasi SMA Nusantara Dapat Sambutan Positif Masyarakat',
                    summary: 'Acara Pameran Gelar Karya SMA Nusantara berlangsung meriah dan menampilkan berbagai karya kreatif siswa. Mugiyanto mengapresiasi kreativitas siswa dan berharap kegiatan ini terus diadakan. Pameran ini didukung guru, orang tua, dan masyarakat untuk membangun generasi kreatif.',
                    author: 'Figur Angger',
                    body: `<p>Pameran Gelar Karya bertema “Mewujudkan Generasi Hebat Cinta Kreativitas” yang diadakan oleh SMA Nusantara menjadi ajang bagi siswa untuk menampilkan potensi seni dan kreativitas mereka. Acara yang berlangsung di aula utama sekolah ini berjalan meriah dan menarik perhatian masyarakat. Kepala Kampung Sidomulyo, Mugiyanto, hadir bersama istrinya untuk menyaksikan langsung karya-karya siswa.</p>
                    <p>Dalam sambutannya, Mugiyanto menyampaikan rasa bangga atas kreativitas para siswa. Ia menilai bahwa karya-karya yang ditampilkan menunjukkan inovasi yang perlu terus dikembangkan sebagai bekal masa depan. Ia juga menegaskan pentingnya kegiatan seperti ini dalam meningkatkan kepercayaan diri dan semangat belajar siswa.</p>
                    <p>Pameran tersebut menampilkan berbagai hasil karya, mulai dari seni rupa, kerajinan tangan dari bahan daur ulang, kuliner kreasi siswa, hingga inovasi teknologi sederhana. Setiap kelas menyiapkan stan khusus yang memamerkan proses pembuatan dan hasil akhir karya, sehingga pengunjung dapat melihat langsung proses kreatif para siswa.</p>
                    <p>Guru pembina seni rupa, Ibu Ratna, turut menyampaikan apresiasinya terhadap dedikasi siswa. Ia menilai bahwa kegiatan ini memberi kesempatan bagi siswa untuk belajar bekerja sama, berpikir kreatif, dan menyelesaikan masalah secara mandiri. Antusiasme siswa dalam mempersiapkan karya menjadi hal yang sangat membanggakan.</p>
                    <p>Acara ini juga mendapat dukungan dari guru, orang tua, dan tokoh masyarakat yang hadir. Mereka menilai bahwa pameran ini memberikan kontribusi positif bagi pengembangan minat dan bakat siswa. SMA Nusantara berharap kegiatan seperti ini dapat terus dikembangkan untuk mencetak generasi yang kreatif, inovatif, dan sejalan dengan profil pelajar Pancasila.</p>`,
                    date: 'Senin, 17 November 2025 | 13:36 WIB',
                    image: 'karyaseni1.jpg'
                },
                {
                    id: 2,
                    category: 'Karya Seni',
                    title: 'Berita - SMA Nusantara Perkuat Identitas Budaya Lewat Batik Karya Siswa',
                    summary: 'SMA Nusantara mengadakan kegiatan membatik untuk kelas XI sebagai syarat ujian prakarya sekaligus penguatan budaya. Para siswa antusias karena kegiatan ini membantu mereka memahami proses dan nilai batik. Sekolah berharap program ini menumbuhkan kreativitas dan kesadaran budaya pada generasi muda.',
                    author: 'Figur Angger.',
                    body: `<p>SMA Nusantara mengadakan kegiatan membatik sebagai syarat ujian mata pelajaran prakarya untuk siswa kelas XI. Kegiatan dilaksanakan pada Sabtu (22/11) pukul 08.00 WIB di lapangan voli terbuka.</p>
                    <p>Seluruh siswa kelas XI mengikuti kegiatan membatik tersebut. Selain sebagai syarat ujian, kegiatan ini juga bertujuan memperkuat karakter budaya di lingkungan sekolah.</p>
                    <p>Kepala SMA Nusantara, Rina Kusuma, menyampaikan bahwa kegiatan membatik merupakan upaya sekolah untuk menumbuhkan kembali minat generasi muda terhadap warisan budaya lokal. Ia menekankan pentingnya memahami proses kreatif dan nilai budaya dalam batik.</p>
                    <p>Salah satu siswa, Septia Indah, mengaku antusias mengikuti kegiatan tersebut. Ia menyebut proses membatik ternyata menyenangkan dan memberikan pengalaman baru.</p>
                    <p>Melalui kegiatan ini, sekolah berharap dapat menanamkan kreativitas sekaligus meningkatkan kesadaran budaya siswa dalam kurikulum berbasis proyek (P5).</p>`,
                    date: 'Sabtu, 22 November 2025 | 12.20 WIB',
                    image: 'karyaseni2.jpg'
                },
                {
                    id: 3,
                    category: '',
                    title: '',
                    summary: '',
                    author: '',
                    body: `<p></p>
                    <p></p>
                    <p></p>
                    <p></p>
                    <p></p>`,
                    date: '',
                    image: ''
                },
                {
                    id: 4,
                    category: '',
                    title: '',
                    summary: '',
                    author: '',
                    body: `<p></p>
                    <p></p>
                    <p></p>
                    <p></p>
                    <p></p>`,
                    date: '',
                    image: ''
                },
                {
                    id: 5,
                    category: 'Karya Sastra',
                    title: 'Berita - Gerak dan Kata Menyatu Membentuk Harmoni Padu Sendratari',
                    summary: 'Kelas XI SMA Nusantara sukses menggelar pertunjukan sendratari selama satu pekan sebagai syarat tugas akhir mata pelajaran Bahasa Indonesia. Siswa menampilkan berbagai tarian, dialog, dan ekspresi dengan tema legenda, kisah rakyat, dan cerita fiksi. Pertunjukan ini memberikan pengalaman berkesan sekaligus membanggakan bagi seluruh peserta dan warga sekolah.',
                    author: 'Fitri Cahya Dwi Anggriani.',
                    body: `<p>Kelas XI SMA Nusantara sukses menggelar pertunjukan sendratari selama satu pekan, pada 11–18 November 2025, di lantai dua aula utama sekolah. Pertunjukan ini digelar sebagai syarat tugas akhir mata pelajaran Bahasa Indonesia, khususnya materi “drama”.</p>
                    <p>Seluruh siswa kelas XI menampilkan berbagai gerakan tari, narasi, dialog, dan ekspresi dengan penuh kreativitas. Berbagai tema berhasil diangkat, mulai dari legenda daerah, kisah rakyat Nusantara, hingga cerita fiksi yang mengandung nilai moral.</p>
                    <p>Acara dibuka dengan sambutan hangat dari kepala sekolah dan guru pengampu mata pelajaran Bahasa Indonesia. Beberapa judul sendratari yang ditampilkan antara lain Lutung Kasarung, Lembu Suro, Bumi Manusia, Nestapa Prambayu, hingga Maling Kundang.</p>
                    <p>Persiapan pertunjukan telah dilakukan sejak Januari, meliputi penyusunan naskah, latihan koreografi, serta penyiapan properti dan kostum. Kesuksesan acara tak lepas dari kerja sama dan komunikasi yang baik antara siswa dan guru pembimbing.</p>
                    <p>Kegiatan ini memberikan pengalaman berkesan yang tak terlupakan bagi para siswa. Banyak peserta merasa bangga dan bahagia karena berhasil mempersembahkan pertunjukan yang menarik bagi seluruh warga SMA Nusantara.</p>`,
                    date: 'Selasa, 18 November 2025 | 09:12 WIB',
                    image: 'karyasastra1.jpg'
                },
                {
                    id: 6,
                    category: 'Karya Sastra',
                    title: 'Berita - Pameran hingga Panggung Hiburan: FESKO 2025 tampilkan Ragam Kreasi Siswa SMA Nusantara',
                    summary: 'SMA Nusantara menggelar FESKO 2025 pada 29 November dengan tema “Kreasikan Seni, Tunjukkan dalam Aksi”. Acara menampilkan pameran seni, pertunjukan panggung, lomba puisi, dance, tari tradisional, dan kolaborasi vokal siswa. Penampilan band Sheila On 7 menutup kegiatan yang memberi pengalaman dan motivasi bagi seluruh siswa.',
                    author: 'Fitri Cahya Dwi Anggriani.',
                    body: `<p>SMA Nusantara menggelar puncak acara FESKO 2025 pada Sabtu, 29 November 2025, dengan tema “Kreasikan Seni, Tunjukkan dalam Aksi”. Kegiatan ini diikuti seluruh siswa dari kelas X hingga XII dan berlangsung di lapangan voli terbuka sekolah sejak pukul 06.40 hingga 13.00 WIB.</p>
                    <p>Acara dibuka dengan pameran seni rupa di sepanjang jalan menuju panggung hiburan. Berbagai karya siswa, mulai dari lukisan, wayang, kerajinan tangan, puisi, hingga properti sendratari ditampilkan untuk menunjukkan kreativitas dan bakat mereka.</p>
                    <p>Di panggung hiburan, final lomba Harmoni Puisi digelar dengan peserta menampilkan puisi terbaiknya penuh penghayatan dan ekspresi. Selain itu, sejumlah tenant bazaar makanan, minuman, dan aksesoris turut menyemarakkan suasana FESKO 2025.</p>
                    <p>Selama acara, siswa menampilkan berbagai pertunjukan, mulai dari dance modern, tari tradisional, hingga kolaborasi vokal. Penonton menyambut meriah setiap suguhan, dan sesi awarding digelar untuk memberi apresiasi kepada para juara lomba.</p>
                    <p>Acara ditutup dengan penampilan band Sheila On 7 yang menghadirkan musik energik. Guru dan siswa berharap FESKO 2025 menjadi motivasi dan wadah bagi siswa untuk mengembangkan kreativitas, bakat, dan kerja sama secara positif.</p>`,
                    date: 'Sabtu, 29 November 2025 | 19:00 WIB',
                    image: 'karyasastra2.jpg'
                },
                {
                    id: 7,
                    category: 'Karya Sastra',
                    title: 'Features - Puisi “Sepatu Usang”, Membawanya Sebagai Sang Pemenang',
                    summary: 'Tekad dan Motivasi Membawa Arlan Ghifari Bertemu Kebahagiaan Tak Berujung - Keterbatasan ekonomi yang melanda, tak pernah meruntuhkan rasa semangat yang berada di dalam diri Arlan. Mimpi-mimpi yang tergantung satu per satu berhasil tercapai. Lewat sepatu usang yang ia kenakan, Arlan berhasil mengubah nasib hidupnya.',
                    author: 'Fitri Cahya Dwi Anggriani.',
                    body: `<p>Arlan Ghifari, siswa kelas XII SMA Nusantara, berhasil meraih juara satu lomba puisi tingkat nasional sekaligus mendapatkan beasiswa S1 di Universitas Negeri Malang. Keberhasilan ini bukan hanya karena bakatnya, tetapi juga keteguhan dan semangat tinggi yang membawanya mewujudkan salah satu cita-citanya, menempuh pendidikan di perguruan tinggi. Latar belakang keluarganya yang sederhana, ayah sebagai tukang becak dan ibu berjualan gorengan, tidak pernah menjadi penghalang bagi Arlan untuk terus berjuang.</p>
                    <p>Di balik sikapnya yang pendiam, Arlan dikenal sebagai sosok ceria, pintar, disiplin, dan selalu bersemangat. Ketertarikannya pada dunia sastra, terutama puisi, menjadi cara ia memahami kehidupan dan menyalurkan isi hatinya. Setiap pulang sekolah, ia menulis bait-bait puisi di buku lusuh yang selalu dibawanya, lahir dari pengalaman sehari-hari dan perjalanan hidupnya yang penuh perjuangan.</p>
                    <p>Perjalanan Arlan tidak mudah. Setiap hari ia menempuh jarak jauh ke sekolah dengan sepatu usang, melewati jalan berbatu dan genangan air. Bagi Arlan, sepatu itu bukan sekadar alas kaki, tetapi simbol tekad dan perjalanan panjang untuk meraih masa depan yang lebih baik. Hambatan ekonomi dan ejekan teman-teman tidak pernah membuatnya menyerah; sebaliknya, hal itu memotivasinya untuk bekerja lebih keras.</p>
                    <p>Meski sibuk membantu ibu berjualan gorengan, Arlan tetap menyempatkan diri menulis puisi, baik di sela-sela pekerjaan maupun malam hari. Dari kebiasaan ini lahir puisi berjudul “Sepatu Usang”, yang menggambarkan perjuangan dan makna mendalam di balik sepatu yang tampak biasa bagi orang lain. Dorongan guru Bahasa Indonesia membuatnya memberanikan diri mengikuti lomba puisi tingkat nasional, dan puisinya berhasil masuk daftar finalis.</p>
                    <p>Saat perlombaan, Arlan menampilkan puisinya dengan penghayatan penuh, mengingat setiap langkah panjang yang pernah ia tempuh. Kemenangan itu bukan sekadar penghargaan, tetapi juga titik balik hidupnya. Beasiswa yang ia dapat membuka pintu menuju masa depan, membuktikan bahwa keterbatasan bukan penghalang untuk bermimpi, dan usaha yang tekun dapat mengubah hal yang tampak mustahil menjadi nyata.</p>`,
                    date: 'Selasa, 02 Desember 2025 | 12.20 WIB',
                    image: 'karyasastra3.png'
                },
                {
                    id: 8,
                    category: 'Karya Sastra',
                    title: '',
                    summary: '',
                    author: '',
                    body: `<p></p>
                    <p></p>
                    <p></p>
                    <p></p>
                    <p></p>`,
                    date: '',
                    image: ''
                },
                {
                    id: 9,
                    category: 'Karya Ilmiah',
                    title: 'Berita - Dari Gawai ke Riset Ilmiah: Citra Dewi, Siswi SMA Nusantara, Bongkar Dampak Aplikasi Video pada Konsentrasi Belajar',
                    summary: 'SMA Nusantara mengadakan kegiatan membatik untuk kelas XI sebagai syarat ujian prakarya sekaligus penguatan budaya. Para siswa antusias karena kegiatan ini membantu mereka memahami proses dan nilai batik. Sekolah berharap program ini menumbuhkan kreativitas dan kesadaran budaya pada generasi muda.',
                    author: 'Jihaan Nabiila Layyina.',
                    body: `<p>Suasana tegang bercampur fokus terlihat jelas di Aula Serbaguna SMA Nusantara saat berlangsungnya sesi ujian Karya Tulis Ilmiah (KTI) bagi siswa-siswi kelas XII, pada hari Rabu, 19 November 2025 (19-11-2025). Kegiatan ini bukan hanya formalitas, melainkan ajang pembuktian kemampuan akademik dan kedalaman riset mandiri mereka di hadapan dewan penguji yang terdiri dari para guru senior.</p>
                    <p>Puncak perhatian tertuju pada presentasi siswi berprestasi, Citra Dewi, dengan karya berupa artikel yang berjudul “Dampak Aplikasi Singkat Video Terhadap Konsentrasi Belajar Siswa SMA Nusantara.” Dengan setiap isi halaman yang terstruktur dan argumen yang lugas, Citra menjelaskan metodologi pengumpulan datanya, termasuk survei terperinci yang ia lakukan di antara 150 responden siswa sekolah.</p>
                    <p>Citra Dewi, siswi yang dikenal memiliki hobi membaca dan analisis data, menjelaskan bahwa ia termotivasi untuk meneliti topik tersebut setelah mengamati tren digital yang sedang marak. "Kami ingin membuktikan secara ilmiah sejauh mana penggunaan media sosial video instan atau video pendek memengaruhi rentang fokus kami di kelas. Ini adalah upaya mencari solusi nyata berbasis data, bukan sekadar opini," ungkap Citra dengan yakin, menjawab pertanyaan kritis dari tim penguji.</p>
                    <p>Wakil Kepala Sekolah Bidang Kurikulum, Bapak Setiawan Adi, M.Pd., menyatakan bahwa program KTI wajib ini adalah investasi jangka panjang. "KTI jauh lebih dari sekadar syarat kelulusan. Ini adalah wahana melatih siswa menguasai metodologi penelitian dan berpikir secara sistematis. Selain itu, dengan adanya KTI, para siswa juga dapat mulai belajar tentang penulisan artikel yang baik dan benar. Kami menuntut mereka untuk mampu mengkritisi, menganalisis, dan mempraktikkan ilmu, yang merupakan bekal penting untuk dunia perkuliahan," jelas Bapak Setiawan, yang menyebut kualitas riset tahun ini menunjukkan peningkatan signifikan.</p>
                    <p>Diharapkan, hasil KTI ini tidak hanya bernilai akademik, tetapi juga menjadi bahan acuan bagi kebijakan sekolah terkait penggunaan gawai dalam lingkungan belajar.</p>`,
                    date: 'Rabu, 19 November 2025 | 14.32 WIB',
                    image: 'ilmiah1.png'
                },
                {
                    id: 10,
                    category: 'Karya Ilmiah',
                    title: 'Berita - Prestasi Gemilang SMA Nusantara di Ajang FIR (Festival Inovasi Remaja) dan National Seminar: Sabet Juara 1, 2, dan 3 Lomba Karya Tulis Ilmiah',
                    summary: 'SMA Nusantara meraih juara 1, 2, dan 3 dalam Festival Inovasi Remaja (FIR) 2025 di Universitas Negeri Yogyakarta. Tiga tim menampilkan karya inovatif mulai dari solusi krisis air, urban farming, hingga kotak pintar pemilah sampah. Prestasi ini menunjukkan kreativitas, kerja sama tim, dan kemampuan siswa bersaing di tingkat nasional.',
                    author: 'Jihaan Nabiila Layyina.',
                    body: `<p>SMA Nusantara kembali menorehkan prestasi membanggakan di tingkat nasional melalui ajang Festival Inovasi Remaja (FIR) 2025 yang dikolaborasikan dengan National Seminar di Universitas Negeri Yogyakarta. Kegiatan ini menjadi wadah bagi pelajar untuk mengekspresikan gagasan kreatif, menulis ilmiah, dan menciptakan inovasi bermanfaat bagi masyarakat.</p>
                    <p>Tiga tim terbaik dari SMA Nusantara berhasil menempati posisi juara 1, 2, dan 3. Tim A, yang beranggotakan Christo Pramesta, Farhan Ramadhan, dan Reno Ardhana, meraih Juara 1 dengan karya esai “Teknologi Sederhana untuk Mengurangi Krisis Air di Kawasan Pedesaan,” yang menawarkan solusi filtrasi air murah dan mudah diterapkan.</p>
                    <p>Tim B yang terdiri atas Devano, Rizky, dan Bagas meraih Juara 2 melalui artikel ilmiah “Dampak Urban Farming Terhadap Ketahanan Pangan Keluarga di Perkotaan,” yang menyajikan analisis peran kebun kecil sebagai solusi pangan keluarga urban. Sementara itu, Tim C beranggotakan Aditya Mahendra, Lidia Putri, dan Keisha Putri mendapatkan Juara 3 dengan inovasi “Smart Waste Box,” alat pemilah sampah berbasis sensor cahaya.</p>
                    <p>Keberhasilan ini bukan hanya soal hasil lomba, tetapi juga proses belajar dan kerja sama tim. Keisha Putri dari Tim C menyampaikan rasa bangganya, menekankan pentingnya keberanian mencoba, memperbaiki, dan belajar bersama. Prestasi ini diharapkan dapat mendorong siswa lain di SMA Nusantara untuk berani menulis dan berinovasi.</p>
                    <p>Wakil Kepala Sekolah Bidang Kurikulum, Bapak Setiawan Adi, M.Pd., memberikan apresiasi atas usaha dan pencapaian siswa. Guru pembimbing menambahkan bahwa keberhasilan ini merupakan hasil kerja kolektif yang panjang, dari diskusi ide, riset, hingga penyuntingan akhir. Prestasi ini menjadi inspirasi bagi seluruh siswa untuk terus mengembangkan kreativitas, berpikir kritis, dan berkontribusi bagi masyarakat.</p>`,
                    date: 'Rabu, 26 November 2025 | 10.49 WIB',
                    image: 'ilmiah2.png'
                },
                {
                    id: 11,
                    category: 'Karya Ilmiah',
                    title: 'Berita - Ajang Inovasi Siswa: SMA Nusantara Sukses Menggelar Kompetisi Karya Ilmiah Intra-Sekolah “Nusantara Muda”',
                    summary: 'SMA Nusantara menggelar kompetisi internal “Nusantara Muda” untuk menumbuhkan kreativitas dan semangat riset siswa. Kegiatan ini melibatkan penulisan esai, artikel, dan karya kreatif bertema “Lingkungan & Masyarakat” dengan workshop dan seleksi internal. Juara 1, 2, dan 3 diumumkan setelah presentasi final di hadapan juri dan teman-teman.',
                    author: 'Jihaan Nabiila Layyina.',
                    body: `<p>SMA Nusantara kembali menggelar kompetisi tahunan “Nusantara Muda”, sebuah ajang karya tulis ilmiah dan esai yang diorganisir oleh OSIS. Kompetisi ini bertujuan mendorong semangat riset, kreativitas, dan daya kritis siswa dari kelas X hingga XII tanpa harus menunggu lomba eksternal.</p>
                    <p>Kegiatan dimulai dengan pendaftaran online, diikuti workshop tiga hari tentang penulisan, riset lapangan sederhana, dan etika penulisan ilmiah. Workshop ini dipandu oleh guru pembimbing dan alumni berpengalaman untuk mempersiapkan peserta menghasilkan karya berkualitas.</p>
                    <p>Setelah tahap persiapan, peserta mengikuti seleksi internal dengan menulis karya sesuai tema “Lingkungan & Masyarakat”. Karya dikumpulkan secara daring dan dinilai oleh dewan juri dari guru bidang IPA, IPS, dan Bahasa berdasarkan orisinalitas, kedalaman gagasan, kelayakan implementasi, dan kualitas penulisan.</p>
                    <p>Puncak acara berupa seminar kecil di aula sekolah, di mana finalis mempresentasikan karya mereka di hadapan juri dan teman-teman. Setelah sesi tanya jawab dan penilaian, diumumkanlah pemenang Nusantara Muda 2025, dengan juara 1, 2, dan 3 diraih oleh tiga tim berbeda.</p>
                    <p>Kepala OSIS dan guru pembimbing menyampaikan apresiasi atas partisipasi siswa. Mereka menekankan bahwa proses riset, menulis, dan presentasi mengajarkan disiplin, kolaborasi, dan kemampuan berpikir kritis. Menurut guru, kemampuan ini lebih berharga daripada sekadar predikat juara, karena menyiapkan siswa untuk tantangan akademik dan kehidupan nyata.</p>`,
                    date: 'Rabu, 3 Desember 2025 | 13.47 WIB',
                    image: 'ilmiah3.png'
                },
                {
                    id: 12,
                    category: 'Karya Ilmiah',
                    title: 'Melampaui Batas: Kisah Aira, Siswi Berkebutuhan Khusus yang Menembus Panggung Karya Ilmiah',
                    summary: 'Semangat dan Inklusivitas Mengantarkan Aira Rahmadani pada Panggung Karya Ilmiah - Keterbatasan penglihatan yang ia miliki tak pernah memadamkan semangat belajar dalam diri Aira. Dengan ketekunan yang tidak pernah goyah, ia merangkai gagasan hingga menjadi karya ilmiah yang menginspirasi banyak orang. Dari layar yang diperbesar hingga suara pembaca teks yang membimbingnya, Aira membuktikan bahwa keterbatasan bukanlah penghalang untuk meraih prestasi tertinggi.',
                    author: 'Jihaan Nabiila Layyina',
                    body: `<p>Di tengah riuh dinamika SMA Nusantara, Aira Rahmadani, siswi kelas XI, sering terlihat duduk di sudut perpustakaan dengan buku dan laptopnya. Meski memiliki gangguan penglihatan parsial sejak lahir, ia tetap tekun membaca dan meneliti dengan bantuan kacamata tebal dan layar yang diperbesar hingga 250%. Keterbatasan fisik itu tidak menghalanginya menyalurkan rasa ingin tahu terhadap fenomena sosial dan lingkungan.</p>
                    <p>Kegemarannya membaca buku dan artikel sains populer membawanya menemukan “kesenangan baru”: menulis esai ilmiah. Bagi Aira, menulis bukan sekadar tugas sekolah, melainkan cara membuktikan bahwa keterbatasan fisik tidak membatasi ruang pikir manusia. “Kalau sudah penasaran, ya dikejar sampai paham,” ujarnya sambil tersenyum.</p>
                    <p>Pada awal 2025, Aira memberanikan diri mengikuti lomba esai ilmiah “Nalar Muda Nusantara” yang digagas OSIS. Ia menulis artikel berjudul “Cahaya di Balik Layar: Peran Teknologi Bagi Pelajar Berkebutuhan Khusus”, menggabungkan pengalaman personal, analisis ilmiah, dan ajakan moral untuk mendukung inklusivitas pendidikan.</p>
                    <p>Dalam proses penulisan, Aira memanfaatkan wawancara daring, jurnal dengan fitur text-to-speech, dan menyusun poin-poin besar sebelum merangkai paragraf. Usahanya berbuah manis ketika ia keluar sebagai juara pertama, dengan juri menilai tulisannya kuat secara argumentasi dan menyajikan perspektif yang jarang diangkat penulis sebaya.</p>
                    <p>Kemenangan itu menjadi awal perjalanan baru bagi Aira. Ia kini menginspirasi teman-teman dan adik kelas, mendorong mereka untuk menulis dan berkarya. Guru pembina literasi, Ibu Ratih, memuji semangatnya, sementara Aira sendiri bertekad menulis lebih banyak lagi, membuktikan bahwa inklusi pendidikan bukan sekadar teori, tetapi bisa menjadi cerita nyata di sekolah.</p>`,
                    date: 'Selasa, 09 Desember 2025 | 12.50 WIB',
                    image: 'ilmiah4'
                },
                {
                    id: 13,
                    category: 'Eksperimen Kreatif',
                    title: 'Berita - SMA Nusantara Dorong Inovasi Energi Bersih: Siswa Ubah Air Gambut Jadi Listrik',
                    summary: 'Siswa SMA Nusantara memamerkan proyek sains memanfaatkan air gambut sebagai sumber energi listrik pada Science Week. Prototipe mini menggunakan bahan sederhana dan menghasilkan tegangan hingga 13 volt, mirip sel volta. Proyek ini bagian dari Green Innovation Lab untuk mendorong eksperimen energi berkelanjutan dan kesadaran lingkungan.',
                    author: 'Ghefira Indah Saraswati.',
                    body: `<p>Siswa SMA Nusantara berhasil meluncurkan proyek sains inovatif yang memanfaatkan air gambut sebagai sumber energi listrik. Proyek ini dipamerkan dalam Science Week sekolah dan mendapat sambutan hangat dari guru dan pengunjung.</p>
                    <p>Menggunakan bahan-bahan sederhana seperti air gambut, lempeng tembaga dan seng bekas, serta kawat, tim siswa membuat prototipe pembangkit listrik mini yang menghasilkan tegangan hingga 13 volt. Teknik ini mirip konsep sel volta, di mana keasaman air gambut berfungsi sebagai penghantar ion.</p>
                    <p>Putri Nazwa, salah satu penggagas proyek dari kelas XI, menjelaskan motivasinya. Ia menyoroti potensi lahan gambut lokal yang belum dimanfaatkan secara optimal dan ingin menunjukkan bahwa energi terbarukan bisa diperoleh dari sumber daya sekitar.</p>
                    <p>Guru Fisika SMA Nusantara, Ibu Ratna Dewi, memberi apresiasi tinggi terhadap inisiatif siswa. Ia menekankan bahwa eksperimen ini merupakan pembelajaran STEM kontekstual yang mendorong kreativitas sekaligus kesadaran lingkungan.</p>
                    <p>Proyek ini juga menjadi bagian dari program Green Innovation Lab untuk siswa kelas X hingga XII, yang memberi ruang bereksperimen dan mengembangkan solusi energi berkelanjutan. Ke depan, tim berencana memperbesar kapasitas pembangkit, menguji efisiensi, dan bekerja sama dengan komunitas lokal untuk implementasi di desa-desa yang memiliki sumber gambut melimpah.</p>`,
                    date: 'Kamis, 20 November 2025 | 15.10 WIB',
                    image: 'eksperimen1.png'
                },
                {
                    id: 14,
                    category: 'Eksperimen Kreatif',
                    title: 'Berita - Siswa SMA Nusantara Kembangkan Proyek Sains Energi Bersih dari Air Bekas Cucian',
                    summary: 'Siswa SMA Nusantara memamerkan proyek energi bersih dari air bekas cucian pada Science Exploration Day. Prototipe menggunakan elektrolisis ramah lingkungan untuk menghasilkan listrik skala kecil. Sekolah berencana mengembangkan proyek ini lebih lanjut dan mengikuti kompetisi penelitian tingkat provinsi.',
                    author: 'Ghefira Indah Saraswati',
                    body: `<p>Siswa SMA Nusantara menarik perhatian warga sekolah setelah mengembangkan proyek sains bertema energi bersih pada Science Exploration Day, Jumat (15/11/2025), di aula sekolah. Tim siswa kelas XI berhasil mengolah air bekas cucian menjadi sumber listrik sederhana menggunakan metode elektrolisis ramah lingkungan.</p>
                    <p>Proyek ini berawal dari keresahan siswa melihat limbah air rumah tangga yang terbuang sia-sia. Mereka merancang prototipe sederhana dengan elektroda berbahan karbon untuk menghasilkan arus listrik skala kecil.</p>
                    <p>Ketua tim, Alya Putri (17), menjelaskan bahwa ide muncul saat mereka mengerjakan tugas penelitian terapan. “Air bekas cucian masih bisa dimanfaatkan, bukan cuma dibuang. Kami menguji beberapa bahan elektroda sampai menemukan kombinasi stabil,” ujar Alya.</p>
                    <p>Proyek ini tidak hanya menarik perhatian siswa SMA Nusantara, tetapi juga tamu dari sekolah lain. Banyak yang mencoba langsung alat tersebut dan bertanya mengenai cara kerja serta peluang pengembangannya, termasuk Rafi dari SMA Harapan Jaya yang mengaku terinspirasi.</p>
                    <p>Guru Fisika SMA Nusantara, Ibu Ratih Handayani, menilai proyek ini menunjukkan pembelajaran berbasis eksperimen yang kontekstual. Sekolah berencana mendorong tim untuk mengikuti kompetisi tingkat provinsi dan mengembangkan prototipe tahap kedua agar menghasilkan energi lebih stabil dan efisien.</p>`,
                    date: 'Kamis, 27 November 2025 | 14.00 WIB',
                    image: 'eksperimen2.png'
                },
                {
                    id: 15,
                    category: 'Eksperimen Kreatif',
                    title: '',
                    summary: '',
                    author: '',
                    body: `<p></p>
                    <p></p>
                    <p></p>
                    <p></p>
                    <p></p>`,
                    date: '',
                    image: ''
                },
                {
                    id: 16,
                    category: 'Eksperimen Kreatif',
                    title: '',
                    summary: '',
                    author: '',
                    body: `<p></p>
                    <p></p>
                    <p></p>
                    <p></p>
                    <p></p>`,
                    date: '',
                    image: ''
                },
            ];
            const KaryaSeniKategori = newsData.filter(item => item.category === 'Karya Seni');
            const KaryaSastraKategori = newsData.filter(item => item.category === 'Karya Sastra');
            const KaryaIlmiahKategori = newsData.filter(item => item.category === 'Karya Ilmiah');
            const EksperimenKreatifKategori = newsData.filter(item => item.category === 'Eksperimen Kreatif');

            // Elemen DOM
            const newsGrid = document.getElementById('newsGrid');
            const newsModal = document.getElementById('newsModal');
            const modalTitle = document.getElementById('modalTitle');
            const modalImage = document.getElementById('modalImage');
            const modalBody = document.getElementById('modalBody');
            const modalAuthor = document.getElementById('modalAuthor');
            const modalCategory = document.getElementById('modalCategory');
            const modalDate = document.getElementById('modalDate');
            const newsCloseBtn = document.querySelector('.news-close-btn');
            const filterBtns = document.querySelectorAll('.filter-btn');
            const searchInput = document.getElementById('searchInput');
            const searchButton = document.getElementById('searchButton');

            // Elemen DOM untuk PPDB
            const ppdbModal = document.getElementById('ppdbModal');
            const ppdbLink = document.getElementById('ppdbLink');
            const ppdbCloseBtn = document.querySelector('.ppdb-close-btn');
            const timelineLink = document.getElementById('timelineLink');
            
            // Elemen DOM untuk Navigasi
            const berandaLink = document.getElementById('berandaLink');
            const berandaPage = document.getElementById('berandaPage');
            const ppdbPage = document.getElementById('ppdbPage');

            let currentFilter = 'semua';

            // Fungsi untuk membuat card berita
            const createNewsCard = (news) => {
                const card = document.createElement('div');
                card.className = 'news-card';
                card.dataset.category = news.category;
                card.innerHTML = `
                    <img src="${news.image}" alt="${news.title}">
                    <div class="news-card-content">
                        <div class="meta">
                            <span class="category">${news.category.charAt(0).toUpperCase() + news.category.slice(1).replace('-', ' ')}</span>
                            <span class="date">${news.date}</span>
                        </div>
                        <h3>${news.title}</h3>
                        <p>${news.summary}</p>
                    </div>
                `;
                card.addEventListener('click', () => openModal(news));
                return card;
            };

            // Fungsi untuk menampilkan berita
            const displayNews = (filter = 'semua') => {
                newsGrid.innerHTML = '';
                let newsToDisplay = newsData;

                if (filter !== 'semua') {
                    newsToDisplay = newsData.filter(item => item.category === filter);
                }

                newsToDisplay.forEach(news => {
                    newsGrid.appendChild(createNewsCard(news));
                });
            };

            // Fungsi untuk membuka modal berita
            const openModal = (news) => {
                modalTitle.textContent = news.title;
                modalImage.src = news.image;
                modalBody.innerHTML = news.body; // Menggunakan innerHTML untuk menampilkan paragraf
                modalAuthor.textContent = `Penulis: ${news.author}`;
                modalCategory.textContent = news.category.charAt(0).toUpperCase() + news.category.slice(1).replace('-', ' ');
                modalDate.textContent = news.date;
                newsModal.style.display = 'block';
                document.body.style.overflow = 'hidden';
            };

            // Fungsi untuk menutup modal
            const closeModal = () => {
                newsModal.style.display = 'none';
                ppdbModal.style.display = 'none';
                document.body.style.overflow = 'auto';
            };

            // Event Listener untuk menutup modal
            newsCloseBtn.addEventListener('click', closeModal);
            ppdbCloseBtn.addEventListener('click', closeModal);
            window.addEventListener('click', (event) => {
                if (event.target === newsModal || event.target === ppdbModal) {
                    closeModal();
                }
            });

            // Event Listener untuk navigasi
            berandaLink.addEventListener('click', (e) => {
                e.preventDefault();
                showPage('beranda');
            });

            ppdbLink.addEventListener('click', (e) => {
                e.preventDefault();
                ppdbModal.style.display = 'block';
                document.body.style.overflow = 'hidden';
            });

            timelineLink.addEventListener('click', (e) => {
                e.preventDefault();
                closeModal(); // Tutup modal dulu
                showPage('ppdb');
            });

            function showPage(page) {
                // Sembunyikan semua halaman
                document.querySelectorAll('.page-section').forEach(p => p.classList.remove('active'));
                // Hapus kelas aktif dari semua link
                document.querySelectorAll('nav ul li a').forEach(l => l.classList.remove('active'));

                if (page === 'beranda') {
                    berandaPage.classList.add('active');
                    berandaLink.classList.add('active');
                } else if (page === 'ppdb') {
                    ppdbPage.classList.add('active');
                    ppdbLink.classList.add('active');
                }
            }

            // Fungsi untuk menyaring berita (logika diubah)
            const filterNews = () => {
                let filteredNews = newsData;

                // Filter berdasarkan kategori (logika baru)
                const filterNewsByCategory = (category) => {
                    currentFilter = category;
                displayNews(category);
            };

                // Filter berdasarkan pencarian
                const searchTerm = searchInput.value.toLowerCase();
                if (searchTerm) {
                    filteredNews = filteredNews.filter(news =>
                        news.title.toLowerCase().includes(searchTerm) ||
                        news.summary.toLowerCase().includes(searchTerm) ||
                        news.category.toLowerCase().includes(searchTerm)
                    );
                    // Jika ada pencarian, tampilkan hasil pencarian saja
                    newsGrid.innerHTML = '';
                    if (filteredNews.length === 0) {
                        newsGrid.innerHTML = '<p style="grid-column: 1/-1; text-align: center; font-size: 1.1rem; color: var(--text-color);">Berita tidak ditemukan.</p>';
                    } else {
                        filteredNews.forEach(news => {
                            newsGrid.appendChild(createNewsCard(news));
                        });
                    }
                } else {
                    // Jika tidak ada pencarian, tampilkan berdasarkan filter kategori
                    displayNews(currentFilter);
                }
            };

            // Event Listener untuk tombol filter
            filterBtns.forEach(btn => {
    btn.addEventListener('click', () => {
        filterBtns.forEach(b => b.classList.remove('active'));
        btn.classList.add('active');

        const category = btn.dataset.category;
        if(category === 'semua') {
            displayNews();
        } else {
            displayNews(category);
        }
    });
});

            // Event Listener untuk pencarian
            searchButton.addEventListener('click', () => {
                const keyword = searchInput.value.toLowerCase();
                const filteredNews = newsData.filter(news => 
                    news.title.toLowerCase().includes(keyword) && 
                    (currentFilter === 'semua' || news.category === currentFilter)
                );
                newsGrid.innerHTML = '';
                filteredNews.forEach(news => {
                    newsGrid.appendChild(createNewsCard(news));
                });
            });

            // Tampilkan semua berita saat halaman dimuat
            displayNews('semua');
        });
    </script>
</body>
</html>
