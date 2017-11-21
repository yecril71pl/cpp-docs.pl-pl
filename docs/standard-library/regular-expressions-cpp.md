---
title: "Wyrażenia regularne (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++, regular expressions
- regular expressions, Visual C++
- regular expressions
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9c32cc76c27b89bd3820e24bc7f38da0d12e0add
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="regular-expressions-c"></a>Wyrażenia regularne (C++)
Standardowa biblioteka C++ obsługuje wiele gramatyk wyrażenia regularnego. W tym temacie omówiono warianty gramatyki, gdy za pomocą wyrażeń regularnych.  
  
##  <a name="regexgrammar"></a>Gramatyka wyrażeń regularnych  
Gramatyka wyrażenie regularne do użycia przez określono przy użyciu jednego z `std::regex_constants::syntax_option_type` wartości wyliczenia. Te gramatyki wyrażenia regularnego są zdefiniowane w std::regex_constants:

-   `ECMAScript`: To jest najbliżej gramatyki używane przez JavaScript i języków .NET.
-   `basic`: Nazwa podstawowa wyrażeń regularnych POSIX lub BRE.
-   `extended`POSIX rozszerzone wyrażenia regularne lub ERE.
-   `awk`: W tym `extended`, ale ma dodatkowe specjalne niedrukowalne znaki.
-   `grep`: W tym `basic`, ale pozwala także nowy wiersz znaków (\n) do oddzielania alternations.
-   `egrep`: W tym `extended`, ale pozwala także znaki nowego wiersza oddzielić alternatios.

Domyślnie, jeśli gramatyki nie jest określony `ECMAScript` zakłada, że. Można określić tylko jeden gramatyki.  
  
Oprócz gramatyki można zastosować kilka flag:  
-   `icase`: Ignorowanie wielkości liter podczas dopasowywania.  
-   `nosubs`: Ignoruj oznaczony jako odpowiedniki (czyli wyrażenia w nawiasach); nie podstawienia są przechowywane.  
-   `optimize`: Upewnij się, szybciej, dopasowania na możliwy koszt większa czasu konstrukcji.  
-   `collate`: Za pomocą sekwencji sortowania zależne od ustawień regionalnych (na przykład zakresów w formie "[a-z]").  
  
Zero lub więcej flag mogą być łączone z gramatyki, aby określić zachowanie aparat wyrażeń regularnych. Jeśli tylko określonych flag `ECMAScript` zakłada, że jako gramatyki.

### <a name="element"></a>Element  
 Element może być jednym z następujących:  
  
-   *Zwykłej znak* ten sam znak w sekwencji docelowych, które odpowiadają.  
  
-   A *wieloznacznego* '.' który dopasowuje dowolny znak w sekwencji docelowej z wyjątkiem nowym wierszem.  
  
-   A *nawiasów wyrażenia* w formie "[`expr`]", zgodnej z znak lub element sortowania w sekwencji docelowego, który jest również w zestawie zdefiniowany przez wyrażenie `expr`, lub w postaci "[^`expr`]", która Dopasowuje znak lub element sortowania w sekwencji docelowej, która nie znajduje się w zestawie zdefiniowany przez wyrażenie `expr`.  
  
     Wyrażenie `expr` może zawierać dowolną kombinację następujących czynności:  
  
    -   Pojedynczy znak. Dodaje ten znak do zestawu zdefiniowane przez `expr`.  
  
    -   A *znaku zakresu* w postaci "`ch1`-`ch2`". Dodaje znaki, które są reprezentowane przez wartości z zakresu zamknięte [`ch1`, `ch2`] w zestawie zdefiniowane przez `expr`.  
  
    -   A *znak klasy* w formie "[:`name`:]". Dodaje znaki w klasie o nazwie zestaw zdefiniowanych przez `expr`.  
  
    -   *Klasy równoważność* w formie "[=`elt`=]". Dodaje elementy sortowania, które są równoważne `elt` zestaw zdefiniowanych przez `expr`.  
  
    -   A *sortowania symbol* w formie "[.`elt`.]". Dodaje element sortowania `elt` zestaw zdefiniowanych przez `expr`.  
  
-   *Zakotwiczenia*. Kotwica '^' pasuje do początku sekwencji docelowej; kotwica '$' pasuje do końca sekwencji docelowej.  
  
 A *grupy przechwytywania* w postaci "( *Podwyrażenie* )", lub "\\( *Podwyrażenie* \\)" w `basic` i `grep`, która Dopasowuje sekwencja znaków w sekwencji docelowy równoważona wzorzec między ograniczników.  
  
-   *Tożsamości specjalne* w postaci "\\`k`", zgodnej znak `k` w procesie docelowym.  
  
 Przykłady:  
  
-   „a” pasuje do sekwencji docelowej „a”, ale nie pasuje do sekwencji docelowych „B”, „b” lub „c”.  
  
-   „.” pasuje do wszystkich sekwencji docelowych „a”, „B”, „b” i „c”.  
  
-   „[b-z]” pasuje do sekwencji docelowych „b” i „c”, ale nie pasuje do sekwencji docelowych „a” lub „B”.  
  
-   „[:lower:]” pasuje do sekwencji docelowych „a”, „b” i „c”, ale nie pasuje do sekwencji docelowej „B”.  
  
