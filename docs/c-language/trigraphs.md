---
title: Trigramy
ms.date: 11/04/2016
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
ms.openlocfilehash: 2106f7dda6ecc71478b29cfad3f15dfee0483025
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523908"
---
# <a name="trigraphs"></a>Trigramy

Źródłowy zestaw znaków programów źródłowych języka C jest zawarty w 7-bitowym zestawie znaków ASCII, ale jest nadzbiorem niezmiennego zestawu kodów ISO 646-1983. Sekwencje trójznaków pozwalają programom języka C na zapisywanie tylko przy użyciu niezmiennego zestawu kodów ISO (Międzynarodowej Organizacji Normalizacyjnej). Trójznaki są sekwencjami trzech znaków (rozpoczętymi przez dwa kolejne znaki zapytania), które kompilator zamienia na odpowiadający im znak interpunkcyjny. Możesz używać trójznaków w plikach źródłowych języka C z zestawem znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych.

C ++ 17 usuwa trójznaków, od języka. Implementacje mogą w dalszym ciągu obsługuje trójznaków w ramach zdefiniowanych w implementacji mapowania z pliku fizycznego źródła, aby *zestaw znaków podstawowego źródła*, chociaż standardowe zachęca implementacji nie Aby to zrobić. Za pomocą języka C ++ 14 trójznaków są obsługiwane w C.

Visual C++ w dalszym ciągu obsługuje podstawienia trójznaków, ale jest domyślnie wyłączona. Uzyskać informacji o sposobie włączania podstawienia trójznaków, zobacz [/Zc: trigraphs (podstawianie Trigramów)](../build/reference/zc-trigraphs-trigraphs-substitution.md).

Poniższa tabela pokazuje dziewięć sekwencji trójznaków. Wszystkie wystąpienia znaków interpunkcyjnych z pierwszej kolumny są zamieniane w pliku źródłowym na odpowiadający znak z drugiej kolumny.

### <a name="trigraph-sequences"></a>Sekwencje trójznakowe

|Trójznak|Znak interpunkcyjny|
|--------------|---------------------------|
|??=|#|
|??(|[|
|??/|\|
|??)|]|
|??'|^|
|??\<|{|
|??!|&#124;|
|??>|}|
|??-|~|

Trójznak jest zawsze traktowany jako pojedynczy znak źródłowy. Tłumaczenie trójznaków zachodzi odbywa się w pierwszym [fazie tłumaczenia](../preprocessor/phases-of-translation.md), przed rozpoznawaniem znaków ucieczki w literałach ciągu i stałych znakowych. Rozpoznawane jest tylko dziewięć trójznaków pokazanych w powyższej tabeli. Wszystkie inne sekwencje znaków są pozostawiane nieprzetłumaczone.

Znak sekwencji ucieczki  **\\?**, zapobiega błędnej interpretacji sekwencji znaków trójznaków. (Aby uzyskać informacje dotyczące sekwencji ucieczki, zobacz [sekwencje ucieczki](../c-language/escape-sequences.md).) Na przykład, jeśli spróbujesz wydrukować ciąg `What??!` za pomocą instrukcji `printf`

```
printf( "What??!\n" );
```

ciąg zostanie wydrukowany `What|` ponieważ `??!` jest sekwencją trójznaku zamienianą `|` znaków. Napisz instrukcję w następujący sposób, aby poprawnie wydrukować ciąg:

```
printf( "What?\?!\n" );
```

W tej instrukcji `printf`, znak ucieczki ukośnika odwrotnego przed drugim znakiem zapytania zapobiega błędnej interpretacji `??!` jako trójznaku.

## <a name="see-also"></a>Zobacz też

[/Zc:trigraphs (Podstawianie trigramów)](../build/reference/zc-trigraphs-trigraphs-substitution.md)<br/>
[Identyfikatory w języku C](../c-language/c-identifiers.md)