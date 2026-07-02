<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Muria Cool - Spesialis Pasang & Perbaikan AC Kudus</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #0056b3;
            --secondary-color: #00b4d8;
            --dark-color: #0f172a;
            --light-color: #f8fafc;
            --snow-color: #e2e8f0;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: var(--dark-color);
            color: var(--light-color);
            overflow-x: hidden;
            position: relative;
        }

        /* Canvas untuk Efek Salju */
        #snowCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        /* Running Text / Marquee */
        .running-text {
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 8px 0;
            font-size: 0.9rem;
            font-weight: 600;
            position: relative;
            z-index: 10;
            box-shadow: 0 4px 15px rgba(0, 180, 216, 0.3);
        }

        /* Header & Jam */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(15, 23, 42, 0.8);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            position: sticky;
            top: 0;
            z-index: 10;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: white;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .logo span {
            color: var(--secondary-color);
        }

        .digital-clock {
            background: rgba(255, 255, 255, 0.05);
            padding: 8px 15px;
            border-radius: 20px;
            border: 1px solid rgba(0, 180, 216, 0.3);
            font-weight: 600;
            color: var(--secondary-color);
            box-shadow: 0 0 10px rgba(0, 180, 216, 0.1);
        }

        /* Hero / Welcome Section */
        .hero {
            padding: 60px 5% 40px;
            text-align: center;
            position: relative;
            z-index: 5;
        }

        .welcome-badge {
            background: rgba(0, 180, 216, 0.1);
            color: var(--secondary-color);
            padding: 6px 16px;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 15px;
            border: 1px solid rgba(0, 180, 216, 0.2);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .hero h1 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 15px;
            line-height: 1.2;
        }

        .hero p {
            color: #94a3b8;
            max-width: 600px;
            margin: 0 auto;
            font-size: 1rem;
        }

        /* Container Utama Form */
        .main-container {
            max-width: 600px;
            margin: 0 auto 80px;
            padding: 0 20px;
            position: relative;
            z-index: 5;
        }

        .booking-card {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 24px;
            padding: 35px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .form-group {
            margin-bottom: 25px;
        }

        .form-group label {
            display: block;
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 8px;
            color: #cbd5e1;
        }

        .form-control {
            width: 100%;
            padding: 14px 16px;
            background: rgba(15, 23, 42, 0.6);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            color: white;
            font-size: 0.95rem;
            transition: all 0.3s ease;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--secondary-color);
            box-shadow: 0 0 15px rgba(0, 180, 216, 0.2);
        }

        select.form-control {
            cursor: pointer;
        }

        /* Aturan tampilan opsi select di beberapa browser */
        select.form-control option {
            background-color: var(--dark-color);
            color: white;
        }

        textarea.form-control {
            resize: vertical;
            min-height: 110px;
        }

        /* Tombol Order WA */
        .btn-submit {
            width: 100%;
            padding: 16px;
            background: linear-gradient(135deg, #00b4d8, #0077b6);
            border: none;
            border-radius: 12px;
            color: white;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            box-shadow: 0 8px 20px rgba(0, 180, 216, 0.3);
        }

        .btn-submit:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 25px rgba(0, 180, 216, 0.4);
        }

        .btn-submit:active {
            transform: translateY(1px);
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 20px;
            font-size: 0.8rem;
            color: #64748b;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            background: rgba(15, 23, 42, 0.9);
            position: relative;
            z-index: 5;
        }

        /* Responsif Mobile */
        @media (max-width: 480px) {
            header { padding: 15px 4%; }
            .hero h1 { font-size: 2rem; }
            .booking-card { padding: 25px 20px; }
        }
    </style>
