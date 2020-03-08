---
title: 'Składnia specyfikacji formatu: funkcje printf i wprintf'
ms.date: 10/21/2019
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
ms.openlocfilehash: 024e757f57e62ba2b30048c783798180b4da2b9a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865505"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Składnia specyfikacji formatu: funkcje printf i wprintf

Różne funkcje `printf` i `wprintf` przyjmują ciąg formatu i argumenty opcjonalne i tworzą sformatowaną sekwencję znaków dla danych wyjściowych. Ciąg formatu zawiera zero lub więcej *dyrektyw*, które są znakami literału dla danych wyjściowych lub zakodowanych *specyfikacji konwersji* , które opisują sposób formatowania argumentu w danych wyjściowych. W tym artykule opisano składnię używaną do kodowania specyfikacji konwersji w ciągu formatu. Aby uzyskać listę tych funkcji, zobacz [przesyłanie strumieniowe we/wy](../c-runtime-library/stream-i-o.md). 

Specyfikacja konwersji składa się z pól opcjonalnych i wymaganych w tej postaci:

**%** [[*flags*](#flags)] [[*Width*](#width)] [.[ *precyzja*](#precision)] [[*size*](#size)][*Typ*](#type)

Każde pole specyfikacji konwersji jest znakiem lub cyfrą, która oznacza określoną opcję formatu lub specyfikator konwersji. Pole wymagany *Typ* określa rodzaj konwersji, która ma zostać zastosowana do argumentu. Opcjonalne *flagi*, *Szerokość*i *precyzja* kontrolują dodatkowe aspekty formatowania, takie jak spacje wiodące lub zera, uzasadnienie i wyświetlana dokładność. Pole *rozmiar* określa rozmiar zużytego i przekonwertowanego argumentu.

Podstawowa specyfikacja konwersji zawiera tylko znak procentu i *Typ* . Na przykład `%s` określa konwersję ciągu. Aby znak procentu był wyświetlany, należy użyć składni `%%`. Jeśli po znaku procentu następuje znak, który nie ma znaczenia jako pola formatu, zostanie wywołana procedura obsługi nieprawidłowego parametru. Aby uzyskać więcej informacji, zobacz [Walidacja parametrów](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> W celu zapewnienia bezpieczeństwa i stabilności upewnij się, że ciągi specyfikacji konwersji nie są zdefiniowane przez użytkownika. Rozważmy na przykład program, który monituje użytkownika o wprowadzenie nazwy, a dane wejściowe przechowuje w zmiennej o nazwie `user_name` będącej ciągiem tekstowym. W celu wyświetlenia wartości zmiennej `user_name` nie należy robić tak:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Zamiast tego należy zrobić tak:
>
> `printf( "%s", user_name );`

<a name="type"></a>

> [!NOTE] 
> W programie Visual Studio 2015 `printf` i `scanf` Rodzina funkcji zostały zadeklarowane jako **wbudowane** i przeniesione do nagłówków `<stdio.h>` i `<conio.h>`. W przypadku migrowania starszego kodu w połączeniu z tymi funkcjami może być widoczny *LNK2019* . Aby uzyskać więcej informacji, [Zobacz C++ historia zmian wizualnych 2003-2015](../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

## <a name="type-conversion-specifier"></a>Specyfikator konwersji typów

Znak specyfikatora konwersji *typu* określa, czy odpowiedni argument ma być interpretowany jako znak, ciąg, wskaźnik, liczba całkowita, czy liczba zmiennoprzecinkowa. Znak *typu* jest jedynym wymaganym polem specyfikacji konwersji i pojawia się po dowolnych opcjonalnych polach.

Argumenty występujące po ciągu formatu są interpretowane według odpowiedniego znaku *typu* i opcjonalnego prefiksu [rozmiaru](#size) . Konwersje dla typów znaków `char` i `wchar_t` są określane przy użyciu języka **c** lub **c**, a ciągi o pojedynczym bajcie i wielu bajtach są określane za pomocą **s** lub **s**, w zależności od tego, która funkcja formatowania jest używana. Argumenty znaków i ciągów, które są określone przy użyciu języka **c** i **s** , są interpretowane jako `char` i `char*` przez `printf` funkcji rodzinnych lub `wchar_t` i `wchar_t*` przez `wprintf` funkcje rodziny. Argumenty znaków i ciągów, które są określone przy użyciu języka **C** i **S** , są interpretowane jako `wchar_t` i `wchar_t*` przez `printf` funkcji rodzinnych lub `char` i `char*` przez `wprintf` funkcje rodziny. To zachowanie jest zależne od firmy Microsoft.

Typy całkowite, takie jak `short`, `int`, `long`, `long long`i ich `unsigned` wariantów, są określane przy użyciu **d**, **i**, **o**, **u**, **x**i **x**. Typy zmiennoprzecinkowe, takie jak `float`, `double`i `long double`, są określane przy użyciu **a**, **a**, **e**, **e**, **f**, **f**, **g**i **g**. Domyślnie, chyba że są modyfikowane przez prefiks *rozmiaru* , argumenty całkowite są przekształcane na typ `int`, a argumenty zmiennoprzecinkowe są przekształcane na `double`. W systemach 64-bitowych `int` jest wartością 32-bitową; w związku z tym 64-bitowe liczby całkowite będą obcinane, gdy są sformatowane do danych wyjściowych, chyba że używany jest prefiks *size* **I64** **lub nie** . Typy wskaźników, które są określone przez **p** , używają domyślnego rozmiaru wskaźnika dla platformy.

> [!NOTE]
> **Specyficzne dla firmy Microsoft:** Znak **z typu z** oraz zachowanie znaków typu **c**, **c**, **s**i **s** , gdy są one używane z funkcjami `printf` i `wprintf`, są rozszerzeniami firmy Microsoft. Standard ISO C używa **c** i **s** konsekwentnie dla wąskich znaków i ciągów, a **C** i **s** dla szerokich znaków i ciągów, we wszystkich funkcjach formatowania.

### <a name="type-field-characters"></a>Znaki pola typu

|Znak typu|Argument|Format danych wyjściowych|
|--------------------|--------------|-------------------|
|**s**|Znak|Gdy jest używany z funkcjami `printf`, określa znak jednobajtowy; w przypadku użycia z funkcjami `wprintf`, określa znak dwubajtowy.|
|**C**|Znak|Gdy jest używany z funkcjami `printf`, określa znak dwubajtowy; gdy jest używany z funkcjami `wprintf`, określa znak jednobajtowy.|
|**Wykres**|Liczba całkowita|Cyfra dziesiętna ze znakiem.|
|**i**|Liczba całkowita|Cyfra dziesiętna ze znakiem.|
|**wyjścia**|Liczba całkowita|Liczba całkowita bez znaku.|
|**'t**|Liczba całkowita|Liczba całkowita dziesiętna bez znaku.|
|**y**|Liczba całkowita|Szesnastkowa liczba całkowita bez znaku; używa "abcdef".|
|**Y**|Liczba całkowita|Szesnastkowa liczba całkowita bez znaku; używa "ABCDEF".|
|**e**|Liczba zmiennoprzecinkowa|Wartość ze znakiem, która ma postać [-]*d. dddd*__e ±__*DD*\[*d*], gdzie *d* jest jedną cyfrą dziesiętną, *dddd* to co najmniej jedna cyfra dziesiętna w zależności od określonej precyzji lub sześć domyślnie, a *DD*\[*d*] ma dwie lub trzy cyfry dziesiętne, w zależności od [formatu danych wyjściowych](../c-runtime-library/set-output-format.md) i rozmiaru wykładnika.|
|**Adres**|Liczba zmiennoprzecinkowa|Identyczny z formatem **e** , z tą różnicą, że **e** zamiast **e** wprowadza wykładnik.|
|**n**|Liczba zmiennoprzecinkowa|Wartość ze znakiem, która ma postać [-]*dddd* __.__ *dddd*, gdzie *dddd* to co najmniej jedna cyfra dziesiętna. Liczba cyfr przed punktem dziesiętnym zależy od wielkości liczby, a liczba cyfr po przecinku jest zależna od wymaganej precyzji lub sześciu domyślnie.|
|**N**|Liczba zmiennoprzecinkowa|Identyczny z formatem **f** , z wyjątkiem tego, że nieskończoność i Nan dane wyjściowe są pisane wielkimi literami.|
|**g**|Liczba zmiennoprzecinkowa|Wartości podpisane są wyświetlane w formacie **f** lub **e** , w zależności od tego, który jest bardziej zwarty dla danej wartości i dokładności. Format **e** jest używany tylko wtedy, gdy wykładnik wartości jest mniejszy niż-4 lub większy lub równy argumentowi *precyzji* . Końcowe zera są obcinane, a punkt dziesiętny pojawia się tylko wtedy, gdy jedna lub więcej cyfr należy do niego.|
|**G**|Liczba zmiennoprzecinkowa|Identyczny z formatem **g** , z tą różnicą, że **e**, zamiast **e**, wprowadza wykładnik (tam, gdzie to konieczne).|
|**z**|Liczba zmiennoprzecinkowa|Podpisana szesnastkowa wartość zmiennoprzecinkowa o podwójnej precyzji, która ma postać [-] 0x*h. hhhh*__p ±__*DD*, gdzie *h. hhhh* to cyfry szesnastkowe (przy użyciu małych liter) mantysy, a *DD* to jedna lub więcej cyfr dla wykładnika. Precyzja określa liczbę cyfr po punkcie.|
|**Z**|Liczba zmiennoprzecinkowa|Podpisana szesnastkowa wartość zmiennoprzecinkowa o podwójnej precyzji, która ma postać [-] 0X*h. hhhh*__P ±__*DD*, gdzie *h. hhhh* to cyfry szesnastkowe (przy użyciu wielkich liter) mantysy, a *DD* to jedna lub więcej cyfr dla wykładnika. Precyzja określa liczbę cyfr po punkcie.|
|**Azotan**|Wskaźnik na liczbę całkowitą|Liczba znaków, które zostały pomyślnie wpisane do strumienia lub buforu. Ta wartość jest przechowywana w postaci liczby całkowitej, której adres jest podawany jako argument. Rozmiar liczby całkowitej wskazywanej w można kontrolować przy użyciu prefiksu specyfikacji rozmiaru argumentu. Specyfikator **n** jest domyślnie wyłączony; Aby uzyskać więcej informacji, zobacz ważne uwagi dotyczące zabezpieczeń.|
|**St**|Typ wskaźnika|Wyświetla argument jako adres w cyfrach szesnastkowych.|
|**wolumin**|Ciąg|Gdy jest używany z funkcjami `printf`, Określa jednobajtowy lub wielobajtowy ciąg znaków; w przypadku używania z funkcjami `wprintf`, określa ciąg znaków dwubajtowych. Znaki są wyświetlane do pierwszego znaku null lub do czasu osiągnięcia wartości *precyzji* .|
|**Wolumin**|Ciąg|W przypadku użycia z funkcjami `printf`, określa ciąg znaków dwubajtowych; w przypadku używania z funkcjami `wprintf`, określa ciąg znaków pojedynczego bajtu lub wielobajtowego. Znaki są wyświetlane do pierwszego znaku null lub do czasu osiągnięcia wartości *precyzji* .|
|**Porządku**|Struktura `ANSI_STRING` lub `UNICODE_STRING`|Gdy do argumentu jest przenoszona adres [ANSI_STRING](/windows/win32/api/ntdef/ns-ntdef-string) lub [UNICODE_STRING](/windows/win32/api/ntdef/ns-ntdef-_unicode_string) , program wyświetla ciąg zawarty w buforze wskazanym przez `Buffer` pole struktury. Użyj prefiksu modyfikatora *rozmiaru* **w** , aby określić argument `UNICODE_STRING`, na przykład `%wZ`. W polu `Length` struktury musi być ustawiona Długość (w bajtach) ciągu. W polu `MaximumLength` struktury musi być ustawiona Długość (w bajtach) buforu.<br /><br /> Zazwyczaj znak **z typu z** jest używany tylko w funkcjach debugowania sterowników, które używają specyfikacji konwersji, takiej jak `dbgPrint` i `kdPrint`.|

Począwszy od programu Visual Studio 2015, jeśli argument, który odpowiada specyfikatorowi konwersji zmiennoprzecinkowej (**a**, **a**, **e**, **e**, **f**, **f**, **g**, **g**) jest nieskończony, nieokreślony lub NaN, sformatowane dane wyjściowe są zgodne ze standardem C99. W tej tabeli wymieniono sformatowane dane wyjściowe:

|Wartość|Dane wyjściowe|
|-----------|------------|
|nieskończoność|`inf`|
|Cichy NaN|`nan`|
|Sygnalizowanie NaN|`nan(snan)`|
|Nieokreślony NaN|`nan(ind)`|

Wszystkie te wartości mogą być poprzedzone znakiem. Jeśli znak specyfikatora konwersji *typu* zmiennoprzecinkowego jest wielką literą, dane wyjściowe są również formatowane wielkimi literami. Na przykład, jeśli specyfikator formatu jest `%F`, a nie `%f`, nieskończoność jest formatowana jako `INF` zamiast `inf`. Funkcje `scanf` mogą również analizować te ciągi, dzięki czemu te wartości mogą przekonywać rundy za pomocą funkcji `printf` i `scanf`.

Przed uruchomieniem programu Visual Studio 2015 CRT użył innego niestandardowego formatu dla danych wyjściowych nieskończonych, nieokreślonych i NaN:

|Wartość|Dane wyjściowe|
|-----------|------------|
|+ nieskończoność|`1.#INF` *cyfry losowe*|
|-nieskończoność|`-1.#INF` *cyfry losowe*|
|Nieokreślony (taki sam jak cichy NaN)|*cyfra `.#IND`* liczbami *losowymi*|
|NaN|*cyfra `.#NAN`* liczbami *losowymi*|

Dowolne z tych elementów mogło zostać poprzedzone znakiem i być sformatowane nieco inaczej w zależności od szerokości pola i precyzji, czasami z nietypowymi skutkami. Na przykład `printf("%.2f\n", INFINITY)` może drukować `1.#J`, ponieważ #INF będzie "zaokrąglona" do 2 cyfr dokładności.

> [!NOTE]
> Jeśli argument, który odnosi się do `%s` lub `%S`lub pole `Buffer` argumentu, który odpowiada `%Z`, jest wskaźnikiem o wartości null, zostanie wyświetlony komunikat "(null)".

> [!NOTE]
> We wszystkich formatach wykładniczych minimalna liczba cyfr do wyświetlenia jest równa 2, przy użyciu trzech tylko w razie potrzeby. Za pomocą funkcji [_set_output_format](../c-runtime-library/set-output-format.md) można ustawić liczbę cyfr wyświetlanych na trzy w celu zachowania zgodności z kodem zapisanym dla Visual Studio 2013 i wcześniej.

> [!IMPORTANT]
> Ponieważ format `%n` jest z natury niezabezpieczony, jest domyślnie wyłączony. Jeśli w ciągu formatu wystąpi `%n`, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../c-runtime-library/parameter-validation.md). Aby włączyć obsługę `%n`, zobacz [_set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Dyrektywy flag

Pierwsze opcjonalne pole w specyfikacji konwersji zawiera *dyrektywy flag*, zero lub więcej znaków flagi, które określają Justowanie danych wyjściowych i kontrolowanie danych wyjściowych znaków, pustych, wiodących zer, punktów dziesiętnych i szesnastkowych prefiksów. W specyfikacji konwersji może pojawić się więcej niż jedna dyrektywa flag, a znaki flagi mogą pojawiać się w dowolnej kolejności.

### <a name="flag-characters"></a>Znaki flagi

|Flaga|Znaczenie|Domyślne|
|----------|-------------|-------------|
|**-**|Wyrównaj wynik z lewej strony do pola.|Wyrównaj do prawej.|
|**+**|Użyj znaku (+ lub-), aby utworzyć prefiks wartości wyjściowej, jeśli jest ona typu ze znakiem.|Znak jest wyświetlany tylko w przypadku ujemnych wartości podpisanych (-).|
|**0**|Jeśli *Szerokość* jest poprzedzona przez **0**, zera wiodące są dodawane do momentu osiągnięcia minimalnej szerokości. Jeśli zostanie wyświetlona **wartość 0** i **-** , wartość **0** jest ignorowana. Jeśli **określono wartość 0** dla formatu liczb całkowitych (**i**, **u**, **x**, **x**, **o**, **d**), a Specyfikacja dokładności również jest obecna, na przykład `%04.d`— **wartość 0** jest ignorowana. Jeśli **wartość 0** jest określona dla formatu a **lub** zmiennoprzecinkowego, zera wiodące są poprzedzone mantysy, po prefiksie `0x` lub `0X`.|Brak dopełnienia.|
|**puste** (' ')|Użyj pustej wartości, aby prefiksować wartość wyjściową, jeśli jest ona podpisana i dodatnia. Wartość pusta jest ignorowana, jeśli są wyświetlane flagi puste i +.|Nie pojawia się żadne puste.|
|**#**|Gdy jest używany z formatem **o**, **x**lub **x** , flaga **#** używa odpowiednio 0, 0x lub 0x, aby prefiksować dowolną niezerową wartość wyjściową.|Nie pojawia się żadne puste.|
||Gdy jest używany z **e**, **e**, **f**, **f**, **a**lub w formacie, flaga **#** wymusza, aby wartość wyjściowa zawierała separator dziesiętny.|Punkt dziesiętny jest wyświetlany tylko wtedy, gdy cyfry są zgodne.|
||Gdy jest używany z formatem **g** lub **g** , flaga **#** wymusza wartość wyjściową, aby zawierała przecinek dziesiętny i uniemożliwia obcinanie końcowych zer.<br /><br /> Ignorowane, gdy jest używany z **c**, **d**, **i**, **u**lub **s**.|Punkt dziesiętny jest wyświetlany tylko wtedy, gdy cyfry są zgodne. Końcowe zera są obcinane.|

<a name="width"></a>

## <a name="width-specification"></a>Specyfikacja szerokości

W specyfikacji konwersji pole opcjonalnej specyfikacji szerokości pojawia się po każdym z *flag* znaków. Argument *Width* jest nieujemną liczbą całkowitą dziesiętną, która określa minimalną liczbę znaków, które są wyprowadzane. Jeśli liczba znaków w wartości wyjściowej jest mniejsza niż określona szerokość, puste są dodawane do lewej lub prawej strony wartości — w zależności od tego, czy flaga wyrównania w lewo ( **-** ) jest określona — do momentu osiągnięcia minimalnej szerokości. Jeśli *Szerokość* jest poprzedzona przez 0, zera wiodące są dodawane do liczby całkowitej lub konwersji zmiennoprzecinkowej do momentu osiągnięcia minimalnej szerokości, z wyjątkiem sytuacji, gdy konwersja jest nieskończona lub NaN.

Specyfikacja szerokości nigdy nie powoduje obcięcia wartości. Jeśli liczba znaków w wartości wyjściowej jest większa niż określona szerokość lub *Szerokość* nie zostanie podana, wszystkie znaki wartości są wyprowadzane zgodnie ze specyfikacją *precyzji* .

Jeśli Specyfikacja szerokości jest gwiazdką (`*`), argument `int` z listy argumentów poda wartość. Argument *Width* musi poprzedzać wartość, która jest formatowana na liście argumentów, jak pokazano w poniższym przykładzie:

`printf("%0*d", 5, 3);  /* 00003 is output */`

Brakująca lub niewielka wartość *szerokości* w specyfikacji konwersji nie powoduje obcięcia wartości wyjściowej. Jeśli wynik konwersji jest szerszy niż wartość *szerokości* , pole zostanie rozwinięte, aby zawierało wynik konwersji.

<a name="precision"></a>

## <a name="precision-specification"></a>Specyfikacja dokładności

W specyfikacji konwersji trzecie pole opcjonalne jest specyfikacją precyzji. Zawiera kropkę (.), a następnie nieujemną liczbę całkowitą dziesiętną, która w zależności od typu konwersji określa liczbę znaków ciągu, liczbę miejsc dziesiętnych lub liczbę cyfr znaczących, które mają być wyprowadzane.

W przeciwieństwie do specyfikacji szerokości, Specyfikacja dokładności może spowodować Obcinanie wartości wyjściowej lub zaokrąglenie wartości zmiennoprzecinkowej. Jeśli *precyzja* jest określona jako 0, a wartość do przekonwertowania to 0, wynik nie ma znaków wyjściowych, jak pokazano w tym przykładzie:

`printf( "%.0d", 0 );      /* No characters output */`

Jeśli Specyfikacja dokładności jest gwiazdką (\*), argument `int` z listy argumentów poda wartość. Na liście argumentów argument *dokładności* musi poprzedzać wartość, która jest formatowana, jak pokazano w poniższym przykładzie:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

Znak *typu* określa interpretację *dokładności* lub precyzję domyślną, gdy *precyzja* zostanie pominięta, jak pokazano w poniższej tabeli.

### <a name="how-precision-values-affect-type"></a>Jak wartości dokładności mają wpływ na typ

|Typ|Znaczenie|Domyślne|
|----------|-------------|-------------|
|**a**, **a**|Precyzja określa liczbę cyfr po punkcie.|Domyślna precyzja to 13. Jeśli precyzja to 0, nie jest drukowany punkt dziesiętny, chyba że zostanie użyta flaga **#** .|
|**c**, **c**|Precyzja nie ma żadnego wpływu.|Znak jest drukowany.|
|**d**, **i**, **o**, **u**, **x**, **x**|Precyzja określa minimalną liczbę cyfr do wydrukowania. Jeśli liczba cyfr w argumencie jest mniejsza niż *precyzja*, wartość wyjściowa zostanie uzupełniona o zero. Wartość nie jest obcinana, gdy liczba cyfr przekracza *precyzję*.|Domyślna precyzja to 1.|
|**e**, **e**|Precyzja określa liczbę cyfr do wydrukowania po przecinku dziesiętnym. Ostatnia wydrukowana cyfra jest zaokrąglana.|Domyślna precyzja to 6. Jeśli *precyzja* to 0 lub kropka (.) pojawia się bez cyfry po niej, nie jest drukowany żaden punkt dziesiętny.|
|**f**, **f**|Wartość precyzji określa liczbę cyfr po przecinku dziesiętnym. Jeśli zostanie wyświetlony punkt dziesiętny, przed nim zostanie wyświetlona co najmniej jedna cyfra. Wartość jest zaokrąglana do odpowiedniej liczby cyfr.|Domyślna precyzja to 6. Jeśli *precyzja* to 0, lub jeśli kropka (.) pojawia się bez cyfry po niej, nie jest drukowany żaden punkt dziesiętny.|
|**g**, **g**|Precyzja określa maksymalną liczbę cyfr znaczących.|Drukowane są sześć cyfr znaczących, a końcowe zera są obcinane.|
|**s**, **s**|Precyzja określa maksymalną liczbę znaków do wydrukowania. Nie są drukowane znaki o przekroczeniu *precyzji* .|Znaki są drukowane, dopóki nie zostanie osiągnięty znak o wartości null.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Specyfikacja rozmiaru argumentu

W specyfikacji konwersji pole *size* jest modyfikatorem długości argumentów dla specyfikatora konwersji *typu* . Prefiks pola *rozmiaru* dla pola *Typ* —**hh**, **h**, **j**, **l** (małe litery l), **l**, **wszystkie**, **t**, z, **z**, **I** (wielkie I), **I32**i **I64**— określa "rozmiar" odpowiadającego argumentu — Long lub Short, 32-bitowy lub 64-bitowy, znak jednobajtowy lub szeroki, w zależności od specyfikatora konwersji, który modyfikuje. Te prefiksy rozmiarów są używane z znakami *typu* w `printf` i `wprintf` rodziny funkcji do określenia interpretacji rozmiarów argumentów, jak pokazano w poniższej tabeli. Pole *size* jest opcjonalne dla niektórych typów argumentów. Gdy nie określono prefiksu rozmiaru, program formatujący zużywa argumenty całkowite — na przykład podpisane lub niepodpisane `char`, `short`, `int`, `long`i typy wyliczeniowe — jako 32-bitowe typy `int`, a `float`, `double`i `long double` argumenty zmiennoprzecinkowe są używane jako 64-bitowe typy `double`. To zachowanie jest zgodne z domyślnymi regułami podwyższania poziomu argumentów dla list argumentów zmiennych. Aby uzyskać więcej informacji na temat promocji argumentów, zobacz wielokropki i argumenty domyślne w [wyrażeniach przyrostkowych](../cpp/postfix-expressions.md). W systemach 32-bitowych i 64-bitowych specyfikacja konwersji argumentu 64-bit Integer musi zawierać prefiks size o wartości **szystkie** lub **I64**. W przeciwnym razie zachowanie programu formatującego nie jest zdefiniowane.

Niektóre typy mają różne rozmiary w 32-bitowym i 64-bitowym kodzie. Na przykład `size_t` to 32 bitów Long w kodzie skompilowanym dla x86 i 64 bitów w kodzie skompilowanym dla x64. Aby utworzyć kod formatowania niezależny od na platformie dla typów o zmiennej szerokości, można użyć modyfikatora rozmiaru argumentu o zmiennej szerokości. Alternatywnie można użyć modyfikatora rozmiaru argumentu 64-bitowego i jawnie podnieść typ argumentu o zmiennej szerokości do 64 bitów. Modyfikator rozmiaru **argumentu (wielkie i)** firmy Microsoft obsługuje argumenty całkowite o zmiennej szerokości, ale zaleca się Modyfikatory **j**, **t**i **z** dla różnych typów dla przenośności.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Prefiksy rozmiarów dla specyfikatorów typu printf i wprintf

|Aby określić|Użyj prefiksu|Ze specyfikatorem typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**formacie**|**d**, **i**, **o**, **u**, **x**lub **x**|
|`short int`<br />`short unsigned int`|**c**|**d**, **i**, **o**, **u**, **x**lub **x**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x**lub **x**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x**lub **x**|
|`intmax_t`<br />`uintmax_t`|**j** lub **I64**|**d**, **i**, **o**, **u**, **x**lub **x**|
|`long double`|**l** (mała litera l) lub **l**|**a**, **a**, **e**, **e**, **f**, **f**, **g**lub **g**|
|`long int`<br />`long unsigned int`|**l** (mała litera l)|**d**, **i**, **o**, **u**, **x**lub **x**|
|`long long int`<br />`unsigned long long int`|**wszystkie** (małe litery)|**d**, **i**, **o**, **u**, **x**lub **x**|
|`ptrdiff_t`|**t** lub **I** (wielkie litery I)|**d**, **i**, **o**, **u**, **x**lub **x**|
|`size_t`|**z** lub **i** (wielkie litery I)|**d**, **i**, **o**, **u**, **x**lub **x**|
|Znak jednobajtowy|**c**|**c** lub **c**|
|Znak dwubajtowy|**l** (mała litera l) lub **w**|**c** lub **c**|
|Jednobajtowy ciąg znaków|**c**|**s**, **s**lub **Z**|
|Ciąg znaków dwubajtowych|**l** (mała litera l) lub **w**|**s**, **s**lub **Z**|

Typy `ptrdiff_t` i `size_t` są `__int32` lub `unsigned __int32` na platformach 32-bitowych, a `__int64` lub `unsigned __int64` na platformach 64-bitowych. Prefiksy **i** (wielkie i), **j**, **t**i **z** mają poprawną szerokość argumentu dla danej platformy.

W wizualizacji C++, chociaż `long double` jest typem odrębnym, ma tę samą reprezentację wewnętrzną co `double`.

Specyfikator typu **HC** lub **HC** jest synonimem języka **c** w `printf` Functions i with **c** w funkcjach `wprintf`. Specyfikator **typu** **LC**, LC **,** dblubbinding jest synonimem języka **c** w `printf` functions i with **c** w funkcjach `wprintf`. Specyfikator typu **HS** lub **HS** jest synonimem elementu **s** w `printf` Functions i with **s** w funkcjach `wprintf`. Specyfikator typu **ls**, **ls**, **WS** lub **ws** jest synonimem elementu **s** w `printf` Functions i with **s** w funkcjach `wprintf`.

> [!NOTE]
> **Specyficzne dla firmy Microsoft:** Prefiksy **i (wielkie i)** , **I32**, **I64**i **w** stosunku do rozmiaru argumentów są rozszerzeniami firmy Microsoft i nie są zgodne ze standardem ISO C. Prefiks **h** , gdy jest używany z danymi typu `char` oraz prefiks **l** (małe litery l), gdy jest używany z danymi typu `double` są rozszerzeniami firmy Microsoft.

## <a name="see-also"></a>Zobacz też

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[printf_p Parametry pozycyjne](../c-runtime-library/printf-p-positional-parameters.md)
