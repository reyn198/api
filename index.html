<?php
$host = "localhost"; $user = "root"; $pass = ""; $db = "db_perpustakaan";
$conn = new mysqli($host, $user, $pass, $db);
if ($conn->connect_error) { die("Koneksi Gagal: " . $conn->connect_error); }

// --- LOGIKA EXPORT JSON ---
if (isset($_GET['print_json'])) {
    header('Content-Type: application/json');
    $res_all = $conn->query("SELECT * FROM buku ORDER BY id DESC");
    $all_data = []; while($row = $res_all->fetch_assoc()) { $all_data[] = $row; }
    echo json_encode(["library" => "Reynold Library", "total" => count($all_data), "books" => $all_data], JSON_PRETTY_PRINT);
    exit();
}

// --- LOGIKA CRUD ---
if (isset($_POST['save'])) {
    $id = $_POST['id']; $k = $conn->real_escape_string($_POST['kode_buku']); 
    $j = $conn->real_escape_string($_POST['judul']); $p = $conn->real_escape_string($_POST['penulis']); 
    $kat = $conn->real_escape_string($_POST['kategori']); $th = $conn->real_escape_string($_POST['tahun_terbit']);
    $ch = (int)$_POST['chapter']; $hal = (int)$_POST['halaman']; $s = (int)$_POST['stok'];
    $gambar = $_POST['gambar_lama'] ?? '';
    if (isset($_FILES['cover']['name']) && $_FILES['cover']['name'] != "") {
        $target_dir = "uploads/"; if (!is_dir($target_dir)) mkdir($target_dir, 0777, true);
        $file_name = time() . "_" . basename($_FILES["cover"]["name"]);
        if (move_uploaded_file($_FILES["cover"]["tmp_name"], $target_dir . $file_name)) {
            if($gambar && file_exists($target_dir.$gambar)) unlink($target_dir.$gambar);
            $gambar = $file_name;
        }
    }
    if ($id) { $conn->query("UPDATE buku SET kode_buku='$k', judul='$j', penulis='$p', tahun_terbit='$th', kategori='$kat', chapter='$ch', halaman='$hal', stok='$s', gambar='$gambar' WHERE id=$id"); }
    else { $conn->query("INSERT INTO buku (kode_buku,judul,penulis,penerbit,tahun_terbit,kategori,chapter,halaman,stok,gambar) VALUES ('$k','$j','$p','Umum','$th','$kat','$ch','$hal','$s', '$gambar')"); }
    header("Location: index.php"); exit();
}

if (isset($_GET['hapus'])) { 
    $res = $conn->query("SELECT gambar FROM buku WHERE id=" . (int)$_GET['hapus']);
    $row = $res->fetch_assoc(); if($row['gambar'] && file_exists("uploads/".$row['gambar'])) unlink("uploads/".$row['gambar']);
    $conn->query("DELETE FROM buku WHERE id=" . (int)$_GET['hapus']); header("Location: index.php"); exit();
}

$q = $conn->real_escape_string($_GET['q'] ?? '');
$sql = "SELECT * FROM buku WHERE judul LIKE '%$q%' OR penulis LIKE '%$q%' OR kategori LIKE '%$q%' ORDER BY id DESC";
$res = $conn->query($sql); $data = []; while($r = $res->fetch_assoc()) { $data[] = $r; }
$edit = isset($_GET['edit']) ? $conn->query("SELECT * FROM buku WHERE id=" . (int)$_GET['edit'])->fetch_assoc() : null;
$categories = ["Action", "Adventure", "Fantasy", "Isekai", "Romance", "Horror", "Filsafat", "Sejarah", "Sains", "Novel", "Panduan", "Cerita Rakyat"];
?>

