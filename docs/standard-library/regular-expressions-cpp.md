---
title: Wyrażenia regularne (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
ms.openlocfilehash: db5a7eacc136b3f30187692c7ea10792b84eb3fc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451378"
---
# <a name="regular-expressions-c"></a>Wyrażenia regularne (C++)

Biblioteka C++ standardowa obsługuje wiele gramatyk wyrażeń regularnych. W tym temacie omówiono różnice gramatyczne dostępne podczas używania wyrażeń regularnych.

## <a name="regexgrammar"></a>Gramatyka wyrażenia regularnego

Gramatyka wyrażenia regularnego do użycia jest określona przez użycie jednej z `std::regex_constants::syntax_option_type` wartości wyliczenia. Te gramatyki wyrażeń regularnych są zdefiniowane w std:: regex_constants:

- `ECMAScript`: Jest to najbliżej gramatyki używanej przez język JavaScript i języki .NET.
- `basic`: Podstawowe wyrażenia w standardzie POSIX lub BRE.
- `extended`: Rozszerzone wyrażenia regularne lub ERE.
- `awk`: Jest `extended`to, ale ma dodatkowe ucieczki dla znaków niedrukowalnych.
- `grep`: Jest `basic`to, ale umożliwia także znak nowego wiersza ("\n"), aby oddzielić zmiany.
- `egrep`: Jest `extended`to, ale umożliwia także znak nowego wiersza do oddzielania alternatyw.

Domyślnie, jeśli nie określono gramatyki, `ECMAScript` przyjmuje się. Można określić tylko jedną gramatykę.

Oprócz gramatyki można zastosować kilka flag:
- `icase`: Ignoruj wielkość liter podczas dopasowywania.
- `nosubs`: Ignoruj oznaczone dopasowania (czyli wyrażenia w nawiasach); nie są przechowywane podstawiania.
- `optimize`: Szybsze dopasowanie, przy możliwym kosztie większego czasu konstrukcji.
- `collate`: Użyj sekwencji sortowania z uwzględnieniem ustawień regionalnych (na przykład zakresów w postaci "[a-z]").

Aby określić zachowanie aparatu wyrażeń regularnych, można połączyć zero lub więcej flag z gramatyką. Jeśli określono tylko flagi, założono, `ECMAScript` że Gramatyka.

### <a name="element"></a>Element

Element może być jednym z następujących:

- *Zwykły znak* , który pasuje do tego samego znaku w sekwencji docelowej.

- *Symbol* wieloznaczny ".", który pasuje do dowolnego znaku w sekwencji docelowej z wyjątkiem nowego wiersza.

- *Wyrażenie* w nawiasie klamrowym w postaci`expr`"[]", które dopasowuje znak lub element sortowania w sekwencji docelowej, który jest również w zestawie zdefiniowanym przez wyrażenie `expr`lub w postaci "[^`expr`]", który pasuje do znaku lub element sortowania w sekwencji docelowej, który nie należy do zestawu zdefiniowanego przez wyrażenie `expr`.

   Wyrażenie `expr` może zawierać dowolną kombinację następujących elementów:

   - Pojedynczy znak. Dodaje ten znak do zestawu zdefiniowanego przez `expr`.

   - *Zakres znaków* w formie "`ch1`-`ch2`". Dodaje znaki, które są reprezentowane przez wartości w zamkniętym zakresie [`ch1`, `ch2`] do zestawu zdefiniowanego przez `expr`.

   - *Klasa znaku* w postaci "[:`name`:]". Dodaje znaki w nazwanej klasie do zestawu zdefiniowanego przez `expr`.

   - *Klasa równoważności* w postaci "[=`elt`=]". Dodaje elementy sortowania, które są równoważne `elt` z zestawem zdefiniowanym przez. `expr`

   - *Symbol sortowania* formularza "[.`elt`.]". Dodaje element `elt` sortowania do zestawu zdefiniowanego przez `expr`.

- *Zakotwiczenie*. Kotwica '^' pasuje do początku sekwencji docelowej; kotwica '$' pasuje do końca sekwencji docelowej.

*Grupa przechwytywania* formularza "(Podwyrażenie)  " lub "\\(Podwyrażenie  \\)" w `basic` i `grep`, która dopasowuje sekwencję znaków w sekwencji docelowej, która jest dopasowywana przez wzorzec między ogranicznikami.

- *Identyfikator ucieczki* w postaci "\\`k`", który pasuje do znaku `k` w sekwencji docelowej.

Przykłady:

- „a” pasuje do sekwencji docelowej „a”, ale nie pasuje do sekwencji docelowych „B”, „b” lub „c”.

- „.” pasuje do wszystkich sekwencji docelowych „a”, „B”, „b” i „c”.

- „[b-z]” pasuje do sekwencji docelowych „b” i „c”, ale nie pasuje do sekwencji docelowych „a” lub „B”.

- „[:lower:]” pasuje do sekwencji docelowych „a”, „b” i „c”, ale nie pasuje do sekwencji docelowej „B”.

- „(a)” pasuje do sekwencji docelowej „a” i kojarzy grupę przechwytywania 1 z podsekwencją „a”, ale nie pasuje do sekwencji docelowych „B”, „b” lub „c”.

W `ECMAScript`, `basic`, `dd` i,element`dd`może\\być również odwołaniem wstecznym formularza "", gdzie reprezentuje wartość dziesiętną N, która pasuje do sekwencji znaków w elemencie docelowym  `grep` Sekwencja, która jest taka sama jak sekwencja znaków, która jest zgodna z podgrupą *przechwytywania*. Na przykład, „(a)\1” odpowiada sekwencji docelowej „aa”, ponieważ pierwsza (i tylko) grupa przechwytywania pasuje do początkowej sekwencji „a”, a następnie \1 pasuje do ostatniej sekwencji „a”.

W `ECMAScript`programie element może być również jednym z następujących elementów:

- *Grupa nie* przechwytuje formularza "(?: subexpression  )". Pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami.

- Ograniczony *Format pliku ucieczki* w postaci "\f", "\n", "\r", "\t" lub "\v". Pasują one, odpowiednio, do wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulatora poziomego i tabulatora pionowego w sekwencji docelowej.

- *Pozytywne potwierdzenie* formularza "(= subexpression)  ". Pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami, ale nie zmienia pozycji dopasowania w sekwencji docelowej.

- *Ujemne potwierdzenie* formularza "(! *subexpression* ) ". Pasuje do dowolnej sekwencji znaków w sekwencji docelowej, do której nie pasuje wzorzec między ogranicznikami, i nie zmienia pozycji dopasowania w sekwencji docelowej.

- *Szesnastkowa sekwencja ucieczki* w postaci "\x`hh`". Dopasowuje znak w sekwencji docelowej, który jest reprezentowany przez dwie cyfry `hh`szesnastkowe.

- *Sekwencja unikowa Unicode* w postaci "\u`hhhh`". Dopasowuje znak w sekwencji docelowej, który jest reprezentowany przez cztery cyfry `hhhh`szesnastkowe.

- *Sekwencja ucieczki kontrolki* w postaci "\c`k`". Dopasowuje znak kontrolny, który jest nazwany przez `k`znak.

- *Potwierdzenie granicy słowa* w postaci "\b". Dopasowuje, gdy bieżąca pozycja w sekwencji docelowej jest natychmiast po *granicy słowa*.

- *Ujemne potwierdzenie granicy słowa* w postaci "\b". Dopasowuje, gdy bieżąca pozycja w sekwencji docelowej nie jest natychmiast po *granicy słowa*.

- *DSW znak ucieczki* w postaci "\d", "\d", "\s", "\s", "\w", "\w". Zawiera skróconą nazwę klasy znaków.

Przykłady:

- „(?:a)” pasuje do sekwencji docelowej „a”, ale „(?:a)\1” jest nieprawidłowe, ponieważ nie istnieje żadna grupa przechwytywania 1.

- "(= a) a" pasuje do sekwencji docelowej "a". Asercja pozytywna pasuje do początkowej sekwencji „a” w sekwencji docelowej, a końcowe „a” w wyrażeniu regularnym pasuje do sekwencji początkowej „a” w sekwencji docelowej.

- "(! a) a" nie pasuje do sekwencji docelowej "a".

- a\B. pasuje do sekwencji docelowej "a ~", ale nie pasuje do sekwencji docelowej "AB".

- A\B. pasuje do sekwencji docelowej "AB", ale nie pasuje do sekwencji docelowej "a ~".

W `awk`programie element może być również jednym z następujących elementów:

- *Format pliku ucieczki* w postaci "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" lub "\v". Pasują one, odpowiednio, do odwrotnego ukośnika, alertu, backspace, wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulatora poziomego i tabulatora pionowego w sekwencji docelowej.

- *Ósemkowa sekwencja ucieczki* w formie\\`ooo`"". Dopasowuje znak w sekwencji docelowej, którego reprezentacja jest wartością reprezentowaną przez jedną, dwie lub trzy cyfry `ooo`ósemkowe.

### <a name="repetition"></a>Powtórzenie

Każdy element inny niż *pozytywne potwierdzenie*, *negatywne potwierdzenie*lub zakotwiczenie może następować przez liczbę powtórzeń. Najbardziej ogólnym rodzajem liczby powtórzeń jest format "{`min`,`max`}" lub "\\{`min`,`max`\\}" w `basic` i `grep`. Element, który następuje po tej formie liczby powtórzeń, dopasowuje co najmniej `min` kolejne wystąpienia i nie więcej niż `max` kolejne wystąpienia sekwencji, które pasują do elementu. Na przykład "a{2,3}" pasuje do sekwencji docelowej "AA" i sekwencji docelowej "aaa", ale nie do sekwencji docelowej "a" ani do sekwencji docelowej "aaaa".

Licznik powtórzeń może mieć również jedną z następujących postaci:

- "{`min`}" lub "\\{`min`\\}" w `basic` i `grep`. Równoważne "{`min`,`min`}".

- "{`min`,}" lub "\\{`min`,\\}" w `basic` i `grep`. Równoważne "{`min`, unboundd}".

- "\*". Równoważne postaci „{0,nieograniczone}”.

Przykłady:

- "a{2}" pasuje do sekwencji docelowej "AA", ale nie do sekwencji docelowej "a" lub sekwencji docelowej "aaa".

- "a{2,}" pasuje do sekwencji docelowej "AA", sekwencji docelowej "aaa" itd., ale nie pasuje do sekwencji docelowej "a".

- "a\*" pasuje do sekwencji docelowej "", sekwencji docelowej "a", sekwencji docelowej "AA" itd.

W przypadku wszystkich gramatyki `basic` z `grep`wyjątkiem i, liczba powtórzeń może również przyjmować jedną z następujących form:

- "?". Równoważne "{0,1}".

- "+". Odpowiednik wartości "{1, Unbounded}".

Przykłady:

- "a?" pasuje do sekwencji docelowej "" i sekwencji docelowej "a", ale nie do sekwencji docelowej "AA".

- „a+” pasuje do sekwencji docelowej „a”, sekwencji docelowej „aa” itd., ale nie do sekwencji docelowej „”.

W `ECMAScript`programie wszystkie formy liczby powtórzeń mogą następować znak "?", który wyznacza *zachłanne powtórzenia*.

### <a name="concatenation"></a>Połączenie (konkatenacja)

Elementy wyrażenia regularnego, z lub bez *liczby powtórzeń*, można łączyć, aby tworzyć dłuższe wyrażenia regularne. Wyrażenie wynikowe pasuje do sekwencji docelowej będącej połączeniem sekwencji, do których pasują poszczególne elementy. Na przykład "a{2,3}b" pasuje do sekwencji docelowej "AAB" i sekwencji docelowej "aaab", ale nie pasuje do sekwencji docelowej "AB" lub sekwencji docelowej "aaaab".

### <a name="alternation"></a>Alternatywa

We wszystkich gramatykach wyrażeń regularnych z `basic` wyjątkiem `grep`i, za pomocą połączonego wyrażenia regularnego może następować znak&#124;"" i inne połączone wyrażenie regularne. W ten sposób można łączyć dowolną liczbę połączonych wyrażeń regularnych. Wyrażenie wynikowe pasuje do dowolnej sekwencji docelowej, do której pasuje jedno lub więcej z połączonych wyrażeń regularnych.

Jeśli więcej niż jeden z połączonych wyrażeń regularnych pasuje do sekwencji docelowej, `ECMAScript` wybiera pierwszy z połączonych wyrażeń regularnych, które pasują do sekwencji jako dopasowanie (*pierwsze dopasowanie*); drugie wyrażenie regularne gramatyki wybierają te, które osiągają *najdłuższe dopasowanie*. Na przykład "AB&#124;CD" pasuje do sekwencji docelowej "AB" i sekwencji docelowej "CD", ale nie pasuje do sekwencji docelowej "Abd" lub sekwencji docelowej "ACD".

W `grep` i`egrep`, znak nowego wiersza ("\n") może służyć do oddzielania zmiany.

### <a name="subexpression"></a>Wyrażenie cząstkowe

W `basic` i`grep`, Podwyrażenie jest połączeniem. W innych gramatykach wyrażeń regularnych wyrażenie cząstkowe jest alternatywą.

## <a name="grammarsummary"></a>Podsumowanie dotyczące gramatyki

W następującej tabeli podsumowano funkcje, które są dostępne w różnych gramatykach wyrażeń regularnych:

|Element|prosty|rozszerzone|ECMAScript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|alternatywa przy użyciu&#124;' '||+|+||+|+|
|alternatywa przy użyciu '\n'||||+|+||
|kotwica|+|+|+|+|+|+|
|dopasowanie wsteczne|+||+|+|||
|wyrażenie w nawiasie kwadratowym|+|+|+|+|+|+|
|grupa przechwytywania przy użyciu „()”||+|+||+|+|
|Grupa przechwytywania przy użyciu\\"\\()"|+|||+|||
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
|powtórzenie przy użyciu "{}"||+|+||+|+|
|powtórzenie przy użyciu "\\{\\}"|+|||+|||
|powtórzenie przy użyciu "\*"|+|+|+|+|+|+|
|powtórzenie przy użyciu '?' i '+'||+|+||+|+|
|sekwencja unikowa unicode|||+||||
|symbol wieloznaczny|+|+|+|+|+|+|
|asercja granicy słowa|||+||||

## <a name="semanticdetails"></a>Szczegóły semantyczne

### <a name="anchor"></a>Kotwica

Kotwica pasuje do pozycji w ciągu docelowym, a nie do znaku. Kotwica '^' pasuje do początku ciągu docelowego, a kotwica '$' pasuje do końca ciągu docelowego.

### <a name="back-reference"></a>Dopasowanie wsteczne

Odwołanie wsteczne to ukośnik odwrotny, po którym następuje wartość dziesiętna N. Pasuje do zawartości n-tej *grupy przechwytywania*. Wartość N nie może być większa niż liczba grup przechwytywania, które poprzedzają dopasowanie wsteczne. W `basic` i`grep`, wartość N jest określana przez cyfrę dziesiętną, która następuje po ukośniku odwrotnym. W `ECMAScript`programie wartość N jest określana przez wszystkie cyfry dziesiętne, które bezpośrednio po ukośniku odwrotnym. W związku z `basic` tym `grep`w i, wartość N nigdy nie jest większa niż 9, nawet jeśli wyrażenie regularne ma więcej niż dziewięć grup przechwytywania. W `ECMAScript`, wartość N jest nieograniczona.

Przykłady:

- „((a+)(b+))(c+)\3” pasuje do sekwencji docelowej „aabbbcbbb”. Dopasowanie wsteczne „\3” pasuje do tekstu z trzeciej grupy przechwytywania, to znaczy „(b+)”. Nie pasuje do sekwencji docelowej „aabbbcbb”.

- „(a)\2” jest nieprawidłowe.

- "((((((((((((() `basic` `ECMAScript`))))))))))))))" W `basic` odwołaniu wstecznym jest "\ 1". Dopasowanie wsteczne pasuje do zawartości pierwszej grupy przechwytywania (czyli tej, która zaczyna się od „(b” i kończy się ostatnim „)” i znajduje się przed dopasowaniem wstecznym), a końcowe '0' pasuje do zwykłego znaku '0'. W `ECMAScript`programie odwołanie wsteczne to "\ 10". Pasuje do dziesiątej grupy przechwytywania, to znaczy tej najbardziej w środku.

### <a name="bracket-expression"></a>Wyrażenie w nawiasie kwadratowym

Wyrażenie w nawiasie kwadratowym definiuje zestaw znaków i *elementy sortowania*. Kiedy wyrażenie w nawiasie kwadratowym zaczyna się od znaku '^', dopasowanie zakończy się pomyślnie, jeśli do bieżącego znaku w sekwencji docelowej nie pasuje żaden element w zestawie. W przeciwnym razie dopasowanie się powiedzie, jeśli do bieżącego znaku w sekwencji docelowej pasuje dowolny z elementów w zestawie.

Zestaw znaków może być definiowany przez wystawienie dowolnej kombinacji *pojedynczych znaków*, *zakresów znaków*, *klas znaków*, *klas równoważności*i *symboli sortowania*.

### <a name="capture-group"></a>Grupa przechwytywania

Grupa przechwytywania oznacza swoją zawartość jako pojedynczą jednostkę w gramatyce wyrażeń regularnych i nadaje etykietę tekstowi docelowemu, który pasuje do jej zawartości. Etykieta skojarzona z każdą grupą przechwytywania to numer, który zależy od policzenia nawiasów otwierających, oznaczających grupy przechwytywania, aż do nawiasu otwierającego włącznie, który oznacza bieżącą grupę przechwytywania. W tej implementacji maksymalna liczba grup przechwytywania to 31.

Przykłady:

- „ab+” pasuje do sekwencji docelowej „abb”, ale nie pasuje do sekwencji docelowej „abab”.

- „(ab)+” nie pasuje do sekwencji docelowej „abb”, ale pasuje do sekwencji docelowej „abab”.

- „((a+)(b+))(c+)” pasuje do sekwencji docelowej „aabbbc” i kojarzy grupę przechwytywania 1 z podsekwencją „aabbb”, grupę przechwytywania 2 z podsekwencją „aa”, grupę przechwytywania 3 z „bbb” i grupę przechwytywania 4 z podsekwencją „c”.

### <a name="character-class"></a>Klasa znaków

Klasa znaków w wyrażeniu w nawiasie kwadratowym dodaje wszystkie znaki w nazwanej klasie do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć klasę znaków, należy użyć „[:”, po którym następuje nazwa klasy, a na koniec „:]”. Wewnętrznie nazwy klas znaków są rozpoznawane przez wywołanie `id = traits.lookup_classname`. Znak `ch` należy do takiej klasy, jeśli `traits.isctype(ch, id)` zwraca wartość true. Szablon domyślny `regex_traits` obsługuje nazwy klas w poniższej tabeli.

|Nazwa klasy|Opis|
|----------------|-----------------|
|„alnum”|małe litery, wielkie litery i cyfry|
|„alpha”|małe litery i wielkie litery|
|„blank”|spacja lub tabulator|
|„cntrl”|znaki *ucieczki formatu pliku*|
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

Symbol sortowania w wyrażeniu w nawiasie kwadratowym dodaje *element sortowania* do zestawu, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć symbol sortowania, użyj "[." a następnie element sortowania, po którym następuje ".]".

### <a name="control-escape-sequence"></a>Kontrolna sekwencja unikowa

Kontrolna sekwencja unikowa to ukośnik odwrotny, po którym następuje litera „c”, po której następuje jedna z liter od 'a' do 'z' lub od 'A' do 'Z'. Pasuje do znaku kontrolnego ASCII, który jest nazwany przez tę literę. Na przykład "\ci" pasuje do sekwencji docelowej "\x09", ponieważ \<> Ctrl-i ma wartość 0x09.

### <a name="dsw-character-escape"></a>Sekwencja unikowa DSW.

Sekwencja unikowa dsw to skrócona nazwa klasy znaków, jak pokazano w poniższej tabeli.

|Sekwencja unikowa|Równoważna nazwana klasa|Domyślna nazwana klasa|
|---------------------|----------------------------|-------------------------|
|„\d”|„[[:d:]]”|„[[:digit:]]”|
|„\D”|„[^[:d:]]”|„[^[:digit:]]”|
|„\s”|„[[:s:]]”|„[[:space:]]”|
|„\S”|„[^[:s:]]”|„[^[:space:]]”|
|„\w”|„[[:w:]]”|"[a-zA-Z0-9_]"\*|
|„\W”|„[^[:w:]]”|"[^a-zA-Z0-9_]"\*|

\*Zestaw znaków ASCII

### <a name="equivalence-class"></a>Klasa równoważności

Klasa równoważności w wyrażeniu w nawiasie kwadratowym dodaje wszystkie znaki i *elementy sortowania* , które są równoważne elementowi sortowania w definicji klasy równoważności, do zestawu, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć klasę równoważności, należy użyć „[=”, po którym następuje element sortujący, a na koniec „=]”. Wewnętrznie, dwa elementy `elt1` sortowania i `elt2` są równoważne, jeśli `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.

### <a name="file-format-escape"></a>Sekwencja unikowa formatu pliku

Format pliku ucieczki składa się ze zwykłych sekwencji unikowych języka C,\\"\\", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Mają one zwykłe znaczenie, to znaczy ukośnik odwrotny, alert, Backspace, podawanie formularza, nowy wiersz, znak powrotu karetki, tabulator poziomy i tabulator pionowy. W `ECMAScript`, "\a" i "\b" są niedozwolone. ("\\\\" jest dozwolone, ale jest to sekwencja ucieczki, a nie format pliku ucieczki).

### <a name="hexadecimal-escape-sequence"></a>Szesnastkowa sekwencja unikowa

Szesnastkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje litera 'x' i dwie cyfry szesnastkowe (0-9a-fA-F). Pasuje do znaku w sekwencji docelowej, która ma wartość określoną przez te dwie cyfry. Na przykład, „\x41” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="identity-escape"></a>Ucieczka tożsamości

Ucieczka tożsamości to odwrotny ukośnik, po którym następuje pojedynczy znak. Pasuje do tego znaku. Jest wymagana, gdy znak ma specjalne znaczenie; dzięki ucieczce tożsamości to znaczenie jest usuwane. Przykład:

- "a\*" pasuje do sekwencji docelowej "aaa", ale nie pasuje do sekwencji docelowej "a\*".

- "a\\\*" nie pasuje do sekwencji docelowej "aaa", ale pasuje do sekwencji docelowej "a\*".

Zestaw znaków, które są dozwolone w ucieczce tożsamości, zależy od gramatyki wyrażeń regularnych, jak pokazano w poniższej tabeli.

|Gramatyka|Dozwolone znaki ucieczki tożsamości|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended`Plus {"" ","/"}|
|`ECMAScript`|Wszystkie znaki z wyjątkiem tych, które mogą być częścią identyfikatora. Zwykle dotyczy to liter, cyfr, "$", "\_" i sekwencji unikowych Unicode. Aby uzyskać więcej informacji, zobacz temat specyfikacji języka ECMAScript.|

### <a name="individual-character"></a>Pojedynczy znak

Pojedynczy znak w wyrażeniu w nawiasie kwadratowym dodaje ten znak do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Gdziekolwiek w wyrażeniu w nawiasie kwadratowym, z wyjątkiem początku, '^' reprezentuje sam siebie.

Przykłady:

- „[abc]” pasuje do sekwencji docelowych „a”, „b” i „c”, ale nie do sekwencji „d”.

- „[^abc]” pasuje do sekwencji docelowej „d”, ale nie do sekwencji docelowych „a”, „b” lub „c”.

- „[a^bc]” pasuje do sekwencji docelowych „a”, „b”, „c” i „^” , ale nie do sekwencji docelowej „d”.

We wszystkich gramatykach wyrażeń regularnych, `ECMAScript`z wyjątkiem, jeśli '] ' jest pierwszym znakiem, który następuje po otwarciu ' [' lub jest pierwszym znakiem, który następuje po początkowym ' ^ ', reprezentuje sam siebie.

Przykłady:

- „[]a” jest nieprawidłowe, ponieważ nie ma ']', aby zakończyć wyrażenie w nawiasie kwadratowym.

- „[]abc]” pasuje do sekwencji docelowych „a”, „b”, „c” i „]”, ale nie do sekwencji docelowej „d”.

