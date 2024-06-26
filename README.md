# Zadanie: Zprzężenie zwrotne

| Termin oddania | Punkty     |
|----------------|:-----------|
| 17.05.2024  23:00   |    10      |

--- 
Przekroczenie terminu o **n** zajęć wiąże się z karą:
- punkty uzyskanie za realizację zadania są dzielone przez **2<sup>n</sup>**.

--- 

### Napisz program, który ...
 będzie modelował układ samostabilizujących się obiektów. Przykładem może być zadanie Rynek z zajęć programistycznych (treść poniżej).
 W zadaniu wykorzystano wzorzec Obserwator do zbierania informacji o poszczególnych grupach obieków. 
 Zaproponuj alternatywne rozwiązanie, które:
 - nie będzie korzystało ze wzorca Obserwator
 - będzie pozwalało skonfigurować algorytm samostabilizujący się dla N grup obiektów, z któych dane emitowane przez każdą grupę są ważne dla pozostałych; patrz [Sprzężenie zwrotne](https://mfiles.pl/pl/index.php/Sprz%C4%99%C5%BCenie_zwrotne).
 - układ będzie posiadał algorytm stabilizacji.


## Zadanie Rynek

- **Sprzedawcy** posiadają ograniczoną liczbę produktów w jednostce czasu, 
	które oferują na wolnym rynku po cenach, które zależą od:
    - kosztu wytworzenia produktu
    - inflacji (w czasie spada wartość pieniądza)
    - marży (ile chce na produkcie zarobić sprzedawca).

    Celem sprzedawcy jest osiągnięcie jak największego zysku.

- **Kupujący** posiadają potrzeby, zasady i pieniądze.
    Produkty są podzielone na dwie kategorie: produkty pierwszej potrzeby i luksusowe.
    Kupujący obserwują oferty produktów na rynku. Ich zachowanie opisują następujące reguły:
    - nimimalna wielkość zakupu produktów pierszej potrzeby w jednostce czasu jest ustalona dla każdego kupującego
    - chcą kupić określone produkty luksusowe i śledzą ich ceny ale nie muszą ich kupić natychmiast
    - mają wiedzę o skali inflacji
    - ich skłonność do zakupu produktu spada wraz z rosnącą ceną produktu, 
	niezależnie czy wzrost cen był spowodowany inflacją czy marżą.
    
- **Bank Centralny** obserwuje wzrost cen produktów oraz obroty na rynku.
    Ustala bieżący poziom inflacji. 
    Celem Banku stara się utrzymanie stałego wpływu podatkowego liczone jako 
    iloczyn inflacji i obrotów przy danej inflacji.
    
    
### Wykorzystaj:
- **Wzorzec odwiedzający** do aktualizacji danych o produktach u sprzedawców oraz parametrów kupujących.
    Przykładową implementację wzorca odwiedzający w C# znajdziesz w katalogu: `\Examples\ShoppingCart`.
- **Wzorzec obserwator** do pasywnego obserwowania następujących zmian:
    - Sprzedawcy i Kupujący obserwują Bank Centralny by dowiedzieć się jaki jest poziom inflacji
    - Kupujący obserwują oferty Sprzedawców i mogą na nie reagować ale nie muszą
	- Bank Centralny obserwuje Sprzedawców i Kupujących, by korygować algorytm inflacyjny utrzymujący 
	stałe wpływy podatkowe.
   
    Przykładową implementację wzorca obserwator w C# znajdziesz w katalogu: `\Examples\IObserverNet40`.

	Rozwiązanie zadania może zostać wykonane w dowolnym języku / technologii.
	
### Uwaga 1
Projekt powinien również zawierać odpowiednie testy jednostkowe do implementowanej funkcjonalności.

### Uwaga 2
Dla uproszczenia implementacji można rozważyć implementację opartą na turach.

### Uwaga 3
Zaimplementowany model powinien być stabilny i odporny na zakłócenia.
