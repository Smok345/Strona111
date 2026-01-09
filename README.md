## zaczynam od importowania bazy danych oraz prodów.
oraz wklejenia ich do folderu sklep w XAMPP:
<img width="874" height="249" alt="image" src="https://github.com/user-attachments/assets/5e82826c-424e-49ee-8805-b95d3b209757" />
jak mozna zobaczyc to samo pojawia sie w xampp:
<img width="134" height="92" alt="image" src="https://github.com/user-attachments/assets/912556fd-84fe-4242-be39-fbce3ddef68e" />
teraz robie storne internetowa:
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <title>Sklep internetowy</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #333;
            color: white;
            padding: 20px;
        }

        main {
            margin-top: 40px;
        }

        a.button {
            display: inline-block;
            padding: 15px 25px;
            background-color: #007bff;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-size: 18px;
        }

        a.button:hover {
            background-color: #0056b3;
        }

        footer {
            margin-top: 60px;
            padding: 10px;
            background-color: #ddd;
        }
    </style>
</head>
<body>

<header>
    <h1>Witamy w prostym sklepie</h1>
    <p>Projekt HTML + PHP + MySQL</p>
</header>

<main>
    <p>Ta strona prezentuje listę produktów pobieranych z bazy danych.</p>
    <p>Kliknij przycisk poniżej, aby zobaczyć produkty.</p>

    <a href="produkty.php" class="button">Przejdź do produktów</a>
</main>

<footer>
    <p>© 2026 Sklep internetowy – projekt szkolny</p>
</footer>

</body>
</html>
--------------------------------------------------------------------------------------------------------------
Zapisuje to jako pli html i wklejam tam gdzie mam folder pliki i baze danych:
<img width="934" height="306" alt="image" src="https://github.com/user-attachments/assets/57cddb78-b765-4af7-a13c-dfed85c94f59" />