- „[^]abc]” pasuje do sekwencji docelowej „d”, ale nie do sekwencji docelowych „a”, „b”, „c” lub „]”.

W `ECMAScript`, użyj znaku\\"]", aby reprezentować znak "]" w wyrażeniu w nawiasie kwadratowym.

Przykłady:

- „[]a” pasuje do sekwencji docelowej „a”, ponieważ wyrażenie w nawiasie kwadratowym jest puste.

- "[\\] ABC]" pasuje do sekwencji docelowych "a", "b", "c" i "]", ale nie do sekwencji docelowej "d".

### <a name="negative-assert"></a>Asercja negatywna

Asercja negatywna pasuje do wszystkiego oprócz swojej zawartości. Nie używa żadnych znaków w sekwencji docelowej. Na przykład "(! AA) (a\*)" pasuje do sekwencji docelowej "a" i kojarzy grupę przechwytywania 1 z podsekwencją "a". Nie pasuje do sekwencji docelowej „aa” ani do sekwencji docelowej „aaa”.

### <a name="negative-word-boundary-assert"></a>Asercja negatywna granicy słowa

Ujemne potwierdzenie granicy słowa jest zgodne, jeśli bieżąca pozycja w ciągu docelowym nie jest natychmiast po *granicy słowa*.

### <a name="non-capture-group"></a>Grupa nieprzechwytująca

