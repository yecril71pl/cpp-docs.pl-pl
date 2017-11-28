---
title: "Składnia specyfikacji formatu: funkcje printf i wprintf | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e8c81bfa9f87d9612d989cef84ddf538ff28d98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Składnia specyfikacji formatu: funkcje printf i wprintf

Różnych `printf` i `wprintf` funkcje ciągu formatu i argumentów opcjonalnych i tworzące sformatowana sekwencja znaków dla danych wyjściowych. Ciąg formatu zawiera zero lub więcej *dyrektywy*, które są albo znaki wyjścia lub zakodowanym *konwersji* opisują sposób formatowania argumentu w danych wyjściowych. W tym temacie opisano składnię używany do kodowania specyfikacje konwersji w ciągu formatu. Aby uzyskać listę tych funkcji, zobacz [we/wy strumienia](../c-runtime-library/stream-i-o.md).

Specyfikacja konwersji składa się z opcjonalne i wymagane pola w tym formularzu:

**%**[[*flagi*](#flags)] [[*szerokość*](#width)] [.[ *dokładności*](#precision)] [[*rozmiar*](#size)][*typu*](#type)

Każde pole specyfikacji konwersja jest znak lub liczba oznacza, że specyfikator opcji lub konwersja określonego formatu. Wymagane *typu* pole określa rodzaj konwersji ma zostać zastosowany do argumentu. Opcjonalny *flagi*, *szerokość*, i *dokładności* pola kontrolować format dodatkowe aspekty takich jak spacje początkowe lub zera, uzasadnienie i dokładność wyświetlane. *Rozmiar* pole określa rozmiar argumentu używane i przekonwertowane.

Specyfikacja konwersji podstawowa zawiera znak procentu i *typu* znaków. Na przykład `%s` określa Konwersja ciągu. Aby znak procentu był wyświetlany, należy użyć składni `%%`. Jeśli znak procentu następuje znak, który nie ma znaczenia jako pole format, program obsługi nieprawidłowych parametrów jest wywoływany. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Zabezpieczeń i stabilności upewnij się, że specyfikacji konwersji, który ciągi są nie zdefiniowane przez użytkownika. Rozważmy na przykład program, który monituje użytkownika o wprowadzenie nazwy, a dane wejściowe przechowuje w zmiennej o nazwie `user_name` będącej ciągiem tekstowym. W celu wyświetlenia wartości zmiennej `user_name` nie należy robić tak:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Zamiast tego należy zrobić tak:
>
> `printf( "%s", user_name );`

<a name="type"></a>

## <a name="type-conversion-specifier"></a>Specyfikator konwersji typu

*Typu* znak specyfikatora konwersji Określa, czy interpretować odpowiadającego mu argumentu jako znak, ciąg, wskaźnik, liczbą całkowitą lub liczba zmiennoprzecinkowa. *Typu* pole specyfikacji tylko konwersji wymagana jest znak i wydaje się po dowolne pola opcjonalne.

Argumenty, które należy wykonać ciąg formatu interpretowania zgodnie z odpowiadającego *typu* znaków oraz opcjonalny [rozmiar](#size) prefiks. Konwersje typów znakowych `char` i `wchar_t` są określane przy użyciu **c** lub **C**, i ciągów jednobajtowe i wielobajtowe lub wielu znaków są określane przy użyciu **s** lub **S**, w zależności od używanego formatowania funkcji. Argumenty znaków i ciąg, które są określane przy użyciu **c** i **s** będą interpretowane jako `char` i `char*` przez `printf` rodziny funkcji, lub jako `wchar_t` i `wchar_t*` przez `wprintf` rodziny funkcji. Argumenty znaków i ciąg, które są określane przy użyciu **C** i **S** będą interpretowane jako `wchar_t` i `wchar_t*` przez `printf` rodziny funkcji, lub jako `char` i `char*` przez `wprintf` rodziny funkcji. To zachowanie jest określonych firmy Microsoft.

Liczba całkowita typów, takie jak `short`, `int`, `long`, `long long`i ich `unsigned` wariantów, są określane przy użyciu **d**, **i**, **o**, **u**, **x**, i **X**. Zmiennoprzecinkowe takich jak typy `float`, `double`, i `long double`, są określane przy użyciu **a**, **A**, **e**, **E**, **f**, **F**, **g**, i **G**. Domyślnie chyba że zostaną one zmienione przez *rozmiar* prefiksu, liczba całkowita argumenty są przekształcić `int` typu i argumentów zmiennoprzecinkowe są przekształcone na `double`. W systemach 64-bitowych `int` jest 32-bitową wartość; w związku z tym zostanie obcięta 64-bitowych liczb całkowitych, gdy są one formatowane dla danych wyjściowych, chyba że *rozmiar* prefiks **ll** lub **komputerach 64**jest używany. Typy wskaźnika, które są określone przez **p** Użyj domyślnego rozmiaru wskaźnika dla platformy.

> [!NOTE]
> **Dotyczące firmy Microsoft**  
> **Z** wpisz znak i zachowanie **c**, **C**, **s**, i **S** typu znaków podczas ich są używane z `printf` i `wprintf` funkcje są rozszerzenia Microsoft. Standard języka ISO C używa **c** i **s** spójnie dla wąskie znaków i ciągi, i **C** i **S** znaki dwubajtowe i ciągi, w wszystkie funkcje formatowania.

### <a name="type-field-characters"></a>Znaki pola typu

|Znaki typu|Argument|Format danych wyjściowych|
|--------------------|--------------|-------------------|
|**c**|Znak|W przypadku użycia z `printf` funkcje, określa znaków jednobajtowych; w przypadku użycia z `wprintf` funkcje, określa znaków dwubajtowych.|
|**C**|Znak|W przypadku użycia z `printf` funkcje, określa znaków dwubajtowych; w przypadku użycia z `wprintf` funkcje, określa znaków jednobajtowych.|
|**d**|Liczba całkowita|Podpisana dziesiętną liczbą całkowitą.|
|**i**|Liczba całkowita|Podpisana dziesiętną liczbą całkowitą.|
|**o**|Liczba całkowita|Ósemkową liczby całkowitej bez znaku.|
|**u**|Liczba całkowita|Dziesiętną liczbą całkowitą bez znaku.|
|**x**|Liczba całkowita|Szesnastkową liczby całkowitej bez znaku; używa "abcdef".|
|**X**|Liczba całkowita|Szesnastkową liczby całkowitej bez znaku; używa "ABCDEF".|
|**e**|Zmiennoprzecinkowe|Wartość, która ma formę [-] podpisane*d.dddd*__e±__*dd*[*d*] gdzie *d* jest jedną cyfrę, *dddd* jest jeden lub więcej cyfr dziesiętnych, w zależności od określona precyzja lub sześć domyślnie i *dd*[*d*] jest dwóch lub trzech cyfr dziesiętnych, w zależności od [format danych wyjściowych](../c-runtime-library/set-output-format.md) i rozmiar wykładnik.|
|**E**|Zmiennoprzecinkowe|Taki sam jak **e** formatowania z wyjątkiem **E** zamiast **e** wprowadza wykładnik.|
|**f**|Zmiennoprzecinkowe|Wartość, która ma formę [-] podpisane*dddd*__.__ *dddd*, gdzie *dddd* jest jeden lub więcej cyfr dziesiętnych. Liczba cyfr przed separatorem dziesiętnym zależy od wielkości numer, a liczba cyfr po dziesiętnego zależy od żądanego dokładność lub sześć domyślnie.|
|**F**|Zmiennoprzecinkowe|Taki sam jak **f** formatowania z tą różnicą, że Wielka nieskończoności i nan danych wyjściowych.|
|**k**|Zmiennoprzecinkowe|Podpisem wartości zostają wyświetlone w **f** lub **e** sformatować, nastąpi mniejszych podanej wartości i precyzji. **e** format jest używany tylko wtedy, gdy wykładnik wartość jest mniejsza niż -4 lub większa niż lub równa *dokładności* argumentu. Końcowe zero są obcinane i dziesiętnego jest wyświetlana tylko wtedy, gdy jeden lub więcej cyfr po nim.|
|**K**|Zmiennoprzecinkowe|Taki sam jak **g** sformatować, z wyjątkiem **E**, a nie **e**, wprowadza wykładnik (o ile jest to możliwe).|
|**a**|Zmiennoprzecinkowe|Podpisana szesnastkową wartość zmiennoprzecinkowe podwójnej precyzji, która ma formę [-] 0 x*h.hhhh*__p±__*dd*, gdzie *h.hhhh* są szesnastkowy cyfry (przy użyciu małych liter) mantysa i *dd* są co najmniej jedną cyfrę dla wykładnik. Dokładność określa liczbę cyfr po punkcie.|
|**A**|Zmiennoprzecinkowe|Podpisana szesnastkową wartość zmiennoprzecinkowe podwójnej precyzji, która ma formę [-] 0 X*h.hhhh*__P±__*dd*, gdzie *h.hhhh* są szesnastkowy cyfry (przy użyciu wielkimi literami) mantysa i *dd* są co najmniej jedną cyfrę dla wykładnik. Dokładność określa liczbę cyfr po punkcie.|
|**n**|Wskaźnik do liczby całkowitej.|Liczba znaków, które zostały pomyślnie zapisane do tej pory strumienia lub buforu. Ta wartość jest przechowywana w całkowitą, której adres jest podawana jako argument. Rozmiar całkowitą wskazywał kontrolowana przez prefiks Specyfikacja rozmiaru argumentu. **n**  Specyfikator jest domyślnie wyłączona; informacji, zobacz uwagę ważny.|
|**p**|Typ wskaźnika|Wyświetla argument jako adresu cyfr szesnastkowych.|
|**s**|String|W przypadku użycia z `printf` funkcje, określa ciąg znaków jednobajtowych lub wielobajtowego; w przypadku użycia z `wprintf` funkcje, określa ciąg znaków dwubajtowych. Znaki są wyświetlane do pierwszego znaku null lub do czasu *dokładności* osiągnięciem wartości.|
|**S**|String|W przypadku użycia z `printf` funkcje, określa ciąg znaków dwubajtowych; w przypadku użycia z `wprintf` funkcje, określa ciąg znaków jednobajtowych lub wielobajtowego. Znaki są wyświetlane do pierwszego znaku null lub do czasu *dokładności* osiągnięciem wartości.|
|**Z**|`ANSI_STRING`lub `UNICODE_STRING` — struktura|Jeśli adres [ANSI_STRING](http://msdn.microsoft.com/library/windows/hardware/ff540605.aspx) lub [UNICODE_STRING](http://msdn.microsoft.com/library/windows/hardware/ff564879.aspx) struktury jest przekazywany jako argument, wyświetla ciąg znajdujący się w buforze wskazywana przez `Buffer` pola struktury. Użyj *rozmiar* prefiks modyfikator **w** do określenia `UNICODE_STRING` argument — na przykład `%wZ`. `Length` Pola struktury musi mieć ustawioną w bajtach długość ciągu. `MaximumLength` Pola struktury musi mieć ustawioną w bajtach długość buforu.<br /><br /> Zazwyczaj **Z** znaku typu jest używana tylko debugowanie funkcji używających specyfikacji konwersji, takie jak sterownik `dbgPrint` i `kdPrint`.|

W programie Visual Studio 2015, jeśli argument, który odpowiada specyfikatorowi konwersji liczb zmiennoprzecinkowych (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) jest nieskończone nieokreślony, lub NaN, sformatowane wyniki zgodne ze standardem C99. Poniższa tabela zawiera sformatowane dane wyjściowe:

|Wartość|Dane wyjściowe|
|-----------|------------|
|nieskończoności|`inf`|
|Quiet NaN|`nan`|
|Sygnalizacji NaN|`nan(snan)`|
|Nieokreślony NaN|`nan(ind)`|

Dowolne z tych wartości może być poprzedzona znakiem. Jeśli zmiennoprzecinkowe *typu* konwersji specyfikator znak jest wielką literą, a następnie dane wyjściowe jest sformatowany także wielkimi literami. Na przykład, jeśli specyfikator formatu jest `%F` zamiast `%f`, nieskończoności jest w formacie `INF` zamiast `inf`. `scanf` Funkcji również mogą analizować te ciągi, dzięki te wartości można zmieniać przesyłania danych za pośrednictwem `printf` i `scanf` funkcji.

Przed Visual Studio 2015 CRT zastosowania różnych niestandardowym formacie dane wyjściowe nieskończone nieokreślony i wartości NaN:

|Wartość|Dane wyjściowe|
|-----------|------------|
|+ infinity|`1.#INF`*losowe cyfry*|
|-infinity|`-1.#INF`*losowe cyfry*|
|Nieskończona (tak samo jak quiet NaN)|*cyfra* `.#IND` *losowe cyfry*|
|NaN|*cyfra* `.#NAN` *losowe cyfry*|

Żadnego z tych adresów może poprzedzona znakiem i mogła zostać sformatowana nieco inaczej w zależności od szerokość pola i dokładność, niekiedy z efektami nietypowe. Na przykład `printf("%.2f\n", INFINITY)` przetwarzającej `1.#J` ponieważ #INF czy "zaokrąglony" dokładności 2 cyfr.

> [!NOTE]
> Jeśli argument, który odpowiada `%s` lub `%S`, lub `Buffer` pole argumentu, który odpowiada `%Z`, wskaźnika o wartości null, jest wyświetlany jest "(null)".

> [!NOTE]
> W wszystkie formaty wykładniczej minimalną liczbę cyfr wykładnik, do wyświetlenia jest dwóch, przy użyciu trzech tylko wtedy, gdy jest to konieczne. Za pomocą [_set_output_format —](../c-runtime-library/set-output-format.md) funkcji, można ustawić liczbę miejsc po przecinku wyświetlane do trzech zgodności z poprzednimi wersjami z kodu napisanego dla programu Visual Studio 2013 i przed.

> [!IMPORTANT]
> Ponieważ `%n` format jest z założenia niezabezpieczone, jest domyślnie wyłączona. Jeśli `%n` napotkano w ciągu formatu zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md). Aby włączyć `%n` obsługi, zobacz [_set_printf_count_output —](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Dyrektywy flagowania

Pierwsze pole opcjonalne w specyfikacji konwersji zawiera *Flaga dyrektywy*, zero lub więcej znaków, które Określ uzasadnienie danych wyjściowych i Dostosuj wyjściowych znaków, puste wartości, zer, miejsc dziesiętnych i ósemkowe Flaga i prefiksy szesnastkową. Więcej niż jedna dyrektywa flagi może występować w specyfikacji konwersji, i Flaga znaki mogą być wyświetlane w dowolnej kolejności.

### <a name="flag-characters"></a>Flaga znaków

|Flaga|Znaczenie|Domyślny|
|----------|-------------|-------------|
|**-**|Wyrównaj do lewej wynik względem szerokości danego pola.|Wyrównaj do prawej.|
|**+**|Użyj znaku (+ lub -) jako prefiks wartość wyjściowa, jeśli jest z poziomu typu ze znakiem.|Znak pojawia się tylko w przypadku wartości ujemnych podpisem (-).|
|**0**|Jeśli *szerokość* jest poprzedzony **0**, początkowego znaku są dodawane zera, aż do osiągnięcia minimalnej szerokości. Jeśli oba **0** i  **-**  są wyświetlane, **0** jest ignorowana. Jeśli **0** określono format liczby całkowitej (**i**, **u**, **x**, **X**, **o**, **d**), a także znajdują się specyfikacja dokładności — na przykład `%04.d`— **0** jest ignorowana. Jeśli **0** określono **a** lub **A** format liczb zmiennoprzecinkowych zera wiodące jest dołączany na początku mantysa, po `0x` lub `0X` prefiks.|Nie dopełnienie.|
|**puste** ("")|Użyj pustego jako prefiks wartość wyjściowa, jeśli jest on podpisany i dodatnią. Pusty jest ignorowana, jeśli obie pustym i + flagi pojawiają się.|Pojawi się puste.|
|**#**|Gdy jest używana z **o**, **x**, lub **X** format  **#**  Flaga używa 0, 0 x, lub 0 X, odpowiednio do prefiksu any różną od zera Wartość wyjściowa.|Pojawi się puste.|
||Gdy jest używana z **e**, **E**, **f**, **F**, **a** lub **A** Format,  **#**  flaga wymusza wartość wyjściowa zawiera separatorem dziesiętnym.|Dziesiętnego jest wyświetlana tylko wtedy, gdy cyfry po nim.|
||Gdy jest używana z **g** lub **G** format  **#**  flaga wymusza wartość wyjściowa zawierają punktu dziesiętnego i uniemożliwia obcięcie końcowe zera.<br /><br /> Ignorowane w przypadku użycia z **c**, **d**, **i**, **u**, lub **s**.|Dziesiętnego jest wyświetlana tylko wtedy, gdy cyfry po nim. Końcowe zero są obcinane.|

<a name="width"></a>

## <a name="width-specification"></a>Specyfikacja szerokości

W specyfikacji konwersji pola Specyfikacja szerokości opcjonalne pojawia się po jednej *flagi* znaków. *Szerokość* argument jest ujemna dziesiętną liczbą całkowitą, która określa minimalną liczbę znaków, które są danymi wyjściowymi. Jeśli liczba znaków w wartości wyjściowych jest mniejsza niż określona szerokość, spacje są dodawane do lewej lub prawej wartości — w zależności od tego, czy flaga wyrównanie w lewo (**-**) określono — do minimum Szerokość zostanie osiągnięty. Jeśli *szerokość* jest poprzedzone przez 0, zera wiodące są dodawane do liczby całkowitej lub konwersje zmiennoprzecinkowe aż do osiągnięcia minimalnej szerokości, z wyjątkiem przypadków, gdy konwersji wartości infinity lub NaN.

Specyfikacja szerokości nigdy nie powoduje, że wartość do skrócenia. Jeśli liczba znaków w wartości wyjściowych jest większa niż określona szerokość lub *szerokość* jest nie określono wszystkich znaków w wartości są dane wyjściowe, podlegają *dokładności* specyfikacji.

Jeśli specyfikacja szerokości jest znak gwiazdki (`*`), `int` argumentu z listy argumentów dostarcza wartość. *Szerokość* argumentu musi poprzedzać wartości sformatowany na liście argumentów, jak pokazano w poniższym przykładzie:

`printf("%0*f", 5, 3);  /* 00003 is output */`

Brak lub małych *szerokość* wartość w specyfikacji konwersji nie powoduje obcięcie wartości danych wyjściowych. Jeśli wynik konwersji jest szerszy niż *szerokość* wartość pola rozszerza zawiera wynik konwersji.

<a name="precision"></a>

## <a name="precision-specification"></a>Specyfikacja dokładności

W specyfikacji konwersji trzecie pole opcjonalne to specyfikacja dokładności. Składa się z kropki (.), a następnie nieujemną dziesiętną liczbą całkowitą, która w zależności od typu konwersji, określa liczbę znaków ciągu, liczbę miejsc dziesiętnych lub liczbę cyfr znaczących jako dane wyjściowe.

W odróżnieniu od Specyfikacja szerokości Specyfikacja dokładności może spowodować obcięcie wartość wyjściowa albo zaokrąglanie wartości zmiennoprzecinkowych. Jeśli *dokładności* jest określony jako 0 i wartość do skonwertowania wynosi 0, wynik żadnych danych wyjściowych znaków, jak pokazano w poniższym przykładzie:

`printf( "%.0d", 0 );      /* No characters output */`

Jeśli specyfikacja dokładności jest znak gwiazdki (\*), `int` argumentu z listy argumentów dostarcza wartość. Na liście argumentów *dokładności* argumentu musi poprzedzać wartość formatowania, jak pokazano w poniższym przykładzie:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

*Typu* znaku określa interpretacji z *dokładności* lub domyślna dokładność podczas *dokładności* zostanie pominięty, jak pokazano w poniższej tabeli.

### <a name="how-precision-values-affect-type"></a>Wpływ dokładności wartości typu

|Typ|Znaczenie|Domyślny|
|----------|-------------|-------------|
|**a**, **A**|Dokładność określa liczbę cyfr po punkcie.|Domyślna dokładność to 13. Jeśli dokładności ma wartość 0, chyba że drukowania dziesiętnego nie  **#**  flaga jest wykorzystywana.|
|**c**, **C**|Dokładność nie ma znaczenia.|Znak jest drukowana.|
|**d**, **i**, **o**, **u**, **x**, **X**|Dokładność określa minimalną liczbę cyfr ma być drukowana. Jeśli liczba cyfr w argumencie jest mniejsza niż *dokładności*, wartość wyjściowa jest uzupełniana na zerami z lewej strony. Wartość nie zostanie obcięta podczas przekracza liczbę miejsc po przecinku *dokładności*.|Dokładność domyślna to 1.|
|**e**, **E**|Dokładność określa liczbę miejsc po przecinku do wydrukowania po punkcie dziesiętnym. Ostatnia cyfra drukowanych jest zaokrąglana.|Dokładność domyślna to 6. Jeśli *dokładności* ma wartość 0 lub kropki (.) pojawi się bez numer, drukowania nie separatorem dziesiętnym.|
|**f**, **F**|Wartości dokładności określa liczbę cyfr po punkcie dziesiętnym. Jeśli pojawi się separatorem dziesiętnym, co najmniej jedną cyfrę pojawia się przed nim. Wartość jest zaokrąglana do odpowiedniej liczby miejsc po przecinku.|Dokładność domyślna to 6. Jeśli *dokładności* ma wartość 0 lub jeśli bez numer, pojawi się kropki (.), drukowania nie separatorem dziesiętnym.|
|**g**, **G**|Dokładność określa maksymalną liczbę cyfr znaczących wydrukować.|Sześć cyfr znaczących są drukowane i końcowe zera są obcinane.|
|**s**, **S**|Dokładność określa maksymalną liczbę znaków, które ma być drukowana. Znaki powyżej *dokładności* nie są drukowane.|Znaki są drukowane, dopóki nie napotkano znak null.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Specyfikacja rozmiaru argumentu

W specyfikacji konwersji *rozmiar* pole jest modyfikator długości argumentu *typu* specyfikatora konwersji. *Rozmiar* pola prefiksy do *typu* pola —**hh**, **h**, **j**, **l** (małe litery L), **L**, **ll**, **t**, **w**, **z**, **I**(wielkie i), **I32**, i **komputerach 64**— określ "rozmiar" odpowiadającego mu argumentu — długie lub krótka, 32-bitowy lub 64-bitowy, znaków jednobajtowych lub znaków dwubajtowych — w zależności od Specyfikator konwersji, które modyfikują. Używane z tymi prefiksami rozmiar *typu* znaków `printf` i `wprintf` rodziny funkcji, aby określić interpretacji rozmiary argumentu, jak pokazano w poniższej tabeli. *Rozmiar* pole jest opcjonalne w przypadku niektórych typów argumentów. Jeśli nie określono żadnego prefiksu rozmiar, program formatujący korzysta z argumentami całkowitą — na przykład podpisane lub unsigned `char`, `short`, `int`, `long`i typy wyliczeniowe — jako 32-bitowa `int` typów i `float`, `double`, i `long double` argumenty zmiennoprzecinkowe są używane jako 64-bitowa `double` typów. Reguły domyślne argument podwyższania poziomu dla listy zmiennych argumentów jest zgodny. Aby uzyskać więcej informacji na temat podwyższania poziomu argumentu, zobacz wielokropki i argumenty domyślne [wyrażenia przyrostków](../cpp/postfix-expressions.md). W systemach zarówno 32-bitowe i 64-bitowych, specyfikacja konwersji argumentu 64-bitową liczbę całkowitą musi zawierać prefiks rozmiar **ll** lub **komputerach 64**. W przeciwnym razie zachowanie elementu formatującego jest niezdefiniowany.

Niektóre typy są różne rozmiary w kodzie 32-bitowe i 64-bitowych. Na przykład `size_t` jest 32-bitowy długo w kodzie skompilowanym x86 i 64-bitowej w kodzie skompilowanym dla x64. Aby utworzyć niezależny od platformy formatowania kodu dla typów o zmiennej szerokości, można użyć modyfikator Rozmiar argumentów o zmiennej szerokości. Alternatywnie użyj modyfikatora rozmiar argumentu 64-bitowych i jawnie wspierania typ argumentów o zmiennej szerokości do 64-bitowy. Specyficzne dla firmy Microsoft **I** (wielkie i) argument rozmiar modyfikator obsługi argumentów całkowitą o zmiennej szerokości, ale zaleca się określonego typu **j**, **t**i **z** Modyfikatory przenośności.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Rozmiar prefiksy printf i wprintf specyfikatory typ formatu

|Aby określić|Użyj prefiksu|Ze specyfikatorem typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`short int`<br />`short unsigned int`|**h**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`__int64`<br />`unsigned __int64`|**KOMPUTERACH 64**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`intmax_t`<br />`uintmax_t`|**j** lub **komputerach 64**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`long double`|**l** (małe litery L) lub **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g**, lub **G**|
|`long int`<br />`long unsigned int`|**l** (małe litery L)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`long long int`<br />`unsigned long long int`|**Wszystki** (małe litery LL)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`ptrdiff_t`|**t** lub **I** (wielkie i)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|`size_t`|**z** lub **I** (wielkie i)|**d**, **i**, **o**, **u**, **x**, lub **X**|
|Znaków|**h**|**c** lub **C**|
|Znaki dwubajtowe|**l** (małe litery L) lub **w**|**c** lub **C**|
|Ciąg znaków|**h**|**s**, **S**, lub **Z**|
|Ciąg znaków dwubajtowych|**l** (małe litery L) lub **w**|**s**, **S**, lub **Z**|

`ptrdiff_t` i `size_t` typy są `__int32` lub `unsigned __int32` na platformach 32-bitowych i `__int64` lub `unsigned __int64` na platformach 64-bitowych. **I** (wielkie i), **j**, **t**, i **z** prefiksy rozmiar zająć szerokość poprawny argument dla platformy.

W programie Visual C++ mimo że `long double` jest typem różne składa się z tym samym reprezentacji wewnętrznej jako `double`.

**Hc** lub **hC** specyfikatora typu jest synonimem **c** w `printf` funkcji i z **C** w `wprintf` funkcji. **Lc**, **lC**, **wc** lub **wC** specyfikatora typu jest synonimem **C** w `printf` Funkcje i **c** w `wprintf` funkcji. **Hs** lub **hS** specyfikatora typu jest synonimem **s** w `printf` funkcji i z **S** w `wprintf` funkcji. **Ls**, **lS**, **ws** lub **wS** specyfikatora typu jest synonimem **S** w `printf` Funkcje i **s** w `wprintf` funkcji.

> [!NOTE]
> **Dotyczące firmy Microsoft**  
> **I** (wielkie i), **I32**, **komputerach 64**, i **w** argument prefiksy modyfikator Rozmiar są rozszerzenia Microsoft i nie są zgodne z ISO C. **h** prefiksu, gdy jest używany z danymi typu `char` i **l** (małe litery L) prefiksu, gdy jest używany z danymi typu `double` są rozszerzenia Microsoft.

## <a name="see-also"></a>Zobacz też

[printf, _printf_l —, wprintf, _wprintf_l —](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)  
[printf_s —, _printf_s_l —, wprintf_s — _wprintf_s_l —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)  
[printf_p parametry pozycyjne](../c-runtime-library/printf-p-positional-parameters.md)  