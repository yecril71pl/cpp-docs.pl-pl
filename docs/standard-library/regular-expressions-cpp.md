---
title: Wyrażenia regularne (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, regular expressions
- regular expressions, Visual C++
- regular expressions
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86c64ff0eda298ba330f3f1e1ff6d953fd859234
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209029"
---
# <a name="regular-expressions-c"></a>Wyrażenia regularne (C++)

Standardowa biblioteka C++ obsługuje wiele gramatykach wyrażeń regularnych. W tym temacie omówiono dostępne warianty gramatyki, gdy za pomocą wyrażeń regularnych.

## <a name="regexgrammar"></a> Gramatyka wyrażeń regularnych

Gramatyka wyrażeń regularnych do użycia przez określono przy użyciu jednego z `std::regex_constants::syntax_option_type` wartości wyliczenia. Te gramatykach wyrażeń regularnych są zdefiniowane w std::regex_constants:

- `ECMAScript`: To jest najbliżej gramatyki posługują się JavaScript oraz języki, platformy .NET.
- `basic`Podstawowe wyrażeń regularnych POSIX lub BRE.
- `extended`POSIX rozszerzonych wyrażeń regularnych lub ERE.
- `awk`: W tym `extended`, ale ma dodatkowych wyprowadza niedrukowalne znaki.
- `grep`: W tym `basic`, ale mogą również nowy wiersz znaków ('\n') do oddzielania alternatyw.
- `egrep`: W tym `extended`, ale również umożliwia znakami nowego wiersza do oddzielania alternatyw.

Domyślnie, jeśli gramatyki nie zostanie określony `ECMAScript` zakłada, że. Może być określona tylko jedna gramatyki.

Oprócz gramatykę można zastosować kilka flag:
- `icase`: Ignoruj wielkość liter podczas dopasowywania.
- `nosubs`: Ignoruj oznaczone dopasowania (czyli wyrażenia w nawiasach); nie podstawienia są przechowywane.
- `optimize`: Upewnij się, dopasowanie szybciej, kosztem możliwe czasu większą konstrukcji.
- `collate`: Za pomocą sekwencji sortowania zależne od ustawień regionalnych (na przykład zakresów w postaci "[a-z]").

Zero lub więcej flagi mogą być łączone z gramatyki, aby określić zachowanie aparatu wyrażenia regularnego. Jeśli tylko określonych flag `ECMAScript` zakłada, że jako gramatyki.

### <a name="element"></a>Element

Element może być jednym z następujących:

- *Zwykły znak* odpowiadającej takiego samego znaku w sekwencji docelowej.

- A *wieloznacznego* ".", dopasowuje dowolny znak w sekwencji docelowej, z wyjątkiem nowego wiersza.

- A *Dopasowywanie wyrażeń* w postaci "[`expr`]", który pasuje do znaku lub elementu sortowania w sekwencji docelowej, który jest również w zestawie, który został zdefiniowany przez wyrażenie `expr`, lub w postaci "[^`expr`]", który Dopasowuje znak lub elementu sortowania w sekwencji docelowej, który nie znajduje się w zestawie, który został zdefiniowany przez wyrażenie `expr`.

     Wyrażenie `expr` może zawierać dowolną kombinację następujących czynników:

    -   Pojedynczy znak. Dodaje ten znak do zestawu zdefiniowanego przez `expr`.

    -   A *zakres znaków* w postaci "`ch1`-`ch2`". Dodaje znaki, które są reprezentowane przez wartości w zamkniętym zakresie [`ch1`, `ch2`] do zestawu zdefiniowanego przez `expr`.

    -   A *klasy znaków* w postaci "[:`name`:]". Dodaje znaki w nazwanej klasie do zestawu zdefiniowanego przez `expr`.

    -   *Klasa równoważności* w postaci "[=`elt`=]". Dodaje elementy sortowania, które są równoważne `elt` do zestawu zdefiniowanego przez `expr`.

    -   A *symbol sortowania* w postaci "[.`elt`.]". Dodaje element sortowania `elt` do zestawu zdefiniowanego przez `expr`.

- *Zakotwiczenia*. Kotwica '^' pasuje do początku sekwencji docelowej; kotwica '$' pasuje do końca sekwencji docelowej.

A *grupa przechwytywania* w postaci "( *Podwyrażenie* )", lub "\\( *Podwyrażenie* \\)" w `basic` i `grep`, który pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami.

- *Ucieczka tożsamości* w postaci "\\`k`", która pasuje do znaku `k` w sekwencji docelowej.

Przykłady:

- „a” pasuje do sekwencji docelowej „a”, ale nie pasuje do sekwencji docelowych „B”, „b” lub „c”.

- „.” pasuje do wszystkich sekwencji docelowych „a”, „B”, „b” i „c”.

- „[b-z]” pasuje do sekwencji docelowych „b” i „c”, ale nie pasuje do sekwencji docelowych „a” lub „B”.

- „[:lower:]” pasuje do sekwencji docelowych „a”, „b” i „c”, ale nie pasuje do sekwencji docelowej „B”.

- „(a)” pasuje do sekwencji docelowej „a” i kojarzy grupę przechwytywania 1 z podsekwencją „a”, ale nie pasuje do sekwencji docelowych „B”, „b” lub „c”.

W `ECMAScript`, `basic`, i `grep`, element może być również *dopasowanie wsteczne* w postaci "\\`dd`", gdzie `dd` reprezentuje wartość dziesiętną N, która pasuje do sekwencji znaki w elemencie docelowym czyli sekwencji jako sekwencja znaków, w której pasuje n-tej *grupa przechwytywania*. Na przykład, „(a)\1” odpowiada sekwencji docelowej „aa”, ponieważ pierwsza (i tylko) grupa przechwytywania pasuje do początkowej sekwencji „a”, a następnie \1 pasuje do ostatniej sekwencji „a”.

W `ECMAScript`, element może też być jednym z następujących czynności:

- A *grupa nieprzechwytująca* w postaci "(?: *Podwyrażenie* )". Pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami.

- Ograniczony *sekwencja unikowa formatu pliku* o postaci "\f", "\n", "\r", "\t" lub "\v". Pasują one, odpowiednio, do wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulatora poziomego i tabulatora pionowego w sekwencji docelowej.

- A *asercja pozytywna* w postaci "(= *Podwyrażenie* )". Pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami, ale nie zmienia pozycji dopasowania w sekwencji docelowej.

- A *asercja negatywna* w postaci "(! *Podwyrażenie* ) ". Pasuje do dowolnej sekwencji znaków w sekwencji docelowej, do której nie pasuje wzorzec między ogranicznikami, i nie zmienia pozycji dopasowania w sekwencji docelowej.

- A *szesnastkowa sekwencja unikowa* w postaci "\x`hh`". Pasuje do znaku w sekwencji docelowej, który jest reprezentowany przez dwie cyfry szesnastkowe `hh`.

- A *sekwencja unikowa unicode* w postaci "\u`hhhh`". Pasuje do znaku w sekwencji docelowej, który jest reprezentowany przez cztery cyfry szesnastkowe `hhhh`.

- A *kontrolować sekwencja unikowa* w postaci "\c`k`". Dopasowuje znak kontrolny, który jest nazwany przez znak `k`.

- A *asercja granicy słowa* w postaci "\b". Pasuje, gdy bieżąca pozycja w sekwencji docelowej występuje natychmiast po *granicy słowa*.

- A *asercja negatywna granicy słowa* w postaci "\B". Pasuje, gdy bieżąca pozycja w sekwencji docelowej nie występuje natychmiast po *granicy słowa*.

- A *sekwencja unikowa dsw* w postaci "\d", "\D", "\s", "\S", "\w", "\W". Zawiera skróconą nazwę klasy znaków.

Przykłady:

- „(?:a)” pasuje do sekwencji docelowej „a”, ale „(?:a)\1” jest nieprawidłowe, ponieważ nie istnieje żadna grupa przechwytywania 1.

- "(=a)" pasuje do sekwencji docelowej "". Asercja pozytywna pasuje do początkowej sekwencji „a” w sekwencji docelowej, a końcowe „a” w wyrażeniu regularnym pasuje do sekwencji początkowej „a” w sekwencji docelowej.

- "(!a)" nie pasuje do sekwencji docelowej "".

- "a\b." pasuje do sekwencji docelowej "~", ale nie pasuje do sekwencji docelowej "ab".

- "a\B." pasuje do sekwencji docelowej "ab", ale nie pasuje do sekwencji docelowej "~".

W `awk`, element może też być jednym z następujących czynności:

- A *sekwencja unikowa formatu pliku* w postaci "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" lub "\v". Pasują one, odpowiednio, do odwrotnego ukośnika, alertu, backspace, wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulatora poziomego i tabulatora pionowego w sekwencji docelowej.

- *Ósemkowa sekwencja unikowa* w postaci "\\`ooo`". Pasuje do znaku w sekwencji docelowej, którego reprezentacja jest wartością reprezentowaną przez jeden, dwa lub trzy cyfry ósemkowe `ooo`.

### <a name="repetition"></a>Powtórzenie

Dowolnego elementu innego niż *asercja pozytywna*, *asercja negatywna*, lub *zakotwiczenia* może następować licznik powtórzeń. Najbardziej ogólny rodzaj licznika powtórzeń ma postać "{`min`,`max`}", lub "\\{`min`,`max`\\}" w `basic` i `grep`. Element, który następuje po tej postaci licznika powtórzeń dopasowuje co najmniej `min` kolejnych wystąpień i nie więcej niż `max` kolejnych wystąpień sekwencji, która pasuje do elementu. Na przykład "{2,3}" pasuje do sekwencji docelowej "aa" i sekwencji docelowej "aaa", ale nie do sekwencji docelowej "a" lub sekwencji docelowej "aaaa".

Licznik powtórzeń może mieć również jedną z następujących postaci:

- "{`min`}", lub "\\{`min`\\}" w `basic` i `grep`. Odpowiednikiem "{`min`,`min`}".

- "{`min`,}", lub "\\{`min`,\\}" w `basic` i `grep`. Odpowiednikiem "{`min`, nieograniczone}".

- "\*". Równoważne postaci „{0,nieograniczone}”.

Przykłady:

- "{2}" pasuje do sekwencji docelowej "aa", ale nie do sekwencji docelowej "a" lub sekwencji docelowej "aaa".

- "{2,}" pasuje do sekwencji docelowej "aa", sekwencji docelowej "aaa" i tak dalej, ale nie pasuje do sekwencji docelowej "".

- "\*" pasuje do sekwencji docelowej "", docelowy sekwencji "a", sekwencji docelowej "aa" itd.

We wszystkich gramatykach, z wyjątkiem `basic` i `grep`, licznik powtórzeń może skorzystać z jednej z następujących form:

- "?". Odpowiednikiem "{0,1}".

- "+". Odpowiednik wartości "{1, nieograniczone}".

Przykłady:

- ""? pasuje do sekwencji docelowej "" i sekwencji docelowej "a", ale nie do sekwencji docelowej "aa".

- „a+” pasuje do sekwencji docelowej „a”, sekwencji docelowej „aa” itd., ale nie do sekwencji docelowej „”.

W `ECMAScript`, wszystkich postaciach licznika powtórzeń może następować znak '?', który wyznacza *powtórzenie niezachłanne*.

### <a name="concatenation"></a>Połączenie (konkatenacja)

Elementy wyrażeń regularnych, z lub bez *liczby powtórzeń*, mogą być łączone w dłuższe wyrażenia regularne. Wyrażenie wynikowe pasuje do sekwencji docelowej będącej połączeniem sekwencji, do których pasują poszczególne elementy. Na przykład "{2,3}b" pasuje do sekwencji docelowej "aab" i sekwencji docelowej "aaab", ale nie pasuje sekwencji docelowej "ab" ani sekwencji docelowej "aaaab".

### <a name="alternation"></a>Alternatywa

We wszystkich gramatykach wyrażeń regularnych, z wyjątkiem `basic` i `grep`, po połączonym wyrażeniu regularnym może następować znak '&#124;"i inne połączone wyrażenie regularne. W ten sposób można łączyć dowolną liczbę połączonych wyrażeń regularnych. Wyrażenie wynikowe pasuje do dowolnej sekwencji docelowej, do której pasuje jedno lub więcej z połączonych wyrażeń regularnych.

Gdy więcej niż jeden z połączonych wyrażeń regularnych pasuje do sekwencji docelowej, `ECMAScript` wybiera pierwsze z połączonych wyrażeń regularnych, który pasuje do sekwencji jako dopasowanie (*pierwsze wystąpienie*); druga gramatyki wyrażenia regularnego wybierają jednego, które daje w wyniku *najdłuższe*. Na przykład "ab&#124;dysk cd" pasuje do sekwencji docelowej "ab" i sekwencji docelowej "cd", ale nie jest zgodny, sekwencji docelowej "abd" lub sekwencji docelowej "acd".

W `grep` i `egrep`, znak nowego wiersza (\n) może służyć do oddzielania alternatyw.

### <a name="subexpression"></a>Wyrażenie cząstkowe

W `basic` i `grep`, Wyrażenie cząstkowe jest połączenie. W innych gramatykach wyrażeń regularnych wyrażenie cząstkowe jest alternatywą.

## <a name="grammarsummary"></a> Krótki opis gramatyki

W następującej tabeli podsumowano funkcje, które są dostępne w różnych gramatykach wyrażeń regularnych:

|Element|Podstawowe|rozszerzone|ECMAScript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|alternatywa przy użyciu "&#124;"||+|+||+|+|
|alternatywa przy użyciu '\n'||||+|+||
|kotwica|+|+|+|+|+|+|
|dopasowanie wsteczne|+||+|+|||
|wyrażenie w nawiasie kwadratowym|+|+|+|+|+|+|
|grupa przechwytywania przy użyciu „()”||+|+||+|+|
|Grupa przechwytywania przy użyciu "\\(\\)"|+|||+|||
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
|Powtórzenie przy użyciu "{}"||+|+||+|+|
|Powtórzenie przy użyciu "\\{\\}"|+|||+|||
|Powtórzenie przy użyciu "\*"|+|+|+|+|+|+|
|powtórzenie przy użyciu '?' i '+'||+|+||+|+|
|sekwencja unikowa unicode|||+||||
|symbol wieloznaczny|+|+|+|+|+|+|
|asercja granicy słowa|||+||||

## <a name="semanticdetails"></a> Szczegóły semantyki

### <a name="anchor"></a>Kotwica

Kotwica pasuje do pozycji w ciągu docelowym, a nie do znaku. Kotwica '^' pasuje do początku ciągu docelowego, a kotwica '$' pasuje do końca ciągu docelowego.

### <a name="back-reference"></a>Dopasowanie wsteczne

Dopasowanie wsteczne to ukośnik odwrotny, po którym następuje wartość dziesiętna N. Pasuje do zawartości n-tej *grupa przechwytywania*. Wartość N nie może być większa niż liczba grup przechwytywania, które poprzedzają dopasowanie wsteczne. W `basic` i `grep`, wartość n jest określana przez cyfrę dziesiętną, która następuje po odwrotnym ukośniku. W `ECMAScript`, wartość n jest określana przez wszystkie cyfry dziesiętne, które bezpośrednio po odwrotnym ukośniku. Dlatego w `basic` i `grep`, wartość N nigdy nie jest większa niż 9, nawet wtedy, gdy wyrażenie regularne ma więcej niż dziewięć grup przechwytywania. W `ECMAScript`, wartość N jest nieograniczona.

Przykłady:

- „((a+)(b+))(c+)\3” pasuje do sekwencji docelowej „aabbbcbbb”. Dopasowanie wsteczne „\3” pasuje do tekstu z trzeciej grupy przechwytywania, to znaczy „(b+)”. Nie pasuje do sekwencji docelowej „aabbbcbb”.

- „(a)\2” jest nieprawidłowe.

- "(b ((())) \10" ma różne znaczenie w `basic` i `ECMAScript`. W `basic` dopasowanie wsteczne to "\1". Dopasowanie wsteczne pasuje do zawartości pierwszej grupy przechwytywania (czyli tej, która zaczyna się od „(b” i kończy się ostatnim „)” i znajduje się przed dopasowaniem wstecznym), a końcowe '0' pasuje do zwykłego znaku '0'. W `ECMAScript`, dopasowanie wsteczne to "\10". Pasuje do dziesiątej grupy przechwytywania, to znaczy tej najbardziej w środku.

### <a name="bracket-expression"></a>Wyrażenie w nawiasie kwadratowym

Wyrażenie w nawiasie kwadratowym definiuje zestaw znaków i *elementy sortujące*. Kiedy wyrażenie w nawiasie kwadratowym zaczyna się od znaku '^', dopasowanie zakończy się pomyślnie, jeśli do bieżącego znaku w sekwencji docelowej nie pasuje żaden element w zestawie. W przeciwnym razie dopasowanie się powiedzie, jeśli do bieżącego znaku w sekwencji docelowej pasuje dowolny z elementów w zestawie.

Zestaw znaków może być zdefiniowany przez wymienienie dowolnej kombinacji *pojedynczych znaków*, *znak zakresów*, *klasy znaku*, *równoważności klasy*, i *symboli sortowania*.

### <a name="capture-group"></a>Grupa przechwytywania

Grupa przechwytywania oznacza swoją zawartość jako pojedynczą jednostkę w gramatyce wyrażeń regularnych i nadaje etykietę tekstowi docelowemu, który pasuje do jej zawartości. Etykieta skojarzona z każdą grupą przechwytywania to numer, który zależy od policzenia nawiasów otwierających, oznaczających grupy przechwytywania, aż do nawiasu otwierającego włącznie, który oznacza bieżącą grupę przechwytywania. W tej implementacji maksymalna liczba grup przechwytywania to 31.

Przykłady:

- „ab+” pasuje do sekwencji docelowej „abb”, ale nie pasuje do sekwencji docelowej „abab”.

- „(ab)+” nie pasuje do sekwencji docelowej „abb”, ale pasuje do sekwencji docelowej „abab”.

- „((a+)(b+))(c+)” pasuje do sekwencji docelowej „aabbbc” i kojarzy grupę przechwytywania 1 z podsekwencją „aabbb”, grupę przechwytywania 2 z podsekwencją „aa”, grupę przechwytywania 3 z „bbb” i grupę przechwytywania 4 z podsekwencją „c”.

### <a name="character-class"></a>Klasa znaków

Klasa znaków w wyrażeniu w nawiasie kwadratowym dodaje wszystkie znaki w nazwanej klasie do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć klasę znaków, należy użyć „[:”, po którym następuje nazwa klasy, a na koniec „:]”. Wewnętrznie, nazwy klasy znaków są rozpoznawane przez wywołanie `id = traits.lookup_classname`. Znak `ch` należy do takiej klasy, jeśli `traits.isctype(ch, id)` zwraca wartość true. Wartość domyślna `regex_traits` szablon obsługuje nazwy klas w poniższej tabeli.

|Nazwa klasy|Opis|
|----------------|-----------------|
|„alnum”|małe litery, wielkie litery i cyfry|
|„alpha”|małe litery i wielkie litery|
|„blank”|spacja lub tabulator|
|„cntrl”|*sekwencja unikowa formatu pliku* znaków|
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

- „[0-7]” reprezentuje zestaw znaków { '0', '1', '2', '3', '4', '5', '6', '7' }. Pasuje do sekwencji docelowych „0”, „1” itd., ale nie do „a”.

- W systemach używających kodowania znaków ASCII, „[h-k]” reprezentuje zestaw znaków { 'h', 'i', 'j', 'k' }. Pasuje do sekwencji docelowych „h”, „i” itd., ale nie do „\x8A” lub „0”.

- W systemach używających kodowania znaków EBCDIC, „[h-k]” reprezentuje zestaw znaków { 'h', 'i', '\x8A', '\x8B', '\x8C', '\x8D', '\x8E', '\x8F', '\x90', 'j', 'k' } ('h' jest kodowane jako 0x88, a 'k' jest kodowane jako 0x92). Pasuje do sekwencji docelowych „h”, „i”, „\x8A” itd., ale nie do „0”.

- „[-0-24]” reprezentuje zestaw znaków { '-', '0', '1', '2', '4' }.

- „[0-2-]” reprezentuje zestaw znaków { '0', '1', '2', '-' }.

- W systemach używających kodowania znaków ASCII, „[+--]” reprezentuje zestaw znaków { '+', ',', '-' }.

Gdy używane są zakresy zależne od ustawień regionalnych, znaki w zakresie są określane przez reguły sortowania dla ustawień regionalnych. W zestawie znajdują się znaki, które są sortowane po pierwszym znaku w definicji zakresu i przed ostatnim znakiem w definicji zakresu. Dwa znaki końcowe również znajdują się w zestawie.

### <a name="collating-element"></a>Element sortujący

Element sortujący to sekwencja wielu znaków, która jest traktowana jako pojedynczy znak.

### <a name="collating-symbol"></a>Symbol sortowania

Symbol sortowania w wyrażeniu w nawiasie kwadratowym dodaje *element sortujący* do zestawu, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć symbol sortowania, należy użyć "[." następuje element sortujący, a następnie "."].

