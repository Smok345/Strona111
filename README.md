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

http://localhost/sklep/index.html

rezultat:

<img width="861" height="595" alt="image" src="https://github.com/user-attachments/assets/75377143-3057-42da-b6df-e9ece625eaef" />


po wciśnięciu przycisku przejdź do produktów przekierowuje nas do strony z produktami gdzie możemy sortować dane:

http://localhost/sklep/produkty.php?kategoria=3&szukaj=

<img width="569" height="269" alt="image" src="https://github.com/user-attachments/assets/d4f34102-bd19-422f-8a90-015cf03152f0" />

tutaj możemy wybierać kategorie np Akcesoria:

<img width="510" height="125" alt="image" src="https://github.com/user-attachments/assets/5df1f9a6-059a-4f4f-b281-a5955b5a1af8" />

-----------------------------------------------------------------------------------------------------------------------------------------
Na dodatkową ocene:
#Co zmieniłem:


$sortowanie = isset($_GET['sort']) ? $_GET['sort'] : "cena_asc";
switch ($sortowanie) {
    case 'cena_desc': $order_sql = "p.cena DESC"; break;
    case 'nazwa_asc': $order_sql = "p.nazwa ASC"; break;
    case 'data_desc': $order_sql = "p.data_dodania DESC"; break;
    default:          $order_sql = "p.cena ASC"; break;
}
<label>Sortuj według:
    <select name="sort">
        <option value="cena_asc" <?php if($sortowanie == 'cena_asc') echo 'selected'; ?>>Ceny (rosnąco)</option>
        <option value="cena_desc" <?php if($sortowanie == 'cena_desc') echo 'selected'; ?>>Ceny (malejąco)</option>
        ...
    </select>
</label>


----------------------------------------------------------------------------------------------------------------------------------------

Rezultat:

<img width="781" height="291" alt="image" src="https://github.com/user-attachments/assets/208cb4e9-0bba-4db6-a8c7-0a7ddf2faf62" />

<img width="780" height="270" alt="image" src="https://github.com/user-attachments/assets/5ed2d3a2-f79d-4a28-a9ed-515aa0b91f8b" />



-------------------------------------------------------------------------------------------------------------------------------------------------------------

