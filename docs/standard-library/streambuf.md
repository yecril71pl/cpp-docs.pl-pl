---
title: '&lt;streambuf —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <streambuf>
dev_langs:
- C++
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db05d1b19a67fc54a148d407fd90992a6d37c4c6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213590"
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
|[basic_streambuf, klasa](https://msdn.microsoft.com/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|Klasa szablonu opisuje abstrakcyjną klasę bazową dla elementu pochodnego dla buforu strumienia, który kontroluje przekazywanie elementów do i z reprezentację określonego strumienia.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