-   „(a)” pasuje do sekwencji docelowej „a” i kojarzy grupę przechwytywania 1 z podsekwencją „a”, ale nie pasuje do sekwencji docelowych „B”, „b” lub „c”.  
  
 W `ECMAScript`, `basic`, i `grep`, można też element *kopii odwołania* w postaci "\\`dd`", gdzie `dd` reprezentuje wartość dziesiętną N odpowiadającą sekwencji znaków w celu sekwencji który jest taki sam, jak sekwencja znaków równoważona określona liczba *grupy przechwytywania*. Na przykład, „(a)\1” odpowiada sekwencji docelowej „aa”, ponieważ pierwsza (i tylko) grupa przechwytywania pasuje do początkowej sekwencji „a”, a następnie \1 pasuje do ostatniej sekwencji „a”.  
  
 W `ECMAScript`, element również może być jedną z następujących czynności:  
  
-   A *grupy z systemem innym niż przechwytywania* w postaci "(: *Podwyrażenie* )". Pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami.  
  
-   Ograniczony *pliku formatu ucieczki* formularza "\f", "\n", "\r", "\t" lub "\v". Pasują one, odpowiednio, do wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulatora poziomego i tabulatora pionowego w sekwencji docelowej.  
  
-   A *assert dodatnie* w postaci "(= *Podwyrażenie* )". Pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami, ale nie zmienia pozycji dopasowania w sekwencji docelowej.  
  
-   A *assert ujemna* w postaci "(! *Podwyrażenie* ) ". Pasuje do dowolnej sekwencji znaków w sekwencji docelowej, do której nie pasuje wzorzec między ogranicznikami, i nie zmienia pozycji dopasowania w sekwencji docelowej.  
  
-   A *szesnastkowa sekwencja unikowa* w postaci "\x`hh`". Pasuje do znaku w sekwencji docelowej, która jest reprezentowana przez dwie cyfry szesnastkowe `hh`.  
  
-   A *sekwencja ucieczki kodu unicode* w postaci "\u`hhhh`". Pasuje do znaku w sekwencji docelowej, która jest reprezentowana przez cztery cyfry szesnastkowe `hhhh`.  
  
-   A *kontrolować — sekwencja specjalna* w postaci "\c`k`". Dopasowuje znak kontrolny, o nazwie znakiem `k`.  
  
-   A *assert granicy słowa* w postaci "\b". Zgodny z bieżącą pozycję w sekwencji docelowego po natychmiast po *granicy słowa*.  
  
-   A *assert granic ujemna word* w postaci "\B". Dopasowuje podczas bieżącej pozycji w sekwencji docelowy nie jest od razu po *granicy słowa*.  
  
-   A *dsw znaku ucieczki* w postaci "\d", "\D", "\s", "\S", "\w", "\W". Zawiera skróconą nazwę klasy znaków.  
  
 Przykłady:  
  
-   "(:a)" odpowiada sekwencji docelowego "a", ale "(:a) \1" jest nieprawidłowy, ponieważ nie istnieje żadna grupa przechwytywania 1.  
  
-   "(=a)" odpowiada sekwencji docelowego "". Asercja pozytywna pasuje do początkowej sekwencji „a” w sekwencji docelowej, a końcowe „a” w wyrażeniu regularnym pasuje do sekwencji początkowej „a” w sekwencji docelowej.  
  
-   "(!a)" jest niezgodny z sekwencji docelowego "".  
  
-   "a\b." odpowiada sekwencji docelowego "~", ale nie pasuje do docelowej sekwencji "ab".  
  
-   "a\B." odpowiada sekwencji docelowego "ab", ale nie odpowiada sekwencji docelowego "~".  
  
 W `awk`, element również może być jedną z następujących czynności:  
  
-   A *pliku formatu ucieczki* w postaci "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" lub "\v". Pasują one, odpowiednio, do odwrotnego ukośnika, alertu, backspace, wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulatora poziomego i tabulatora pionowego w sekwencji docelowej.  
  
-   *Ósemkowa sekwencja unikowa* w postaci "\\`ooo`". Pasuje do znaku w sekwencji docelowego, którego reprezentacja jest wartość reprezentowane przez jedną, dwie lub trzy cyfry ósemkowe `ooo`.  
  
### <a name="repetition"></a>Powtórzenie  
 Dowolnego elementu innego niż *assert dodatnie*, *assert ujemna*, lub *zakotwiczenia* może następować liczba powtórzeń. Najbardziej ogólnym rodzaj liczba powtórzeń ma postać "{`min`,`max`}", lub "\\{`min`,`max`\\}" w `basic` i `grep`. Element, który następuje ten formularz liczba powtórzeń pasuje do co najmniej `min` kolejnych zdarzeń i nie więcej niż `max` kolejnych wystąpień sekwencji pasujący element. Na przykład, „a{2,3}” odpowiada sekwencji docelowej „aa” i sekwencji docelowej „aaa”, ale nie sekwencji docelowej „a” lub sekwencji docelowej „aaaa”.  
  
 Licznik powtórzeń może mieć również jedną z następujących postaci:  
  
-   "{`min`}", lub "\\{`min`\\}" w `basic` i `grep`. Odpowiednik wartości "{`min`,`min`}".  
  
-   "{`min`,}", lub "\\{`min`,\\}" w `basic` i `grep`. Odpowiednik wartości "{`min`, niepowiązany}".  
  
-   "*". Równoważne postaci „{0,nieograniczone}”.  
  
 Przykłady:  
  