### <a name="control-escape-sequence"></a>Kontrolna sekwencja unikowa

Kontrolna sekwencja unikowa to ukośnik odwrotny, po którym następuje litera „c”, po której następuje jedna z liter od 'a' do 'z' lub od 'A' do 'Z'. Pasuje do znaku kontrolnego ASCII, który jest nazwany przez tę literę. Na przykład "\ci" pasuje do sekwencji docelowej "\x09", ponieważ \<ctrl-i > ma wartość 0x09.

### <a name="dsw-character-escape"></a>Sekwencja unikowa DSW.

Sekwencja unikowa dsw to skrócona nazwa klasy znaków, jak pokazano w poniższej tabeli.

|Sekwencja unikowa|Równoważna nazwana klasa|Domyślna nazwana klasa|
|---------------------|----------------------------|-------------------------|
|„\d”|„[[:d:]]”|„[[:digit:]]”|
|„\D”|„[^[:d:]]”|„[^[:digit:]]”|
|„\s”|„[[:s:]]”|„[[:space:]]”|
|„\S”|„[^[:s:]]”|„[^[:space:]]”|
|„\w”|„[[:w:]]”|"[a-zA-Z0-9_]"\*|
|„\W”|„[^[:w:]]”|"[^ a-zA-Z0-9_]"\*|

