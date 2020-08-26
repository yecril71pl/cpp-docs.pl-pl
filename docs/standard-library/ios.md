---
title: '&lt;wykonane&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: 8ba03e5ab5dd90a6f29e08b01576803a00f0bd24
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845487"
---
# <a name="ltiosgt"></a>&lt;wykonane&gt;

Definiuje kilka typów i funkcji podstawowych dla operacji iostreams. Ten nagłówek jest zwykle uwzględniany przez inne nagłówki iostream; rzadko umieszczasz ją bezpośrednio.

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<ios>

**Przestrzeń nazw:** std

> [!NOTE]
> \<ios>Biblioteka używa `#include <iosfwd>` instrukcji.

## <a name="remarks"></a>Uwagi

Duża grupa funkcji to manipulowanie. Manipulator zadeklarowany w elemencie \<ios> Modyfikuje wartości przechowywane w obiekcie argumentów klasy [ios_base](../standard-library/ios-base-class.md). Inne manipulowania wykonuje akcje dotyczące strumieni kontrolowanych przez obiekty typu pochodnego od tej klasy, na przykład specjalizacji jednego z szablonów klas [basic_istream](../standard-library/basic-istream-class.md) lub [basic_ostream](../standard-library/basic-ostream-class.md). Na przykład [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) Czyści flagę formatu `ios_base::skipws` w obiekcie `str` , który może być jednego z tych typów.

Możesz również wywołać Manipulator przez wstawienie go do strumienia wyjściowego lub wyodrębnienie go ze strumienia wejściowego, z powodu specjalnych operacji wstawiania i wyodrębniania dostarczonych dla klas pochodnych `ios_base` . Na przykład:

```cpp
istr>> noskipws;
```

wywołania [noskipws](../standard-library/ios-functions.md#noskipws)(**ISTR**).

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[wykonane](../standard-library/ios-typedefs.md#ios)|Obsługuje klasę systemu iOS ze starej biblioteki iostream.|
|[streamoff —](../standard-library/ios-typedefs.md#streamoff)|Obsługuje operacje wewnętrzne.|
|[streampos](../standard-library/ios-typedefs.md#streampos)|Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.|
|[dane StreamSize](../standard-library/ios-typedefs.md#streamsize)|Określa rozmiar strumienia.|
|[wios](../standard-library/ios-typedefs.md#wios)|Obsługuje klasę wios ze starej biblioteki iostream.|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.|

### <a name="manipulators"></a>Manipulatory

|Nazwa|Opis|
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako **`true`** lub **`false`** w strumieniu.|
|[dec](../standard-library/ios-functions.md#dec)|Określa, że zmienne całkowite pojawiają się w notacji Base 10.|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|Konfiguruje flagi `ios_base` obiektu, aby użyć domyślnego formatu wyświetlania wartości zmiennoprzecinkowych.|
|[FIXED](../standard-library/ios-functions.md#fixed)|Określa, że liczba zmiennoprzecinkowa jest wyświetlana w notacji o stałej liczbie dziesiętnej.|
|[szesnastkowy](../standard-library/ios-functions.md#hex)|Określa, że zmienne całkowite pojawiają się w notacji Base 16.|
|[hexfloat](../standard-library/ios-functions.md#hexfloat)|
|[internal](../standard-library/ios-functions.md#internal)|Powoduje, że znak liczby jest wyrównany do lewej, a liczba powinna być wyrównana do prawej.|
|[lewym](../standard-library/ios-functions.md#left)|Powoduje, że tekst nie jest tak szeroki, jak szerokość danych wyjściowych, która ma być wyświetlana w strumieniu opróżniania z lewego marginesu.|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako 1 lub 0 w strumieniu.|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|Wyłącza opcję wskazującą podstawę notacji, w której wyświetlana jest liczba.|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|Wyświetla tylko liczbę całkowitą części liczb zmiennoprzecinkowych, których część ułamkowa ma wartość zero.|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|Powoduje, że liczby dodatnie nie mogą być podpisywane jawnie.|
|[noskipws](../standard-library/ios-functions.md#noskipws)|Zapoznaj się z miejscem, w którym znajduje się strumień wejściowy.|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|Powoduje, że dane wyjściowe są buforowane i przetwarzane, gdy bufor jest pełny.|
|[nowielkie litery](../standard-library/ios-functions.md#nouppercase)|Określa, że cyfry szesnastkowe i wykładnik w notacji wykładniczej są wyświetlane małymi literami.|
|[ósemkow](../standard-library/ios-functions.md#oct)|Określa, że zmienne całkowite pojawiają się w notacji Base 8.|
|[Kliknij](../standard-library/ios-functions.md#right)|Powoduje, że tekst nie jest tak szeroki, jak szerokość danych wyjściowych, która ma być wyświetlana w strumieniu opróżniania z prawego marginesu.|
|[nauk](../standard-library/ios-functions.md#scientific)|Powoduje wyświetlanie liczb zmiennoprzecinkowych przy użyciu notacji wykładniczej.|
|[showbase](../standard-library/ios-functions.md#showbase)|Wskazuje podstawę notacji, w której wyświetlana jest liczba.|
|[showpoint](../standard-library/ios-functions.md#showpoint)|Wyświetla część liczby zmiennoprzecinkowej i cyfr z prawej strony punktu dziesiętnego, nawet jeśli część ułamkowa jest równa zero.|
|[showpos](../standard-library/ios-functions.md#showpos)|Powoduje jawne podpisywanie liczb dodatnich.|
|[skipws](../standard-library/ios-functions.md#skipws)|Nie należy odczytywać spacji w strumieniu wejściowym.|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|Powoduje, że dane wyjściowe będą przetwarzane, gdy bufor nie jest pusty.|
|[znaki](../standard-library/ios-functions.md#uppercase)|Określa, że cyfry szesnastkowe i wykładnik w notacji wykładniczej są wyświetlane wielką literą.|

### <a name="error-reporting"></a>Raportowanie błędów

|Nazwa|Opis|
|-|-|
|[io_errc](../standard-library/ios-functions.md#io_errc)||
|[is_error_code_enum](../standard-library/ios-functions.md#is_error_code_enum)||
|[iostream_category](../standard-library/ios-functions.md#iostream_category)||
|[make_error_code](../standard-library/ios-functions.md#make_error_code)||
|[make_error_condition](../standard-library/ios-functions.md#make_error_condition)||

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|Szablon klasy zawiera opis funkcji magazynu i elementów członkowskich wspólnych dla strumieni danych wejściowych (szablonu klasy [basic_istream](../standard-library/basic-istream-class.md)) i strumieni wyjściowych ( [basic_ostream](../standard-library/basic-ostream-class.md)szablonu klasy), które są zależne od parametrów szablonu.|
|[FPOS](../standard-library/fpos-class.md)|Szablon klasy opisuje obiekt, który może przechowywać wszystkie informacje potrzebne do przywrócenia dowolnego wskaźnika położenia pliku w ramach dowolnego strumienia.|
|[ios_base](../standard-library/ios-base-class.md)|Klasa zawiera opis funkcji magazynu i elementów członkowskich wspólnych dla strumieni wejściowych i wyjściowych, które nie zależą od parametrów szablonu.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
