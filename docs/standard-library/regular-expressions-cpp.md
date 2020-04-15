---
title: Wyrażenia regularne (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
ms.openlocfilehash: a6ff0fafce9f4b3e029be053d27ca68d096ec108
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368524"
---
# <a name="regular-expressions-c"></a>Wyrażenia regularne (C++)

Standardowa biblioteka języka C++ obsługuje wiele gramatyki wyrażeń regularnych. W tym temacie omówiono odmiany gramatyki dostępne podczas używania wyrażeń regularnych.

## <a name="regular-expression-grammar"></a><a name="regexgrammar"></a>Gramatyka wyrażeń regularnych

Gramatyki wyrażenia regularnego do użycia jest określony `std::regex_constants::syntax_option_type` przez użycie jednej z wartości wyliczenia. Te gramatyki wyrażeń regularnych są zdefiniowane w std::regex_constants:

- `ECMAScript`: Jest to najbliższe gramatyki używanej przez język JavaScript i .NET.
- `basic`: Podstawowe wyrażenia regularne POSIX lub BRE.
- `extended`: POSIX rozszerzone wyrażenia regularne lub ERE.
- `awk`: Jest `extended`to , ale ma dodatkowe wyjścia dla znaków niedrukowych.
- `grep`: Jest `basic`to , ale umożliwia również znaki nowej linii ('\n') oddzielanie naprzemnień.
- `egrep`: Jest `extended`to , ale pozwala również znaki nowego linii do oddzielenia naprzemnań.

Domyślnie, jeśli nie określono `ECMAScript` gramatyki, zakłada się. Można określić tylko jedną gramatykę.

Oprócz gramatyki można zastosować kilka flag:

- `icase`: Ignorowanie przypadku podczas dopasowywania.
- `nosubs`: Ignorowanie oznaczonych dopasowań (czyli wyrażeń w nawiasach); nie są przechowywane żadne zastępstwa.
- `optimize`: Spraw, aby dopasowanie było szybsze, kosztem większego czasu budowy.
- `collate`: Użyj sekwencji sortowania zależnych od ustawień regionalnych (na przykład zakresów formularza "[a-z]").

Zero lub więcej flag może być łączony z gramatyki, aby określić zachowanie aparatu wyrażeń regularnych. Jeśli określono tylko `ECMAScript` flagi, przyjmuje się jako gramatyki.

### <a name="element"></a>Element

Element może być jednym z następujących:

- *Zwykły znak,* który pasuje do tego samego znaku w sekwencji docelowej.

- *Symbol wieloznaczny* '.', który pasuje do dowolnego znaku w sekwencji docelowej z wyjątkiem nowej linii.

- *Wyrażenie nawiasu* formularza`expr`"[ ]", który pasuje do znaku lub elementu sortowania w sekwencji `expr`docelowej, który jest`expr`również w zestawie zdefiniowanym przez wyrażenie , lub formularza "[^ ]", `expr`który pasuje do znaku lub elementu sortowania w sekwencji docelowej, która nie znajduje się w zestawie zdefiniowanym przez wyrażenie .

   Wyrażenie `expr` może zawierać dowolną kombinację następujących elementów:

  - Pojedynczy znak. Dodaje ten znak do `expr`zestawu zdefiniowanego przez .

  - *Zakres znaków* formularza "`ch1`-`ch2`". Dodaje znaki, które są reprezentowane przez`ch1`wartości `ch2`w zamkniętym zakresie `expr`[ , ] do zestawu zdefiniowanego przez .

  - *Klasa znaków* formularza "[:`name`:]". Dodaje znaki w klasie o nazwie `expr`do zestawu zdefiniowanego przez .

  - *Klasa równoważności* formularza "[=`elt`=]". Dodaje elementy sortujące, które `elt` są równoważne `expr`zestawowi zdefiniowanemu przez program .

  - *Symbol sortowania* formularza "[.`elt`.]". Dodaje element `elt` sortowania do zestawu `expr`zdefiniowanego przez .

- *Kotwica*. Kotwica '^' pasuje do początku sekwencji docelowej; kotwica '$' pasuje do końca sekwencji docelowej.

*Grupa przechwytywania* formularza "( *podwyrażenie)",* \\lub " ( *podwyrażenie)"* \\w `basic` i `grep`, która pasuje do sekwencji znaków w sekwencji docelowej, która jest dopasowywać wzorzec między ogranicznikami.

- *Ucieczka tożsamości* formularza\\`k`" ", który `k` pasuje do znaku w sekwencji docelowej.

Przykłady:

- „a” pasuje do sekwencji docelowej „a”, ale nie pasuje do sekwencji docelowych „B”, „b” lub „c”.

- „.” pasuje do wszystkich sekwencji docelowych „a”, „B”, „b” i „c”.

- „[b-z]” pasuje do sekwencji docelowych „b” i „c”, ale nie pasuje do sekwencji docelowych „a” lub „B”.

- „[:lower:]” pasuje do sekwencji docelowych „a”, „b” i „c”, ale nie pasuje do sekwencji docelowej „B”.

- „(a)” pasuje do sekwencji docelowej „a” i kojarzy grupę przechwytywania 1 z podsekwencją „a”, ale nie pasuje do sekwencji docelowych „B”, „b” lub „c”.

W `ECMAScript` `basic`programie `grep`, i element może być również *tylnym odniesieniem* formularza "\\`dd`", gdzie `dd` reprezentuje wartość dziesiętną N, która pasuje do sekwencji docelowej sekwencji docelowej, która jest taka sama jak sekwencja znaków dopasowana przez *grupę przechwytywania*Nth . Na przykład, „(a)\1” odpowiada sekwencji docelowej „aa”, ponieważ pierwsza (i tylko) grupa przechwytywania pasuje do początkowej sekwencji „a”, a następnie \1 pasuje do ostatniej sekwencji „a”.

W `ECMAScript`, element może być również jedną z następujących rzeczy:

- *Grupa nieprzejmująca* formularza "(?: *podwyrażenie* )". Pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami.

- Ograniczony *format pliku ucieczki* formularza "\f", "\n", "\r", "\t" lub "\v". Pasują one, odpowiednio, do wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulatora poziomego i tabulatora pionowego w sekwencji docelowej.

- *Pozytywna potwierdzenia* formularza "(= *podwyrażenie* )". Pasuje do sekwencji znaków w sekwencji docelowej, do której pasuje wzorzec między ogranicznikami, ale nie zmienia pozycji dopasowania w sekwencji docelowej.

- *Negatywne twierdzenie* formularza "(! *podwyrażenie* )". Pasuje do dowolnej sekwencji znaków w sekwencji docelowej, do której nie pasuje wzorzec między ogranicznikami, i nie zmienia pozycji dopasowania w sekwencji docelowej.

- *Szesnastkowa sekwencja ucieczki* `hh`formularza "\x". Dopasowuje znak w sekwencji docelowej, który jest reprezentowany `hh`przez dwie cyfry szesnastkowe .

- *Sekwencja unicode uniku* postaci`hhhh`"\u". Dopasowuje znak w sekwencji docelowej, który jest reprezentowany `hhhh`przez cztery cyfry szesnastkowe .

- *Sekwencja unikowa formantu* formularza "\c".`k` Dopasowuje znak kontrolny nazwany `k`przez znak .

- Potwierdzenie *granicy słowa* formularza "\b". Dopasowuje się, gdy bieżąca pozycja w sekwencji docelowej znajduje się bezpośrednio po *granicy słowa*.

- *Ujemna miara granicy słowa* formularza "\B". Pasuje, gdy bieżąca pozycja w sekwencji docelowej nie jest bezpośrednio po *granicy słowa*.

- *Ucieczka znaku dsw* formularza "\d", "\D", "\s", "\S", "\w", "\W". Zawiera skróconą nazwę klasy znaków.

Przykłady:

- „(?:a)” pasuje do sekwencji docelowej „a”, ale „(?:a)\1” jest nieprawidłowe, ponieważ nie istnieje żadna grupa przechwytywania 1.

- "(=a)a" pasuje do docelowej sekwencji "a". Asercja pozytywna pasuje do początkowej sekwencji „a” w sekwencji docelowej, a końcowe „a” w wyrażeniu regularnym pasuje do sekwencji początkowej „a” w sekwencji docelowej.

- "(!a)a" nie pasuje do docelowej sekwencji "a".

- "a\b". dopasowuje sekwencję docelową "a~", ale nie pasuje do docelowej sekwencji "ab".

- "a\B". dopasowuje sekwencję docelową "ab", ale nie pasuje do sekwencji docelowej "a~".

W `awk`, element może być również jedną z następujących rzeczy:

- Ucieczka *formatu pliku* \\\\formularza " ", "\a", "\b", "\f", "\n", "\r", "\t" lub "\v". Pasują one, odpowiednio, do odwrotnego ukośnika, alertu, backspace, wciągnięcia kartki, nowego wiersza, powrotu karetki, tabulatora poziomego i tabulatora pionowego w sekwencji docelowej.

- *Ósemkowa sekwencja ucieczki* formularza "\\`ooo`". Dopasowuje znak w sekwencji docelowej, którego reprezentacja jest wartością reprezentowaną przez jedną, dwie lub trzy cyfry ósemki `ooo`.

### <a name="repetition"></a>Powtórzenie

Dowolne elementy inne niż *potwierdzenia dodatnie,* *potwierdzenia ujemnego*lub *zakotwiczenia* mogą następować liczba powtórzeń. Najbardziej ogólny rodzaj liczby powtórzeń ma`min`formę`max`"{\\,`min``max`\\}" `basic` lub `grep`" { , }" in i . Element, po którym następuje ta forma liczby `min` powtórzeń pasuje co `max` najmniej kolejnych wystąpień i nie więcej niż kolejne wystąpienia sekwencji, która pasuje do elementu. Na przykład "a"{2,3}pasuje do sekwencji docelowej "aa" i sekwencji docelowej "aaa", ale nie do sekwencji docelowej "a" lub sekwencji docelowej "aaaa".

Licznik powtórzeń może mieć również jedną z następujących postaci:

- "{`min`}"\\lub`min`\\" `basic` { `grep`}" w i . Odpowiednik "{`min``min`, }".

- "{`min`,}"\\lub`min`\\" { `basic` `grep`, }" w i . Odpowiednik "{`min`,unbounded}".

- "\*". Równoważne postaci „{0,nieograniczone}”.

Przykłady:

- "a"{2}pasuje do docelowej sekwencji "aa", ale nie do sekwencji docelowej "a" lub sekwencji docelowej "aaa".

- "a{2,}" pasuje do docelowej sekwencji "aa", sekwencji docelowej "aaa" i tak dalej, ale nie pasuje do docelowej sekwencji "a".

- "a\*" pasuje do sekwencji docelowej "", sekwencji docelowej "a", sekwencji docelowej "aa" i tak dalej.

Dla wszystkich gramatyki z wyjątkiem `basic` i `grep`, liczba powtórzeń może również przybierać jedną z następujących form:

- "?". Odpowiednik "{0,1}"."

- "+". Odpowiednik "{1,unbounded}".

Przykłady:

- "a?" dopasowuje sekwencję docelową "" i sekwencję docelową "a", ale nie sekwencję docelową "aa".

- „a+” pasuje do sekwencji docelowej „a”, sekwencji docelowej „aa” itd., ale nie do sekwencji docelowej „”.

W `ECMAScript`, wszystkie formy liczby powtórzeń może nastąpić znak "?", który oznacza *niechciwe powtórzenia*.

### <a name="concatenation"></a>Łączenie

Elementy wyrażenia regularnego, z *liczeniem powtórzeń*lub bez, mogą być łączone w celu utworzenia dłuższych wyrażeń regularnych. Wyrażenie wynikowe pasuje do sekwencji docelowej będącej połączeniem sekwencji, do których pasują poszczególne elementy. Na przykład "a{2,3}b" pasuje do sekwencji docelowej "aab" i sekwencji docelowej "aaab", ale nie pasuje do sekwencji docelowej "ab" lub sekwencji docelowej "aaaab".

### <a name="alternation"></a>Alternatywa

We wszystkich gramatykach wyrażeń regularnych z wyjątkiem `basic` i `grep`, po połączonym wyrażeniu regularnym może następować znak "&#124;" i inne połączone wyrażenie regularne. W ten sposób można łączyć dowolną liczbę połączonych wyrażeń regularnych. Wyrażenie wynikowe pasuje do dowolnej sekwencji docelowej, do której pasuje jedno lub więcej z połączonych wyrażeń regularnych.

Gdy więcej niż jedno zesłane wyrażenia regularne `ECMAScript` odpowiada sekwencji docelowej, wybiera pierwsze zesłane wyrażenia regularne, które pasują do sekwencji jako dopasowania *(pierwsze dopasowanie);* inne gramatyki wyrażeń regularnych wybrać ten, który osiąga *najdłuższe dopasowanie*. Na przykład "ab&#124;cd" pasuje do docelowej sekwencji "ab" i docelowej sekwencji "cd", ale nie pasuje do docelowej sekwencji "abd" lub sekwencji docelowej "acd".

W `grep` `egrep`i znak nowego bohatera ('\n') może służyć do oddzielania naprzemnień.

### <a name="subexpression"></a>Wyrażenie cząstkowe

W `basic` `grep`i , subexpression jest łączenia. W innych gramatykach wyrażeń regularnych wyrażenie cząstkowe jest alternatywą.

## <a name="grammar-summary"></a><a name="grammarsummary"></a>Podsumowanie gramatyki

W następującej tabeli podsumowano funkcje, które są dostępne w różnych gramatykach wyrażeń regularnych:

|Element|Podstawowe|rozszerzone|Ecmascript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|naprzemiennie za pomocą "&#124;"||+|+||+|+|
|alternatywa przy użyciu '\n'||||+|+||
|kotwica|+|+|+|+|+|+|
|dopasowanie wsteczne|+||+|+|||
|wyrażenie w nawiasie kwadratowym|+|+|+|+|+|+|
|grupa przechwytywania przy użyciu „()”||+|+||+|+|
|grupa przechwytywania\\\\za pomocą " ( )"|+|||+|||
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
|powtarzanie za{}pomocą " "||+|+||+|+|
|powtarzanie za\\pomocą\\" { }"|+|||+|||
|powtarzanie za\*pomocą ' '|+|+|+|+|+|+|
|powtórzenie przy użyciu '?' i '+'||+|+||+|+|
|sekwencja unikowa unicode|||+||||
|symbol wieloznaczny|+|+|+|+|+|+|
|asercja granicy słowa|||+||||

## <a name="semantic-details"></a><a name="semanticdetails"></a>Szczegóły semantyczne

### <a name="anchor"></a>Kotwica

Kotwica pasuje do pozycji w ciągu docelowym, a nie do znaku. Kotwica '^' pasuje do początku ciągu docelowego, a kotwica '$' pasuje do końca ciągu docelowego.

### <a name="back-reference"></a>Dopasowanie wsteczne

Odwołanie wstecz jest ukośnikiem odwrotnym, po którym następuje wartość dziesiętna N. Pasuje do zawartości grupy *przechwytywania*Nth . Wartość N nie może być większa niż liczba grup przechwytywania, które poprzedzają dopasowanie wsteczne. W `basic` `grep`i , wartość N jest określana przez cyfrę dziesiętną, która następuje ukośnik odwrotny. W `ECMAScript`, wartość N jest określana przez wszystkie cyfry dziesiętne, które natychmiast następują po ukośniku odwrotnym. W związku `basic` z `grep`tym w i , wartość N nigdy nie jest większa niż 9, nawet jeśli wyrażenie regularne ma więcej niż dziewięć grup przechwytywania. W `ECMAScript`, wartość N jest nieograniczona.

Przykłady:

- „((a+)(b+))(c+)\3” pasuje do sekwencji docelowej „aabbbcbbb”. Dopasowanie wsteczne „\3” pasuje do tekstu z trzeciej grupy przechwytywania, to znaczy „(b+)”. Nie pasuje do sekwencji docelowej „aabbbcbb”.

- „(a)\2” jest nieprawidłowe.

- "(b(((((((((a))))))))))))\10" ma `basic` różne `ECMAScript`znaczenia w . W `basic` tylnym odwołaniu znajduje się "\1". Dopasowanie wsteczne pasuje do zawartości pierwszej grupy przechwytywania (czyli tej, która zaczyna się od „(b” i kończy się ostatnim „)” i znajduje się przed dopasowaniem wstecznym), a końcowe '0' pasuje do zwykłego znaku '0'. W `ECMAScript`obszarze , odwołanie tylne to "\10". Pasuje do dziesiątej grupy przechwytywania, to znaczy tej najbardziej w środku.

### <a name="bracket-expression"></a>Wyrażenie w nawiasie kwadratowym

Wyrażenie nawiasu definiuje zestaw znaków i *elementów sortowania*. Kiedy wyrażenie w nawiasie kwadratowym zaczyna się od znaku '^', dopasowanie zakończy się pomyślnie, jeśli do bieżącego znaku w sekwencji docelowej nie pasuje żaden element w zestawie. W przeciwnym razie dopasowanie się powiedzie, jeśli do bieżącego znaku w sekwencji docelowej pasuje dowolny z elementów w zestawie.

Zestaw znaków można zdefiniować, wymieniając dowolną kombinację *pojedynczych znaków,* *zakresów znaków,* *klas znaków,* *klas równoważności*i *symboli sortujących.*

### <a name="capture-group"></a>Grupa przechwytywania

Grupa przechwytywania oznacza swoją zawartość jako pojedynczą jednostkę w gramatyce wyrażeń regularnych i nadaje etykietę tekstowi docelowemu, który pasuje do jej zawartości. Etykieta skojarzona z każdą grupą przechwytywania to numer, który zależy od policzenia nawiasów otwierających, oznaczających grupy przechwytywania, aż do nawiasu otwierającego włącznie, który oznacza bieżącą grupę przechwytywania. W tej implementacji maksymalna liczba grup przechwytywania to 31.

Przykłady:

- „ab+” pasuje do sekwencji docelowej „abb”, ale nie pasuje do sekwencji docelowej „abab”.

- „(ab)+” nie pasuje do sekwencji docelowej „abb”, ale pasuje do sekwencji docelowej „abab”.

- „((a+)(b+))(c+)” pasuje do sekwencji docelowej „aabbbc” i kojarzy grupę przechwytywania 1 z podsekwencją „aabbb”, grupę przechwytywania 2 z podsekwencją „aa”, grupę przechwytywania 3 z „bbb” i grupę przechwytywania 4 z podsekwencją „c”.

### <a name="character-class"></a>Klasa znaków

Klasa znaków w wyrażeniu w nawiasie kwadratowym dodaje wszystkie znaki w nazwanej klasie do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Aby utworzyć klasę znaków, należy użyć „[:”, po którym następuje nazwa klasy, a na koniec „:]”. Wewnętrznie nazwy klas znaków są rozpoznawane przez wywołanie `id = traits.lookup_classname`. Znak `ch` należy do takiej klasy, jeśli `traits.isctype(ch, id)` zwraca true. Szablon `regex_traits` domyślny obsługuje nazwy klas w poniższej tabeli.

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

Symbol sortowania w wyrażeniu nawiasu dodaje *element sortowania* do zestawu zdefiniowanego przez wyrażenie nawiasu. Aby utworzyć symbol sortowania, użyj "[." następnie element sortujący, po którym następuje ".]".

### <a name="control-escape-sequence"></a>Kontrolna sekwencja unikowa

Kontrolna sekwencja unikowa to ukośnik odwrotny, po którym następuje litera „c”, po której następuje jedna z liter od 'a' do 'z' lub od 'A' do 'Z'. Pasuje do znaku kontrolnego ASCII, który jest nazwany przez tę literę. Na przykład "\ci" pasuje do sekwencji docelowej \<"\x09", ponieważ ctrl-i> ma wartość 0x09.

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

Klasa równoważności w wyrażeniu nawiasu dodaje wszystkie znaki i *elementy sortujące,* które są równoważne elementowi sortowania w definicji klasy równoważności do zestawu zdefiniowanego przez wyrażenie nawiasu. Aby utworzyć klasę równoważności, należy użyć „[=”, po którym następuje element sortujący, a na koniec „=]”. Wewnętrznie dwa elementy `elt1` sortujące `elt2` i `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`są równoważne, jeśli .

### <a name="file-format-escape"></a>Sekwencja unikowa formatu pliku

Ucieczka formatu pliku składa się ze zwykłych\\\\sekwencji ulatniania znaków języka C, "", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Mają one zwykłe znaczenie, czyli ukośnik odwrotny, alert, backspace, kanał informacyjny formularza, nowy linia, powrót karetki, karta pozioma i pionowa. W `ECMAScript`, "\a" i "\b" nie są dozwolone. ("\\\\" jest dozwolone, ale jest to ucieczka tożsamości, a nie ucieczka formatu pliku).

### <a name="hexadecimal-escape-sequence"></a>Szesnastkowa sekwencja unikowa

Szesnastkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje litera 'x' i dwie cyfry szesnastkowe (0-9a-fA-F). Pasuje do znaku w sekwencji docelowej, która ma wartość określoną przez te dwie cyfry. Na przykład, „\x41” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="identity-escape"></a>Ucieczka tożsamości

Ucieczka tożsamości to odwrotny ukośnik, po którym następuje pojedynczy znak. Pasuje do tego znaku. Jest wymagana, gdy znak ma specjalne znaczenie; dzięki ucieczce tożsamości to znaczenie jest usuwane. Przykład:

- "a\*" pasuje do docelowej sekwencji "aaa",\*ale nie pasuje do sekwencji docelowej "a".

- "a\\\*" nie pasuje do docelowej sekwencji "aaa", ale pasuje do sekwencji docelowej "a".\*

Zestaw znaków, które są dozwolone w ucieczce tożsamości, zależy od gramatyki wyrażeń regularnych, jak pokazano w poniższej tabeli.

|Gramatyka|Dozwolone znaki ucieczki tożsamości|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.',\\'[', ' ' '\*' ', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended`plus { '"' , "/" }|
|`ECMAScript`|Wszystkie znaki z wyjątkiem tych, które mogą być częścią identyfikatora. Zazwyczaj obejmuje to litery, cyfry, '$', '\_i sekwencje unicode escape. Aby uzyskać więcej informacji, zobacz temat specyfikacji języka ECMAScript.|

### <a name="individual-character"></a>Pojedynczy znak

Pojedynczy znak w wyrażeniu w nawiasie kwadratowym dodaje ten znak do zestawu znaków, który jest zdefiniowany przez wyrażenie w nawiasie kwadratowym. Gdziekolwiek w wyrażeniu w nawiasie kwadratowym, z wyjątkiem początku, '^' reprezentuje sam siebie.

Przykłady:

- „[abc]” pasuje do sekwencji docelowych „a”, „b” i „c”, ale nie do sekwencji „d”.

- „[^abc]” pasuje do sekwencji docelowej „d”, ale nie do sekwencji docelowych „a”, „b” lub „c”.

- „[a^bc]” pasuje do sekwencji docelowych „a”, „b”, „c” i „^” , ale nie do sekwencji docelowej „d”.

We wszystkich gramatykach wyrażeń regularnych z wyjątkiem `ECMAScript`, jeśli ']' jest pierwszym znakiem, który następuje po otwarciu '[' lub jest pierwszym znakiem, który następuje po początkowym '^', reprezentuje się.

Przykłady:

- „[]a” jest nieprawidłowe, ponieważ nie ma ']', aby zakończyć wyrażenie w nawiasie kwadratowym.

- „[]abc]” pasuje do sekwencji docelowych „a”, „b”, „c” i „]”, ale nie do sekwencji docelowej „d”.

- „[^]abc]” pasuje do sekwencji docelowej „d”, ale nie do sekwencji docelowych „a”, „b”, „c” lub „]”.

W `ECMAScript`,\\użyj ' ]' do reprezentowania znaku ']' w wyrażeniu nawiasu.

Przykłady:

- „[]a” pasuje do sekwencji docelowej „a”, ponieważ wyrażenie w nawiasie kwadratowym jest puste.

- "[\\]abc]" pasuje do sekwencji docelowych "a", "b", "c" i "]", ale nie do sekwencji docelowej "d".

### <a name="negative-assert"></a>Asercja negatywna

Asercja negatywna pasuje do wszystkiego oprócz swojej zawartości. Nie używa żadnych znaków w sekwencji docelowej. Na przykład "(!aa)(a\*)" pasuje do sekwencji docelowej "a" i kojarzy grupę przechwytywania 1 z podsekwencją "a". Nie pasuje do sekwencji docelowej „aa” ani do sekwencji docelowej „aaa”.

### <a name="negative-word-boundary-assert"></a>Asercja negatywna granicy słowa

Ujemna granica słowa potwierdzenia pasuje, jeśli bieżąca pozycja w ciągu docelowym nie jest bezpośrednio po *granicy słowa*.

### <a name="non-capture-group"></a>Grupa nieprzechwytująca

Grupa nieprzechwytująca oznacza swoją zawartość jako pojedynczą jednostkę w gramatyce wyrażeń regularnych, ale nie nadaje etykiety tekstowi docelowemu. Na przykład "(a)(?:b)\*(c)" dopasowuje tekst docelowy "abbc" i kojarzy grupę przechwytywania 1 z podsekwencją "a" i grupą przechwytywania 2 z podsekwencją "c".

### <a name="non-greedy-repetition"></a>Powtórzenie niezachłanne

Powtórzenie niezachłanne używa najkrótszej podsekwencji sekwencji docelowej, która pasuje do wzorca. Powtórzenie zachłanne używa najdłuższej. Na przykład "(a+)(a\*b)" pasuje do sekwencji docelowej "aaab". Gdy używa się powtórzenia niezachłannego, kojarzy ono grupę przechwytywania 1 z podsekwencją „a” na początku sekwencji docelowej, a grupę przechwytywania 2 z podsekwencją „aab” na końcu sekwencji docelowej. Gdy używa się dopasowania zachłannego, kojarzy ono grupę przechwytywania 1 z podsekwencją „aaa”, a grupę przechwytywania 2 z podsekwencją „b”.

### <a name="octal-escape-sequence"></a>Ósemkowa sekwencja unikowa

Ósemkowa sekwencja unikowa to ukośnik odwrotny, po którym następuje jedna, dwie lub trzy cyfry ósemkowe (0-7). Pasuje do znaku w sekwencji docelowej, który ma wartość określoną przez te cyfry. Jeśli wszystkie cyfry to '0', sekwencja jest nieprawidłowa. Na przykład, „\101” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="ordinary-character"></a>Zwykły znak

Zwykły znak to dowolny prawidłowy znak, który nie ma specjalnego znaczenia w bieżącej gramatyce.

W `ECMAScript`, następujące znaki mają specjalne znaczenie:

- ^  $  \  .  \*+  ?  ( \[ ) ] { } &#124;

W `basic` `grep`i , następujące znaki mają specjalne znaczenie:

- .   \[   \

Również `basic` w `grep`i , następujące znaki mają specjalne znaczenia, gdy są one używane w określonym kontekście:

- '\*ma szczególne znaczenie we wszystkich przypadkach, z wyjątkiem sytuacji, gdy jest to pierwszy znak w wyrażeniu regularnym lub pierwszy znak, który następuje po początkowym "^" w wyrażeniu regularnym lub gdy jest to pierwszy znak grupy przechwytywania lub pierwszy znak, który następuje po początkowym "^" w grupie przechwytywania.

- '^' ma specjalne znaczenie, gdy jest to pierwszy znak wyrażenia regularnego.

- '$' ma specjalne znaczenie, gdy jest to ostatni znak wyrażenia regularnego.

W `extended` `egrep`, `awk`i , następujące znaki mają znaczenie specjalne:

- .   \[\   (   \*   +   ?   { &#124;

Również `extended`w `egrep`, `awk`i , następujące znaki mają specjalne znaczenia, gdy są one używane w określonym kontekście.

- ')' ma specjalne znaczenie, gdy pasuje do poprzedzającego '('.

- '^' ma specjalne znaczenie, gdy jest to pierwszy znak wyrażenia regularnego.

- '$' ma specjalne znaczenie, gdy jest to ostatni znak wyrażenia regularnego.

Zwykły znak pasuje do takiego samego znaku w sekwencji docelowej. Domyślnie oznacza to, że dopasowanie się powiedzie, jeśli dwa znaki są reprezentowane przez tę samą wartość. W dopasowaniu bez uwzględniania wielkości liter `ch0` `ch1` dwa `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`znaki i dopasuj je, jeśli . W dopasowaniu z uwzględnieniem ustawień `ch0` `ch1` regionalnych `traits.translate(ch0) == traits.translate(ch1)`dwa znaki i dopasuj, jeśli .

### <a name="positive-assert"></a>Asercja pozytywna

Asercja pozytywna pasuje do swojej zawartości, ale nie używa żadnych znaków w sekwencji docelowej.

Przykłady:

- "(=aa)(a)"\*pasuje do sekwencji docelowej "aaaa" i kojarzy grupę przechwytywania 1 z podsekwencją "aaaa".

- "aa)(a)"\*pasuje do sekwencji docelowej "aaaa" i kojarzy grupę przechwytywania 1 z podsekwencją "aa" na początku sekwencji docelowej i przechwytywania grupy 2 z podsekwencją "aa" na końcu sekwencji docelowej.

- "(=aa)(a)&#124;(a)" dopasowuje sekwencję docelową "a" i kojarzy grupę przechwytywania 1 z pustą sekwencją (ponieważ pozytywna asertywna nie powiodła się) i przechwytuje grupę 2 z podsekwencją "a". Pasuje też do sekwencji docelowej „aa” i kojarzy grupę przechwytywania 1 z podsekwencją „aa”, a grupę przechwytywania 2 z pustą sekwencją.

### <a name="unicode-escape-sequence"></a>Sekwencja unikowa unicode

Sekwencja unikowa unicode to ukośnik odwrotny, po którym następuje litera 'u' i cztery cyfry szesnastkowe (0-9a-fA-F). Pasuje do znaku w sekwencji docelowej, który ma wartość określoną przez te cztery cyfry. Na przykład, „\u0041” pasuje do sekwencji docelowej „A”, kiedy jest używane kodowanie znaków ASCII.

### <a name="wildcard-character"></a>Symbol wieloznaczny

Symbol wieloznaczny pasuje do dowolnego znaku w wyrażeniu docelowym z wyjątkiem nowego wiersza.

### <a name="word-boundary"></a>Granica słowa

Granica słowa występuje w następujących sytuacjach:

- Bieżący znak znajduje się na początku sekwencji docelowej i jest jednym ze znaków wyrazu`A-Za-z0-9_.`

- Bieżąca pozycja znaku jest poza końcem sekwencji docelowej, a ostatni znak w sekwencji docelowej jest jednym ze znaków słowa.

- Bieżący znak jest jednym ze znaków słowa, a znak poprzedzający nie jest.

- Bieżący znak nie jest jednym ze znaków słowa, a znak poprzedzający jest.

### <a name="word-boundary-assert"></a>Asercja granicy słowa

Granica słowa assert pasuje, gdy bieżąca pozycja w ciągu docelowym znajduje się bezpośrednio po *granicy słowa*.

## <a name="matching-and-searching"></a><a name="matchingandsearching"></a>Dopasowywanie i wyszukiwanie

Aby wyrażenie regularne pasowało do sekwencji docelowej, całe wyrażenie regularne musi pasować do całej sekwencji docelowej. Na przykład, wyrażenie regularne „bcd” pasuje do sekwencji docelowej „bcd”, ale nie pasuje do sekwencji docelowej „abcd” ani sekwencji docelowej „bcde”.

Aby wyszukiwanie wyrażenia regularnego zostało wykonane pomyślnie, gdzieś w sekwencji docelowej musi istnieć podsekwencja, która odpowiada wyrażeniu regularnemu. Wyszukiwanie znajduje zazwyczaj pasującą podsekwencję najbliżej lewej strony.

Przykłady:

- Wyszukanie wyrażenia regularnego „bcd” w sekwencji docelowej „bcd” zakończy się pomyślnie i dopasuje całą sekwencję. To samo wyszukiwanie w sekwencji docelowej „abcd” również zakończy się pomyślnie i dopasuje ostatnie trzy znaki. To samo wyszukiwanie w sekwencji docelowej „bcde” również zakończy się pomyślnie i dopasuje pierwsze trzy znaki.

- Wyszukanie wyrażenia regularnego „bcd” w sekwencji docelowej „bcdbcd” zakończy się pomyślnie i dopasuje pierwsze trzy znaki.

Jeśli istnieje więcej niż jedna podsekwencja, która pasuje w którymś miejscu w sekwencji docelowej, istnieją dwa sposoby wyboru pasującego wzorca. *Pierwsze dopasowanie* wybiera podsekwencję, która została znaleziona jako pierwsza, gdy wyrażenie regularne jest dopasowywane. *Najdłuższy mecz* wybiera najdłuższą podsekwencję spośród tych, które pasują w tej lokalizacji. Jeśli istnieje więcej niż jedna podsekwencja, która ma maksymalną długość, najdłuższe wystąpienie wybiera tę, która została znaleziona jako pierwsza. Na przykład, gdy używane jest pierwsze dopasowanie, wyszukiwanie wyrażenia regularnego "b&#124;bc" w sekwencji docelowej "abcd" odpowiada podsekwencji "b", ponieważ lewy termin naprzemienności odpowiada tej podsekwencji; w związku z tym, pierwszy mecz nie próbuje prawej strony terminu naprzemienności. Gdy jest używane najdłuższe wystąpienie, to samo wyszukiwanie pasuje do „bc” ponieważ „bc” jest dłuższe niż „b”.

Częściowe wystąpienie powiedzie się, jeśli dopasowanie osiąga koniec sekwencji docelowej bez niepowodzenia, nawet jeśli nie osiągnęło końca wyrażenia regularnego. W związku z tym, po pomyślnym częściowym wystąpieniu, dodanie znaków do sekwencji docelowej mogłoby spowodować niepowodzenie późniejszego częściowego wystąpienia. Jednakże, po niepowodzeniu częściowego wystąpienia, dodanie znaków do sekwencji docelowej nie może spowodować powodzenia późniejszego częściowego wystąpienia. Na przykład, przy częściowym wystąpieniu, „ab” pasuje do sekwencji docelowej „a”, ale nie „ac”.

## <a name="format-flags"></a><a name="formatflags"></a>Formatowanie flag

|Reguły formatu ECMAScript|Reguły formatu sed|Tekst zastępczy|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Sekwencja znaków zgodna z całym`[match[0].first, match[0].second)`wyrażeniem regularnym ( )|
|"$$"||"$"|
||"\\&"|"&"|
|"$"\`(znak dolara, po którym następuje wycena wstecz)|| Sekwencja znaków poprzedzająca podsekwencję, która`[match.prefix().first, match.prefix().second)`pasuje do wyrażenia regularnego ( )|
|„$'” (znak dolara, po którym następuje cudzysłów pojedynczy)||Sekwencja znaków, która następuje po podsekwencji, która pasuje do wyrażenia regularnego (`[match.suffix().first, match.suffix().second)`)|
|„$n”|„\n”|Sekwencja znaków, która pasuje `n`do `n` grupy przechwytywania na pozycji,`[match[n].first, match[n].second)`gdzie jest liczbą z 0 a 9 ( )|
||"\\\n"|„\n”|
|„$nn”||Sekwencja znaków, która pasuje `nn`do `nn` grupy przechwytywania na pozycji, gdzie`[match[nn].first, match[nn].second)`jest liczbą z 10 a 99 ( )|

## <a name="see-also"></a>Zobacz też

[Omówienie biblioteki standardowej języka C++](../standard-library/cpp-standard-library-overview.md)