\*Zestaw znaków ASCII

### <a name="equivalence-class"></a>Klasa równoważności

Klasa równoważności w wyrażeniu w nawiasie kwadratowym dodaje wszystkie znaki i *elementy sortujące* , które są równoważne elementowi sortującemu w definicji klasy równoważności, do zestawu, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć klasę równoważności, należy użyć „[=”, po którym następuje element sortujący, a na koniec „=]”. Wewnętrznie, dwa elementy sortujące `elt1` i `elt2` są równoważne Jeśli `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.

### <a name="file-format-escape"></a>Sekwencja unikowa formatu pliku

Sekwencja unikowa formatu pliku składa się zwykle C sekwencji specjalnych języka, "\\\\", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Mają one zwykłe znaczenia, oznacza to, że ukośnik odwrotny, alert, backspace, wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulator poziomy i tabulator pionowy, odpowiednio. W `ECMAScript`, "\a" i "\b" nie są dozwolone. ("\\\\" jest dozwolony, ale jest to ucieczka tożsamości, nie unikowa formatu pliku).

### <a name="hexadecimal-escape-sequence"></a>Szesnastkowa sekwencja unikowa

Szesnastkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje litera 'x' i dwie cyfry szesnastkowe (0-9a-fA-F). Pasuje do znaku w sekwencji docelowej, która ma wartość określoną przez te dwie cyfry. Na przykład, „\x41” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="identity-escape"></a>Ucieczka tożsamości

Ucieczka tożsamości to odwrotny ukośnik, po którym następuje pojedynczy znak. Pasuje do tego znaku. Jest wymagana, gdy znak ma specjalne znaczenie; dzięki ucieczce tożsamości to znaczenie jest usuwane. Na przykład:

- "\*" pasuje do sekwencji docelowej "aaa", ale nie pasuje do sekwencji docelowej "\*".

- "\\\*" nie pasuje do sekwencji docelowej "aaa", ale pasuje do sekwencji docelowej "\*".

Zestaw znaków, które są dozwolone w ucieczce tożsamości, zależy od gramatyki wyrażeń regularnych, jak pokazano w poniższej tabeli.

|Gramatyka|Dozwolone znaki ucieczki tożsamości|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended` plus {' "', '/'}|
|`ECMAScript`|Wszystkie znaki z wyjątkiem tych, które mogą być częścią identyfikatora. Zazwyczaj obejmuje to litery, cyfry, '$', '\_"i sekwencje unikowe unicode. Aby uzyskać więcej informacji, zobacz temat specyfikacji języka ECMAScript.|

