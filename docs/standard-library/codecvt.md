---
title: '&lt;codecvt&gt;'
ms.date: 11/04/2016
f1_keywords:
- codecvt
- <codecvt>
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
ms.openlocfilehash: e571c1ca8beef684a40bbf643e83aba3f205fc8e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230120"
---
# <a name="ltcodecvtgt"></a>&lt;codecvt&gt;

Definiuje kilka szablonów klas, które opisują obiekty na podstawie szablonu klasy [codecvt](../standard-library/codecvt-class.md). Te obiekty mogą działać jako zestawy [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) , które kontrolują konwersje między sekwencją wartości typu `Elem` a sekwencją wartości typu **`char`** .

## <a name="syntax"></a>Składnia

```cpp
#include <codecvt>
```

## <a name="remarks"></a>Uwagi

Zestawy reguł ustawień regionalnych zadeklarowane w tym nagłówku konwertują między kilka kodowania znaków. W przypadku znaków dwubajtowych (przechowywanych w ramach programu w liczbach całkowitych o stałym rozmiarze):

- UCS-4 to Unicode (ISO 10646) zakodowany w ramach programu jako 32-bitową liczbę całkowitą.

- Ciąg UCS-2 jest zakodowany w formacie Unicode w ramach programu jako 16-bitową liczbę całkowitą.

- UTF-16 jest zakodowana w formacie Unicode w ramach programu jako jedną lub 2 16-bitową liczbę całkowitą. (Należy zauważyć, że to nie spełnia wszystkich wymagań prawidłowego kodowania znaków dwubajtowych dla standardu C lub standard C++. Nie jest to jednak powszechnie używane.

Dla strumieni bajtów (przechowywanych w pliku, przesyłanych w postaci sekwencji bajtów lub przechowywanych w ramach programu w tablicy **`char`** ):

- UTF-8 jest zakodowana w formacie Unicode w strumieniu bajtów jako jeden lub więcej ośmiu bajtów z kolejnością bajtów deterministycznych.

- UTF-16LE jest zakodowana w formacie Unicode w strumieniu bajtów jako UTF-16 z każdą 16-bitową liczbą całkowitą prezentowaną jako 2 8-bitowe bajty, mniej znaczący bajt.

- Kodowanie UTF-16BE jest zakodowane w formacie Unicode w strumieniu bajtów jako UTF-16 z każdą 16-bitową liczbą całkowitą prezentowaną jako 2 8-bitowe bajty, najpierw bardziej znaczący bajt.

### <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|Określa informacje o konfiguracji dla zestawów reguł ustawień regionalnych.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[codecvt_utf8](codecvt-utf8-class.md)|Reprezentuje zestaw reguł ustawień regionalnych, który konwertuje między znaki szerokie kodowane jako UCS-2 lub UCS-4, oraz strumień bajtów zakodowany jako UTF-8.|
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|Reprezentuje zestaw reguł ustawień regionalnych, który konwertuje między znaki szerokie kodowane jako UTF-16 i strumień bajtów zakodowany jako UTF-8.|
|[codecvt_utf16](codecvt-utf16-class.md)|Reprezentuje zestaw reguł ustawień regionalnych, który konwertuje między znaki szerokie kodowane jako UCS-2 lub UCS-4 i strumień bajtów zakodowany jako UTF-16LE lub UTF-16BE.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<codecvt>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
