Suplemencik vel ciekawostka vel wiedza
======================================

Komputery, elektronika, tak wyszło, liczą w systemie dwójkowym. Ot uznano, że najłatwiej w elektronice jest utrzymywać i rozpoznawać stan niski i wysoki, że coś jest włączone lub nie, jak żarówka, stąd te cyfry 1 i 0.

Skoro komputer myśli binarnie, a człowiek myśli w systemie dziesiętnym, to takie dwa typy liczb w programowaniu mają naturalny sens. Poza tym można wymyślać dowolne inne systemy liczbowe, więc skąd zjawisko, że w wielu językach programowania można wprowadzać dodatkowo liczby ósemkowe lub szesnastkowe, a nie czwórkowe, jedenastkowe, czy osiemnastkowe?

Co więcej, dopiero w planowanym na 2023 rok standardzie C ma być dopuszczone wpisywanie liczb dwójkowych, bo do tej pory, bez pomocy rozszerzeń kompilatora, się nie da! W C++ jest od 2014, czyli prawie 30 lat od jego powstania. A przecież wydawać by się mogło, że to absolutna podstawa!

Wzięło się to z tego, że wpisywanie liczb binarnych jest żmudne i ciężko zorientować się, która cyfra, jest która, np. taka niewielka liczba jak 668 w zapisie binarnym ma 10 cyfr: $1010011100_{2}$. A tymczasem systemy, których podstawa jest potęgą dwójki, jak 8 czy 16, doskonale nadają się do prostego zapisywania liczb binarnych krócej. Rozpiszmy powyższą liczbę binarną:

$1010011100_{2} = 0 \cdot 2^0 + 0 \cdot 2 ^ 1 + 1 \cdot 2 ^ 2 + 1 \cdot 2 ^ 3 + 1 \cdot 2 ^ 4 + 0 \cdot 2 ^ 5 + 0 \cdot 2 ^ 6 + 1 \cdot 2 ^ 7 + 0 \cdot 2 ^ 8 + 1 \cdot 2 ^ 9$

Zróbmy teraz małe przekształcenia. Najpierw, pogrupujmy po 3 składniki:

$... = (0 \cdot 2^0 + 0 \cdot 2 ^ 1 + 1 \cdot 2 ^ 2) + (1 \cdot 2 ^ 3 + 1 \cdot 2 ^ 4 + 0 \cdot 2 ^ 5) + (0 \cdot 2 ^ 6 + 1 \cdot 2 ^ 7 + 0 \cdot 2 ^ 8) + (1 \cdot 2 ^ 9 + 0 \cdot 2 ^ {10} + 0 \cdot 2 ^ {11} )$

Na końcu dopisałem sobie $0 \cdot 2^{10} + 0 \cdot 2^{11}$, bo przecież nikt nie broni napisać więcej zer z przodu w liczbie, tak by mieć $001010011100_{2}$, a dzięki temu mamy równo po trzy. Teraz z każdego nawiasu wyłączmy najmniejszą wspólną potęgę dwójki:

$... = 2^0(0 \cdot 2^0 + 0 \cdot 2 ^ 1 + 1 \cdot 2 ^ 2) + 2^3(1 \cdot 2^0 + 1 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2) + 2^6(0 \cdot 2 ^ 0 + 1 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2) + 2^9(1 \cdot 2 ^ 0 + 0 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2)$

Następnie policzmy tylko potęgi przed nawiasami:

$... = 1(0 \cdot 2^0 + 0 \cdot 2 ^ 1 + 1 \cdot 2 ^ 2) + 8(1 \cdot 2^0 + 1 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2) + 64(0 \cdot 2 ^ 0 + 1 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2) + 512(1 \cdot 2 ^ 0 + 0 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2)$

Wyszło nam 1, 8, 64, 512. Czy widać tu jakąś zależność? To są kolejne potęgi ósemki! Zapiszmy je w taki właśnie sposób:

$... = 8^0(0 \cdot 2^0 + 0 \cdot 2 ^ 1 + 1 \cdot 2 ^ 2) + 8^1(1 \cdot 2^0 + 1 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2) + 8^2(0 \cdot 2 ^ 0 + 1 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2) + 8^3(1 \cdot 2 ^ 0 + 0 \cdot 2 ^ 1 + 0 \cdot 2 ^ 2)$

Teraz na zewnątrz mamy, zastępując nawiasy symbolami:

$8^0a + 8^1b + 8^2c + 8^3d$

Czyli mamy rozpisaną liczbę ósemkową o postaci $\mathrm{dcba_8}$, gdzie $\mathrm{d}$, $\mathrm{c}$, $\mathrm{b}$ i $\mathrm{a}$ to cyfry tej liczby. Co ciekawsze, każdy z nawiasów jest w postaci:

$2^0f + 2^1g + 2^2h$

co oznacza, że każdy jest krótką liczbą dwójkową postaci $\mathrm{hgf_2}$. A co jest po kolei w tych nawiasach, spisując je od tyłu jako liczby binarne, jednocześnie spisując cyfry od tyłu?

$001_2$ $010_2$ $011_2$ $100_2$

Jest to nasza pierwotna liczba dwójkowa, pogrupowana po 3 cyfry (grupowanie od prawej, na początku doszły dwa zera, te, które wcześniej dopisaliśmy, by też była trzycyfrowa grupa).

Wartości tych osobnych liczb dwójkowych, mamy zapisane w nawiasach, wracając do działania, policzmy wreszcie nawiasy:

$... = 8^0(0 \cdot 1 + 0 \cdot 2 + 1 \cdot 4) + 8^1(1 \cdot 1 + 1 \cdot 2 + 0 \cdot 4) + 8^2(0 \cdot 1 + 1 \cdot 2 + 0 \cdot 4) + 8^3(1 \cdot 1 + 0 \cdot 2 + 0 \cdot 4)$  
$= 8^0(0 + 0 + 4) + 8^1(1 + 2 + 0) + 8^2(0 + 2 + 0) + 8^3(1 + 0 + 0) = 8^0 \cdot 4 + 8^1 \cdot 3 + 8^2 \cdot 2  + 8^3 \cdot 1$

I w ten sposób na końcu mamy wyraźnie rozpisaną liczbę w systemie o podstawie 8 - $1234_8$. Innymi słowy:

$1010011100_2 = 1234_8$

Możemy łatwo to zweryfikować w interaktywnym Pythonie:

~~~
>>> 0b1010011100
668
>>> 0o1234
668
~~~

Te zdbyt długie równania służą tylko pokazaniu, skąd bierze się zależność. W praktyce kluczowe jest zwrócenie uwagi na to, że każda z kolejnych cyfr ósemkowych od tyłu, odpowiada 3 cyfrom dwójkowym grupowanym również od tyłu. Zatem w życiu codziennym, chcąc zapisać liczbę $1010011100_{2}$, grupujemy w głowie jej cyfry:

$1|010|011|100_{2}$

I każdą tak powstałą 3-cyfrową liczbę binarną przeliczamy w pamięci (bo to łatwe!) na jej wartość dziesiętną.

$1_{2} = 1$  
$010_{2} = 2$  
$011_{2} = 3$  
$100_{2} = 4$

Tak otrzymane liczby są po prostu kolejnymi cyframi liczby ósemkowej:

$1234_{8}$

Dokładnie tak samo powstają liczby szesnastkowe, tylko tam grupuje się o jedną cyfrę więcej.

$10|1001|1100_{2}$

I liczymy:

$10_2 = 2$  
$1001_2 = 9$  
$1100_2 = 12$

Ponieważ "cyfrę" 12 zapisujemy w liczbach szesnastkowych jako literę C (A = 10, B = 11, C = 12, itd.), to otrzymujemy:

$\mathrm{29C_{16}}$

Weryfikacja Pythonem:

~~~
>>> 0x29c
668
~~~

Inaczej jeszcze to ujmując, na 3 cyfrach binarnych możemy zapisać liczby od 0 $(000_2)$ do 7 $(111_2)$, czyli dokładnie zakres systemu o podstawie 8. A na 4 cyfrach binarnych od 0 $(0000_2)$ do 15 (lub F, $1111_2$), co się pokrywa z zakresem systemu szesnastkowego.

A liczenie w pamięci jest bardzo proste, gdy wie się, że:

$0001_2 = 1$  
$0010_2 = 2$  
$0100_2 = 4$  
$1000_2 = 8$

To tylko dodawanie w pamięci!

A jeśli chodzi o wybór ósemkowego lub szesnastkowego. Pewną przewagą szesnastkowego jest to, że ponieważ najpopularniejszy rozmiar bajta w komputerach to 8 bitów (tak, bajt wcale nie musi mieć 8-bitów, 8-bitowa liczba nazywa się poprawnie oktetem), gdzie wszystkie rozmiary danych są wielokrotnością tych 8 bitów, czyli 8 cyfr, zawsze się one równo dzielą po 4 cyfry.

Zadanko
-------

A we wszystkim powyższym chodzi o to, by nie bać się przeliczać długich liczb, ponieważ niezależnie od tego, jak są długie, to między szesnastkowym, ósemkowym i dwójkowym przelicza się to bez wysiłku, prosto zapisując liczby. Jedynie przeliczanie z i na dziesiętny, codzienny system, wymaga nieco więcej wysiłku. I jakoś tak często łatwiej ogarnąć, co jest czym, niż wpisując długie ciągi dwójkowe, nawet jeżeli język na to pozwala.

Choć mi często braowało bezpośrednich liczb binarnych przy robieniu masek bitowych, do tego coraz popularniejszą funkcją w językach są separatory do grupowania cyfr. W Pythonie jest to znak podkreślnika, więc długą liczbę można zapisać jako np. `0b1000_0001_1100_0110`. W C++ (od 2014) niestety wybrano apostrof co, nie dosyć, że brzydko wygląda, to jeszcze myli edytory i inne narzędzia do składni uznające, że w apostrofach powinna być litera i podświetlają wszystko między nimi lub traktują je jako błąd. W C do tej pory nie ma separatora, ale wszystko wskazuje na to, że niestety pójdą za przykładem C++ i będzie to ` 0b1000'0001'1100'0110`

W każdym razie dla przekonania się, że to proste, spróbujcie w głowie przeliczyć sobie każdą z liczb tak, by mieć jej postać binarną, ósemkową i szesnastkową. Tym razem zapis jak z języka programowania:

```
0b10111010110010000000011111010110
0b11100100101100
0b10100000100110010000100100010
0b1111000011110000
0b111000111
0o20062666620
0o16640646044
0o36063325575
0o7700
0o76543210
0xABCDCBA
0x291106f4
0x339c1c9d
0xFEDCBA9876543210
```

Łatwo będzie wyniki sprawdzić wklejając je do Pythona. Należy pamiętać o prefiksach `0b`, `0o` i `0x`. I można śmiało grupy cyfr oddzielać znakiem `_`. W razie czego Python ma też funkcje `bin()`, `oct()` i `hex()`. Ale jeśli ktoś ma chwilę, to zachęcam do przećwiczenia tego w głowie, by potem nie trzeba było za każdym razem sięgać po kalkulator (również apki na telefonie mają czasami tryb programisty, gdzie można łatwo systemy zmieniać), gdy się zobaczy liczbę ósemkową lub szesnastkową.