<!DOCTYPE html>
<html lang="id" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>REYNOLD LIBRARY </title>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;700;800&family=Orbitron:wght@600&display=swap" rel="stylesheet">
    <style>
        /* --- PALET WARNA HARMONIS --- */
        :root {
            --bg: #0f172a; 
            --card: #1e293b; 
            --primary: #38bdf8; /* Soft Cyan */
            --accent: #7dd3fc; 
            --text: #f1f5f9;
            --text-dim: #94a3b8;
            --border: rgba(56, 189, 248, 0.2);
            --input-bg: rgba(15, 23, 42, 0.6);
        }

        [data-theme="light"] {
            --bg: #f8fafc;
            --card: #ffffff;
            --primary: #0284c7; /* Deep Blue */
            --accent: #0ea5e9;
            --text: #0f172a;
            --text-dim: #64748b;
            --border: rgba(2, 132, 199, 0.1);
            --input-bg: #f1f5f9;
        }

        * { box-sizing: border-box; transition: background 0.4s, color 0.4s, border 0.4s, transform 0.3s; }
        
        body { 
            font-family: 'Plus Jakarta Sans', sans-serif; 
            background: var(--bg); 
            color: var(--text);
            margin: 0; min-height: 100vh;
        }

        .container { max-width: 1200px; margin: auto; padding: 0 20px; }

        /* --- NAVIGATION --- */
        nav { 
            backdrop-filter: blur(12px); 
            background: rgba(var(--bg), 0.8);
            border-bottom: 1px solid var(--border);
            padding: 15px 0; position: sticky; top: 0; z-index: 1000;
        }
        .nav-content { display: flex; justify-content: space-between; align-items: center; }
        .logo { font-family: 'Orbitron', sans-serif; font-size: 20px; color: var(--primary); text-decoration: none; letter-spacing: 1px; }

        /* --- GLASS PANEL --- */
        .glass-box { 
            background: var(--card); 
            border: 1px solid var(--border); 
            border-radius: 20px; padding: 25px; 
            margin: 30px 0;
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1);
        }

        .form-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 15px; }
        
        input, select { 
            background: var(--input-bg); border: 1px solid var(--border); 
            padding: 12px; color: var(--text); border-radius: 10px; outline: none; font-size: 14px;
        }
        input:focus { border-color: var(--primary); }

        .btn { 
            padding: 12px 20px; border-radius: 10px; border: none; font-weight: 700; cursor: pointer;
            font-size: 12px; text-transform: uppercase;
        }
        .btn-primary { background: var(--primary); color: #fff; }
        .btn-primary:hover { opacity: 0.9; transform: translateY(-2px); }

        /* --- DATA GRID --- */
        .grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 25px; margin-top: 30px; }
        .card { 
            background: var(--card); border-radius: 20px; overflow: hidden; position: relative;
            border: 1px solid var(--border); height: 340px;
        }
        .card:hover { border-color: var(--primary); transform: translateY(-8px); }
        
        .card-img { width: 100%; height: 100%; object-fit: cover; }
        .card-body { 
            position: absolute; inset: 0; 
            background: linear-gradient(to top, rgba(15, 23, 42, 0.9) 10%, transparent 60%);
            display: flex; flex-direction: column; justify-content: flex-end; padding: 15px;
        }

        .badge { 
            position: absolute; top: 12px; left: 12px; background: var(--primary); color: #fff;
            padding: 5px 10px; border-radius: 8px; font-weight: 800; font-size: 10px;
        }

        .actions { 
            position: absolute; top: 12px; right: 12px; display: flex; gap: 6px; opacity: 0; 
        }
        .card:hover .actions { opacity: 1; }
        .act-btn { width: 32px; height: 32px; border-radius: 50%; display: flex; align-items: center; justify-content: center; background: rgba(0,0,0,0.4); text-decoration: none; border: 1px solid rgba(255,255,255,0.2); }

        /* --- PRINT PDF TABLE --- */
        #printableTable { display: none; }
        
        @media print {
            body * { visibility: hidden; }
            #printableTable, #printableTable * { visibility: visible; }
            #printableTable { display: table; width: 100%; position: absolute; left: 0; top: 0; border-collapse: collapse; }
            #printableTable th, #printableTable td { border: 1px solid #ccc; padding: 10px; text-align: left; color: #000; }
        }

        @media (max-width: 600px) {
            .grid { grid-template-columns: repeat(2, 1fr); gap: 15px; }
        }
    </style>
</head>
<body>

<table id="printableTable">
    <thead>
        <tr>
            <th>No</th>
            <th>Nama Buku</th>
            <th>Rilis</th>
            <th>Genre</th>
            <th>Kode</th>
        </tr>
    </thead>
    <tbody>
        <?php $no=1; foreach($data as $r): ?>
        <tr>
            <td><?= $no++ ?></td>
            <td><?= $r['judul'] ?></td>
            <td><?= $r['tahun_terbit'] ?></td>
            <td><?= $r['kategori'] ?></td>
            <td><?= $r['kode_buku'] ?></td>
        </tr>
        <?php endforeach; ?>
    </tbody>
</table>

