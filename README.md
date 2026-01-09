## zaczynam od importowania bazy danych oraz prodów.
oraz wklejenia ich do folderu sklep w XAMPP:     XAMPP -> htdocs

<img width="874" height="249" alt="image" src="https://github.com/user-attachments/assets/5e82826c-424e-49ee-8805-b95d3b209757" />

jak mozna zobaczyc to samo pojawia sie w xampp:


<img width="134" height="92" alt="image" src="https://github.com/user-attachments/assets/912556fd-84fe-4242-be39-fbce3ddef68e" />

teraz robie storne internetowa:

<img width="494" height="804" alt="image" src="https://github.com/user-attachments/assets/27a8c001-6cf7-42ad-b1e8-3c7cdf570822" />



--------------------------------------------------------------------------------------------------------------
Zapisuje to jako plik html i wklejam tam gdzie mam folder pliki i baze danych:

<img width="934" height="306" alt="image" src="https://github.com/user-attachments/assets/57cddb78-b765-4af7-a13c-dfed85c94f59" />

jak teraz go uruchamiam wypisując:

file:///C:/Users/PREDATOR/Downloads/doxama/htdocs/sklep/strona.html

rezultat:

<img width="1910" height="650" alt="image" src="https://github.com/user-attachments/assets/9281b0c7-42d0-4300-8deb-5961cd11dcb4" />

po wciśnięciu przycisku przejdź do produktów przekierowuje nas do strony z produktami gdzie możemy sortować dane:

http://localhost/sklep/produkty.php?kategoria=3&szukaj=

<img width="569" height="269" alt="image" src="https://github.com/user-attachments/assets/d4f34102-bd19-422f-8a90-015cf03152f0" />

tutaj możemy wybierać kategorie np Akcesoria:

<img width="510" height="125" alt="image" src="https://github.com/user-attachments/assets/5df1f9a6-059a-4f4f-b281-a5955b5a1af8" />

-----------------------------------------------------------------------------------------------------------------------------------------
Na dodatkową ocene:
<?php
$host = "localhost";
$user = "root";
$pass = "";
$db   = "sklep";

$conn = new mysqli($host, $user, $pass, $db);

if ($conn->connect_error) {
    die("Błąd połączenia z bazą: " . $conn->connect_error);
}

$conn->set_charset("utf8mb4");

// Pobranie kategorii do formularza
$sql_kategorie = "SELECT id, nazwa FROM kategorie ORDER BY nazwa";
$wynik_kategorie = $conn->query($sql_kategorie);

// 1. POBIERANIE PARAMETRÓW FILTROWANIA I SORTOWANIA
$wybrana_kategoria = isset($_GET['kategoria']) ? (int)$_GET['kategoria'] : 0;
$szukaj = isset($_GET['szukaj']) ? trim($_GET['szukaj']) : "";
$sortowanie = isset($_GET['sort']) ? $_GET['sort'] : "cena_asc"; // Domyślna wartość

// 2. LOGIKA USTALANIA KOLEJNOŚCI (ORDER BY)
switch ($sortowanie) {
    case 'cena_desc':
        $order_sql = "p.cena DESC";
        break;
    case 'nazwa_asc':
        $order_sql = "p.nazwa ASC";
        break;
    case 'data_desc':
        $order_sql = "p.data_dodania DESC";
        break;
    case 'cena_asc':
    default:
        $order_sql = "p.cena ASC";
        break;
}

// 3. BUDOWANIE ZAPYTANIA SQL
$sql_produkty = "
    SELECT p.id, p.nazwa, p.opis, p.cena, p.data_dodania, k.nazwa AS kategoria
    FROM produkty p
    LEFT JOIN kategorie k ON p.id_kategorii = k.id
    WHERE 1=1
";

if ($wybrana_kategoria > 0) {
    $sql_produkty .= " AND p.id_kategorii = " . $wybrana_kategoria;
}

if ($szukaj !== "") {
    $szukaj_esc = $conn->real_escape_string($szukaj);
    $sql_produkty .= " AND p.nazwa LIKE '%" . $szukaj_esc . "%'";
}

// Dołączamy wybrane sortowanie
$sql_produkty .= " ORDER BY " . $order_sql;

$wynik_produkty = $conn->query($sql_produkty);
?>
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <title>Lista produktów</title>
    <style>
        table, th, td { border: 1px solid #000; border-collapse: collapse; padding: 8px; }
        th { background-color: #eee; }
        form { margin-bottom: 20px; background-color: #f5f5f5; padding: 15px; border: 1px solid #ccc; }
        label { margin-right: 10px; font-weight: bold; }
        select, input { margin-right: 20px; }
    </style>
</head>
<body>

<h1>Lista produktów</h1>
<p><a href="index.html">← Powrót do strony głównej</a></p>

<form method="get" action="produkty.php">
    <label>Kategoria:
        <select name="kategoria">
            <option value="0">-- wszystkie --</option>
            <?php
            if ($wynik_kategorie && $wynik_kategorie->num_rows > 0) {
                while ($kat = $wynik_kategorie->fetch_assoc()) {
                    $selected = ($kat['id'] == $wybrana_kategoria) ? 'selected' : '';
                    echo '<option value="' . $kat['id'] . '" ' . $selected . '>' .
                         htmlspecialchars($kat['nazwa']) .
                         '</option>';
                }
            }
            ?>
        </select>
    </label>

    <label>Szukaj:
        <input type="text" name="szukaj" value="<?php echo htmlspecialchars($szukaj); ?>" placeholder="Nazwa produktu...">
    </label>

    <label>Sortuj według:
        <select name="sort">
            <option value="cena_asc" <?php if($sortowanie == 'cena_asc') echo 'selected'; ?>>Ceny (rosnąco)</option>
            <option value="cena_desc" <?php if($sortowanie == 'cena_desc') echo 'selected'; ?>>Ceny (malejąco)</option>
            <option value="nazwa_asc" <?php if($sortowanie == 'nazwa_asc') echo 'selected'; ?>>Nazwy (A-Z)</option>
            <option value="data_desc" <?php if($sortowanie == 'data_desc') echo 'selected'; ?>>Daty (od najnowszych)</option>
        </select>
    </label>

    <button type="submit">Zastosuj</button>
</form>

<table>
    <tr>
        <th>ID</th>
        <th>Nazwa</th>
        <th>Kategoria</th>
        <th>Opis</th>
        <th>Cena</th>
        <th>Data dodania</th>
    </tr>
<?php
if ($wynik_produkty && $wynik_produkty->num_rows > 0) {
    while ($row = $wynik_produkty->fetch_assoc()) {
        echo "<tr>";
        echo "<td>" . $row['id'] . "</td>";
        echo "<td>" . htmlspecialchars($row['nazwa']) . "</td>";
        echo "<td>" . htmlspecialchars($row['kategoria']) . "</td>";
        echo "<td>" . htmlspecialchars($row['opis']) . "</td>";
        echo "<td>" . number_format($row['cena'], 2, ',', ' ') . " zł</td>";
        echo "<td>" . $row['data_dodania'] . "</td>";
        echo "</tr>";
    }
} else {
    echo '<tr><td colspan="6">Brak produktów spełniających kryteria.</td></tr>';
}
$conn->close();
?>
</table>

</body>
</html>









Rezultat:

<img width="781" height="291" alt="image" src="https://github.com/user-attachments/assets/208cb4e9-0bba-4db6-a8c7-0a7ddf2faf62" />
-------------------------------------------------------------------------------------------------------------------------------------------------------------