### <a name="individual-character"></a>Pojedynczy znak

Pojedynczy znak w wyrażeniu w nawiasie kwadratowym dodaje ten znak do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Gdziekolwiek w wyrażeniu w nawiasie kwadratowym, z wyjątkiem początku, '^' reprezentuje sam siebie.

Przykłady:

- „[abc]” pasuje do sekwencji docelowych „a”, „b” i „c”, ale nie do sekwencji „d”.

- „[^abc]” pasuje do sekwencji docelowej „d”, ale nie do sekwencji docelowych „a”, „b” lub „c”.

- „[a^bc]” pasuje do sekwencji docelowych „a”, „b”, „c” i „^” , ale nie do sekwencji docelowej „d”.

We wszystkich gramatykach wyrażeń regularnych, z wyjątkiem `ECMAScript`, jeśli "]" jest pierwszym znakiem, który następuje po otwierającym ' ["lub jest pierwszym znakiem, który następuje po początkowym ' ^', reprezentuje sam siebie.

Przykłady:

- „[]a” jest nieprawidłowe, ponieważ nie ma ']', aby zakończyć wyrażenie w nawiasie kwadratowym.

- „[]abc]” pasuje do sekwencji docelowych „a”, „b”, „c” i „]”, ale nie do sekwencji docelowej „d”.