</head>
<body>

    <!-- Efek Latar Belakang Salju -->
    <canvas id="snowCanvas"></canvas>

    <!-- Running Text Teratas -->
    <div class="running-text">
        <marquee behavior="scroll" direction="left" scrollamount="6">
            ❄️ Nikmati Kembali Udara Sejuk dan Segar Beserta Muria Cool Kudus — Layanan Cepat, Rapi, Profesional, dan Bergaransi! ❄️
        </marquee>
    </div>

    <!-- Navigasi / Header -->
    <header>
        <div class="logo">MURIA<span>COOL</span></div>
        <div class="digital-clock" id="clock">00:00:00 WIB</div>
    </header>

    <!-- Welcome Section -->
    <section class="hero">
        <div class="welcome-badge">Selamat Datang di Muria Cool</div>
        <h1>Hadirkan Sejuknya Udara Muria<br>ke Ruangan Anda</h1>
        <p>Solusi teknis terbaik untuk pemasangan baru, relokasi unit, dan perbaikan kerusakan segala jenis komponen AC di wilayah Kudus.</p>
    </section>

    <!-- Formulir Pemesanan -->
    <main class="main-container">
        <div class="booking-card">
            <form id="orderForm" onsubmit="sendToWhatsApp(event)">
                
                <!-- Input Pilihan Layanan -->
                <div class="form-group">
                    <label for="layanan">Pilih Jenis Layanan</label>
                    <select id="layanan" class="form-control" required>
                        <option value="" disabled selected>-- Pilih Layanan AC --</option>
                        <option value="Perbaikan / Troubleshooting AC">Perbaikan / Perbaikan AC Kerusakan</option>
                        <option value="Pemasangan AC Baru / Bekas">Pemasangan AC Baru / Bekas</option>
                        <option value="Bongkar Pasang AC (Relokasi)">Bongkar Pasang AC (Pindah Lokasi)</option>
                        <option value="Pengisian / Tambah Freon">Pemeriksaan & Isi Ulang Freon</option>
                    </select>
                </div>

                <!-- Input Detail Keluhan -->
                <div class="form-group">
                    <label for="deskripsi">Deskripsi Keluhan / Detail Kerusakan</label>
                    <textarea id="deskripsi" class="form-control" placeholder="Contoh: AC tidak dingin hanya keluar angin, muncul kode eror, unit outdoor mati, atau pipa bocor menetes air..." required></textarea>
                </div>

                <!-- Input Alamat Pelanggan -->
                <div class="form-group">
                    <label for="alamat">Alamat Lengkap Lokasi</label>
                    <textarea id="alamat" class="form-control" placeholder="Tuliskan alamat lengkap pengerjaan (Nama jalan, nomor rumah, RT/RW, desa/kelurahan, kecamatan di Kudus)..." required></textarea>
                </div>

                <!-- Tombol Submit -->
                <button type="submit" class="btn-submit">
                    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z"></path></svg>
                    Pesan Sekarang via WhatsApp
                </button>
                
            </form>
        </div>
    </main>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 Muria Cool Kudus. Semua Hak Dilindungi.</p>
    </footer>

    <!-- Logic JavaScript -->
    <script>
        // 1. SISTEM JAM DIGITAL REAL-TIME
        function updateClock() {
            const now = new Date();
            let hours = now.getHours().toString().padStart(2, '0');
            let minutes = now.getMinutes().toString().padStart(2, '0');
            let seconds = now.getSeconds().toString().padStart(2, '0');
            document.getElementById('clock').textContent = `${hours}:${minutes}:${seconds} WIB`;
        }
        setInterval(updateClock, 1000);
        updateClock();

        // 2. LOGIK PENGIRIMAN DATA KE WHATSAPP
        function sendToWhatsApp(event) {
            event.preventDefault(); // Mencegah reload halaman formal

            // Mengambil data dari input form
            const nomorWA = "6285124569347"; 
            const layanan = document.getElementById('layanan').value;
            const deskripsi = document.getElementById('deskripsi').value;
            const alamat = document.getElementById('alamat').value;

            // Merangkai teks pesan teks yang rapi untuk dikirim
            const teksPesan = 
                `*Halo Muria Cool, Saya ingin memesan jasa AC* ❄️\n\n` +
                `*Jenis Layanan:* \n${layanan}\n\n` +
                `*Detail Keluhan / Kerusakan:* \n${deskripsi}\n\n` +
                `*Alamat Lokasi Rumah:* \n${alamat}\n\n` +
                `Mohon segera dikonfirmasi jadwal kedatangan teknisinya. Terima kasih!`;

            // Proses encode karakter teks agar valid diletakkan dalam URL tautan
            const urlWhatsApp = `https://api.whatsapp.com/send?phone=${nomorWA}&text=${encodeURIComponent(teksPesan)}`;

            // Membuka tab baru dan langsung mengarahkan ke obrolan WhatsApp sistem nomor tujuan
            window.open(urlWhatsApp, '_blank');
        }

        // 3. EFEK VISUAL SALJU BERGERAK (SNOWFLAKES AUTOMATION)
        const canvas = document.getElementById("snowCanvas");
        const ctx = canvas.getContext("2d");

        let width = (canvas.width = window.innerWidth);
        let height = (canvas.height = window.innerHeight);

        window.addEventListener("resize", function () {
            width = (canvas.width = window.innerWidth);
            height = (canvas.height = window.innerHeight);
        });

        const numFlakes = 45;
        const flakes = [];

        for (let i = 0; i < numFlakes; i++) {
            flakes.push({
                x: Math.random() * width,
                y: Math.random() * height,
                r: Math.random() * 3 + 1, 
                d: Math.random() * numFlakes, 
                vy: Math.random() * 1 + 0.5, 
                vx: Math.random() * 0.5 - 0.25 
            });
        }

        function drawSnow() {
            ctx.clearRect(0, 0, width, height);
            ctx.fillStyle = "rgba(226, 232, 240, 0.6)";
            ctx.beginPath();
            for (let i = 0; i < numFlakes; i++) {
                const f = flakes[i];
                ctx.moveTo(f.x, f.y);
                ctx.arc(f.x, f.y, f.r, 0, Math.PI * 2, true);
            }
            ctx.fill();
            moveSnow();
        }

        function moveSnow() {
            for (let i = 0; i < numFlakes; i++) {
                const f = flakes[i];
                f.y += f.vy;
                f.x += f.vx;

                // Jika butiran salju keluar batas bawah layar, reset kembali ke atas
                if (f.y > height) {
                    flakes[i] = { x: Math.random() * width, y: 0, r: f.r, d: f.d, vy: f.vy, vx: f.vx };
                }
            }
        }

        function runAnimation() {
            drawSnow();
            requestAnimationFrame(runAnimation);
        }
        runAnimation();
    </script>
