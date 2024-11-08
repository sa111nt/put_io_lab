# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu.
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu.

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.


## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC5](#uc5): Przekazanie produktu kupującemu

[Kupujący](#ac2):
* [UC2](#uc2): Oferowanie kwoty za produkt
* [UC3](#uc3): Wygrywanie aukcji
* [UC4](#uc4): Przekazanie należności sprzedającemu

---
<a id="uc1"></a>

### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>


### UC2: Oferowanie kwoty za produkt

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) wystawia cenę za produkt oraz poda swoje dane.
2. System sprawzdi czy cena jest wyższa od aktualnej o co najmniej 1 złotówke.
3. System potwierdzi nową cenę za produkt.
4. System zapisze dane [kupującego](#ac2).
5. System zaktualizuje nową cenę za produkt.
   

**Scenariusze alternatywne:** 

2.A. Podano kwotę nie wyższa od poprzedniej o 1 zł
* 2.A.1. System informuje o błędnie podanej kwocie.
* 2.A.2 Przejdz do kroku 1.

---


<a id="uc3"></a> 

### UC3: Wygranie aukcji

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. Skończył się czas aukcji.
2. System pobiera dane [kupującego](#ac2) z aktualną najwyższą ceną za produkt.
3. System ogłasza zwyciężscę.

---


<a id="uc4"></a>

### UC4: Przekazanie należności [sprzedającemu](#ac1)

**Aktorzy** [Kupujący](#ac2), [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Kupujący](#ac2) przekazuje należność do systemu.
2. System sprawdza przekazaną kwotę
3. System potwierdza przekazaną kwotę.
4. System przekezuję kwotę [Sprzedającemu](#ac1),


**Scenariusze alternatywne:** 
1.A [Kupujący](#ac2) nie przekazał należności do systemu
* 1.A.1 System informuje o błędnie przekaznej należności.
* 1.A.2 Przejdz do kroku 1.

---

<a id="uc5"><a>

**Aktorzy** [Kupujący](#ac2)

### UC5: Przekazanie produktu [Kupującemu](#ac2)
1. Sprzedający przekazuje produkt do systemu.
2. System ponownie sprawdza produkt według jego opisu.
3. System potwierdza stan produktu.
4. System przekazuje produkt [kupującemu](#ac2).

**Scenariusze alternatywne:** 
2.A Stan produktu nie odpowiada swojemu opisowi.
* 2.A.1 System informuje o błędnie podanym opisie produktu.
* 2.A.2 Przejdz do kroku 1.






## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | ... |
| ------------------------------------------------- | ------ | ------- | --- |
| UC1: Wystawienia produktu na aukcję               |    C   |    C    | ... |
| ???                                               |  ...   |  ...    | ... |