- „[^]abc]” pasuje do sekwencji docelowej „d”, ale nie do sekwencji docelowych „a”, „b”, „c” lub „]”.

W `ECMAScript`, użyj "\\]' do reprezentowania znaku ']' w wyrażeniu w nawiasie kwadratowym.

Przykłady:

- „[]a” pasuje do sekwencji docelowej „a”, ponieważ wyrażenie w nawiasie kwadratowym jest puste.

- "[\\] [abc]" pasuje do sekwencji docelowych "a", "b", "c" i "]", ale nie do sekwencji docelowej "d".

### <a name="negative-assert"></a>Asercja negatywna

Asercja negatywna pasuje do wszystkiego oprócz swojej zawartości. Nie używa żadnych znaków w sekwencji docelowej. Na przykład "(!aa) (\*)" pasuje do sekwencji docelowej "" i kojarzy grupę przechwytywania 1 z podsekwencją "". Nie pasuje do sekwencji docelowej „aa” ani do sekwencji docelowej „aaa”.

### <a name="negative-word-boundary-assert"></a>Asercja negatywna granicy słowa

Asercja negatywna granicy słowa pasuje, gdy bieżąca pozycja w ciągu docelowym nie występuje natychmiast po *granicy słowa*.

### <a name="non-capture-group"></a>Grupa nieprzechwytująca

