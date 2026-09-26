# Jaringan-komputer
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Praktikum Jaringan Komputer - LAN & File Sharing</title>
    <!-- Google Fonts & FontAwesome Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        :root {
            --bg-main: #0f172a;
            --bg-card: #1e293b;
            --bg-card-hover: #334155;
            --accent-primary: #6366f1;
            --accent-secondary: #06b6d4;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border-color: #334155;
            --radius-lg: 16px;
            --radius-md: 10px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Plus Jakarta Sans', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-main);
            line-height: 1.6;
        }

        /* Container */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header / Identity Banner */
        header {
            background: linear-gradient(135deg, rgba(99, 102, 241, 0.15) 0%, rgba(6, 182, 212, 0.15) 100%);
            border-bottom: 1px solid var(--border-color);
            padding: 40px 0;
            margin-bottom: 40px;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
        }

        .header-title h1 {
            font-size: 2.2rem;
            font-weight: 800;
            background: linear-gradient(to right, #818cf8, #22d3ee);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 8px;
        }

        .header-title p {
            color: var(--text-muted);
            font-size: 1.1rem;
        }

        .identity-card {
            background-color: var(--bg-card);
            border: 1px solid var(--border-color);
            padding: 20px;
            border-radius: var(--radius-lg);
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px 20px;
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.3);
        }

        .identity-item {
            font-size: 0.9rem;
        }

        .identity-item span {
            color: var(--text-muted);
            display: block;
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .identity-item strong {
            color: var(--text-main);
        }

        /* Navigation */
        nav {
            background: rgba(30, 41, 59, 0.8);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 40px;
        }

        nav .container {
            display: flex;
            justify-content: center;
            gap: 15px;
            padding: 12px 20px;
            overflow-x: auto;
        }

        nav a {
            color: var(--text-muted);
            text-decoration: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            white-space: nowrap;
        }

        nav a:hover, nav a.active {
            color: var(--text-main);
            background-color: var(--accent-primary);
        }

        /* Section Styling */
        section {
            margin-bottom: 60px;
        }

        .section-header {
            margin-bottom: 25px;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .section-header i {
            font-size: 1.8rem;
            color: var(--accent-secondary);
        }

        .section-header h2 {
            font-size: 1.6rem;
            font-weight: 700;
        }

        /* Tools Grid */
        .tools-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
        }

        .tool-card {
            background-color: var(--bg-card);
            border: 1px solid var(--border-color);
            padding: 25px;
            border-radius: var(--radius-lg);
            text-align: center;
            transition: transform 0.3s ease, border-color 0.3s ease;
        }

        .tool-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-primary);
        }

        .tool-card i {
            font-size: 2.5rem;
            color: var(--accent-primary);
            margin-bottom: 15px;
        }

        .tool-card h3 {
            font-size: 1.1rem;
            margin-bottom: 8px;
        }

        .tool-card p {
            color: var(--text-muted);
            font-size: 0.85rem;
        }

        /* Steps Layout */
        .steps-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .step-card {
            background-color: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-lg);
            padding: 25px;
            display: flex;
            gap: 20px;
            align-items: flex-start;
        }

        .step-number {
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            flex-shrink: 0;
        }

        .step-content h3 {
            margin-bottom: 8px;
            font-size: 1.2rem;
        }

        .step-content p, .step-content ul {
            color: var(--text-muted);
            font-size: 0.95rem;
        }

        .step-content ul {
            margin-left: 20px;
            margin-top: 8px;
        }

        /* Pinout Cable Color Code */
        .cable-color-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 15px;
        }

        .color-box {
            background-color: rgba(15, 23, 42, 0.6);
            border: 1px solid var(--border-color);
            padding: 15px;
            border-radius: var(--radius-md);
        }

        .color-box h4 {
            color: var(--accent-secondary);
            margin-bottom: 10px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 5px;
        }

        .color-list {
            list-style: none !important;
            margin-left: 0 !important;
        }

        .color-list li {
            padding: 4px 0;
            font-size: 0.85rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .badge-color {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            display: inline-block;
        }

        /* PPT & Video Grid */
        .media-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
        }

        .media-card {
            background-color: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-lg);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        .media-header {
            padding: 15px 20px;
            background-color: rgba(0, 0, 0, 0.2);
            border-bottom: 1px solid var(--border-color);
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .media-body {
            padding: 20px;
            flex-grow: 1;
        }

        .media-footer {
            padding: 15px 20px;
            border-top: 1px solid var(--border-color);
            background-color: rgba(0, 0, 0, 0.1);
        }

        /* Form Controls */
        .upload-box {
            border: 2px dashed var(--border-color);
            border-radius: var(--radius-md);
            padding: 20px;
            text-align: center;
            background-color: rgba(15, 23, 42, 0.4);
            cursor: pointer;
            transition: border-color 0.3s;
        }

        .upload-box:hover {
            border-color: var(--accent-primary);
        }

        .upload-box i {
            font-size: 2rem;
            color: var(--text-muted);
            margin-bottom: 8px;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            width: 100%;
            padding: 12px 20px;
            background: linear-gradient(135deg, var(--accent-primary), #4f46e5);
            color: white;
            border: none;
            border-radius: var(--radius-md);
            font-weight: 600;
            cursor: pointer;
            text-decoration: none;
            transition: opacity 0.3s ease;
        }

        .btn:hover {
            opacity: 0.9;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                align-items: flex-start;
            }
            .identity-card {
                width: 100%;
                grid-template-columns: 1fr;
            }
            .step-card {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>

    <!-- Header Section -->
    <header>
        <div class="container header-content">
            <div class="header-title">
                <h1>Modul Praktikum Jaringan Komputer</h1>
                <p>Panduan Krimping Kabel UTP, Koneksi 2 Laptop, & File Sharing</p>
            </div>
            
            <div class="identity-card">
                <div class="identity-item">
                    <span>Nama Mahasiswa</span>
                    <strong>Nisa Meidina</strong>
                </div>
                <div class="identity-item">
                    <span>NIM</span>
                    <strong>062640723208</strong>
                </div>
                <div class="identity-item">
                    <span>Kelas / Jurusan</span>
                    <strong>1-TIA / Teknik Komputer</strong>
                </div>
                <div class="identity-item">
                    <span>Program Studi</span>
                    <strong>D4 TIMD</strong>
                </div>
                <div class="identity-item" style="grid-column: span 2;">
                    <span>Dosen Pengampu</span>
                    <strong>Dr. Ali Firdaus, S.Kom., M.Kom.</strong>
                </div>
            </div>
        </div>
    </header>

    <!-- Navigation -->
    <nav>
        <div class="container">
            <a href="#peralatan"><i class="fa-solid fa-toolbox"></i> Alat & Bahan</a>
            <a href="#krimping"><i class="fa-solid fa-network-wired"></i> Merangkai Kabel LAN</a>
            <a href="#koneksi"><i class="fa-solid fa-laptop"></i> Hubungkan 2 Laptop</a>
            <a href="#sharing"><i class="fa-solid fa-folder-open"></i> Sharing File</a>
            <a href="#ppt-section"><i class="fa-solid fa-file-powerpoint"></i> PPT Presentasi</a>
            <a href="#video-section"><i class="fa-solid fa-video"></i> Video Tutorial</a>
        </div>
    </nav>

    <div class="container">

        <!-- Alat dan Bahan -->
        <section id="peralatan">
            <div class="section-header">
                <i class="fa-solid fa-tools"></i>
                <h2>Peralatan yang Dibutuhkan</h2>
            </div>
            <div class="tools-grid">
                <div class="tool-card">
                    <i class="fa-solid fa-ethernet"></i>
                    <h3>Kabel UTP</h3>
                    <p>Media transmisi data standar (Cat5e / Cat6) untuk membuat jaringan LAN.</p>
                </div>
                <div class="tool-card">
                    <i class="fa-solid fa-plug"></i>
                    <h3>Konektor RJ45</h3>
                    <p>Konektor standar tempat pin kabel UTP dimasukkan dan dikunci.</p>
                </div>
                <div class="tool-card">
                    <i class="fa-solid fa-scissors"></i>
                    <h3>Tang Crimping</h3>
                    <p>Alat khusus untuk mengupas kabel, memotong wire, dan mengunci RJ45.</p>
                </div>
                <div class="tool-card">
                    <i class="fa-solid fa-microchip"></i>
                    <h3>LAN Tester</h3>
                    <p>Alat penguji kontinuitas sinyal untuk memastikan 8 pin terhubung sempurna.</p>
                </div>
            </div>
        </section>

        <!-- Merangkai Kabel LAN -->
        <section id="krimping">
            <div class="section-header">
                <i class="fa-solid fa-network-wired"></i>
                <h2>Langkah Merangkai Kabel LAN</h2>
            </div>
            <div class="steps-container">
                <div class="step-card">
                    <div class="step-number">1</div>
                    <div class="step-content">
                        <h3>Kupas Jaket Luar Kabel</h3>
                        <p>Gunakan pisau pemotong pada tang crimping untuk mengupas pembungkus luar kabel UTP sekitar 2 cm secara hati-hati agar serat dalam tidak terpotong.</p>
                    </div>
                </div>

                <div class="step-card">
                    <div class="step-number">2</div>
                    <div class="step-content">
                        <h3>Luruskan dan Urutkan Warna Kabel</h3>
                        <p>Pisahkan tiap pasang kabel lalu luruskan. Susun sesuai standar standar urutan pinout yang dibutuhkan:</p>
                        
                        <div class="cable-color-grid">
                            <div class="color-box">
                                <h4>Standar Straight (T568B - T568B)</h4>
                                <p style="font-size:0.8rem; margin-bottom:8px;">Digunakan untuk perangkat berbeda (Laptop to Switch)</p>
                                <ul class="color-list">
                                    <li><span class="badge-color" style="background:#ff9933;"></span>1. Putih-Orange</li>
                                    <li><span class="badge-color" style="background:#ff6600;"></span>2. Orange</li>
                                    <li><span class="badge-color" style="background:#99ccff;"></span>3. Putih-Hijau</li>
                                    <li><span class="badge-color" style="background:#0066ff;"></span>4. Biru</li>
                                    <li><span class="badge-color" style="background:#66b2ff;"></span>5. Putih-Biru</li>
                                    <li><span class="badge-color" style="background:#00cc44;"></span>6. Hijau</li>
                                    <li><span class="badge-color" style="background:#d9b38c;"></span>7. Putih-Cokelat</li>
                                    <li><span class="badge-color" style="background:#663300;"></span>8. Cokelat</li>
                                </ul>
                            </div>
                            <div class="color-box">
                                <h4>Standar Crossover (T568A ke T568B)</h4>
                                <p style="font-size:0.8rem; margin-bottom:8px;">Digunakan untuk perangkat sejenis (Laptop to Laptop)</p>
                                <p style="font-size:0.85rem; color:var(--text-muted);">Ujung A memakai standar T568A, Ujung B memakai standar T568B.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="step-card">
                    <div class="step-number">3</div>
                    <div class="step-content">
                        <h3>Potong Rata & Masukkan ke Konektor RJ45</h3>
                        <p>Ratakan ujung 8 kawat kabel menggunakan pisau tang crimping (sisa panjanga ± 1.5 cm). Masukkan kabel ke dalam konektor RJ45 hingga posisi kawat menembus sampai ujung tembaga konektor.</p>
                    </div>
                </div>

                <div class="step-card">
                    <div class="step-number">4</div>
                    <div class="step-content">
                        <h3>Press / Crimp Konektor</h3>
                        <p>Masukkan konektor RJ45 yang telah terpasang kabel ke slot tang crimping. Tekan gagang tang crimping dengan kuat sampai terdengar bunyi "klik" atau tembaga mengunci kawat.</p>
                    </div>
                </div>

                <div class="step-card">
                    <div class="step-number">5</div>
                    <div class="step-content">
                        <h3>Uji Menggunakan LAN Tester</h3>
                        <p>Masukkan kedua ujung kabel ke master & remote pada LAN Tester. Nyalakan alat: Jika urutan lampu indikator nomor 1 sampai 8 menyala bergantian sesuai standar, kabel siap digunakan.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Menghubungkan 2 Laptop -->
        <section id="koneksi">
            <div class="section-header">
                <i class="fa-solid fa-laptop-code"></i>
                <h2>Menghubungkan 2 Laptop via Kabel LAN</h2>
            </div>
            <div class="steps-container">
                <div class="step-card">
                    <div class="step-number"><i class="fa-solid fa-plug"></i></div>
                    <div class="step-content">
                        <h3>1. Colokkan Kabel LAN</h3>
                        <p>Hubungkan ujung kabel RJ45 ke port Ethernet Laptop 1 dan ujung lainnya ke port Ethernet Laptop 2.</p>
                    </div>
                </div>
                <div class="step-card">
                    <div class="step-number"><i class="fa-solid fa-gear"></i></div>
                    <div class="step-content">
                        <h3>2. Konfigurasi IP Address Laptop 1 (Host A)</h3>
                        <ul>
                            <li>Buka <strong>Control Panel > Network and Internet > Network and Sharing Center</strong>.</li>
                            <li>Klik pada koneksi <strong>Ethernet</strong> > Pilih <strong>Properties</strong>.</li>
                            <li>Klik 2x pada <strong>Internet Protocol Version 4 (TCP/IPv4)</strong>.</li>
                            <li>Pilih "Use the following IP address":
                                <br>• IP Address: <code>192.168.1.1</code>
                                <br>• Subnet Mask: <code>255.255.255.0</code>
                            </li>
                            <li>Klik OK.</li>
                        </ul>
                    </div>
                </div>
                <div class="step-card">
                    <div class="step-number"><i class="fa-solid fa-gear"></i></div>
                    <div class="step-content">
                        <h3>3. Konfigurasi IP Address Laptop 2 (Host B)</h3>
                        <ul>
                            <li>Lakukan langkah yang sama seperti Laptop 1.</li>
                            <li>Atur pengaturan IPv4:
                                <br>• IP Address: <code>1