-   „a{2}” pasuje do sekwencji docelowej „aa”, ale nie sekwencji docelowej „a” ani sekwencji docelowej „aaa”.  
  
-   „a{2,}” pasuje do sekwencji docelowej „aa”, sekwencji docelowej „aaa” itp., ale nie pasuje do sekwencji docelowej „a”.  
  
-   „a*” pasuje do sekwencji docelowej „”, sekwencji docelowej „a”, sekwencji docelowej „aa” itd.  
  
 Dla wszystkich gramatykach z wyjątkiem `basic` i `grep`, liczba powtórzeń również można wykonać jedną z następujących formatów:  
  
-   "?". Równoważne postaci „{0,1}”.  
  
-   "+". Wartość równoważna "{1, niepowiązany}".  
  
 Przykłady:  
  
-   ""? odpowiada sekwencji docelowego "" i sekwencji docelowego "a", ale nie sekwencji docelowego "aa".  
  
-   „a+” pasuje do sekwencji docelowej „a”, sekwencji docelowej „aa” itd., ale nie do sekwencji docelowej „”.  
  
 W `ECMAScript`, wszystkich formularzy liczby powtórzeń może następować znak ", który wyznacza *niezachłanne powtarzania*.  
  
### <a name="concatenation"></a>Połączenie (konkatenacja)  
 Wyrażenie regularne elementy, bez *liczby powtórzeń*, może zostać dołączona do formularza dłużej wyrażeń regularnych. Wyrażenie wynikowe pasuje do sekwencji docelowej będącej połączeniem sekwencji, do których pasują poszczególne elementy. Na przykład, „a{2,3}b” pasuje do sekwencji docelowej „aab” i sekwencji docelowej „aaab”, ale nie pasuje do sekwencji docelowej „ab” ani sekwencji docelowej „aaaab”.  
  
### <a name="alternation"></a>Alternatywa  
 W wszystkich gramatykach wyrażenia regularnego z wyjątkiem `basic` i `grep`, połączonych wyrażenia regularnego może następować znak "&#124;" i połączonych innego wyrażenia regularnego. W ten sposób można łączyć dowolną liczbę połączonych wyrażeń regularnych. Wyrażenie wynikowe pasuje do dowolnej sekwencji docelowej, do której pasuje jedno lub więcej z połączonych wyrażeń regularnych.  
  
 Gdy zgodna z więcej niż jeden z połączonych wyrażeń regularnych sekwencji docelowej `ECMAScript` wybierze pierwszy połączonych wyrażeń regularnych, który odpowiada sekwencji jako dopasowania (*najpierw odpowiada*); innych wyrażenie regularne gramatyki wybierz jedną, która uzyskuje *najdłuższe dopasowanie*. Na przykład, "ab &#124; cd" dopasowań sekwencji docelowego "ab" i sekwencji docelowego "cd", ale nie odpowiada sekwencji docelowego "abd" lub sekwencji docelowego "acd".  
  
 W `grep` i `egrep`, znaku nowego wiersza (\n) może służyć do rozdzielania alternations.  
  
### <a name="subexpression"></a>Wyrażenie cząstkowe  
 W `basic` i `grep`, Podwyrażenie jest złączeniem. W innych gramatykach wyrażeń regularnych wyrażenie cząstkowe jest alternatywą.  
  
##  <a name="grammarsummary"></a>Krótki opis gramatyki  
 W następującej tabeli podsumowano funkcje, które są dostępne w różnych gramatykach wyrażeń regularnych:  
  
|Element|Podstawowe|rozszerzone|ECMAScript|grep|egrep|awk|  
|-------------|---------|---------|----------|----------|-----------|---------|  
|za pomocą wyrażenia warunkowe "&#124;"||+|+||+|+|  
|alternatywa przy użyciu '\n'||||+|+||  
|kotwica|+|+|+|+|+|+|  
|dopasowanie wsteczne|+||+|+|||  
|wyrażenie w nawiasie kwadratowym|+|+|+|+|+|+|  
|grupa przechwytywania przy użyciu „()”||+|+||+|+|  
|Przechwytywanie grupy przy użyciu "\\(\\)"|+|||+|||  
|kontrolna sekwencja unikowa|||+||||  
|sekwencja unikowa dsw|||+||||  
|sekwencja unikowa formatu pliku|||+|||+|  
|szesnastkowa sekwencja unikowa|||+||||  
|ucieczka tożsamości|+|+|+|+|+|+|  
|asercja negatywna|||+||||  
|asercja negatywna granicy słowa|||+||||  
|grupa nieprzechwytująca|||+||||  
|powtórzenie niezachłanne|||+||||  
|ósemkowa sekwencja unikowa||||||+|  
|zwykły znak|+|+|+|+|+|+|  
|asercja pozytywna|||+||||  
|powtórzenie przy użyciu „{}”||+|+||+|+|  
|przy użyciu powtarzania "\\{\\}"|+|||+|||  
|powtórzenie przy użyciu '*'|+|+|+|+|+|+|  
|powtórzenie przy użyciu '?' i '+'||+|+||+|+|  
|sekwencja unikowa unicode|||+||||  
|symbol wieloznaczny|+|+|+|+|+|+|  
|asercja granicy słowa|||+||||  
  
##  <a name="semanticdetails"></a>Szczegóły semantycznego  
  