<nav class="no-print">
    <div class="container nav-content">
        <a href="index.php" class="logo">REYNOLD <strong>LIBRARY</strong></a>
        <div style="display:flex; gap:10px;">
            <button onclick="toggleTheme()" class="btn" style="background:var(--input-bg); color:var(--text); border:1px solid var(--border);">🌓 TEMA</button>
            <a href="https://wa.me/6285269142008" class="btn btn-primary" style="text-decoration:none">KONTAK</a>
        </div>
    </div>
</nav>

<div class="container no-print">
    <div style="padding: 40px 0; text-align: center;">
        <h1 style="margin:0; font-weight: 800; font-size: 32px; letter-spacing: -1px;">MILIKK MAS<span style="color:var(--primary)">MAS JAWAA</span></h1>
        <p style="color: var(--text-dim); margin-top: 5px;">SEMUA FAVORIT.</p>
    </div>

    <div class="glass-box">
        <form method="POST" enctype="multipart/form-data">
            <input type="hidden" name="id" value="<?= $edit['id'] ?? '' ?>">
            <input type="hidden" name="gambar_lama" value="<?= $edit['gambar'] ?? '' ?>">
            <div class="form-grid">
                <input type="text" name="judul" placeholder="Judul Buku" value="<?= $edit['judul'] ?? '' ?>" required>
                <select name="kategori">
                    <?php foreach($categories as $cat): ?>
                        <option value="<?= $cat ?>" <?= ($edit && $edit['kategori'] == $cat) ? 'selected' : '' ?>><?= $cat ?></option>
                    <?php endforeach; ?>
                </select>
                <input type="number" name="chapter" placeholder="Halaman/Chapter" value="<?= $edit['chapter'] ?? '1' ?>">
                <input type="text" name="tahun_terbit" placeholder="Tahun Rilis" value="<?= $edit['tahun_terbit'] ?? '2024' ?>">
                <input type="text" name="kode_buku" placeholder="Kode Buku" value="<?= $edit['kode_buku'] ?? '' ?>" required>
                <input type="file" name="cover" style="font-size: 11px;">
                <button type="submit" name="save" class="btn btn-primary"><?= $edit ? 'UPDATE' : 'SIMPAN' ?></button>
            </div>
        </form>
    </div>

    <div style="display:flex; gap:15px; margin-bottom: 20px; flex-wrap: wrap;">
        <form method="GET" style="flex-grow: 1;">
            <input type="text" name="q" placeholder="Cari Koleksi..." value="<?= htmlspecialchars($q) ?>" style="width:100%; border-radius: 12px; padding: 12px 20px;">
        </form>
        <button onclick="window.print()" class="btn" style="background:#0ea5e9; color:#fff;">PRINT PDF</button>
        <a href="index.php?print_json=true" target="_blank" class="btn" style="background:#6366f1; color:#fff; text-decoration:none;">JSON</a>
    </div>

    <div class="grid">
        <?php foreach($data as $r): ?>
        <div class="card">
            <div class="badge"><?= $r['kategori'] ?></div>
            
            <div class="actions">
                <a href="index.php?edit=<?= $r['id'] ?>" class="act-btn">✏️</a>
                <a href="index.php?hapus=<?= $r['id'] ?>" class="act-btn" onclick="return confirm('Hapus?')">🗑️</a>
            </div>

            <?php if($r['gambar'] && file_exists("uploads/".$r['gambar'])): ?>
                <img src="uploads/<?= $r['gambar'] ?>" class="card-img">
            <?php else: ?>
                <div style="height:100%; display:flex; align-items:center; justify-content:center; background:var(--input-bg); color:var(--text-dim);">NO_COVER</div>
            <?php endif; ?>

            <div class="card-body">
                <h3 style="margin:0; font-size:16px;"><?= $r['judul'] ?></h3>
                <div style="font-size:11px; color:var(--primary); margin-top:5px; font-weight:700;">
                    <?= $r['kode_buku'] ?> • <?= $r['tahun_terbit'] ?>
                </div>
            </div>
        </div>
        <?php endforeach; ?>
    </div>

    <footer style="text-align:center; padding:40px 0; border-top:1px solid var(--border); margin-top:50px; color:var(--text-dim); font-size:12px;">
        REYNOLD LIBRARY &copy; 2026
    </footer>
</div>

<script>
    function toggleTheme() {
        const h = document.documentElement;
        const n = h.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
        h.setAttribute('data-theme', n);
        localStorage.setItem('theme', n);
    }
    document.documentElement.setAttribute('data-theme', localStorage.getItem('theme') || 'dark');
</script>
</body>
</html>