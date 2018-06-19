---
title: '&lt;IOS&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <ios>
- ios/std::<ios>
dev_langs:
- C++
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e7ae83cd92ac8441d842e704446d519f57d4f65
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847731"
---
# <a name="ltiosgt"></a>&lt;dla systemu IOS&gt;

Definiuje kilka typy i funkcje podstawowe działania iostream. Ten nagłówek znajduje się zwykle dla Ciebie przez inny nagłówki iostream; rzadko uwzględniania go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <ios>

```

## <a name="remarks"></a>Uwagi

Dużą grupę funkcje są manipulatory. Manipulatora zadeklarowany w \<systemu ios > zmienia wartości przechowywane w obiekcie klasy jej argument [ios_base —](../standard-library/ios-base-class.md). Inne manipulatory wykonywać działania na strumienie kontrolowane przez obiekty typu pochodzących z tej klasy, takie jak specjalizacja jednej z klas szablonów [basic_istream —](../standard-library/basic-istream-class.md) lub [basic_ostream —](../standard-library/basic-ostream-class.md). Na przykład [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) usuwa flagę format `ios_base::skipws` w obiekcie **str**, które mogą być jednego z tych typów.

Możesz także wywołać manipulatora przez wstawienie go w strumieniu wyjściowym lub wyodrębniania go ze strumienia wejściowego z powodu specjalnych operacji wstawiania i wyodrębniania dostarczony dla klas pochodnych `ios_base`. Na przykład:

```cpp
istr>> noskipws;
```

wywołania [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**).

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[dla systemu IOS](../standard-library/ios-typedefs.md#ios)|Obsługuje klasy systemu ios z biblioteki iostream stary.|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|Obsługuje operacje wewnętrzne.|
|[streampos](../standard-library/ios-typedefs.md#streampos)|Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|Określa rozmiar strumienia.|
|[wios](../standard-library/ios-typedefs.md#wios)|Obsługuje wios klasy z biblioteki iostream stary.|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.|

### <a name="manipulators"></a>Manipulatory

|||
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako **true** lub **false** w strumieniu.|
|[DEC](../standard-library/ios-functions.md#dec)|Określa, czy liczba całkowita zmienne są widoczne w podstawowej notacji 10.|
|[defaultfloat —](../standard-library/ios-functions.md#ios_defaultfloat)|Konfiguruje flagi z `ios_base` obiekt, aby użyć domyślnego formatu wyświetlania dla wartości typu float.|
|[Stałe](../standard-library/ios-functions.md#fixed)|Określa, że liczba zmiennoprzecinkowa jest wyświetlana w notacji stałej dziesiętnej.|
|[hex](../standard-library/ios-functions.md#hex)|Określa, czy liczba całkowita zmienne są widoczne w podstawowej notacji 16.|
|[internal](../standard-library/ios-functions.md#internal)|Powoduje, że liczba Zaloguj, aby być wyrównane do lewej oraz numer do prawej.|
|[left](../standard-library/ios-functions.md#left)|Powoduje, że tekst, który nie jest szerokie, jak szerokość dane wyjściowe mają być widoczne w opróżnienia strumienia do lewego marginesu.|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|Określa, że zmienne typu [bool](../cpp/bool-cpp.md) są wyświetlane jako 1 lub 0 w strumieniu.|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|Wyłącza wskazujący base notational, w którym jest wyświetlany numer.|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|Wyświetla tylko część liczby całkowitej liczby zmiennoprzecinkowe, których część ułamkowa wynosi zero.|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|Powoduje, że dodatnie nie jawnie były podpisane.|
|[noskipws](../standard-library/ios-functions.md#noskipws)|Spowodować spacje odczytywane przez strumień wejściowy.|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|Powoduje, że dane wyjściowe buforowane i przetwarzane, gdy bufor jest pełna.|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|Określa, że cyfr szesnastkowych i wykładnik w notacji naukowej są pisane małymi literami.|
|[oct](../standard-library/ios-functions.md#oct)|Określa, czy liczba całkowita zmienne są widoczne w podstawowej notacji 8.|
|[right](../standard-library/ios-functions.md#right)|Powoduje, że tekst, który nie jest szerokie, jak szerokość dane wyjściowe mają być widoczne w opróżnienia strumienia do prawego marginesu.|
|[scientific](../standard-library/ios-functions.md#scientific)|Przyczyny zmiennoprzecinkową liczby będzie wyświetlana w notacji wykładniczej.|
|[showbase](../standard-library/ios-functions.md#showbase)|Wskazuje podstawowy notational, w którym jest wyświetlany numer.|
|[showpoint](../standard-library/ios-functions.md#showpoint)|Wyświetla część liczby całkowitej liczbie zmiennoprzecinkowej i cyfr z prawej strony punktu dziesiętnego nawet wtedy, gdy część ułamkowa wynosi zero.|
|[showpos](../standard-library/ios-functions.md#showpos)|Powoduje, że dodatnie jawnie były podpisane.|
|[skipws](../standard-library/ios-functions.md#skipws)|Spowodować spacje nie można odczytać strumienia wejściowego.|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|Powoduje, że dane wyjściowe do przetworzenia, gdy bufor nie jest pusty.|
|[wielkie litery](../standard-library/ios-functions.md#uppercase)|Określa, że cyfr szesnastkowych i wykładnik w notacji naukowej są pisane wielkimi literami.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_ios —](../standard-library/basic-ios-class.md)|Klasy szablonów w tym artykule opisano funkcje magazynu i element członkowski wspólne dla obu strumienie wejściowe (szablonu klasy [basic_istream —](../standard-library/basic-istream-class.md)) i strumienie wyjściowe (szablonu klasy [basic_ostream —](../standard-library/basic-ostream-class.md)) zależnych od Parametry szablonu.|
|[fpos —](../standard-library/fpos-class.md)|Klasa szablonu opisuje obiekt, który może przechowywać wszystkie informacje niezbędne do przywrócenia wskaźnik dowolnego położenie pliku w jakimkolwiek strumieniu.|
|[ios_base](../standard-library/ios-base-class.md)|Klasa opisuje magazyn i funkcje Członkowskie wspólne dla wejścia i wyjścia strumieni, które nie są zależne od parametrów szablonu.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
