#Zapytanie 1 do bazy danych:


SELECT Rodzaj, Nazwa, Gramatura, Cena
FROM wyroby
WHERE Rodzaj = 'INNE';

Komenda/Klauzula,Opis
SELECT,"Wskazuje kolumny, które mają zostać zwrócone w wyniku zapytania."
FROM wyroby,"Wskazuje tabelę, z której dane mają być pobrane (w tym przypadku wyroby)."
WHERE,"Służy do filtrowania wierszy. Określa warunek, który musi być spełniony, aby wiersz został włączony do wyniku."
'INNE',"Warunek filtrujący: tylko wiersze, gdzie wartość w kolumnie Rodzaj jest równa 'INNE'."
<img width="586" height="670" alt="obraz" src="https://github.com/user-attachments/assets/6687cdfc-72cd-437d-affe-7e887d5aaa3c" />




#Zadnaie2: 
Cel: Wybór unikalnych, posortowanych malejąco rodzajów wyrobów.


SQL:

SELECT DISTINCT Rodzaj
FROM wyroby
ORDER BY Rodzaj DESC;

Komenda/Klauzula,Opis
SELECT DISTINCT,"Instrukcja SELECT połączona z klauzulą DISTINCT. DISTINCT zapewnia, że w zwróconym zestawie wyników każda wartość w kolumnie Rodzaj pojawi się tylko raz (eliminuje duplikaty)."
ORDER BY,Służy do sortowania zwróconych wyników.
Rodzaj DESC,Sortuje wyniki na podstawie kolumny Rodzaj w kolejności malejącej (DESC - Descending).

<img width="522" height="820" alt="obraz" src="https://github.com/user-attachments/assets/16be47f0-a334-4550-a318-e29d515bb3d4" />



#Zadanie 4: 
Cel: Wybór pól ID oraz Nazwa dla wyrobów, których nazwa zawiera słowo "Chałka".

Kwerenda:
SQL

SELECT ID, Nazwa
FROM wyroby
WHERE Nazwa LIKE '%Chałka%';

Opis:
Komenda/Klauzula,Opis
WHERE,Służy do filtrowania wierszy.
LIKE,Operator używany w klauzuli WHERE do wyszukiwania określonego wzorca w kolumnie.
'%Chałka%',"Wzorzec wyszukiwania. Znak % (procent) jest symbolem wieloznacznym, który zastępuje dowolną sekwencję znaków (lub brak znaków). W tym przypadku oznacza to: znajdź wiersze, w których Nazwa zawiera słowo ""Chałka"" (może być coś przed i coś po)."


Zadanie3:
Cel: Wybór pól ID oraz Nazwa dla wyrobów, których nazwa zawiera słowo "Chałka".

Kwerenda:
SQL

SELECT ID, Nazwa
FROM wyroby
WHERE Nazwa LIKE '%Chałka%';


Opis:
Komenda/Klauzula,Opis
WHERE,Służy do filtrowania wierszy.
LIKE,Operator używany w klauzuli WHERE do wyszukiwania określonego wzorca w kolumnie.
'%Chałka%',"Wzorzec wyszukiwania. Znak % (procent) jest symbolem wieloznacznym, który zastępuje dowolną sekwencję znaków (lub brak znaków). W tym przypadku oznacza to: znajdź wiersze, w których Nazwa zawiera słowo ""Chałka"" (może być coś przed i coś po)."


<img width="755" height="716" alt="obraz" src="https://github.com/user-attachments/assets/1c1cb11f-df15-45ef-93d7-4c6809b64e09" />
#Zadanie4:

Cel: Wybór pola Rodzaj oraz obliczenie średniej ceny dla każdej grupy wyrobów, zaokrąglonej do dwóch miejsc po przecinku, z aliasem "Średnia cena".
Komendy:
SQL

SELECT
    Rodzaj,
    ROUND(AVG(Cena), 2) AS "Średnia cena"
FROM
    wyroby
GROUP BY
    Rodzaj;
Opis:
Komenda/Klauzula,Opis
AVG(Cena),Funkcja agregująca obliczająca średnią wartość kolumny Cena w danej grupie wierszy.
"ROUND(..., 2)",Funkcja matematyczna zaokrąglająca wartość. W tym przypadku zaokrągla wynik AVG(Cena) do 2 miejsc po przecinku.
"AS ""Średnia cena""",Nadaje nowo utworzonej kolumnie obliczeniowej czytelny alias (nazwę).
GROUP BY,Grupuje wiersze o tych samych wartościach w kolumnie Rodzaj w grupy. Funkcja agregująca (AVG) jest następnie stosowana do każdej z tych grup z osobna.


<img width="692" height="828" alt="obraz" src="https://github.com/user-attachments/assets/cb7ddc03-0735-45fb-a419-321bbfa2cbc0" />




