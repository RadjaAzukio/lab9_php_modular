# lab9_php_modular


### Header
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/css" media="screen" />
    <style>
        .container {
            text-align: center;
        }

        nav {
            display: inline-block;
        }
    </style>
</head>

<body>
    <div class="container">
        <header>
            <h1>Modularisasi Menggunakan Require</h1>
        </header>
        <nav>
            <a href="home.php">Home</a>
            <a href="about.php">Tentang</a>
            <a href="kontak.php">Kontak</a>
            <a href="index.php">Data Barang</a>
        </nav>
    </div>
</body>

</html>
```
##### Tampilan Header
![image](https://github.com/RadjaAzukio/lab9_php_modular/assets/115551911/4732ee38-72b2-407f-9495-798b7db381d5)


### Menu/Index
```
<?php
include("koneksi.php");
// Fungsi hapus data
if (isset($_GET['action']) && $_GET['action'] == 'hapus' && isset($_GET['id_barang'])) {
    $id_barang_hapus = $_GET['id_barang'];

    // Lakukan proses hapus data di database
    $sql_hapus = "DELETE FROM data_barang WHERE id_barang = $id_barang_hapus";
    mysqli_query($conn, $sql_hapus);
}
// query untuk menampilkan data
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);
?>
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <link href="style.css" rel="stylesheet" type="text/css" />
    <title>Data Barang</title>
</head>
<?php require('header.php'); ?>

<body>
    <div class="container">
        <h1>Data Barang</h1>
        <div class="main">
            <table>
                <a href="tambah.php">Tambah</a>
                <tr>
                    <th>Gambar</th>
                    <th>Nama Barang</th>
                    <th>Kategori</th>
                    <th>Harga Jual</th>
                    <th>Harga Beli</th>
                    <th>Stok</th>
                    <th>Aksi</th>
                </tr>
                <?php if ($result) : ?>
                    <?php while ($row = mysqli_fetch_array($result)) : ?>
                        <tr>
                            <td>
                                <img src="gambar/<?= $row['gambar']; ?>" alt="<?= $row['nama']; ?>" style="width: 100px;">
                            </td>
                            <td><?= $row['nama']; ?></td>
                            <td><?= $row['kategori']; ?></td>
                            <td><?= $row['harga_beli']; ?></td>
                            <td><?= $row['harga_jual']; ?></td>
                            <td><?= $row['stok']; ?></td>
                            <td><?= $row['id_barang']; ?>
                                <a href="ubah.php?id=<?= $row['id_barang']; ?>">Ubah</a>
                                <a href="?action=hapus&id_barang=<?= $row['id_barang']; ?>" onclick="return confirm('Anda yakin ingin menghapus data ini?')">Hapus</a>
                            </td>
                        </tr>
                    <?php endwhile;
                else : ?>
                    <tr>
                        <td colspan="7">Belum ada data</td>
                    </tr>
                <?php endif; ?>
            </table>
        </div>
    </div>
</body>
<?php require('footer.php'); ?>

</html>
```

##### Tampilan Menu/Index
![image](https://github.com/RadjaAzukio/lab9_php_modular/assets/115551911/8ccdcbee-b123-4cd8-a833-c3f181be2e09)

### Footer
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            margin: 0;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        footer {
            text-align: center;
            padding: 10px;
            background-color: #f2f2f2;
            /* Tambahkan warna latar belakang sesuai kebutuhan */
        }
    </style>
</head>

<body>
    <div class="container">
        <!-- Konten halaman Anda di sini -->

        <footer>
            <p>&copy; 2023, Informatika, Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>

</html>
```

##### Tampilan Footer
![image](https://github.com/RadjaAzukio/lab9_php_modular/assets/115551911/60809391-7999-408a-b1d3-b27f042031c3)


### Hasil Akhir Sebelum dan Setelah Diberi Header&Footer
![image](https://github.com/RadjaAzukio/lab9_php_modular/assets/115551911/879b1b2e-4e52-46d5-bb90-a64890b3c428)
![image](https://github.com/RadjaAzukio/lab9_php_modular/assets/115551911/c1ac617d-9fb0-4cd3-af49-09a1bba8367a)

