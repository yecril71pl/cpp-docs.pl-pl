---
title: '&lt;dla systemu IOS&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: 1566f9105a61b1c037e86fd2e4b280ed6dd2020e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385222"
---
# <a name="ltiosgt"></a>&lt;dla systemu IOS&gt;

Definiuje kilka typów i funkcji podstawowych operacji iostream. Ten nagłówek będzie zazwyczaj uwzględniony dla Ciebie innego nagłówków iostream; rzadko uwzględniania go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <ios>
```

## <a name="remarks"></a>Uwagi

Dużej grupy funkcji są manipulatory. Manipulator zadeklarowanych w \<dla systemu ios > powoduje zmianę wartości przechowywane w obiekcie klasy jej argument [ios_base —](../standard-library/ios-base-class.md). Inne manipulatory wykonywać akcje na strumienie kontrolowane przez obiekty typu pochodzącego z tej klasy, takie jak specjalizacja jednej z klas szablonów [basic_istream](../standard-library/basic-istream-class.md) lub [basic_ostream](../standard-library/basic-ostream-class.md). Na przykład [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) czyści flagi formatu `ios_base::skipws` w obiekcie `str`, który może być jednego z tych typów.

Można również wywołać manipulator przez wstawienie go do strumienia wyjściowego lub wyodrębniania ze strumienia wejściowego, ze względu na specjalne operacji wstawienia i wydobycia dostarczony dla klas pochodnych `ios_base`. Na przykład:

```cpp
istr>> noskipws;
```

wywołania [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**).

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[dla systemu IOS](../standard-library/ios-typedefs.md#ios)|Obsługuje klasy dla systemu ios ze starego biblioteką iostream.|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|Obsługuje operacje wewnętrznego.|
|[streampos](../standard-library/ios-typedefs.md#streampos)|Zawiera bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|Określa rozmiar strumienia.|
|[wios](../standard-library/ios-typedefs.md#wios)|Obsługuje klasy wios ze starego biblioteką iostream.|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|Zawiera bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są traktowane jako **true** lub **false** w strumieniu.|
|[dec](../standard-library/ios-functions.md#dec)|Określa, czy zmiennych całkowitych są wyświetlane w podstawowej notacji 10.|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|Określa flagi o `ios_base` obiekt ma być używany domyślny format wyświetlania dla wartości zmiennoprzecinkowych.|
|[Stała](../standard-library/ios-functions.md#fixed)|Określa, czy liczba zmiennoprzecinkowa jest wyświetlana w notacji dziesiętnej stałej.|
|[hex](../standard-library/ios-functions.md#hex)|Określa, czy zmiennych całkowitych są wyświetlane w podstawowej notacji 16.|
|[internal](../standard-library/ios-functions.md#internal)|Powoduje, że znak numeru, aby być wyrównane do lewej i numer do prawej.|
|[left](../standard-library/ios-functions.md#left)|Powoduje, że tekst, który nie jest szerokie, jak szerokość dane wyjściowe pojawią się w opróżniania strumienia do lewego marginesu.|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są traktowane jako 1 lub 0 w strumieniu.|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|Wyłącza wskazujący notational podstawowy, w którym jest wyświetlany numer.|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|Wyświetla tylko część liczby całkowitej liczby zmiennoprzecinkowe, którego część ułamkową wynosi zero.|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|Powoduje, że liczb dodatnich nie jawnie były podpisane.|
|[noskipws](../standard-library/ios-functions.md#noskipws)|Spowodować miejsca do magazynowania zostanie odczytany przez strumień wejściowy.|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|Powoduje, że dane wyjściowe buforowane i przetworzone zapełnienia buforu.|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|Określa, że cyfry szesnastkowe i wykładnika w notacji naukowej są pisane małymi literami.|
|[oct](../standard-library/ios-functions.md#oct)|Określa, czy zmiennych całkowitych są wyświetlane w podstawowej notacji 8.|
|[right](../standard-library/ios-functions.md#right)|Powoduje, że tekst, który nie jest szerokie, jak szerokość dane wyjściowe pojawią się w opróżniania strumienia do prawego marginesu.|
|[scientific](../standard-library/ios-functions.md#scientific)|Powoduje, że mają być wyświetlane przy użyciu notacji wykładniczej liczb zmiennoprzecinkowych.|
|[showbase](../standard-library/ios-functions.md#showbase)|Wskazuje podstawowy notational, w którym jest wyświetlany numer.|
|[showpoint](../standard-library/ios-functions.md#showpoint)|Wyświetla część liczba całkowita liczba zmiennoprzecinkowa i cyfr z prawej strony punktu dziesiętnego, nawet wtedy, gdy część ułamkową wynosi zero.|
|[showpos](../standard-library/ios-functions.md#showpos)|Powoduje, że liczb dodatnich jawnie były podpisane.|
|[skipws](../standard-library/ios-functions.md#skipws)|Spowodować miejsca do magazynowania nie można odczytać strumienia wejściowego.|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|Powoduje, że dane wyjściowe mają być przetwarzane, gdy ten bufor nie jest pusty.|
|[wielkie litery](../standard-library/ios-functions.md#uppercase)|Określa, że cyfry szesnastkowe i wykładnika w notacji naukowej są pisane wielkimi literami.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|Klasa szablonu Opisuje funkcje magazynu i elementów członkowskich, które muszą być wspólne dla obu strumienie wejściowe (szablonu klasy [basic_istream](../standard-library/basic-istream-class.md)) i strumieni danych wyjściowych (szablonu klasy [basic_ostream](../standard-library/basic-ostream-class.md)) zależą od Parametry szablonu.|
|[fpos —](../standard-library/fpos-class.md)|Klasa szablonu opisuje obiekt, który można przechowywać wszystkie informacje niezbędne do przywrócenia wskaźnika dowolnego położenie pliku w dowolnej usłudze stream.|
|[ios_base](../standard-library/ios-base-class.md)|Klasa opisuje magazynu i funkcje Członkowskie wspólne dla danych wejściowych i wyjściowych strumieni, które nie są zależne od parametrów szablonu.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
