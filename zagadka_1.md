Wstępniak do systemów liczbowych
================================

Ci, którzy już trochę programują, pewnie spotkali się z zapisami liczbami w postaci np. 0b1111011, 0o173, 0x7B czy może z jakimś dziwnym niepotrzebnym dodatkowym zerem jak 0173. Wszystkie te liczby w naszej codziennej matematyce to liczba 123, przy okazji też symbol "{" w Unicode. Form zapisu jest więcej. A i mogliście slyszeć, że nazywa się to liczbami binarnymi (to ta z początkiem 0b), ósemkowymi (zarówno 0o jak i samo 0) czy szesnastkowymi (0x).

Jak to się liczy? Prosto. Wystarczy umieć dodawać, mnożyć i potęgować (czyli znowu - mnożyć). Najprościej jest to pokazać na liczbie 173, zapisanej dziesiętnie, czyli tak, jak liczymy na co dzień:

$3 \cdot 10^0 + 2 \cdot 10^1 + 1 \cdot 10^2 = 3 \cdot 1 + 2 \cdot 10 + 1 \cdot 100 = 3 + 20 + 100 = 123$

Ale o co chodzi? Chodzi o to, że kolejne cyfry czytane od prawej strony mnożymy przez rosnącą potęgę podstawy systemu liczbowego, zaczynając od potęgi 0.

Podstawa, czyli to co potęgujemy, bierze się z nazwy systemu. System dziesiętny ma podstawę 10, szesnastkowy - 16, dwójkowy (binarny) - 2, ósemkowy - 8. W systemie o podstawie N, są dostępne cyfry od 0 do N - 1, czyli dla systemu o podstawie N = 10 (tym codziennym), są cyfry od 0 do 9, ale w systemie o podstawie 8 - od 0 do 7. Dla systemu o podstawie 16 są zatem "cyfry" od 0 do 15, ale dla wygody, by był to jeden znak, przyjęło się zapisywać "cyfry" od 10 do 15 jako litery od A do F. A w tym, w którym myśli komputer - dwójkowym - tylko cyfry 0 i 1. Wracająć do liczenia:

$0b1111011 = 1 \cdot 2^0 + 1 \cdot 2^1 + 0 \cdot 2^2 + 1 \cdot 2^3 + 1 \cdot 2^4 + 1 \cdot 2^5 + 1 \cdot 2^6 = 1 \cdot 1 + 1 \cdot 2 + 0 \cdot 4 + 1 \cdot 8 + 1 \cdot 16 + 1 \cdot 32 + 1 \cdot 64 = 1 + 2 + 0 + 8 + 16 + 32 + 64 = 123$

$0o173 = 3 \cdot 8^0 + 7 \cdot 8^1 + 1 \cdot 8^2 = 3 \cdot 1 + 7 \cdot 8 + 1 \cdot 64 = 3 + 56 + 64 = 123$

$0x7B = 11 \cdot 16^0 + 7 \cdot 16^1 = 11 \cdot 1 + 7 \cdot 16 = 11 + 112 = 123$

Możemy również wymyślać systemy o dowolnych innych podstawach. Może być system trójkowy albo dziewiątkowy.

Zagadka
-------

Poza programowaniem, klasycznie podstawę systemu zapisuje się w indeksie dolnym przy liczbie, np.

$1111011_2$  
$173_8$  
$123_{10}$  
$7B_{16}$

W ramach zagadki policz dziesiętną wartość poniższych liczb i sprawdź jakie odpowiadają im litery (np. [`man 7 ascii`]), by uzyskać hasło:

$1110011_{2}$  
$11002_{3}$  
$1233_{4}$  
$410_{5}$  
$312_{6}$  
$166_{7}$  
$154_{8}$  
$140_{9}$  
$116_{10}$  
$89_{11}$  
$96_{12}$  
$7C_{13}$  
$7C_{14}$  
$76_{15}$  
$43_{16}$  

[`man 7 ascii`]: https://man7.org/linux/man-pages/man7/ascii.7.html