Grupa nieprzechwytująca oznacza swoją zawartość jako pojedynczą jednostkę w gramatyce wyrażeń regularnych, ale nie nadaje etykiety tekstowi docelowemu. Na przykład "(a)(?:b)\*(c)" pasuje do tekstu docelowego "abbc" i kojarzy grupę przechwytywania 1 z podsekwencją ""i grupę przechwytywania 2 z podsekwencją "c". "_FITTED

### <a name="non-greedy-repetition"></a>Powtórzenie niezachłanne

Powtórzenie niezachłanne używa najkrótszej podsekwencji sekwencji docelowej, która pasuje do wzorca. Powtórzenie zachłanne używa najdłuższej. Na przykład "(a+) (\*b)" pasuje do sekwencji docelowej "aaab". Gdy używa się powtórzenia niezachłannego, kojarzy ono grupę przechwytywania 1 z podsekwencją „a” na początku sekwencji docelowej, a grupę przechwytywania 2 z podsekwencją „aab” na końcu sekwencji docelowej. Gdy używa się dopasowania zachłannego, kojarzy ono grupę przechwytywania 1 z podsekwencją „aaa”, a grupę przechwytywania 2 z podsekwencją „b”.

### <a name="octal-escape-sequence"></a>Ósemkowa sekwencja unikowa

Ósemkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje jedna, dwie lub trzy cyfry ósemkowe (0-7). Pasuje do znaku w sekwencji docelowej, który ma wartość określoną przez te cyfry. Jeśli wszystkie cyfry to '0', sekwencja jest nieprawidłowa. Na przykład, „\101” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="ordinary-character"></a>Zwykły znak

Zwykły znak to dowolny prawidłowy znak, który nie ma specjalnego znaczenia w bieżącej gramatyce.

W `ECMAScript`, następujące znaki mają specjalne znaczenie:

- ^  $  \  .  \*  +  ?  (  )  [  ]  {  }  &#124;

W `basic` i `grep`, następujące znaki mają specjalne znaczenie:

- .   [   \

Również w `basic` i `grep`, następujące znaki mają specjalne znaczenie, gdy są one używane w szczególnym kontekście:

- "\*' ma specjalne znaczenie we wszystkich przypadkach, z wyjątkiem sytuacji, gdy jest pierwszy znak w wyrażeniu regularnym lub pierwszy znak, który następuje po początkowym ' ^' w wyrażeniu regularnym, lub gdy jest to pierwszy znak przechwycenia grupy lub pierwszy znak następuje po początkowym ' ^' w grupie przechwytywania.

- '^' ma specjalne znaczenie, gdy jest to pierwszy znak wyrażenia regularnego.

- '$' ma specjalne znaczenie, gdy jest to ostatni znak wyrażenia regularnego.

W `extended`, `egrep`, i `awk`, następujące znaki mają specjalne znaczenie:

- .   [   \   (   \*   +   ?   {   &#124;

Również w `extended`, `egrep`, i `awk`, następujące znaki mają specjalne znaczenie, gdy są one używane w szczególnym kontekście.

- ')' ma specjalne znaczenie, gdy pasuje do poprzedzającego '('.

- '^' ma specjalne znaczenie, gdy jest to pierwszy znak wyrażenia regularnego.

- '$' ma specjalne znaczenie, gdy jest to ostatni znak wyrażenia regularnego.

Zwykły znak pasuje do takiego samego znaku w sekwencji docelowej. Domyślnie oznacza to, że dopasowanie się powiedzie, jeśli dwa znaki są reprezentowane przez tę samą wartość. W dopasowanie bez uwzględniania wielkości liter, dwa znaki `ch0` i `ch1` dopasowania, jeśli `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. W przypadku dopasowania zależne od ustawień regionalnych, dwa znaki `ch0` i `ch1` dopasowania, jeśli `traits.translate(ch0) == traits.translate(ch1)`.

### <a name="positive-assert"></a>Asercja pozytywna

Asercja pozytywna pasuje do swojej zawartości, ale nie używa żadnych znaków w sekwencji docelowej.

Przykłady:

- "(=aa) (\*)" pasuje do sekwencji docelowej "aaaa" i kojarzy grupę przechwytywania 1 z podsekwencją "aaaa".

- "(aa) (\*)" pasuje do sekwencji docelowej "aaaa" i kojarzy grupę przechwytywania 1 z podsekwencją "aa" na początku docelowego sekwencji, a grupę przechwytywania 2 z podsekwencją "aa" na końcu sekwencji docelowej.

- "(=aa)(a)&#124;()" pasuje do sekwencji docelowej "" i kojarzy grupę przechwytywania 1 z pustą sekwencją (ponieważ asercja pozytywna nie powiodła się) a grupę przechwytywania 2 z podsekwencją "". Pasuje też do sekwencji docelowej „aa” i kojarzy grupę przechwytywania 1 z podsekwencją „aa”, a grupę przechwytywania 2 z pustą sekwencją.

### <a name="unicode-escape-sequence"></a>Sekwencja unikowa unicode

Sekwencja unikowa unicode to ukośnik odwrotny, po którym następuje litera 'u' i cztery cyfry szesnastkowe (0-9a-fA-F). Pasuje do znaku w sekwencji docelowej, który ma wartość określoną przez te cztery cyfry. Na przykład, „\u0041” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="wildcard-character"></a>Symbol wieloznaczny

Symbol wieloznaczny pasuje do dowolnego znaku w wyrażeniu docelowym z wyjątkiem nowego wiersza.

### <a name="word-boundary"></a>Granica słowa

Granica słowa występuje w następujących sytuacjach:

- Bieżący znak jest na początku sekwencji docelowej i jest jednym ze znaków słowa `A-Za-z0-9_.`

- Bieżąca pozycja znaku jest poza końcem sekwencji docelowej, a ostatni znak w sekwencji docelowej jest jednym ze znaków słowa.

- Bieżący znak jest jednym ze znaków słowa, a znak poprzedzający nie jest.

- Bieżący znak nie jest jednym ze znaków słowa, a znak poprzedzający jest.

### <a name="word-boundary-assert"></a>Asercja granicy słowa

Asercja granicy słowa pasuje, gdy bieżąca pozycja w ciąg docelowym jest natychmiast po *granicy słowa*.

## <a name="matchingandsearching"></a> Dopasowywanie i wyszukiwanie

Aby wyrażenie regularne pasowało do sekwencji docelowej, całe wyrażenie regularne musi pasować do całej sekwencji docelowej. Na przykład, wyrażenie regularne „bcd” pasuje do sekwencji docelowej „bcd”, ale nie pasuje do sekwencji docelowej „abcd” ani sekwencji docelowej „bcde”.

Aby wyszukiwanie wyrażenia regularnego zostało wykonane pomyślnie, gdzieś w sekwencji docelowej musi istnieć podsekwencja, która odpowiada wyrażeniu regularnemu. Wyszukiwanie znajduje zazwyczaj pasującą podsekwencję najbliżej lewej strony.

Przykłady:

- Wyszukanie wyrażenia regularnego „bcd” w sekwencji docelowej „bcd” zakończy się pomyślnie i dopasuje całą sekwencję. To samo wyszukiwanie w sekwencji docelowej „abcd” również zakończy się pomyślnie i dopasuje ostatnie trzy znaki. To samo wyszukiwanie w sekwencji docelowej „bcde” również zakończy się pomyślnie i dopasuje pierwsze trzy znaki.

- Wyszukanie wyrażenia regularnego „bcd” w sekwencji docelowej „bcdbcd” zakończy się pomyślnie i dopasuje pierwsze trzy znaki.

Jeśli istnieje więcej niż jedna podsekwencja, która pasuje w którymś miejscu w sekwencji docelowej, istnieją dwa sposoby wyboru pasującego wzorca. *Pierwsze wystąpienie* wybiera podsekwencję, która została znaleziona jako pierwsza po dopasowaniu wyrażenia regularnego. *Najdłuższe* wybiera najdłuższą podsekwencję z tych, które pasują w tej lokalizacji. Jeśli istnieje więcej niż jedna podsekwencja, która ma maksymalną długość, najdłuższe wystąpienie wybiera tę, która została znaleziona jako pierwsza. Na przykład, gdy zostanie użyte pierwsze wystąpienie, wyszukiwanie wyrażenia regularnego "b&#124;bc" w elemencie docelowym sekwencji "abcd" pasuje do podsekwencji "b", ponieważ po lewej stronie termin alternatywy pasuje do tej podsekwencji; Dlatego pierwsze dopasowanie nie próbuje prawej strony alternatywy. Gdy jest używane najdłuższe wystąpienie, to samo wyszukiwanie pasuje do „bc” ponieważ „bc” jest dłuższe niż „b”.

Częściowe wystąpienie powiedzie się, jeśli dopasowanie osiąga koniec sekwencji docelowej bez niepowodzenia, nawet jeśli nie osiągnęło końca wyrażenia regularnego. W związku z tym, po pomyślnym częściowym wystąpieniu, dodanie znaków do sekwencji docelowej mogłoby spowodować niepowodzenie późniejszego częściowego wystąpienia. Jednakże, po niepowodzeniu częściowego wystąpienia, dodanie znaków do sekwencji docelowej nie może spowodować powodzenia późniejszego częściowego wystąpienia. Na przykład, przy częściowym wystąpieniu, „ab” pasuje do sekwencji docelowej „a”, ale nie „ac”.

## <a name="formatflags"></a> Flagi formatu

|Reguły formatu ECMAScript|Reguły formatu sed|Tekst zastępczy|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Sekwencja znaków, który odpowiada całego wyrażenia regularnego (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"\\&"|"&"|
|"$\`" (znak dolara następuje odwrócony pojedynczy cudzysłów)||Sekwencja znaków poprzedzająca podsekwencję, która odpowiada wyrażeniu regularnemu (`[match.prefix().first, match.prefix().second)`)|
|„$'” (znak dolara, po którym następuje cudzysłów pojedynczy)||Sekwencja znaków, który następuje po podsekwencję, która odpowiada wyrażeniu regularnemu (`[match.suffix().first, match.suffix().second)`)|
|„$n”|„\n”|Sekwencja znaków, który pasuje do grupy przechwytywania w pozycji `n`, gdzie `n` jest liczbą z zakresu od 0 do 9 (`[match[n].first, match[n].second)`)|
||"\\\n"|„\n”|
|„$nn”||Sekwencja znaków, który pasuje do grupy przechwytywania w pozycji `nn`, gdzie `nn` jest liczbą z zakresu od 10 do 99 (`[match[nn].first, match[nn].second)`)|

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