### <a name="anchor"></a>Kotwica  
 Kotwica pasuje do pozycji w ciągu docelowym, a nie do znaku. Kotwica '^' pasuje do początku ciągu docelowego, a kotwica '$' pasuje do końca ciągu docelowego.  
  
### <a name="back-reference"></a>Dopasowanie wsteczne  
 Odwołanie do tyłu jest ukośnik odwrotny, w którym następuje wartość dziesiętną N. Jest on zgodny zawartość określona liczba *grupy przechwytywania*. Wartość N nie może być większa niż liczba grup przechwytywania, które poprzedzają dopasowanie wsteczne. W `basic` i `grep`, wartość N jest określany przez dziesiętną wartością cyfrową, znajdujący się ukośniku odwrotnym. W `ECMAScript`, wartość N jest określany przez wszystkie cyfr dziesiętnych, które bezpośrednio po ukośniku odwrotnym. W związku z tym w `basic` i `grep`, wartość N jest nigdy nie więcej niż 9, nawet jeśli wyrażenie regularne ma więcej niż dziewięć grup przechwytywania. W `ECMAScript`, wartość N jest niepowiązany.  
  
 Przykłady:  
  
-   „((a+)(b+))(c+)\3” pasuje do sekwencji docelowej „aabbbcbbb”. Dopasowanie wsteczne „\3” pasuje do tekstu z trzeciej grupy przechwytywania, to znaczy „(b+)”. Nie pasuje do sekwencji docelowej „aabbbcbb”.  
  
-   „(a)\2” jest nieprawidłowe.  
  
-   "(((())) \10 b" ma inną funkcję `basic` i `ECMAScript`. W `basic` odwołania wstecznego jest "\1". Dopasowanie wsteczne pasuje do zawartości pierwszej grupy przechwytywania (czyli tej, która zaczyna się od „(b” i kończy się ostatnim „)” i znajduje się przed dopasowaniem wstecznym), a końcowe '0' pasuje do zwykłego znaku '0'. W `ECMAScript`, odwołania wstecznego jest "\10". Pasuje do dziesiątej grupy przechwytywania, to znaczy tej najbardziej w środku.  
  
### <a name="bracket-expression"></a>Wyrażenie w nawiasie kwadratowym  
 Wyrażenie nawiasu definiuje zestaw znaków i *sortowanie elementów*. Kiedy wyrażenie w nawiasie kwadratowym zaczyna się od znaku '^', dopasowanie zakończy się pomyślnie, jeśli do bieżącego znaku w sekwencji docelowej nie pasuje żaden element w zestawie. W przeciwnym razie dopasowanie się powiedzie, jeśli do bieżącego znaku w sekwencji docelowej pasuje dowolny z elementów w zestawie.  
  
 Zestaw znaków można zdefiniować poprzez wyszczególnienie dowolną kombinację *znaki*, *znak zakresy*, *klasy znaku*, *równoważność klasy*, i *sortowania symbole*.  
  
### <a name="capture-group"></a>Grupa przechwytywania  
 Grupa przechwytywania oznacza swoją zawartość jako pojedynczą jednostkę w gramatyce wyrażeń regularnych i nadaje etykietę tekstowi docelowemu, który pasuje do jej zawartości. Etykieta skojarzona z każdą grupą przechwytywania to numer, który zależy od policzenia nawiasów otwierających, oznaczających grupy przechwytywania, aż do nawiasu otwierającego włącznie, który oznacza bieżącą grupę przechwytywania. W tej implementacji maksymalna liczba grup przechwytywania to 31.  
  
 Przykłady:  
  
-   „ab+” pasuje do sekwencji docelowej „abb”, ale nie pasuje do sekwencji docelowej „abab”.  
  
-   „(ab)+” nie pasuje do sekwencji docelowej „abb”, ale pasuje do sekwencji docelowej „abab”.  
  
-   „((a+)(b+))(c+)” pasuje do sekwencji docelowej „aabbbc” i kojarzy grupę przechwytywania 1 z podsekwencją „aabbb”, grupę przechwytywania 2 z podsekwencją „aa”, grupę przechwytywania 3 z „bbb” i grupę przechwytywania 4 z podsekwencją „c”.  
  
### <a name="character-class"></a>Klasa znaków  
 Klasa znaków w wyrażeniu w nawiasie kwadratowym dodaje wszystkie znaki w nazwanej klasie do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć klasę znaków, należy użyć „[:”, po którym następuje nazwa klasy, a na koniec „:]”. Wewnętrznie, nazwy klas znaków są rozpoznawane przez wywołanie metody `id = traits.lookup_classname`. Znak `ch` należy do takiej klasy `traits.isctype(ch, id)` zwraca wartość true. Wartość domyślna `regex_traits` szablon obsługuje nazwy klas w poniższej tabeli.  
  
|Nazwa klasy|Opis|  
|----------------|-----------------|  
|„alnum”|małe litery, wielkie litery i cyfry|  
|„alpha”|małe litery i wielkie litery|  
|„blank”|spacja lub tabulator|  
|„cntrl”|*pliku formatu ucieczki* znaków|  
|„digit”|cyfry|  
|„graph”|małe litery, wielkie litery, cyfry i znaki interpunkcyjne|  
|„lower”|małe litery|  
|„print”|małe litery, wielkie litery, cyfry, znaki interpunkcyjne i spacje|  
|„punct”|znaki interpunkcyjne|  
|„space”|spacje|  
|„upper”|wielkie litery|  
|„xdigit”|cyfry, 'a', 'b', 'c', 'd', 'e', 'f', 'A', 'B', 'C', 'D', 'E', 'F'|  
|„d”|tak samo jak digit|  
|„s”|tak samo jak space|  
|„w”|tak samo jak alnum|  
  
