<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kalkulator Sederhana</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 50px; }
        form { display: inline-block; padding: 20px; border: 1px solid #ccc; border-radius: 10px; }
        input, select, button { margin: 10px; padding: 10px; }
        .hasil { margin-top: 20px; font-size: 18px; color: green; }
    </style>
</head>
<body>
    <h1>Kalkulator Sederhana</h1>
    <form method="POST" action="">
        <input type="number" name="angka1" placeholder="Angka pertama" required step="any">
        <select name="operasi" required>
            <option value="">Pilih operasi</option>
            <option value="+">Penjumlahan (+)</option>
            <option value="-">Pengurangan (-)</option>
            <option value="*">Perkalian (*)</option>
            <option value="/">Pembagian (/)</option>
        </select>
        <input type="number" name="angka2" placeholder="Angka kedua" required step="any">
        <br>
        <button type="submit" name="hitung">Hitung</button>
    </form>

    <?php
    if (isset($_POST['hitung'])) {
        $angka1 = floatval($_POST['angka1']);
        $angka2 = floatval($_POST['angka2']);
        $operasi = $_POST['operasi'];
        $hasil = 0;
        $error = "";

        switch ($operasi) {
            case '+':
                $hasil = $angka1 + $angka2;
                break;
            case '-':
                $hasil = $angka1 - $angka2;
                break;
            case '*':
                $hasil = $angka1 * $angka2;
                break;
            case '/':
                if ($angka2 != 0) {
                    $hasil = $angka1 / $angka2;
                } else {
                    $error = "Error: Pembagian dengan nol tidak diperbolehkan.";
                }
                break;
            default:
                $error = "Operasi tidak valid.";
        }

        if ($error) {
            echo "<div class='hasil' style='color: red;'>$error</div>";
        } else {
            echo "<div class='hasil'>Hasil: " . htmlspecialchars($hasil) . "</div>";
        }
    }
    ?>
</body>
</html># kalkulator
