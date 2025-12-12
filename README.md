#Zapytanie 1 do bazy danych:


SELECT Rodzaj, Nazwa, Gramatura, Cena
FROM wyroby
WHERE Rodzaj = 'INNE';

Komenda/Klauzula,Opis
SELECT,"Wskazuje kolumny, które mają zostać zwrócone w wyniku zapytania."
FROM wyroby,"Wskazuje tabelę, z której dane mają być pobrane (w tym przypadku wyroby)."
WHERE,"Służy do filtrowania wierszy. Określa warunek, który musi być spełniony, aby wiersz został włączony do wyniku."
'INNE',"Warunek filtrujący: tylko wiersze, gdzie wartość w kolumnie Rodzaj jest równa 'INNE'."

