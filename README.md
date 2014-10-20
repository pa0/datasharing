Jak udostępnić dane statystykowi?
===========

To jest przewodnik dla tych, którzy chcą skorzystać z pomocy statystyka, co wiąże się z przekazaniem mu jakiś danych.
Szczególnie mam na myśli:

* współpracujących nad pracą badawczą
* studentów i doktorantów, którzy potrzebują pomocy w obliczeniach lub konsultacji

Celem tego przewodnika jest spisanie wytycznych, które ułatwią współpracę i wskażą najlepszy sposób udostępniania danych oraz unikania pułapek. Wszyscy statystycy szacują, że proces przygotowania danych zajmuje im 80-95% czasu poświęconego na analizy. Przestrzeganie zawartych tu wskazówek pozwoli uzyskać wyniki bardzo szybko, ponieważ czas statystyka będzie spożytkowany bardziej produktywnie.

Oczywiście statystycy przeważnie potrafią z każdej formy danych przygotować analizowalną formę, ale osoba zbierająca dane zrobi to lepiej i szybciej, ponieważ ma informacje na temat danych, które statystyk często musi zdobyć (co zajmuje czas).

Co powinien otrzymać statystyk?
====================

Dla przyśpieszenia i ułatwienia analiz dane powinny być:

1. Danymi surowymi,
2. zapisane wg schludnego schematu:
	* każda zmienna zawiera jedną kolumnę
	* każdy wiersz zawiera jedną obserwację
	* każdy pomiar tworzy tabelę
3. z książką kodową opisującą każdą zmienną z jej możliwymi wartościami (np. zakres, lub kategorie)
4. oraz dokładny przepis jak z danych surowych uzyskać zmienne. 

Osobną kwestią jest umiejętne sformułowanie problemu badawczego i pytania do statystyka. Ale zajmijmy się najpierw danymi ;-)

Pokrótce o każdym z punktów: 

### Surowe dane

Surowe dane mają tą cechę, że są efektem pomiaru nie poddanym żadnym manipulacjom. Czy to będzie plik wynikowy z przyrządu pomiarowego, czy ręcznie wprowadzone liczby z pomiaru kwestionariuszowego - dane są ok, jeśli nic z nim nie robiono. Nic to znaczy:

1. żaden program komputerowy ich nie obrabiał
1. nie były zmieniane żadne wartości
1. nic nie było też usuwane
1. nie były też dokonywane żadne podsumowania i analizy w pliku

Kilka przykładów:

* output z urządzenia pomiarowego [binary file](http://en.wikipedia.org/wiki/Binary_file)
* dane z Twitera [JSON](http://en.wikipedia.org/wiki/JSON)
* dane do [metaanalizy](http://github.com/pa0/datasharing/dane do metaanalizy.csv)

Przeliczanie lub zmienianie danych jest częstym błedem, który sprawia, że statystyk musi najpierw wykonać dedektywistyczną pracę analilzując dlaczego dane wyglądają właśnie w taki sposób. 

### Schludny format danych

Wielkość i format pliku nie ma znaczenia. Ważny jest porządek. Zgodnie z zasadą "garbage in = garbage out" to co jest potrzebne do analizy to przejrzystość sposobu zapisania danych. Na poziomie ogólnym można o tym poczytać u [Hadley Wickham](http://had.co.nz/) w [tym artykule](http://vita.had.co.nz/papers/tidy-data.pdf) lub zobaczyć na [tym filmie](http://vimeo.com/33727555). Przedstawiony tam punkt widzenia dotyczy pakietu [R](http://www.r-project.org/), który może jest, a może nie jest Tobie znany, ale ma zastosowanie w większości przypadków przygotowywania danych.

Dla przypomnienia 4 reguły dotyczące przygotowania danych:

1. każda zmienna zawiera się w jednej kolumnie
1. każda obserwacja zawiera się w jednym wierszu
1. dane powinny mieścić się w jednej tabeli
1. jeśli z różnych wględów potrzebne jest kilka tabel powiny one zawierać kolumnę z wartościami (ID) pozwalającymi połączyć je ze sobą

Jednym z dobrych zwyczajów jest umieszczenie w pierwszym wierszu danych *pełnej* nazwy zmiennej, np.: 'WiekPodczasBadania' zamiast 'WPB'
W przypadku danych kwestionariuszowych często kolejne pytania składają się na jakiś wynik sumaryczny - w nazwie kolumn można to zawrzeć podając kolejno kw1, kw2, ... kwN, gdzie "kw" jest nazwą kwestionariusza a jeszcze lepiej skali.

Dane moga być zapisane w Excelu, lecz najlepiej w jednym arkuszu bez makr i formuł. Alternatywnym dobrym formatem jest plik tekstowy [CSV](http://en.wikipedia.org/wiki/Comma-separated_values) lub [TAB-delimited](http://en.wikipedia.org/wiki/Tab-separated_values).


### Reguły przeliczania (książka kodowa)

W wiekszości przypadków dane powinny być opisane szerzej niż wynika to z ich charakterystyki liczbowej. Minimalnie powinny być podane:

1. Informacja o zmiennych (wraz z jednostkami, np. wiek w latach) 
1. Sposób uzyskania z danych surowych zmiennych
1. Informację o planie badawczym - w jaki sposób dane zostały pozyskane (np. powtarzane pomiary, badania kwestionariuszowe, itp.)

Format tego dokumentu jest dowolny tekstowy, który jest Tobie wygodny.

#### Jak opisać zmienne

Jeśli w zbiorze z danymi zamieszczono cyfry także dla zmiennych kategorialnych (np. wykształcenie, płeć) koniecznym jest podanie jakie cyfry jakim kategoriom odpowiadają, ale preferowanym sposobem zapisu jest używanie opisów tekstowych: "kobieta" - "mężczyzna", "niski" - "średni" - "wysoki". Ten sposób zmniejsza liczbę błędów związaną z kodowaniem.

Braki danych powinny być zakodowane wartością `NA`. 

Wszelkie informacje zawarte w plikach z danymi powinny być dostępne w postaci tekstowej, tzn. jeśli np. w Excelu kolorami zaznaczone są osoby o określonej płci lub grupy to po imporcie do pakietu statystycznego ta informacja zginie.


Czego można się spodziewać po statystyku
====================

Jeśli otrzyma on tak przygotowane dane wynik analiz będzie dostępny dużo szybciej. Oczywiście nie oznacza to braku pytań i wiele sytuacji z danymi wymyka się z tych ram. Ale ich przestrzeganie pozwoli ograniczyć do minimum _inżynierię wsteczną_ aby uzyskać czyste, analizowalne dane.

Dobrze zrobiona analiza statystyczna zawiera:

1. Opis procedur analitycznych 
1. Skrypt do ich przeprowadzenia samodzielnie (w przypadku R)
1. Pliki wynikowe w postaci raportu z tabelami i rycinami, które analiza wygenerowała

Na podstawie tych informacji powinno być możliwe powtórzenie analiz a każdy etap analiz powinien być jasny i zrozumiały. Jeśli tak nie jest należy zapytać statystyka, tak aby nawet jeśli nie będzie możliwe powtórzenie analiz zrozumiałe będą jego poszczególne etapy.


#### Autorzy
====================

Na podstawie wersji angielskiej napisanej przez:
* [Jeff Leek](http://biostat.jhsph.edu/~jleek/) - Wrote the initial version.
* [L. Collado-Torres](http://bit.ly/LColladoTorres) - Fixed typos, added links.
* [Nick Reich](http://people.umass.edu/nick/) - Added tips on storing data as text.

Przygotował wersję polską i zlokalizował dla Nauk Społecznych:
* [Paweł Kleka](http://amu.edu.pl/~kleka)


