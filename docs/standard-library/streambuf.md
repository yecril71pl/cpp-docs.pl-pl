---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 87fb74f62abffdd62b8c0179b13f53d96439d6c6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449577"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Uwzględnij iostreams standardowy nagłówek \<streambuf >, aby zdefiniować klasę szablonu [basic_streambuf](../standard-library/basic-streambuf-class.md), która jest podstawowa dla operacji klas iostreams. Ten nagłówek jest zwykle dołączany przez inny z nagłówków iostreams; rzadko trzeba dołączyć go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Specjalizacja `basic_streambuf` , która używa **znaków** jako parametrów szablonu.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Specjalizacja `basic_streambuf` , która używa **wchar_t** jako parametrów szablonu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_streambuf, klasa](basic-streambuf-class.md)|Klasa szablonu opisuje abstrakcyjną klasę bazową dla tworzenia bufora strumienia, która kontroluje przekazywanie elementów do i z określonej reprezentacji strumienia.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