### <a name="character-range"></a>Zakres znaków  
 Zakres znaków w wyrażeniu w nawiasie kwadratowym dodaje wszystkie znaki w zakresie do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć zakres znaków, należy umieścić znak '-' między pierwszym i ostatnim znakiem z zakresu. W ten sposób umieszcza się w zestawie wszystkie znaki, które mają liczbową wartość, która jest większa niż lub równa wartości liczbowej pierwszego znaku i mniejsza niż lub równa wartości liczbowej ostatniego znaku. Należy zauważyć, że ten zestaw dodanych znaków zależy od reprezentacji znaków specyficznej dla platformy. Jeśli znak '-' występuje na początku lub na końcu wyrażenia w nawiasie kwadratowym lub jako pierwszy lub ostatni znak zakresu znaków, reprezentuje sam siebie.  
  
 Przykłady:  
  
-   „[0-7]” reprezentuje zestaw znaków { '0', '1', '2', '3', '4', '5', '6', '7' }. Pasuje do sekwencji docelowych „0”, „1” itd., ale nie do „a”.  
  
-   W systemach używających kodowania znaków ASCII, „[h-k]” reprezentuje zestaw znaków { 'h', 'i', 'j', 'k' }. Pasuje do sekwencji docelowych „h”, „i” itd., ale nie do „\x8A” lub „0”.  
  
-   W systemach używających kodowania znaków EBCDIC, „[h-k]” reprezentuje zestaw znaków { 'h', 'i', '\x8A', '\x8B', '\x8C', '\x8D', '\x8E', '\x8F', '\x90', 'j', 'k' } ('h' jest kodowane jako 0x88, a 'k' jest kodowane jako 0x92). Pasuje do sekwencji docelowych „h”, „i”, „\x8A” itd., ale nie do „0”.  
  
-   „[-0-24]” reprezentuje zestaw znaków { '-', '0', '1', '2', '4' }.  
  
-   „[0-2-]” reprezentuje zestaw znaków { '0', '1', '2', '-' }.  
  
-   W systemach używających kodowania znaków ASCII, „[+--]” reprezentuje zestaw znaków { '+', ',', '-' }.  
  
 Gdy używane są zakresy zależne od ustawień regionalnych, znaki w zakresie są określane przez reguły sortowania dla ustawień regionalnych. W zestawie znajdują się znaki, które są sortowane po pierwszym znaku w definicji zakresu i przed ostatnim znakiem w definicji zakresu. Dwa znaki końcowe również znajdują się w zestawie.  
  
### <a name="collating-element"></a>Element sortujący  
 Element sortujący to sekwencja wielu znaków, która jest traktowana jako pojedynczy znak.  
  
### <a name="collating-symbol"></a>Symbol sortowania  
 Dodaje symbol sortowania w wyrażeniu nawiasu *sortowania elementu* do zestawu, który jest zdefiniowany przez wyrażenie nawiasu. Aby utworzyć symbol sortowania, użyj "[." po elemencie sortowania następuje "."].  
  
### <a name="control-escape-sequence"></a>Kontrolna sekwencja unikowa  
 Kontrolna sekwencja unikowa to ukośnik odwrotny, po którym następuje litera „c”, po której następuje jedna z liter od 'a' do 'z' lub od 'A' do 'Z'. Pasuje do znaku kontrolnego ASCII, który jest nazwany przez tę literę. Na przykład "\ci" pasuje sekwencji docelowego "\x09", ponieważ \<ctrl-i > ma wartość 0x09.  
  
### <a name="dsw-character-escape"></a>Sekwencja unikowa DSW.  
 Sekwencja unikowa dsw to skrócona nazwa klasy znaków, jak pokazano w poniższej tabeli.  
  
|Sekwencja unikowa|Równoważna nazwana klasa|Domyślna nazwana klasa|  
|---------------------|----------------------------|-------------------------|  
|„\d”|„[[:d:]]”|„[[:digit:]]”|  
|„\D”|„[^[:d:]]”|„[^[:digit:]]”|  
|„\s”|„[[:s:]]”|„[[:space:]]”|  
|„\S”|„[^[:s:]]”|„[^[:space:]]”|  
|„\w”|„[[:w:]]”|„[a-zA-Z0-9_]”*|  
|„\W”|„[^[:w:]]”|„[^a-zA-Z0-9_]”*|  
  
 *Zestaw znaków ASCII  
  
