#Zapytanie 1 do bazy danych:


SELECT Rodzaj, Nazwa, Gramatura, Cena
FROM wyroby
WHERE Rodzaj = 'INNE';

Komenda/Klauzula,Opis
SELECT,"Wskazuje kolumny, które mają zostać zwrócone w wyniku zapytania."
FROM wyroby,"Wskazuje tabelę, z której dane mają być pobrane (w tym przypadku wyroby)."
WHERE,"Służy do filtrowania wierszy. Określa warunek, który musi być spełniony, aby wiersz został włączony do wyniku."
'INNE',"Warunek filtrujący: tylko wiersze, gdzie wartość w kolumnie Rodzaj jest równa 'INNE'."


#Zadnaie2: Cel: Wybór unikalnych, posortowanych malejąco rodzajów wyrobów.


SQL:

SELECT DISTINCT Rodzaj
FROM wyroby
ORDER BY Rodzaj DESC;

Komenda/Klauzula,Opis
SELECT DISTINCT,"Instrukcja SELECT połączona z klauzulą DISTINCT. DISTINCT zapewnia, że w zwróconym zestawie wyników każda wartość w kolumnie Rodzaj pojawi się tylko raz (eliminuje duplikaty)."
ORDER BY,Służy do sortowania zwróconych wyników.
Rodzaj DESC,Sortuje wyniki na podstawie kolumny Rodzaj w kolejności malejącej (DESC - Descending).

