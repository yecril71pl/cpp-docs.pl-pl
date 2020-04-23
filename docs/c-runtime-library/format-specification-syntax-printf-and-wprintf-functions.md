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
ms.openlocfilehash: 781c90414090ff8a21414c72f744ed275e315d56
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032164"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Składnia specyfikacji formatu: funkcje printf i wprintf

Różne `printf` funkcje `wprintf` przyjmują ciąg formatu i opcjonalne argumenty i tworzą sformatowaną sekwencję znaków dla danych wyjściowych. Ciąg formatu zawiera zero lub więcej dyrektyw , które są *znakami*literału dla danych wyjściowych lub zakodowanych *specyfikacji konwersji,* które opisują sposób formatowania argumentu w danych wyjściowych. Ten artykuł zawiera opis składni używanej do kodowania specyfikacji konwersji w ciągu formatu. Aby uzyskać listę tych funkcji, zobacz [We/Wy strumienia](../c-runtime-library/stream-i-o.md).

Specyfikacja konwersji składa się z opcjonalnych i wymaganych pól w tym formularzu:

**%**[[*flagi*](#flags)] [[*szerokość*](#width)] [. [*precyzja*](#precision)] [[*rozmiar*](#size)] [*typ*](#type)

Każde pole specyfikacji konwersji jest znakiem lub liczbą, która oznacza określoną opcję formatu lub specyfikator konwersji. Wymagane pole *typu* określa rodzaj konwersji, która ma być zastosowana do argumentu. Opcjonalne *flagi,* *szerokość*i *precyzyjne* pola kontrolują dodatkowe aspekty formatu, takie jak spacje wiodące lub zera, justyny i wyświetlana precyzja. Pole *rozmiar* określa rozmiar argumentu zużytego i przekonwertowanego.

Podstawowa specyfikacja konwersji zawiera tylko znak procentu i znak *typu.* Na przykład `%s` określa konwersję ciągów. Aby znak procentu był wyświetlany, należy użyć składni `%%`. Jeśli znak procentu następuje znak, który nie ma znaczenia jako pole formatu, wywoływany jest nieprawidłowy program obsługi parametrów. Aby uzyskać więcej informacji, zobacz [Sprawdzanie poprawności parametrów](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Dla zabezpieczeń i stabilności, upewnij się, że parametry specyfikacji konwersji nie są zdefiniowane przez użytkownika. Rozważmy na przykład program, który monituje użytkownika o wprowadzenie nazwy, a dane wejściowe przechowuje w zmiennej o nazwie `user_name` będącej ciągiem tekstowym. W celu wyświetlenia wartości zmiennej `user_name` nie należy robić tak:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Zamiast tego należy zrobić tak:
>
> `printf( "%s", user_name );`

<a name="type"></a>

> [!NOTE]
> W programie Visual Studio 2015 `printf` i `scanf` rodziny funkcji zostały zadeklarowane jako **wbudowane** i przeniesione do `<stdio.h>` i `<conio.h>` nagłówki. Jeśli migrujesz starszy kod, może zostać wyświetlony *LNK2019* w związku z tymi funkcjami. Aby uzyskać więcej informacji, zobacz [Visual C++ change history 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

## <a name="type-conversion-specifier"></a>Specyfikator konwersji typu

Znak specyfikatora konwersji *typu* określa, czy interpretować odpowiedni argument jako znak, ciąg, wskaźnik, liczbę całkowitą lub liczbę zmiennoprzecinkową. Znak *typu* jest jedynym wymaganym polem specyfikacji konwersji i pojawia się po wszystkich polach opcjonalnych.

Argumenty, które następują po ciągu formatu są interpretowane zgodnie z odpowiednim znakiem *typu* i opcjonalnym prefiksem [rozmiaru.](#size) Konwersje dla `char` typów `wchar_t` znaków i są określane za pomocą **c** lub **C,** a ciągi znaków jedno-bajtowych i wielobędowych lub szerokich są określane za pomocą **s** lub **S**, w zależności od używanej funkcji formatowania. Argumenty znaków i ciągów, które są określone `char` przy `char*` `printf` użyciu **c** i `wchar_t` `wchar_t*` **s** są interpretowane jako i przez funkcje rodzinne lub jako i przez `wprintf` funkcje rodzinne. Argumenty znaków i ciągów, które są określone `wchar_t` przy `wchar_t*` `printf` użyciu **C** i `char` `char*` **S** są interpretowane jako i przez funkcje rodzinne lub jako i przez `wprintf` funkcje rodzinne. To zachowanie jest specyficzne dla firmy Microsoft.

Typy całkowite, `short`takie `int` `long`jak `long long`, `unsigned` , , i ich warianty, są określane za pomocą **d**, **i**, **o**, **u**, **x**i **X**. Typy zmiennoprzecinowe, `float`takie jak , `double`i `long double`, są określone za pomocą , **A**, **e**, **E**, **f**, **F**, **g**i **G**. **a** Domyślnie, chyba że są one modyfikowane przez prefiks *rozmiaru,* argumenty liczby całkowitej są zmuszane do `int` pisania, a argumenty zmiennoprzecinowe są przymuszone do `double`. W systemach 64-bitowych `int` wartość jest wartością 32-bitową; w związku z tym 64-bitowe liczby całkowite zostaną obcięte, gdy są sformatowane dla danych wyjściowych, chyba że używany jest prefiks *rozmiaru* **ll** lub **I64.** Typy wskaźników, które są określone przez **p** używać domyślnego rozmiaru wskaźnika dla platformy.

> [!NOTE]
> **Specyficzne dla firmy Microsoft:** Znak typu **Z** oraz zachowanie znaków **typu c**, **C**, **s**i `printf` **S,** gdy są używane z funkcjami i funkcjami, `wprintf` są rozszerzeniami firmy Microsoft. Norma ISO C używa **c** i **s** konsekwentnie dla wąskich znaków i ciągów znaków oraz **C** i **S** dla szerokich znaków i ciągów we wszystkich funkcjach formatowania.

### <a name="type-field-characters"></a>Typy znaków pola

|Znak typu|Argument|Format wyjściowy|
|--------------------|--------------|-------------------|
|**C**|Znak|W przypadku `printf` użycia z funkcjami określa znak jedno bajtowy; gdy jest `wprintf` używany z funkcjami, określa szeroki znak.|
|**C**|Znak|W przypadku `printf` użycia z funkcjami określa szeroki znak; gdy jest `wprintf` używany z funkcjami, określa znak jedno bajtowy.|
|**D**|Liczba całkowita|Podpisana dziesiętna ćwięk.|
|**I**|Liczba całkowita|Podpisana dziesiętna ćwięk.|
|**o**|Liczba całkowita|Niepodpisana ósemka całkowitej.|
|**U**|Liczba całkowita|Niepodpisaną dziesiętną całkowitej.|
|**X**|Liczba całkowita|Niepodpisana szesnastkowa tynekcjowa; używa "abcdef".|
|**X**|Liczba całkowita|Niepodpisana szesnastkowa tynekcjowa; używa "ABCDEF".|
|**E**|Zmiennoprzecinkowych|Podpisana wartość, która ma formę [-]*d.dddd*__e±__*dd*\[*d*], gdzie *d* jest jedną cyfrą dziesiętną, *dddd* jest jedną lub więcej cyfr dziesiętnych w zależności od określonej precyzji lub sześć domyślnie, a *dd*\[*d*] to dwie lub trzy cyfry dziesiętne w zależności od [formatu wyjściowego](../c-runtime-library/set-output-format.md) i rozmiaru wykładnika.|
|**E**|Zmiennoprzecinkowych|Identyczne z formatem **e,** z tą różnicą, że **E** zamiast **e** wprowadza wykładnik.|
|**F**|Zmiennoprzecinkowych|Podpisana wartość, która ma formularz [-]*dddd*__.__ *dddd*, gdzie *dddd* jest jedną lub więcej cyfr dziesiętnych. Liczba cyfr przed przecinem dziesiętnym zależy od wielkości liczby, a liczba cyfr po przecinku zależy od żądanej precyzji lub domyślnie sześciu.|
|**F**|Zmiennoprzecinkowych|Identyczne z formatem **f,** z tą różnicą, że dane wyjściowe nieskończoności i nan są kapitalizowane.|
|**G**|Zmiennoprzecinkowych|Podpisane wartości są wyświetlane w formacie **f** lub **e,** w zależności od tego, która z tych wartości jest bardziej kompaktowa dla danej wartości i precyzji. Format **e** jest używany tylko wtedy, gdy wykładnik wartości jest mniejszy niż -4 lub większy lub równy argumentowi *precyzji.* Końcowe zera są obcinane, a przecinek dziesiętnych pojawia się tylko wtedy, gdy podąża za nim jedna lub więcej cyfr.|
|**G**|Zmiennoprzecinkowych|Identyczny z formatem **g,** z tą różnicą, że **E**, a nie **e,** wprowadza wykładnik (w stosownych przypadkach).|
|**A**|Zmiennoprzecinkowych|Podpisana sześciokątna podwójna wartość zmiennoprzecinkowa, która ma formę [-]0x*h.hhhh*__p±__*dd*, gdzie *h.hhhh* są cyframi sześciokątnymi (przy użyciu dolnych liter) mantysi, a *dd* są jedną lub więcej cyfr dla wykładnika. Dokładność określa liczbę cyfr po punkcie.|
|**A**|Zmiennoprzecinkowych|Podpisana sześciokątna podwójna wartość zmiennoprzecinkowa, która ma formę [-]0X*h.hhhh*__P±__*dd*, gdzie *h.hhhh* są cyframi szesnastkowymi (przy użyciu wielkich liter) mantysi, a *dd* są jedną lub kilkoma cyframi wykładnika. Dokładność określa liczbę cyfr po punkcie.|
|**N**|Wskaźnik do liczby całkowitej|Liczba znaków, które zostały pomyślnie zapisane do tej pory do strumienia lub buforu. Ta wartość jest przechowywana w całkowitej liczby, której adres jest podany jako argument. Rozmiar liczby całkowitej wskazywalnej może być kontrolowany przez prefiks specyfikacji rozmiaru argumentu. **Specyfikator n** jest domyślnie wyłączony; informacje można znaleźć w ważnej notatce bezpieczeństwa.|
|**P**|Typ wskaźnika|Wyświetla argument jako adres w cyfrach szesnastowych.|
|**S**|Ciąg|W przypadku `printf` użycia z funkcjami określa jedno-lub wielo bajtowy ciąg znaków; gdy jest `wprintf` używany z funkcjami, określa ciąg znaków szerokoznakowych. Znaki są wyświetlane do pierwszego znaku null lub do momentu osiągnięcia wartości *precyzji.*|
|**S**|Ciąg|W przypadku `printf` użycia z funkcjami określa ciąg znaków szerokich; gdy jest `wprintf` używany z funkcjami, określa jedno-bajtowy lub wielo bajtowy ciąg znaków. Znaki są wyświetlane do pierwszego znaku null lub do momentu osiągnięcia wartości *precyzji.*|
|**Z**|`ANSI_STRING`lub `UNICODE_STRING` struktura|Gdy adres [ANSI_STRING](/windows/win32/api/ntdef/ns-ntdef-string) lub [UNICODE_STRING](/windows/win32/api/ntdef/ns-ntdef-_unicode_string) struktury jest przekazywana jako argument, wyświetla ciąg zawarty w buforze `Buffer` wskazywany przez pole struktury. Użyj prefiksu modyfikatora `UNICODE_STRING` *rozmiaru* **w,** aby określić argument , `%wZ`na przykład . Pole `Length` struktury musi być ustawione na długość, w bajtach, ciągu. Pole `MaximumLength` konstrukcji musi być ustawione na długość, w bajtach, buforu.<br /><br /> Zazwyczaj znak typu **Z** jest używany tylko w funkcjach debugowania sterowników, które używają specyfikacji konwersji, takich jak `dbgPrint` i `kdPrint`.|

Począwszy od programu Visual Studio 2015, jeśli argument odpowiadający specyfikatorowi konwersji zmiennoprzecinkowej ( a , **A**, **e**, **E**, **f**, **F**, **g**, **G**) jest nieskończony, nieokreślony lub NaN, sformatowane dane wyjściowe są zgodne ze**standardem**C99. W tej tabeli wymieniono sformatowane dane wyjściowe:

|Wartość|Dane wyjściowe|
|-----------|------------|
|Nieskończoności|`inf`|
|Cichy NaN|`nan`|
|Sygnalizacja NaN|`nan(snan)`|
|Nieokreślony NaN|`nan(ind)`|

Każda z tych wartości może być poprzedzony znakiem. Jeśli specyfikator konwersji *typu* zmiennoprzecinkowego jest wielkimi literami, dane wyjściowe są również formatowane wielkimi literami. Na przykład, jeśli specyfikator `%F` formatu `%f`jest zamiast , `INF` nieskończoność `inf`jest sformatowany jako zamiast . Funkcje `scanf` można również przeanalizować te ciągi, dzięki czemu `printf` wartości `scanf` te można zrobić w obie strony przez i funkcje.

Przed programem Visual Studio 2015 program CRT używał innego, niestandardowego formatu dla wartości danych wyjściowych nieskończonych, nieokreślonych i NaN:

|Wartość|Dane wyjściowe|
|-----------|------------|
|+ nieskończoność|`1.#INF`*cyfry losowe*|
|- nieskończoność|`-1.#INF`*cyfry losowe*|
|Nieokreślony (tak samo jak cichy NaN)|*cyfry* `.#IND` *losowe cyfry*|
|NaN|*cyfry* `.#NAN` *losowe cyfry*|

Każdy z nich mógł być poprzedzony znakiem i mógł być sformatowany nieco inaczej w zależności od szerokości i precyzji pola, czasami z nietypowymi efektami. Na przykład `printf("%.2f\n", INFINITY)` można `1.#J` wydrukować, ponieważ #INF będzie "zaokrąglone" do 2 cyfr precyzji.

> [!NOTE]
> Jeśli argument, który `%s` odpowiada `%S`lub `Buffer` , lub pole `%Z`argumentu, który odpowiada , jest wskaźnik null, "(null)" jest wyświetlany.

> [!NOTE]
> We wszystkich formatach wykładniczych minimalna liczba cyfr wykładnika do wyświetlenia wynosi dwa, używając trzech tylko wtedy, gdy jest to konieczne. Za pomocą funkcji [_set_output_format](../c-runtime-library/set-output-format.md) można ustawić liczbę cyfr wyświetlanych na trzy dla zgodności z poprzednimi kodami napisanych dla programu Visual Studio 2013 i wcześniej.

> [!IMPORTANT]
> Ponieważ `%n` format jest z natury niezabezpieczony, jest domyślnie wyłączony. Jeśli `%n` wystąpi w ciągu formatu, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametru.](../c-runtime-library/parameter-validation.md) Aby `%n` włączyć obsługę, zobacz [_set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Dyrektywy bandery

Pierwsze opcjonalne pole w specyfikacji konwersji zawiera *dyrektywy flagowe,* zero lub więcej znaków flagi określających wyjściowe uzasadnienie i kontrolę danych wyjściowych znaków, pustych pól, zer wiodących, punktów dziesiętnych oraz przedrostków ósemkowych i szesnastkowych. Więcej niż jedna dyrektywa flagi może pojawić się w specyfikacji konwersji, a znaki flagi mogą być wyświetlane w dowolnej kolejności.

### <a name="flag-characters"></a>Oznaczanie znaków

|Flaga|Znaczenie|Domyślne|
|----------|-------------|-------------|
|**-**|Wyrównanie wyniku do lewej w obrębie danej szerokości pola.|Wyrównanie do prawej.|
|**+**|Użyj znaku (+ lub -), aby prefiks wartości wyjściowej, jeśli jest typu podpisanego.|Znak jest wyświetlany tylko dla wartości podpisanych ujemnych (-).|
|**0**|Jeśli *szerokość* jest poprzedzony przez **0**, zera wiodące są dodawane do momentu osiągnięcia minimalnej szerokości. Jeśli zarówno **0,** jak i **-** pojawiają się, **0** jest ignorowana. Jeśli dla formatu liczb całkowitych określony jest **0** (**i**, **u**, **x,** **X**, `%04.d` **o**, **d)** i specyfikacja precyzji jest również dostępna — na przykład — **0** jest ignorowana. Jeśli dla formatu zmiennoprzecinkowego **a** lub **A** określono **0,** zera wiodące `0x` `0X` są dołączane do mantysi, po lub prefiksie.|Bez dopełnienie.|
|**puste** (' ')|Użyj pustego, aby prefiks wartości wyjściowej, jeśli jest podpisana i dodatnia. Puste jest ignorowane, jeśli pojawią się flagi puste i +.|Nie pojawia się puste.|
|**#**|Gdy jest używany w formacie **o**, **x** **#** lub **X,** flaga używa 0, 0x lub 0X, odpowiednio, do prefiksu dowolnej wartości wyjściowej niezerowej.|Nie pojawia się puste.|
||Gdy jest używany w formacie **e**, **E**, **f**, **#** **F**, **a**lub **A,** flaga wymusza wartość wyjściową, aby zawierała przecinek dziesiętnych.|Przecinka dziesiętna jest wyświetlana tylko wtedy, gdy są zgodne z jego danymi.|
||Gdy jest używany w formacie **g** lub **#** **G,** flaga wymusza wartość wyjściową zawierać dziesiętny punkt i zapobiega obcinaniu końcowych zer.<br /><br /> Ignorowane w przypadku użycia z **c**, **d**, **i**, **u**, lub **s**.|Przecinka dziesiętna jest wyświetlana tylko wtedy, gdy są zgodne z jego danymi. Końcowe zera są obcinane.|

<a name="width"></a>

## <a name="width-specification"></a>Specyfikacja szerokości

W specyfikacji konwersji opcjonalne pole specyfikacji szerokości jest wyświetlane po wszystkich *znakach flag.* Argument *width* jest nienajmową liczbą dziesiętną, która kontroluje minimalną liczbę znaków, które są dane wyjściowe. Jeśli liczba znaków w wartości wyjściowej jest mniejsza niż określona szerokość, puste miejsca są dodawane po lewej lub**-** prawej stronie wartości — w zależności od tego, czy określono flagę wyrównania do lewej ( ) do momentu osiągnięcia minimalnej szerokości. Jeśli *szerokość* jest poprzedzony przez 0, zera wiodące są dodawane do liczby całkowitej lub zmiennoprzecinkowych konwersji, aż do osiągnięcia minimalnej szerokości, z wyjątkiem, gdy konwersja jest nieskończoności lub NaN.

Specyfikacja szerokości nigdy nie powoduje, że wartość ma być obcięty. Jeśli liczba znaków w wartości wyjściowej jest większa niż określona szerokość lub jeśli *szerokość* nie jest podana, wszystkie znaki wartości są dane wyjściowe, z zastrzeżeniem *specyfikacji precyzji.*

Jeśli specyfikacja szerokości jest gwiazdką`*` `int` ( ), argument z listy argumentów dostarcza wartość. Argument *width* musi poprzedzać wartość sformatowaną na liście argumentów, jak pokazano w tym przykładzie:

`printf("%0*d", 5, 3);  /* 00003 is output */`

Brakujące lub małe wartości *szerokości* w specyfikacji konwersji nie powoduje obcinania wartości wyjściowej. Jeśli wynik konwersji jest szerszy niż wartość *szerokości,* pole zostanie rozwinięte, aby zawierało wynik konwersji.

<a name="precision"></a>

## <a name="precision-specification"></a>Specyfikacja precyzji

W specyfikacji konwersji trzecim opcjonalnym polem jest specyfikacja precyzji. Składa się z kropki (.), po której następuje nieujemna liczba całkowita dziesiętna, która w zależności od typu konwersji określa liczbę znaków ciągu, liczbę miejsc dziesiętnych lub liczbę cyfr znaczących, które mają być dane wyjściowe.

W przeciwieństwie do specyfikacji szerokości, specyfikacja precyzji może spowodować obcięcie wartości wyjściowej lub zaokrąglenie wartości zmiennoprzecinkowej. Jeśli *precyzja* jest określona jako 0, a wartość do konwersji wynosi 0, wynik nie jest wynikiem wyjściowym znaków, jak pokazano w tym przykładzie:

`printf( "%.0d", 0 );      /* No characters output */`

Jeśli specyfikacja precyzji jest\*gwiazdką `int` ( ), argument z listy argumentów dostarcza wartość. Na liście argumentów argument *precyzji* argument musi poprzedzać wartość, która jest sformatowana, jak pokazano w tym przykładzie:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

Znak *typu* określa interpretację *precyzji* lub domyślną precyzję po *pominięciu precyzji,* jak pokazano w poniższej tabeli.

### <a name="how-precision-values-affect-type"></a>Jak wartości precyzji wpływają na typ

|Typ|Znaczenie|Domyślne|
|----------|-------------|-------------|
|**a**, **A**|Dokładność określa liczbę cyfr po punkcie.|Domyślna precyzja to 13. Jeśli dokładność wynosi 0, nie jest drukowany **#** żaden punkt dziesiętny, chyba że używana jest flaga.|
|**c**, **C**|Precyzja nie ma wpływu.|Znak jest drukowany.|
|**d**, **i**, **o**, **u**, **x**, **X**|Dokładność określa minimalną liczbę cyfr do wydrukowania. Jeśli liczba cyfr w argumie jest mniejsza niż *dokładność,* wartość wyjściowa jest wyściełana po lewej stronie zerami. Wartość nie jest obcinana, gdy liczba cyfr przekracza *dokładność*.|Domyślna precyzja to 1.|
|**e**, **E**|Dokładność określa liczbę cyfr, które mają być drukowane po przecinku dziesiętnym. Ostatnia wydrukowana cyfra jest zaokrąglana.|Domyślna precyzja to 6. Jeśli *dokładność* wynosi 0 lub kropka (.) pojawia się bez liczby po niej, nie jest drukowany punkt dziesiętny.|
|**f**, **F**|Wartość precyzji określa liczbę cyfr po przecinku dziesiętnym. Jeśli pojawi się przecinek dziesiętny, przed nim pojawia się co najmniej jedna cyfra. Wartość jest zaokrąglana do odpowiedniej liczby cyfr.|Domyślna precyzja to 6. Jeśli *dokładność* wynosi 0 lub jeśli kropka (.) pojawia się bez liczby po niej, nie jest drukowany punkt dziesiętny.|
|**g**, **G**|Dokładność określa maksymalną liczbę drukowanych cyfr znaczących.|Wydrukowano sześć cyfr znaczących, a wszystkie końcowe zera zostaną obcięty.|
|**s**, **S**|Dokładność określa maksymalną liczbę znaków do wydrukowania. Znaki przekraczające *precyzję* nie są drukowane.|Znaki są drukowane do momentu napotkania znaku zerowego.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Specyfikacja rozmiaru argumentu

W specyfikacji konwersji pole *rozmiaru* jest modyfikatorem długości argumentu dla specyfikatora konwersji *typu.* Prefiksy pola *rozmiaru* do pola *typu:* **hh**, **h**, **j**, **l** (małe litery L), **L**, **ll**, **t**, **w**, **z**, **I** (wielkie litery i), **I32**i **I64**— określają "rozmiar" odpowiedniego argumentu — długi lub krótki, 32-bitowy lub 64-bitowy, jednobędowy lub szeroki znak — w zależności od specyfikatora konwersji, który modyfikują. Te prefiksy rozmiaru są używane `printf` `wprintf` ze znakami *typu* w i rodzin funkcji, aby określić interpretację rozmiarów argumentów, jak pokazano w poniższej tabeli. Pole *rozmiaru* jest opcjonalne dla niektórych typów argumentów. Jeśli prefiks rozmiaru nie jest określony, formater zużywa argumenty całkowite — `char`na `short` `int`przykład `long`podpisane lub niepodpisane , , `int` i `float`typy wyliczenia — jako typy 32-bitowe i , `double`a `long double` argumenty zmiennoprzecinkowe są używane jako typy 64-bitowe. `double` To zachowanie jest zgodne z domyślnymi regułami promocji argumentów dla list argumentów zmiennych. Aby uzyskać więcej informacji na temat promocji argumentów, zobacz Wielokropek i Argumenty domyślne w [wyrażeniach Postfix](../cpp/postfix-expressions.md). Zarówno w systemach 32-bitowych, jak i 64-bitowych specyfikacja konwersji 64-bitowego argumentu liczby całkowitej musi zawierać prefiks rozmiaru **ll** lub **I64**. W przeciwnym razie zachowanie formatera jest niezdefiniowane.

Niektóre typy są różne rozmiary w kodzie 32-bitowym i 64-bitowym. Na przykład `size_t` jest 32 bitów długości w kodzie skompilowanym dla x86 i 64 bitów w kodzie skompilowany dla x64. Aby utworzyć kod formatowania niezależnego od platformy dla typów o zmiennej szerokości, można użyć modyfikatora rozmiaru argumentu o zmiennej szerokości. Alternatywnie należy użyć modyfikatora rozmiaru argumentu 64-bitowego i jawnie podwyższyć wartość typu argumentu o zmiennej szerokości do 64 bitów. Modyfikator rozmiaru argumentu **I** (wielkie litery i) specyficzny dla firmy Microsoft obsługuje argumenty całkowite o zmiennej szerokości, ale zaleca się modyfikatory **j,** **t**i z specyficzne dla typu, i **z.** dla przenośności.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Prefiksy rozmiaru dla printf i wprintf Format-Type Specifiers

|Aby określić|Używanie prefiksu|Ze specyfikatorem typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`short int`<br />`short unsigned int`|**H**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`intmax_t`<br />`uintmax_t`|**j** lub **I64**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`long double`|**l** (małe litery L) lub **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g**lub **G**|
|`long int`<br />`long unsigned int`|**l** (małe litery L)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`long long int`<br />`unsigned long long int`|**ll** (małe litery LL)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`ptrdiff_t`|**t** lub **I** (wielkie litery i)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`size_t`|**z** lub **I** (wielkie litery i)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|Znak jedno bajtowy|**H**|**c** lub **C**|
|Szeroki znak|**l** (małe litery L) lub **w**|**c** lub **C**|
|Jedno bajtowy ciąg znaków|**H**|**s**, **S**, lub **Z**|
|Ciąg znaków szerokoznakowych|**l** (małe litery L) lub **w**|**s**, **S**, lub **Z**|

`ptrdiff_t` Typy `size_t` i `__int32` `unsigned __int32` są na platformach 32-bitowych i lub `__int64` `unsigned __int64` na platformach 64-bitowych. Prefiksy **I** (wielkie litery i), **j**, **t**i **z** rozmiar przyjmują prawidłową szerokość argumentu dla platformy.

W języku Visual C++, chociaż `long double` jest to odrębny `double`typ, ma taką samą reprezentację wewnętrzną jak .

Specyfikator typu **hc** lub **hC** jest synonimem **funkcji c** w `printf` funkcjach i funkcji **C.** `wprintf` Specyfikator typu **lc**, **lC**, **wc**lub **wC** `printf` jest synonimem funkcji **C** w funkcjach i z funkcjami **c.** `wprintf` Specyfikator typu **hs** lub **hS** jest synonimem **funkcji s** i `printf` **funkcji S.** `wprintf` Specyfikator typu **ls**, **lS**, **ws** lub **wS** jest synonimem `wprintf` funkcji **S** w `printf` funkcjach i **funkcjach s.**

> [!NOTE]
> **Specyficzne dla firmy Microsoft:** I **(wielkie** litery i), **I32**, **I64**i **w** argument size modyfikujące prefiksy są rozszerzeniami firmy Microsoft i nie są zgodne z ISO C. Prefiks **h,** gdy jest używany `char` z danymi typu i **l** (małe litery L) prefiks, gdy jest używany z danymi typu `double` są rozszerzenia firmy Microsoft.

## <a name="see-also"></a>Zobacz też

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[printf_p parametry pozycyjne](../c-runtime-library/printf-p-positional-parameters.md)
