---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 15bfa86a3c697442b66a5f77aa6ea7a9aba5643c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412374"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Dołączyć standardowy nagłówek iostreams \<streambuf > Aby zdefiniować klasę szablonu [basic_streambuf](../standard-library/basic-streambuf-class.md), czyli podstawowy do operacji klasy iostreams. Ten nagłówek będzie zazwyczaj uwzględniony dla Ciebie żadnego innego nagłówków iostreams; rzadko musi go uwzględniać bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Specjalizacja `basic_streambuf` , który używa **char** jako parametry szablonu.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Specjalizacja `basic_streambuf` , który używa **wchar_t** jako parametry szablonu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_streambuf, klasa](basic-streambuf-class.md)|Klasa szablonu opisuje abstrakcyjną klasę bazową dla elementu pochodnego dla buforu strumienia, który kontroluje przekazywanie elementów do i z reprezentację określonego strumienia.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
