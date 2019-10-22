---
title: '&lt;streambuf &gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: ca5f53d67bb32e59c20d1d440879144f0a617c66
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686025"
---
# <a name="ltstreambufgt"></a>&lt;streambuf &gt;

Uwzględnij \<streambuf nagłówka standardowego iostreams >, aby zdefiniować szablon klasy [basic_streambuf](../standard-library/basic-streambuf-class.md), który jest podstawowy dla operacji klas iostreams. Ten nagłówek jest zwykle dołączany przez inny z nagłówków iostreams; rzadko trzeba dołączyć go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Specjalizacja `basic_streambuf`, która używa **znaków** jako parametrów szablonu.|
|[wstreambuf —](../standard-library/streambuf-typedefs.md#wstreambuf)|Specjalizacja `basic_streambuf`, która używa **wchar_t** jako parametrów szablonu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_streambuf, klasa](basic-streambuf-class.md)|Szablon klasy opisuje abstrakcyjną klasę bazową dla tworzenia bufora strumienia, która kontroluje przekazywanie elementów do i z określonej reprezentacji strumienia.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