### <a name="equivalence-class"></a>Klasa równoważności  
 Klasa równoważność w wyrażeniu nawiasu dodaje wszystkie znaki i *sortowanie elementów* odpowiadają elementowi sortowania w definicji klasy równoważność do zestawu, który jest zdefiniowany przez wyrażenie nawiasu. Aby utworzyć klasę równoważności, należy użyć „[=”, po którym następuje element sortujący, a na koniec „=]”. Wewnętrznie dwa elementy sortowania `elt1` i `elt2` są równoważne Jeśli `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.  
  
### <a name="file-format-escape"></a>Sekwencja unikowa formatu pliku  
 Specjalna format pliku składa się z zwykle C języka sekwencje specjalne znaków, "\\\\", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Mają one zwykle znaczenie, oznacza to, ukośnik odwrotny, alert backspace, źródła danych formularza, nowego wiersza, powrotu karetki, tabulator poziomy i tabulator pionowy odpowiednio. W `ECMAScript`, "\a" i "\b" są niedozwolone. ("\\\\" jest dozwolone, ale jest specjalna tożsamości, nie ucieczki format pliku).  
  
### <a name="hexadecimal-escape-sequence"></a>Szesnastkowa sekwencja unikowa  
 Szesnastkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje litera 'x' i dwie cyfry szesnastkowe (0-9a-fA-F). Pasuje do znaku w sekwencji docelowej, która ma wartość określoną przez te dwie cyfry. Na przykład, „\x41” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.  
  
### <a name="identity-escape"></a>Ucieczka tożsamości  
 Ucieczka tożsamości to odwrotny ukośnik, po którym następuje pojedynczy znak. Pasuje do tego znaku. Jest wymagana, gdy znak ma specjalne znaczenie; dzięki ucieczce tożsamości to znaczenie jest usuwane. Na przykład:  
  
-   "\*" odpowiada sekwencji docelowego "aaa", ale nie odpowiada sekwencji docelowego "\*".  
  
-   "\\\*" nie pasuje do docelowej sekwencji "aaa", ale reprezentuje sekwencji docelowego "\*".  
  
 Zestaw znaków, które są dozwolone w ucieczce tożsamości, zależy od gramatyki wyrażeń regularnych, jak pokazano w poniższej tabeli.  
  
|Gramatyka|Dozwolone znaki ucieczki tożsamości|  
|-------------|----------------------------------------|  
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|  
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|  
|`awk`|`extended`plus {""', '/'}|  
|`ECMAScript`|Wszystkie znaki z wyjątkiem tych, które mogą być częścią identyfikatora. Zwykle obejmuje to litery, cyfry, '$', '\_", a sekwencje specjalne unicode. Aby uzyskać więcej informacji, zobacz temat specyfikacji języka ECMAScript.|  
  
### <a name="individual-character"></a>Pojedynczy znak  
 Pojedynczy znak w wyrażeniu w nawiasie kwadratowym dodaje ten znak do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Gdziekolwiek w wyrażeniu w nawiasie kwadratowym, z wyjątkiem początku, '^' reprezentuje sam siebie.  
  
 Przykłady:  
  
-   „[abc]” pasuje do sekwencji docelowych „a”, „b” i „c”, ale nie do sekwencji „d”.  
  
-   „[^abc]” pasuje do sekwencji docelowej „d”, ale nie do sekwencji docelowych „a”, „b” lub „c”.  
  
-   „[a^bc]” pasuje do sekwencji docelowych „a”, „b”, „c” i „^” , ale nie do sekwencji docelowej „d”.  
  
 W wszystkich gramatykach wyrażenia regularnego z wyjątkiem `ECMAScript`, jeśli "]" to pierwszy znak znajdujący się otwarcie "[" lub jest to pierwszy znak znajdujący się początkowego "^", reprezentuje on sam.  
  
 Przykłady:  
  
-   „[]a” jest nieprawidłowe, ponieważ nie ma ']', aby zakończyć wyrażenie w nawiasie kwadratowym.  
  
-   „[]abc]” pasuje do sekwencji docelowych „a”, „b”, „c” i „]”, ale nie do sekwencji docelowej „d”.  
  
-   „[^]abc]” pasuje do sekwencji docelowej „d”, ale nie do sekwencji docelowych „a”, „b”, „c” lub „]”.  
  
 W `ECMAScript`, użyj "\\]" do przedstawienia znaku "]" w wyrażeniu nawiasu.  
  
 Przykłady:  
  
-   „[]a” pasuje do sekwencji docelowej „a”, ponieważ wyrażenie w nawiasie kwadratowym jest puste.  
  
-   "[\\] abc]" odpowiada sekwencji docelowego "a", "b", "c", a "]", ale nie sekwencji docelowego "d".  
  
### <a name="negative-assert"></a>Asercja negatywna  
 Asercja negatywna pasuje do wszystkiego oprócz swojej zawartości. Nie używa żadnych znaków w sekwencji docelowej. Na przykład "(! aa)(a*)" odpowiada sekwencji docelowego "" i skojarzone przechwytywania grupy 1 z podsekwencji "". Nie pasuje do sekwencji docelowej „aa” ani do sekwencji docelowej „aaa”.  
  
### <a name="negative-word-boundary-assert"></a>Asercja negatywna granicy słowa  
 Assert granic ujemna word odpowiada Jeśli bieżącą pozycję w ciągu docelowy nie jest od razu po *granicy słowa*.  
  
### <a name="non-capture-group"></a>Grupa nieprzechwytująca  
 Grupa nieprzechwytująca oznacza swoją zawartość jako pojedynczą jednostkę w gramatyce wyrażeń regularnych, ale nie nadaje etykiety tekstowi docelowemu. Na przykład "(a)(:b)\*(c)" zgodny z tekstem docelowego "abbc" i kojarzy przechwytywania grupy 1 z podsekwencji ""i przechwytywania grupy 2 z podsekwencji "c".  
  
### <a name="non-greedy-repetition"></a>Powtórzenie niezachłanne  
 Powtórzenie niezachłanne używa najkrótszej podsekwencji sekwencji docelowej, która pasuje do wzorca. Powtórzenie zachłanne używa najdłuższej. Na przykład "(a+) (\*b)" odpowiada sekwencji docelowego "aaab". Gdy używa się powtórzenia niezachłannego, kojarzy ono grupę przechwytywania 1 z podsekwencją „a” na początku sekwencji docelowej, a grupę przechwytywania 2 z podsekwencją „aab” na końcu sekwencji docelowej. Gdy używa się dopasowania zachłannego, kojarzy ono grupę przechwytywania 1 z podsekwencją „aaa”, a grupę przechwytywania 2 z podsekwencją „b”.  
  
### <a name="octal-escape-sequence"></a>Ósemkowa sekwencja unikowa  
 Ósemkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje jedna, dwie lub trzy cyfry ósemkowe (0-7). Pasuje do znaku w sekwencji docelowej, który ma wartość określoną przez te cyfry. Jeśli wszystkie cyfry to '0', sekwencja jest nieprawidłowa. Na przykład, „\101” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.  
  
### <a name="ordinary-character"></a>Zwykły znak  
 Zwykły znak to dowolny prawidłowy znak, który nie ma specjalnego znaczenia w bieżącej gramatyce.  
  
 W `ECMAScript`, następujące znaki mają specjalne znaczenie:  
  
-   ^  $  \  .  *  +  ?  (  )  [  ]  {  }  &#124;  
  
 W `basic` i `grep`, następujące znaki mają specjalne znaczenie:  
  
-   .   [   \  
  
 Również w `basic` i `grep`, następujące znaki mają specjalne znaczenie, gdy są one używane w kontekście, w szczególności:  
  
-   "\*" ma specjalne znaczenie we wszystkich przypadkach, z wyjątkiem znajduje pierwszy znak w wyrażeniu regularnym lub pierwszego znaku, który następuje początkowego "^" w wyrażeniu regularnym lub po pierwszym znakiem przechwycenia grupy lub pierwszy znak następuje początkowego "^" w grupie przechwytywania.  
  
-   '^' ma specjalne znaczenie, gdy jest to pierwszy znak wyrażenia regularnego.  
  
-   '$' ma specjalne znaczenie, gdy jest to ostatni znak wyrażenia regularnego.  
  
 W `extended`, `egrep`, i `awk`, następujące znaki mają specjalne znaczenie:  
  
-   .   [   \   (   *   +   ?   {   &#124;  
  
 Również w `extended`, `egrep`, i `awk`, następujące znaki mają specjalne znaczenie, gdy są one używane w określonym kontekście.  
  
-   ')' ma specjalne znaczenie, gdy pasuje do poprzedzającego '('.  
  
-   '^' ma specjalne znaczenie, gdy jest to pierwszy znak wyrażenia regularnego.  
  
-   '$' ma specjalne znaczenie, gdy jest to ostatni znak wyrażenia regularnego.  
  
 Zwykły znak pasuje do takiego samego znaku w sekwencji docelowej. Domyślnie oznacza to, że dopasowanie się powiedzie, jeśli dwa znaki są reprezentowane przez tę samą wartość. W przypadku dopasowania bez uwzględniania wielkości liter, dwa znaki `ch0` i `ch1` dopasowania, jeśli `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. W przypadku dopasowania zależne od ustawień regionalnych, dwa znaki `ch0` i `ch1` dopasowania, jeśli `traits.translate(ch0) == traits.translate(ch1)`.  
  
