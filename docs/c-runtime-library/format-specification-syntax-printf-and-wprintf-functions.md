---
title: 'Składnia specyfikacji formatu: funkcje printf i wprintf | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfb885a5d29c26f4a40d5b93490a06652eff1ffc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216675"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Składnia specyfikacji formatu: funkcje printf i wprintf

Różne `printf` i `wprintf` funkcje ciągu formatu i argumentów opcjonalnych i tworzące sformatowana sekwencja znaków danych wyjściowych. Ciąg formatu zawiera zero lub więcej *dyrektywy*, które są albo znaków literałowych, dane wyjściowe lub zakodowane *specyfikacji konwersji* opisujące sposób formatowania argumentów w danych wyjściowych. W tym temacie opisano składnię wykorzystywaną do zakodowania specyfikacji konwersji w ciągu formatu. Aby uzyskać listę tych funkcji, zobacz [Stream operacji We/Wy](../c-runtime-library/stream-i-o.md).

Specyfikacja konwersji składa się z pól opcjonalnych i wymaganych w tym formularzu:

**%**[[*flagi*](#flags)] [[*szerokość*](#width)] [.[ *dokładności*](#precision)] [[*rozmiar*](#size)][*typu*](#type)

Każde pole specyfikacji konwersji jest znakiem lub liczbą, która oznacza specyfikator opcji lub konwersja określonego formatu. Wymagane *typu* pola określa rodzaj konwersji, która ma być stosowana do argumentu. Opcjonalny *flagi*, *szerokość*, i *dokładności* pól kontrolują dodatkowe aspekty formatu takie jak spacje lub zer, uzasadnienie i wyświetlane dokładności. *Rozmiar* pola określa rozmiar argumentu używane i przekonwertowane.

Specyfikacja konwersji podstawowego zawiera tylko znak procentu i *typu* znaków. Na przykład `%s` określa konwersję na ciąg tekstowy. Aby znak procentu był wyświetlany, należy użyć składni `%%`. Jeśli znak procentu następuje znak, który nie ma znaczenia jako pole formatu, zostanie wywołana procedura obsługi nieprawidłowego parametru. Aby uzyskać więcej informacji, zobacz [Parameter Validation](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Dla bezpieczeństwa i stabilności upewnij się, tej specyfikacji konwersji ciągów są nie zdefiniowane przez użytkownika. Rozważmy na przykład program, który monituje użytkownika o wprowadzenie nazwy, a dane wejściowe przechowuje w zmiennej o nazwie `user_name` będącej ciągiem tekstowym. W celu wyświetlenia wartości zmiennej `user_name` nie należy robić tak:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Zamiast tego należy zrobić tak:
>
> `printf( "%s", user_name );`

<a name="type"></a>

## <a name="type-conversion-specifier"></a>Specyfikator konwersji typu

*Typu* znak specyfikatora konwersji Określa, czy należy interpretować odnośnego argumentu jako znak, ciąg, wskaźnikiem, liczbą całkowitą lub liczba zmiennoprzecinkowa. *Typu* znak jest tylko konwersji wymagane pole specyfikacji i wydaje się po dowolne pola opcjonalne.

Argumenty, które należy wykonać w ciągu formatu są interpretowane zgodnie z odpowiednich *typu* znak i opcjonalną [rozmiar](#size) prefiks. Konwersje dla typów znakowych `char` i `wchar_t` określone za pomocą **c** lub **C**, i ciągów znaków jednobajtowych i wielobajtowych lub znak dwubajtowy są określane za pomocą **s** lub **S**, w zależności od funkcji formatowania jest używany. Znakowe i argumenty, które są określone za pomocą **c** i **s** są interpretowane jako `char` i `char*` przez `printf` rodziny funkcji lub jako `wchar_t` i `wchar_t*` przez `wprintf` rodziny funkcji. Znakowe i argumenty, które są określone za pomocą **C** i **S** są interpretowane jako `wchar_t` i `wchar_t*` przez `printf` rodziny funkcji lub jako `char` i `char*` przez `wprintf` rodziny funkcji. To zachowanie jest specyficzne dla firmy Microsoft.

Liczba całkowita typów, takich jak `short`, `int`, `long`, `long long`i ich `unsigned` wariantów, są określane za pomocą **d**, **i**, **o**, **u**, **x**, i **X**. Zmiennoprzecinkowe takich jak typy `float`, `double`, i `long double`, są określane przy użyciu **a**, **A**, **e**, **E**, **f**, **F**, **g**, i **G**. Domyślnie chyba że zostaną one zmienione przez *rozmiar* prefiksu, argumenty liczby całkowitej są zmuszone do `int` typu i argumenty zmiennoprzecinkowe są zmuszone do `double`. W systemach 64-bitowych `int` jest 32-bitową wartością; w związku z tym, 64-bitowe liczby całkowite zostanie obcięta podczas formatowania danych wyjściowych chyba że *rozmiar* prefiks **ll** lub **I64**jest używany. Typy wskaźników, które są określone przez **p** użyć domyślnego rozmiaru wskaźnika platformy.

> [!NOTE]
> **Microsoft Specific**  
> **Z** wpisz znak i zachowanie **c**, **C**, **s**, i **S** typ znaków, kiedy ich są używane wraz z `printf` i `wprintf` funkcje, są rozszerzeniami Microsoft. Standard ISO C używa **c** i **s** spójnie na wąski znaków i ciągów, i **C** i **S** dla znaków dwubajtowych i ciągów, w wszystkie funkcje formatowania.

### <a name="type-field-characters"></a>Znaki pola typu

|Znak typu|Argument|Format danych wyjściowych|
|--------------------|--------------|-------------------|
|**c**|Znak|Gdy jest używane z `printf` funkcje, określa znak Jednobajtowy; w przypadku użycia z `wprintf` funkcje, określa znak dwubajtowy.|
|**C**|Znak|Gdy jest używane z `printf` funkcje, określa znaków dwubajtowych; w przypadku korzystania z `wprintf` funkcje, określa znaków jednobajtowych.|
|**d**|Liczba całkowita|Oznaczona dziesiętna liczba całkowita.|
|**i**|Liczba całkowita|Oznaczona dziesiętna liczba całkowita.|
|**o**|Liczba całkowita|Nieoznaczona ósemkowa liczba całkowita.|
|**u**|Liczba całkowita|Nieoznaczona dziesiętna liczba całkowita.|
|**x**|Liczba całkowita|Szesnastkowa liczba całkowita bez znaku; używa "abcdef".|
|**X**|Liczba całkowita|Szesnastkowa liczba całkowita bez znaku; zastosowań "ABCDEF".|
|**e**|Zmiennoprzecinkowe|Wartość, która ma postać [-] podpisane*d.dddd*__e±__*dd*[*d*] gdzie *d* jedną cyfrę dziesiętną, jest *dddd* jest jeden lub więcej cyfr dziesiętnych w zależności od określonej dokładności lub sześć domyślnie i *dd*[*d*] jest dwa lub trzy cyfry dziesiętne, w zależności od [format danych wyjściowych](../c-runtime-library/set-output-format.md) i rozmiar wykładnik potęgi.|
|**E**|Zmiennoprzecinkowe|Taka sama jak **e** formatowania, chyba że **E** zamiast **e** wprowadza wykładnik potęgi.|
|**f**|Zmiennoprzecinkowe|Wartość, która ma postać [-] podpisane*dddd*__.__ *dddd*, gdzie *dddd* jest jedna lub więcej cyfr dziesiętnych. Liczba cyfr przed przecinkiem dziesiętnym zależy od wielkości liczbę oraz liczbę cyfr po punkcie dziesiętnym zależy od żądanej dokładności lub sześć domyślnie.|
|**F**|Zmiennoprzecinkowe|Taka sama jak **f** formatowania, poza tym, że dane wyjściowe nieskończoności i nan jest wielką literą.|
|**g**|Zmiennoprzecinkowe|Podpisany wartości są wyświetlane w **f** lub **e** formatowania, która kwota jest bardziej zwarty dla danej wartości i dokładność. **e** format jest używany tylko wtedy, gdy wykładnik wartość jest mniejsza niż -4 lub większa niż lub równa *dokładności* argumentu. Zera końcowe są obcinane i punktu dziesiętnego, jest wyświetlana tylko wtedy, gdy jeden lub więcej cyfr po nim.|
|**G**|Zmiennoprzecinkowe|Taka sama jak **g** formatowania, chyba że **E**, zamiast **e**, wprowadza wykładnik (tam, gdzie jest odpowiedni).|
|**a**|Zmiennoprzecinkowe|Podpisana szesnastkowa wartość zmiennoprzecinkową podwójnej precyzji, która ma postać [-] 0 x*h.hhhh*__p±__*dd*, gdzie *h.hhhh* są szesnastkowy cyfry (przy użyciu małych liter) mantysy i *dd* są jedną lub więcej cyfr wykładnika potęgi. Dokładność określa liczbę cyfr po punkcie.|
|**A**|Zmiennoprzecinkowe|Podpisana szesnastkowa wartość zmiennoprzecinkową podwójnej precyzji, która ma postać [-] 0 X*h.hhhh*__P±__*dd*, gdzie *h.hhhh* są szesnastkowy cyfry (przy użyciu wielkich liter) mantysy i *dd* są jedną lub więcej cyfr wykładnika potęgi. Dokładność określa liczbę cyfr po punkcie.|
|**N**|Wskaźnik do liczby całkowitej.|Liczba znaków, które są pomyślnie zapisywane do tej pory strumienia lub buforu. Ta wartość jest przechowywana w liczbę całkowitą, której adres jest podawana jako argument. Rozmiar liczby całkowitej wskazywany mogą być kontrolowane przez prefiks specyfikacji argumentu rozmiaru. **n** specyfikator jest domyślnie wyłączona; informacji, zobacz uwagę ważne zabezpieczeń.|
|**p**|Typ wskaźnika|Wyświetla argument jako adresu cyfr szesnastkowych.|
|**s**|String|Gdy jest używane z `printf` funkcje, określa ciąg znaków jednobajtowych lub wielobajtowych; w przypadku korzystania z `wprintf` funkcje, określa ciąg znaków dwubajtowych. Znaki są wyświetlane do pierwszego znaku null, lub do momentu *dokładności* osiągnięta wartość.|
|**S**|String|Gdy jest używane z `printf` funkcje, określa ciąg znaków dwubajtowych; w przypadku korzystania z `wprintf` funkcje, określa ciąg znaków jednobajtowych lub wielobajtowego. Znaki są wyświetlane do pierwszego znaku null, lub do momentu *dokładności* osiągnięta wartość.|
|**Z**|`ANSI_STRING` lub `UNICODE_STRING` struktury|Jeśli adres [ANSI_STRING](/windows/desktop/api/ntdef/ns-ntdef-_string) lub [UNICODE_STRING](https://msdn.microsoft.com/library/windows/hardware/ff564879.aspx) struktury jest przekazywany jako argument, wyświetla ciąg znajdujący się w buforze wskazywany przez `Buffer` pola struktury. Użyj *rozmiar* prefiks modyfikator **w** do określenia `UNICODE_STRING` argument — na przykład `%wZ`. `Length` Pola struktury musi być równa długości w bajtach, ciąg. `MaximumLength` Pola struktury musi być równa długości w bajtach rozmiar buforu.<br /><br /> Zazwyczaj **Z** znaku typu jest używany tylko w debugowanie funkcji używających specyfikacja konwersji, takie jak sterownik `dbgPrint` i `kdPrint`.|

W programie Visual Studio 2015, jeśli argument, który odpowiada specyfikatorowi konwersji liczb zmiennoprzecinkowych (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) jest nieskończone nieokreślony, lub NaN, sformatowane wyniki zgodne ze standardem C99. Poniższa tabela zawiera listę sformatowane wyniki:

|Wartość|Dane wyjściowe|
|-----------|------------|
|nieskończoności|`inf`|
|Ciche NaN|`nan`|
|Sygnalizacji NaN|`nan(snan)`|
|Nieokreślony NaN|`nan(ind)`|

Dowolne z tych wartości może być poprzedzony znakiem. W przypadku liczb zmiennoprzecinkowych *typu* znak specyfikatora konwersji jest dużą literą, a następnie dane wyjściowe jest sformatowany także wielkimi literami. Na przykład, jeśli specyfikatorem formatu jest `%F` zamiast `%f`, nieskończoność jest w formacie `INF` zamiast `inf`. `scanf` Funkcje również mogą analizować tych ciągów, dzięki czemu te wartości mogą podejmować przesłania danych za pośrednictwem `printf` i `scanf` funkcji.

Przed Visual Studio 2015 CRT używać innego formatu niestandardowego dla danych wyjściowych nieskończone nieokreślony i wartości NaN:

|Wartość|Dane wyjściowe|
|-----------|------------|
|+ infinity|`1.#INF` *losowe cyfry*|
|-nieskończoność|`-1.#INF` *losowe cyfry*|
|Nieskończona (tak jak cichych NaN)|*cyfra* `.#IND` *losowe cyfry*|
|NaN|*cyfra* `.#NAN` *losowe cyfry*|

Żadnego z tych może być poprzedzona znakiem i mogła zostać sformatowana nieco inaczej w zależności od szerokość pola i dokładności, czasami z nietypowej efekty. Na przykład `printf("%.2f\n", INFINITY)` przetwarzającej `1.#J` ponieważ #INF będzie "zaokrąglony" dokładności 2 cyfry.

> [!NOTE]
> Jeśli argument, który odpowiada `%s` lub `%S`, lub `Buffer` argument, który odnosi się do pola `%Z`, jest pustym wskaźnikiem, "(null)" jest wyświetlana.

> [!NOTE]
> We wszystkich formatach wykładniczego minimalną liczbę cyfr wykładnika, aby wyświetlić jest dwóch, przy użyciu trzech tylko wtedy, gdy jest to konieczne. Za pomocą [_set_output_format —](../c-runtime-library/set-output-format.md) funkcji, można ustawić liczbę cyfr wyświetlanych do trzech zgodności z poprzednimi wersjami przy użyciu kodu napisanego dla programu Visual Studio 2013 i przed.

> [!IMPORTANT]
> Ponieważ `%n` format jest z założenia niezabezpieczone, jest domyślnie wyłączona. Jeśli `%n` występuje w ciągu formatu, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../c-runtime-library/parameter-validation.md). Aby włączyć `%n` obsługi, zobacz [_set_printf_count_output —](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Dyrektywy flagowania

Pierwsze pole opcjonalne w specyfikacji konwersji zawiera *Flaga dyrektywy*, zero lub więcej znaków, które określają uzasadnienie danych wyjściowych i kontrolować dane wyjściowe z znaków, spacji, zer wiodących, separatorów dziesiętnych, ósemkowym i Flaga i prefiksów szesnastkowych. Więcej niż jedna dyrektywa flagi może pojawić się w specyfikacji konwersji i znaki flagi mogą występować w dowolnej kolejności.

### <a name="flag-characters"></a>Flaga znaków

|Flaga|Znaczenie|Domyślny|
|----------|-------------|-------------|
|**-**|Wyrównaj do lewej wynik do szerokości pola.|Wyrównaj do prawej.|
|**+**|Użyj znaku (+ lub -) jako prefiks wartości wyjściowych, jeśli jest on typ ze znakiem.|Znak pojawia się tylko dla wartości ujemnych podpisem (-).|
|**0**|Jeśli *szerokość* jest poprzedzony **0**, wiodące zera są dodawane, aż do osiągnięcia minimalnej szerokości. Jeśli oba **0** i **-** są wyświetlane, **0** jest ignorowana. Jeśli **0** określono format liczby całkowitej (**i**, **u**, **x**, **X**, **o**, **d**), a także występuje Specyfikacja dokładności — na przykład `%04.d`— **0** jest ignorowana. Jeśli **0** określono **a** lub **A** format liczb zmiennoprzecinkowych zera wiodące jest dołączany na początku mantysa, po `0x` lub `0X` prefiks.|Dopełnienie.|
|**puste** ("")|Użyj pustego jako prefiks wartości wyjściowych, jeśli jest podpisem, jak i dodatnie. Pustą jest ignorowana, jeśli obie pustą i + flagi są wyświetlane.|Pojawi się puste.|
|**#**|Gdy jest używany z **o**, **x**, lub **X** formacie **#** Flaga używa 0, 0 x "lub" 0 X odpowiednio do prefiksu, każda wartość różną od zera wartość danych wyjściowych.|Pojawi się puste.|
||Gdy jest używana z **e**, **E**, **f**, **F**, **a** lub **A** Format, **#** flaga wymusza wartość wyjściowa zawiera separatorem dziesiętnym.|Punkt dziesiętny pojawia się tylko wtedy, gdy cyfr po nim.|
||Gdy jest używany z **g** lub **G** formacie **#** flaga wymusza wartość wyjściowa ma zawierać przecinek dziesiętny i zapobiega obcinaniu końcowe zera.<br /><br /> Ignorowane, gdy jest używane z **c**, **d**, **i**, **u**, lub **s**.|Punkt dziesiętny pojawia się tylko wtedy, gdy cyfr po nim. Końcowe zera zostaną obcięte.|

<a name="width"></a>

## <a name="width-specification"></a>Specyfikacje szerokości

W specyfikacji konwersji, pole specyfikacji szerokości opcjonalne pojawia się po każdym *flagi* znaków. *Szerokość* argument jest ujemna dziesiętna liczba całkowita, która określa minimalną liczbę znaków, które są danymi wyjściowymi. Liczba znaków w wartości danych wyjściowych jest mniejsza niż określona szerokość, spacje są dodawane do lewej lub prawej wartości — w zależności od tego, czy Flaga wyrównania po lewej stronie (**-**) jest określony, aż do minimum Szerokość zostanie osiągnięty. Jeśli *szerokość* jest poprzedzony przez 0, zera wiodące są dodawane do liczby całkowitej lub zmiennoprzecinkowej konwersje aż do osiągnięcia minimalnej szerokości, z wyjątkiem sytuacji, gdy konwersja jest infinity lub NaN.

Specyfikacje szerokości nigdy nie powoduje, że wartość do skrócenia. Jeśli liczba znaków w wartości danych wyjściowych jest większy niż określona szerokość lub *szerokość* jest nie jest podany, wszystkie znaki wartości są dane wyjściowe, podlegają *dokładności* specyfikacji.

Jeśli specyfikacja szerokości jest znak gwiazdki (`*`), `int` argumentu z listy argumentów dostarcza wartość. *Szerokość* argumentu musi poprzedzać wartość, która jest formatowana na liście argumentów, jak pokazano w poniższym przykładzie:

`printf("%0*f", 5, 3);  /* 00003 is output */`

Brak lub małych *szerokość* wartość w specyfikacji konwersji nie powoduje obcięcie wartości danych wyjściowych. Jeśli wynik konwersji jest szerszy niż *szerokość* wartość pola jest rozszerzany, aby zawierać wynik konwersji.

<a name="precision"></a>

## <a name="precision-specification"></a>Specyfikacja dokładności

W specyfikacji konwersji trzecie pole opcjonalne jest specyfikacja dokładności. Składa się z kropki (.), następuje nieujemną dziesiętną liczbą całkowitą, w zależności od typu konwersji, określa liczbę znaków w ciągu, liczbę miejsc dziesiętnych lub liczbę cyfr znaczących, jako dane wyjściowe.

W odróżnieniu od Specyfikacja szerokości Specyfikacja dokładności może spowodować obcięcie wartości wyjściowych albo zaokrąglania liczb zmiennoprzecinkowych. Jeśli *dokładności* jest określony jako 0 i wartość do przekonwertowania wynosi 0, wynik jest Brak danych wyjściowych znaków, jak pokazano w poniższym przykładzie:

`printf( "%.0d", 0 );      /* No characters output */`

Jeśli specyfikacja dokładności jest znak gwiazdki (\*), `int` argumentu z listy argumentów dostarcza wartość. Na liście argumentów *dokładności* argumentu musi poprzedzać wartość, która jest formatowana, jak pokazano w poniższym przykładzie:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

*Typu* znak określa albo interpretacji *dokładności* lub domyślna dokładność podczas *dokładności* zostanie pominięty, jak pokazano w poniższej tabeli.

### <a name="how-precision-values-affect-type"></a>Jak wartości dokładności wpływają na typ

|Typ|Znaczenie|Domyślny|
|----------|-------------|-------------|
|**a**, **A**|Dokładność określa liczbę cyfr po punkcie.|Domyślna dokładność jest 13. Jeśli dokładności jest równa 0, drukowany jest nie przecinka dziesiętnego, chyba że **#** flaga jest używana.|
|**c**, **C**|Precyzja nie ma znaczenia.|Znak jest drukowany.|
|**d**, **i**, **o**, **u**, **x**, **X**|Dokładność określa minimalną liczbę cyfr, które ma zostać wydrukowany. Jeśli liczba cyfr w argumencie jest mniejsza niż *dokładności*, wartość wyjściowa jest uzupełniana zerami z lewej. Wartość nie jest obcięty, gdy przekracza liczbę cyfr *dokładności*.|Domyślna dokładność jest 1.|
|**e**, **E**|Dokładność określa liczbę cyfr, które mają być drukowane po punkcie dziesiętnym. Ostatnia cyfra drukowanych jest zaokrąglana.|Dokładność domyślna to 6. Jeśli *dokładności* ma wartość 0 lub kropki (.), który pojawia się bez numer, nie przecinka dziesiętnego, wydrukowaniu.|
|**f**, **F**|Wartość dokładności określa liczbę cyfr po punkcie dziesiętnym. Jeśli pojawi się separator dziesiętny, co najmniej jedną cyfrę pojawia się przed nią. Wartość jest zaokrąglana do odpowiedniej liczby cyfr.|Dokładność domyślna to 6. Jeśli *dokładności* jest równa 0 lub jeśli bez numer, pojawi się kropki (.), wydrukowaniu nie przecinka dziesiętnego.|
|**g**, **G**|Dokładność określa maksymalną liczbę cyfr znaczących wydrukowany.|Sześć cyfr znaczących, wydrukowaniu i dowolne zera końcowe są obcinane.|
|**s**, **S**|Dokładność określa maksymalną liczbę znaków, które mają być drukowane. Znaki nadwyżki *dokładności* nie są drukowane.|Znaki są drukowane, dopóki nie zostanie osiągnięty znaku null.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Specyfikacja rozmiaru argumentu

W specyfikacji konwersji *rozmiar* pole jest modyfikatorem długości argumentu dla *typu* specyfikatora konwersji. *Rozmiar* prefiksy pola do *typu* pola —**hh**, **h**, **"j"**, **l** (mała litera L) **L**, **ll**, **t**, **w**, **z**, **I**(wielkie litery i), **I32**, i **I64**— określ "rozmiar" odpowiedni argument — długi lub krótki, 32-bitowych i 64-bitowy, znaków jednobajtowych lub znaków dwubajtowych — w zależności od specyfikatora konwersji, który modyfikuje. Te prefiksy rozmiarów są używane wraz z *typu* znaki w `printf` i `wprintf` rodzin i funkcji do określenia interpretacji rozmiarów argumentu, jak pokazano w poniższej tabeli. *Rozmiar* pole jest opcjonalne w przypadku niektórych typów argumentów. Gdy żaden prefiks rozmiaru jest określony, program formatujący używa argumenty liczby całkowitej — na przykład podpisane lub niepodpisane `char`, `short`, `int`, `long`oraz typy wyliczeniowe — jako 32-bitowa `int` typów i `float`, `double`, i `long double` argumenty zmiennoprzecinkowe są używane jako 64-bitowa `double` typów. To jest zgodny z regułami podwyższania poziomu argument domyślny, do listy zmiennych argumentów. Aby uzyskać więcej informacji na temat podwyższania poziomu argumentu Zobacz wielokropki i argumenty domyślne w [wyrażenia przyrostków](../cpp/postfix-expressions.md). W systemach 32-bitowych i 64-bitowych, specyfikacja konwersji argumentu 64-bitowa liczba całkowita musi zawierać prefiks rozmiaru **ll** lub **I64**. W przeciwnym razie program formatujący zachowanie jest niezdefiniowane.

Niektóre typy są różne rozmiary w 32-bitowych i 64-bitowego kodu. Na przykład `size_t` jest 32-bitowy długo w kodzie skompilowanym x86 i 64-bitowy w kodzie skompilowanym x64. Aby utworzyć kod formatowania niezależne od platformy, dla typów o zmiennej szerokości, można użyć modyfikatora rozmiar argumentów o zmiennej szerokości. Alternatywnie użyj modyfikatora rozmiar 64-bitowy argument i jawnie podwyższanie poziomu typ argumentu zmiennej szerokości na 64-bitowy. Specyficzne dla firmy Microsoft **I** (wielkie litery i) rozmiar argumentów, modyfikator obsługuje argumenty liczby całkowitej zmiennej szerokości, ale zalecamy określonego typu **"j"**, **t**i **z** Modyfikatory przenośności.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Rozmiar prefiksów dla printf i wprintf specyfikatorów typ formatu

|Aby określić|Użyj prefiksu|Ze specyfikatorem typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`short int`<br />`short unsigned int`|**h**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`intmax_t`<br />`uintmax_t`|**"j"** lub **I64**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`long double`|**l** (mała litera L) lub **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g**, lub **G**|
|`long int`<br />`long unsigned int`|**l** (mała litera L)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`long long int`<br />`unsigned long long int`|**LL** (mała litera LL)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`ptrdiff_t`|**t** lub **I** (wielkie litery i)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`size_t`|**z** lub **I** (wielkie litery i)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|Znak jednobajtowy|**h**|**c** lub **C**|
|znak dwubajtowy|**l** (mała litera L) lub **w**|**c** lub **C**|
|Ciąg znaków jednobajtowych|**h**|**s**, **S**, lub **Z**|
|Ciąg znaków dwubajtowych|**l** (mała litera L) lub **w**|**s**, **S**, lub **Z**|

`ptrdiff_t` i `size_t` typy są `__int32` lub `unsigned __int32` na platformach 32-bitowych i `__int64` lub `unsigned __int64` na platformach 64-bitowych. **I** (wielkie litery i), **"j"**, **t**, i **z** prefiksy rozmiarów zająć szerokość poprawny argument dla platformy.

W programie Visual C++ mimo że `long double` jest typ samodzielnym, ma taką samą reprezentację wewnętrzną jak `double`.

**Hc** lub **hC** Specyfikator typu jest synonimem **c** w `printf` funkcje i **C** w `wprintf` funkcji. **Lc**, **lC**, **wc** lub **wC** Specyfikator typu jest synonimem **C** w `printf` Funkcje i **c** w `wprintf` funkcji. **Hs** lub **hS** Specyfikator typu jest synonimem **s** w `printf` funkcje i **S** w `wprintf` funkcji. **Ls**, **lS**, **ws** lub **wS** Specyfikator typu jest synonimem **S** w `printf` Funkcje i **s** w `wprintf` funkcji.

> [!NOTE]
> **Microsoft Specific**  
> **I** (wielkie litery i), **I32**, **I64**, i **w** argumentu rozmiaru modyfikatora prefiksów to rozszerzenia Microsoft i nie są zgodne z ISO C. **h** prefiksu, gdy jest używany z danymi typu `char` i **l** (mała litera L) prefiksu, gdy jest używany z danymi typu `double` są rozszerzeniami Microsoft.

## <a name="see-also"></a>Zobacz też

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)  
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)  
[printf_p Parametry pozycyjne](../c-runtime-library/printf-p-positional-parameters.md)  