</body>
</html>
const regionQuery = "Jawa Tengah, DIY, Jawa Timur, Indonesia";
            const response = await fetch(`https://nominatim.openstreetmap.org/search?format=json&q=${query}&viewbox=108.0,-6.0,116.0,-9.0&bounded=1&limit=6&addressdetails=1`);
            const data = await response.json();
            
            resDiv.innerHTML = '';
            if (data.length > 0) {
                resDiv.style.display = 'block';
                data.forEach(item => {
                    const div = document.createElement('div');
                    div.className = 'search-item';
                    // Menampilkan alamat yang lebih rapi
                    const addr = item.display_name.split(',').slice(0, 3).join(',');
                    div.innerHTML = `📍 <b>${addr}</b><br><small style="color:#777">${item.display_name}</small>`;
                    div.onclick = () => {
                        document.getElementById(type).value = addr;
                        resDiv.style.display = 'none';
                        if (type === 'jemput') locJemput = {lat: item.lat, lon: item.lon};
                        else locTujuan = {lat: item.lat, lon: item.lon};
                        if (locJemput && locTujuan) hitungRute();
                    };
                    resDiv.appendChild(div);
                });
            } else {
                resDiv.style.display = 'none';
            }
        }, 600);
    }

    async function ambilLokasiSaya() {
        if (!navigator.geolocation) return alert("Maaf, fitur lokasi tidak didukung oleh perangkat Anda.");
        document.getElementById('jemput').value = "Sedang mendeteksi lokasi Anda... 📡";
        navigator.geolocation.getCurrentPosition(async (pos) => {
            locJemput = {lat: pos.coords.latitude, lon: pos.coords.longitude};
            const response = await fetch(`https://nominatim.openstreetmap.org/reverse?format=json&lat=${locJemput.lat}&lon=${locJemput.lon}`);
            const data = await response.json();
            const addr = data.display_name.split(',').slice(0, 3).join(',');
            document.getElementById('jemput').value = addr;
            if (locTujuan) hitungRute();
        }, () => {
            alert("Gagal mengakses lokasi. Pastikan GPS Anda aktif.");
            document.getElementById('jemput').value = "";
        });
    }

    async function hitungRute() {
        const url = `https://router.project-osrm.org/route/v1/driving/${locJemput.lon},${locJemput.lat};${locTujuan.lon},${locTujuan.lat}?overview=false`;
        try {
            const res = await fetch(url);
            const data = await res.json();
            if (data.routes && data.routes[0]) {
                jarakFinal = (data.routes[0].distance / 1000).toFixed(1);
                hitungTarif();
            }
        } catch (e) {
            console.error("Gagal menghitung rute.");
        }
    }

    function hitungTarif() {
        const hargaPerKm = document.getElementById('layanan').selectedOptions[0].getAttribute('data-harga');
        let jarakNum = parseFloat(jarakFinal);
        // Minimal Rp8.000 untuk jarak <= 2km
        let total = (jarakNum <= 2) ? 8000 : (jarakNum * hargaPerKm);
        document.getElementById('tampilan-tarif').innerText = "Rp" + Math.round(total).toLocaleString('id-ID');
    }

    function prosesPesan() {
        if (jarakFinal <= 0) return alert("Silakan masukkan lokasi penjemputan dan tujuan Anda terlebih dahulu.");
        
        document.getElementById('loading-overlay').style.display = 'flex';
        const msgList = [
            "Sedang mencarikan mitra terbaik untuk Anda... 🛵",
            "Menghitung estimasi waktu perjalanan... 🕒",
            "Menghubungkan ke layanan WhatsApp... ✅"
        ];
        let i = 0;
        const interval = setInterval(() => {
            document.getElementById('loading-text').innerText = msgList[i];
            i++;
            if(i >= msgList.length) clearInterval(interval);
        }, 700);

        setTimeout(() => {
            const teks = encodeURIComponent(`*KONFIRMASI PESANAN SURUH AKUDUS*\n\n` +
                `📋 Layanan: ${document.getElementById('layanan').value}\n` +
                `📍 Jemput: ${document.getElementById('jemput').value}\n` +
                `🏁 Tujuan: ${document.getElementById('tujuan').value}\n` +
                `🛣️ Jarak: ${jarakFinal} KM\n` +
                `💰 Total Tarif: ${document.getElementById('tampilan-tarif').innerText}\n\n` +
                `Mohon segera diproses ya, terima kasih! 🙏`);
            window.open(`https://wa.me/6285124569347?text=${teks}`);
            document.getElementById('loading-overlay').style.display = 'none';
        }, 2500);
    }

    // 3. REVIEW LOGIC
    function simpanReview() {
        const nama = document.getElementById('rev-nama').value;
        const pesan = document.getElementById('rev-pesan').value;
        if (!nama || !pesan) return alert("Mohon lengkapi nama dan ulasan Anda.");

        const reviewBaru = { nama, pesan, tgl: new Date().toLocaleDateString('id-ID') };
        let reviews = JSON.parse(localStorage.getItem('suruh_reviews')) || [];
        reviews.unshift(reviewBaru);
        localStorage.setItem('suruh_reviews', JSON.stringify(reviews));

        document.getElementById('rev-nama').value = '';
        document.getElementById('rev-pesan').value = '';
        tampilkanReview();
    }

    function tampilkanReview() {
        const list = document.getElementById('review-list');
        let reviews = JSON.parse(localStorage.getItem('suruh_reviews')) || [
            {nama: "Budi Pratama", pesan: "Pelayanannya sangat memuaskan dan pengemudinya ramah sekali! ⭐⭐⭐⭐⭐", tgl: "13/02/2026"},
            {nama: "Lestari Wahyuni", pesan: "Jastipnya amanah banget, belanjaan sampai dengan selamat tanpa ada yang kurang. Terima kasih! 🙏", tgl: "12/02/2026"}
        ];
        list.innerHTML = reviews.map(r => `
            <div class="review-item">
                <div class="rev-name"><span>👤 ${r.nama}</span> <span class="rev-date">🗓️ ${r.tgl}</span></div>
                <div class="rev-text">"${r.pesan}"</div>
            </div>
        `).join('');
    }
    tampilkanReview();
</script>
</body>
</html>