### <a name="positive-assert"></a>Asercja pozytywna  
 Asercja pozytywna pasuje do swojej zawartości, ale nie używa żadnych znaków w sekwencji docelowej.  
  
 Przykłady:  
  
-   "(=aa) (\*)" odpowiada sekwencji docelowego "aaaa" i kojarzy przechwytywania grupy 1 z podsekwencji "aaaa".  
  
-   "(aa) (\*)" odpowiada sekwencji docelowego "aaaa" i kojarzy przechwytywania grupy 1 z podsekwencji "aa" na początku sekwencji i przechwytywania grupie docelowej 2 z podsekwencji "aa" na końcu sekwencji docelowej.  
  
-   "(=aa)(a) &#124;(a)" odpowiada sekwencji docelowego "" i skojarzone przechwytywania grupy 1 pustą sekwencją (ponieważ pozytywne potwierdzenie nie powiodła się) i przechwytywania grupy 2 z podsekwencji "". Pasuje też do sekwencji docelowej „aa” i kojarzy grupę przechwytywania 1 z podsekwencją „aa”, a grupę przechwytywania 2 z pustą sekwencją.  
  
### <a name="unicode-escape-sequence"></a>Sekwencja unikowa unicode  
 Sekwencja unikowa unicode to ukośnik odwrotny, po którym następuje litera 'u' i cztery cyfry szesnastkowe (0-9a-fA-F). Pasuje do znaku w sekwencji docelowej, który ma wartość określoną przez te cztery cyfry. Na przykład, „\u0041” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.  
  
### <a name="wildcard-character"></a>Symbol wieloznaczny  
 Symbol wieloznaczny pasuje do dowolnego znaku w wyrażeniu docelowym z wyjątkiem nowego wiersza.  
  
### <a name="word-boundary"></a>Granica słowa  
 Granica słowa występuje w następujących sytuacjach:  
  
-   Bieżący znak na początku sekwencji docelowy i jest jeden ze znaków programu word`A-Za-z0-9_.`  
  