Grupa nieprzechwytująca oznacza swoją zawartość jako pojedynczą jednostkę w gramatyce wyrażeń regularnych, ale nie nadaje etykiety tekstowi docelowemu. Na przykład "(a) (?: b)\*(c)" pasuje do tekstu docelowego "abbc" i kojarzy grupę przechwytywania 1 z podsekwencją "a" i grupą przechwytywania 2 z podsekwencją "c".

### <a name="non-greedy-repetition"></a>Powtórzenie niezachłanne

Powtórzenie niezachłanne używa najkrótszej podsekwencji sekwencji docelowej, która pasuje do wzorca. Powtórzenie zachłanne używa najdłuższej. Na przykład "(a +) (a\*b)" pasuje do sekwencji docelowej "aaab". Gdy używa się powtórzenia niezachłannego, kojarzy ono grupę przechwytywania 1 z podsekwencją „a” na początku sekwencji docelowej, a grupę przechwytywania 2 z podsekwencją „aab” na końcu sekwencji docelowej. Gdy używa się dopasowania zachłannego, kojarzy ono grupę przechwytywania 1 z podsekwencją „aaa”, a grupę przechwytywania 2 z podsekwencją „b”.

### <a name="octal-escape-sequence"></a>Ósemkowa sekwencja unikowa

Ósemkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje jedna, dwie lub trzy cyfry ósemkowe (0-7). Pasuje do znaku w sekwencji docelowej, który ma wartość określoną przez te cyfry. Jeśli wszystkie cyfry to '0', sekwencja jest nieprawidłowa. Na przykład, „\101” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="ordinary-character"></a>Zwykły znak

Zwykły znak to dowolny prawidłowy znak, który nie ma specjalnego znaczenia w bieżącej gramatyce.

W `ECMAScript`programie następujące znaki mają specjalne znaczenie:

- ^  $  \  .  \*+  ?  (  )  \[  ]  {  }  &#124;

W `basic` i`grep`, następujące znaki mają specjalne znaczenie:

- .   \[   \

Ponadto w `basic` i `grep`, następujące znaki mają specjalne znaczenie, gdy są używane w określonym kontekście:

- "\*" ma specjalne znaczenie we wszystkich przypadkach, z wyjątkiem sytuacji, gdy jest to pierwszy znak w wyrażeniu regularnym lub pierwszy znak, który następuje po początkowym znaku "^" w wyrażeniu regularnym, lub gdy jest to pierwszy znak grupy przechwytywania lub pierwszy znak, który następuje po początkowym ' ^ ' w grupie przechwytywania.

- '^' ma specjalne znaczenie, gdy jest to pierwszy znak wyrażenia regularnego.

- '$' ma specjalne znaczenie, gdy jest to ostatni znak wyrażenia regularnego.

W `extended`, `egrep`, i`awk`, następujące znaki mają specjalne znaczenie:

- .   \[\   (   \*   +   ?   {   &#124;

Ponadto w `extended`, `egrep`, i `awk`, następujące znaki mają specjalne znaczenie, gdy są używane w określonym kontekście.

- ')' ma specjalne znaczenie, gdy pasuje do poprzedzającego '('.

- '^' ma specjalne znaczenie, gdy jest to pierwszy znak wyrażenia regularnego.

- '$' ma specjalne znaczenie, gdy jest to ostatni znak wyrażenia regularnego.

Zwykły znak pasuje do takiego samego znaku w sekwencji docelowej. Domyślnie oznacza to, że dopasowanie się powiedzie, jeśli dwa znaki są reprezentowane przez tę samą wartość. W przypadku dopasowania bez uwzględniania wielkości liter, dwa `ch0` znaki `ch1` i są `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`zgodne, jeśli. W przypadku dopasowania z uwzględnieniem ustawień regionalnych, `ch0` dwa `ch1` znaki i `traits.translate(ch0) == traits.translate(ch1)`są zgodne, jeśli.

### <a name="positive-assert"></a>Asercja pozytywna

Asercja pozytywna pasuje do swojej zawartości, ale nie używa żadnych znaków w sekwencji docelowej.

Przykłady:

- "(= AA) (a\*)" pasuje do sekwencji docelowej "aaaa" i kojarzy grupę przechwytywania 1 z podsekwencją "aaaa".

- "(AA) (a\*)" pasuje do sekwencji docelowej "aaaa" i kojarzy grupę przechwytywania 1 z podsekwencją "AA" na początku sekwencji docelowej i grupą przechwytywania 2 z podsekwencją "AA" na końcu sekwencji docelowej.

- "(= AA) (a)&#124;(a)" pasuje do sekwencji docelowej "a" i kojarzy grupę przechwytywania 1 z pustą sekwencją (ponieważ pozytywne potwierdzenie nie powiodło się) i grupą przechwytywania 2 z podsekwencją "a". Pasuje też do sekwencji docelowej „aa” i kojarzy grupę przechwytywania 1 z podsekwencją „aa”, a grupę przechwytywania 2 z pustą sekwencją.

### <a name="unicode-escape-sequence"></a>Sekwencja unikowa unicode

Sekwencja unikowa unicode to ukośnik odwrotny, po którym następuje litera 'u' i cztery cyfry szesnastkowe (0-9a-fA-F). Pasuje do znaku w sekwencji docelowej, który ma wartość określoną przez te cztery cyfry. Na przykład, „\u0041” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="wildcard-character"></a>Symbol wieloznaczny

Symbol wieloznaczny pasuje do dowolnego znaku w wyrażeniu docelowym z wyjątkiem nowego wiersza.

### <a name="word-boundary"></a>Granica słowa

Granica słowa występuje w następujących sytuacjach:

- Bieżący znak jest na początku sekwencji docelowej i jest jednym ze znaków słowa`A-Za-z0-9_.`

- Bieżąca pozycja znaku jest poza końcem sekwencji docelowej, a ostatni znak w sekwencji docelowej jest jednym ze znaków słowa.

- Bieżący znak jest jednym ze znaków słowa, a znak poprzedzający nie jest.

- Bieżący znak nie jest jednym ze znaków słowa, a znak poprzedzający jest.

### <a name="word-boundary-assert"></a>Asercja granicy słowa

Potwierdzenie granicy słowa jest zgodne, gdy bieżąca pozycja w ciągu docelowym jest natychmiast po *granicy słowa*.

## <a name="matchingandsearching"></a>Dopasowywanie i wyszukiwanie

Aby wyrażenie regularne pasowało do sekwencji docelowej, całe wyrażenie regularne musi pasować do całej sekwencji docelowej. Na przykład, wyrażenie regularne „bcd” pasuje do sekwencji docelowej „bcd”, ale nie pasuje do sekwencji docelowej „abcd” ani sekwencji docelowej „bcde”.

Aby wyszukiwanie wyrażenia regularnego zostało wykonane pomyślnie, gdzieś w sekwencji docelowej musi istnieć podsekwencja, która odpowiada wyrażeniu regularnemu. Wyszukiwanie znajduje zazwyczaj pasującą podsekwencję najbliżej lewej strony.

Przykłady:

- Wyszukanie wyrażenia regularnego „bcd” w sekwencji docelowej „bcd” zakończy się pomyślnie i dopasuje całą sekwencję. To samo wyszukiwanie w sekwencji docelowej „abcd” również zakończy się pomyślnie i dopasuje ostatnie trzy znaki. To samo wyszukiwanie w sekwencji docelowej „bcde” również zakończy się pomyślnie i dopasuje pierwsze trzy znaki.

- Wyszukanie wyrażenia regularnego „bcd” w sekwencji docelowej „bcdbcd” zakończy się pomyślnie i dopasuje pierwsze trzy znaki.

Jeśli istnieje więcej niż jedna podsekwencja, która pasuje w którymś miejscu w sekwencji docelowej, istnieją dwa sposoby wyboru pasującego wzorca. *Pierwsze dopasowanie* wybiera podsekwencję, która została znaleziona jako pierwsza podczas dopasowywania wyrażenia regularnego. *Najdłuższe dopasowanie* wybiera najdłuższą podsekwencję z tych, które pasują do tej lokalizacji. Jeśli istnieje więcej niż jedna podsekwencja, która ma maksymalną długość, najdłuższe wystąpienie wybiera tę, która została znaleziona jako pierwsza. Na przykład podczas korzystania z pierwszego dopasowania Wyszukiwanie wyrażenia regularnego "b&#124;BC" w sekwencji docelowej "abcd" dopasowuje podsekwencję "b", ponieważ lewa wartość wyrażenia jest zgodna z podsekwencją; w związku z tym pierwsze dopasowanie nie powoduje wypróbowania prawego warunku zmiany. Gdy jest używane najdłuższe wystąpienie, to samo wyszukiwanie pasuje do „bc” ponieważ „bc” jest dłuższe niż „b”.

Częściowe wystąpienie powiedzie się, jeśli dopasowanie osiąga koniec sekwencji docelowej bez niepowodzenia, nawet jeśli nie osiągnęło końca wyrażenia regularnego. W związku z tym, po pomyślnym częściowym wystąpieniu, dodanie znaków do sekwencji docelowej mogłoby spowodować niepowodzenie późniejszego częściowego wystąpienia. Jednakże, po niepowodzeniu częściowego wystąpienia, dodanie znaków do sekwencji docelowej nie może spowodować powodzenia późniejszego częściowego wystąpienia. Na przykład, przy częściowym wystąpieniu, „ab” pasuje do sekwencji docelowej „a”, ale nie „ac”.

## <a name="formatflags"></a>Flagi formatowania

|Reguły formatu ECMAScript|Reguły formatu sed|Tekst zastępczy|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Sekwencja znaków zgodna z całym wyrażeniem regularnym (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"\\&"|"&"|
|"$\`" (znak dolara, po którym następuje cudzysłów tylny)||Sekwencja znaków poprzedzająca podsekwencję, która jest zgodna z wyrażeniem regularnym (`[match.prefix().first, match.prefix().second)`)|
|„$'” (znak dolara, po którym następuje cudzysłów pojedynczy)||Sekwencja znaków, która następuje po podsekwencji, która pasuje do wyrażenia regularnego (`[match.suffix().first, match.suffix().second)`)|
|„$n”|„\n”|Sekwencja znaków zgodna z grupą przechwytywania na pozycji `n`, gdzie `n` jest liczbą z zakresu od 0 do 9 (`[match[n].first, match[n].second)`)|
||"\\\n"|„\n”|
|„$nn”||Sekwencja znaków zgodna z grupą przechwytywania na pozycji `nn`, gdzie `nn` jest liczbą z zakresu od 10 do 99 (`[match[nn].first, match[nn].second)`)|

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)
