<!DOCTYPE html>
<html lang="ms">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JANA e-RPH - Penjana AI</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8f9fa;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
            text-align: center;
        }
        .container {
            background: white;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            max-width: 600px;
            width: 90%;
        }
        .logo {
            width: 80px;
            height: 80px;
            background: #e9ecef;
            border-radius: 50%;
            margin-bottom: 20px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }
        h1 {
            letter-spacing: 2px;
            margin-bottom: 10px;
            color: #333;
        }
        p {
            color: #666;
            line-height: 1.6;
            margin-bottom: 30px;
        }
        .input-group {
            text-align: left;
            margin-bottom: 15px;
        }
        label {
            font-weight: bold;
            display: block;
            margin-bottom: 5px;
        }
        input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
        }
        .button-container {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-top: 25px;
        }
        .btn {
            padding: 15px 25px;
            border: 1px solid #ddd;
            border-radius: 10px;
            background: white;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
            text-transform: uppercase;
            font-size: 0.9rem;
        }
        .btn:hover {
            background: #f0f0f0;
            border-color: #bbb;
        }
        #copyStatus {
            margin-top: 15px;
            color: green;
            font-size: 0.8rem;
            display: none;
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="logo">📖</div>
        <h1>JANA e-RPH</h1>
        <p>Sistem penjanaan Rancangan Pengajaran Harian digital menggunakan teknologi AI untuk memudahkan tugasan guru.</p>

        <div class="input-group">
            <label>Subjek:</label>
            <input type="text" id="subjek" placeholder="Contoh: RBT Tahun 5">
        </div>
        <div class="input-group">
            <label>Standard Kandungan:</label>
            <input type="text" id="sk" placeholder="Contoh: 4.3 Artikel Jahitan">
        </div>
        <div class="input-group">
            <label>Standard Pembelajaran:</label>
            <input type="text" id="sp" placeholder="Contoh: 4.3.1 Mengenal pasti jenis mata jahitan">
        </div>

        <div class="button-container">
            <button class="btn" onclick="generatePrompt()">Klik Untuk Jana Arahan AI</button>
        </div>
        
        <p id="copyStatus">Arahan telah disalin! Sila tampal (Paste) di Gemini AI.</p>
    </div>

    <script>
        function generatePrompt() {
            const subjek = document.getElementById('subjek').value;
            const sk = document.getElementById('sk').value;
            const sp = document.getElementById('sp').value;

            if(!subjek || !sk || !sp) {
                alert("Sila lengkapkan maklumat subjek, SK dan SP.");
                return;
            }

            const fullPrompt = `Anda ialah pembantu guru pintar. Sediakan e-RPH berdasarkan maklumat berikut:
Subjek: ${subjek}
Standard Kandungan: ${sk}
Standard Pembelajaran: ${sp}

Arahan:
1. Sediakan Objektif Pembelajaran berdasarkan standard pembelajaran.
2. Sediakan Kriteria Kejayaan yang jelas boleh diukur.
3. Rancang Aktiviti Pembelajaran yang dibahagikan kepada 3 bahagian:
   a) Set Induksi
   b) Aktiviti Utama
   c) Aktiviti Penutup
4. SYARAT KHAS: Setiap ayat dalam Set Induksi, Aktiviti Utama, dan Aktiviti Penutup MESTI bermula dengan perkataan "Murid".`;

            navigator.clipboard.writeText(fullPrompt).then(() => {
                document.getElementById('copyStatus').style.display = 'block';
            });
        }
    </script>

</body>
</html>