-   Bieżąca pozycja znaku jest poza końcem sekwencji docelowej, a ostatni znak w sekwencji docelowej jest jednym ze znaków słowa.  
  
-   Bieżący znak jest jednym ze znaków słowa, a znak poprzedzający nie jest.  
  
-   Bieżący znak nie jest jednym ze znaków słowa, a znak poprzedzający jest.  
  
### <a name="word-boundary-assert"></a>Asercja granicy słowa  
 Assert granic word odpowiada podczas bieżącej pozycji w ciągu docelowego jest natychmiast po *granicy słowa*.  
  
##  <a name="matchingandsearching"></a>Dopasowywanie i wyszukiwania  
 Aby wyrażenie regularne pasowało do sekwencji docelowej, całe wyrażenie regularne musi pasować do całej sekwencji docelowej. Na przykład, wyrażenie regularne „bcd” pasuje do sekwencji docelowej „bcd”, ale nie pasuje do sekwencji docelowej „abcd” ani sekwencji docelowej „bcde”.  
  
 Aby wyszukiwanie wyrażenia regularnego zostało wykonane pomyślnie, gdzieś w sekwencji docelowej musi istnieć podsekwencja, która odpowiada wyrażeniu regularnemu. Wyszukiwanie znajduje zazwyczaj pasującą podsekwencję najbliżej lewej strony.  
  
 Przykłady:  
  
-   Wyszukanie wyrażenia regularnego „bcd” w sekwencji docelowej „bcd” zakończy się pomyślnie i dopasuje całą sekwencję. To samo wyszukiwanie w sekwencji docelowej „abcd” również zakończy się pomyślnie i dopasuje ostatnie trzy znaki. To samo wyszukiwanie w sekwencji docelowej „bcde” również zakończy się pomyślnie i dopasuje pierwsze trzy znaki.  
  
-   Wyszukanie wyrażenia regularnego „bcd” w sekwencji docelowej „bcdbcd” zakończy się pomyślnie i dopasuje pierwsze trzy znaki.  
  
 Jeśli istnieje więcej niż jedna podsekwencja, która pasuje w którymś miejscu w sekwencji docelowej, istnieją dwa sposoby wyboru pasującego wzorca. *Najpierw odpowiada* wybierze podsekwencji, który został znaleziony najpierw po dopasowaniu wyrażenia regularnego. *Najdłuższy zgodny* wybiera najdłuższym podsekwencji z te, które odpowiada w tej lokalizacji. Jeśli istnieje więcej niż jedna podsekwencja, która ma maksymalną długość, najdłuższe wystąpienie wybiera tę, która została znaleziona jako pierwsza. Na przykład, gdy zostanie użyty pierwszego dopasowania, wyszukaj wyrażenie regularne "b &#124; bc" w celu sekwencji "abcd" odpowiada podsekwencji "b", ponieważ lewa obowiązywania alternacyjne jest zgodna z tym podsekwencji; w związku z tym pierwszego dopasowania próbuj czas po prawej stronie wyrażenia warunkowe. Gdy jest używane najdłuższe wystąpienie, to samo wyszukiwanie pasuje do „bc” ponieważ „bc” jest dłuższe niż „b”.  
  
 Częściowe wystąpienie powiedzie się, jeśli dopasowanie osiąga koniec sekwencji docelowej bez niepowodzenia, nawet jeśli nie osiągnęło końca wyrażenia regularnego. W związku z tym, po pomyślnym częściowym wystąpieniu, dodanie znaków do sekwencji docelowej mogłoby spowodować niepowodzenie późniejszego częściowego wystąpienia. Jednakże, po niepowodzeniu częściowego wystąpienia, dodanie znaków do sekwencji docelowej nie może spowodować powodzenia późniejszego częściowego wystąpienia. Na przykład, przy częściowym wystąpieniu, „ab” pasuje do sekwencji docelowej „a”, ale nie „ac”.  
  
##  <a name="formatflags"></a>Flag formatu  
  
|Reguły formatu ECMAScript|Reguły formatu sed|Tekst zastępczy|  
|-----------------------------|----------------------|----------------------|  
|"$&"|"&"|Sekwencja znaków, który odpowiada wyrażeniu regularnemu całego (`[match[0].first, match[0].second)`)|  
|"$$"||"$"|  
||"\\&"|"&"|  
|"$\`" (dolara następnie oferty wstecz)||Sekwencja znaków poprzedzający podsekwencji, który jest zgodny z wyrażeniem regularnym (`[match.prefix().first, match.prefix().second)`)|  
|„$'” (znak dolara, po którym następuje cudzysłów pojedynczy)||Sekwencja znaków, znajdujący się podsekwencji, który jest zgodny z wyrażeniem regularnym (`[match.suffix().first, match.suffix().second)`)|  
|„$n”|„\n”|Sekwencja znaków, zgodny z grupą przechwytywania na pozycji `n`, gdzie `n` jest liczbą z zakresu od 0 do 9 (`[match[n].first, match[n].second)`)|  
||"\\\n"|„\n”|  
|„$nn”||Sekwencja znaków, zgodny z grupą przechwytywania na pozycji `nn`, gdzie `nn` jest liczbą z zakresu od 10 do 99 (`[match[nn].first, match[nn].second)`)|  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd biblioteki C++ Standard](../standard-library/cpp-standard-library-overview.md)

