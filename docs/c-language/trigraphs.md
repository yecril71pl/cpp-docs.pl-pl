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
ms.openlocfilehash: 3ed8849656ac57f4774825294aba7bb41a050eee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227754"
---
# <a name="trigraphs"></a>Trigramy

Źródłowy zestaw znaków programów źródłowych języka C jest zawarty w 7-bitowym zestawie znaków ASCII, ale jest nadzbiorem niezmiennego zestawu kodów ISO 646-1983. Sekwencje trójznaków pozwalają programom języka C na zapisywanie tylko przy użyciu niezmiennego zestawu kodów ISO (Międzynarodowej Organizacji Normalizacyjnej). Trójznaki są sekwencjami trzech znaków (rozpoczętymi przez dwa kolejne znaki zapytania), które kompilator zamienia na odpowiadający im znak interpunkcyjny. Możesz używać trójznaków w plikach źródłowych języka C z zestawem znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych.

C++ 17 usuwa trigraphs z języka. Implementacje mogą nadal obsługiwać trigraphs jako część mapowania zdefiniowanego przez implementację z fizycznego pliku źródłowego do *podstawowego zestawu znaków źródła*, chociaż standard zachęca do implementacji. Do języka C++ 14 trigraphs są obsługiwane w języku C.

Visual C++ nadal obsługuje podstawianie trójznaków, ale jest domyślnie wyłączone. Aby uzyskać informacje na temat włączania podstawiania trójznaków, zobacz [ `/Zc:trigraphs` (podstawienie trigraphs)](../build/reference/zc-trigraphs-trigraphs-substitution.md).

Poniższa tabela pokazuje dziewięć sekwencji trójznaków. Wszystkie wystąpienia znaków interpunkcyjnych z pierwszej kolumny są zamieniane w pliku źródłowym na odpowiadający znak z drugiej kolumny.

### <a name="trigraph-sequences"></a>Sekwencje trójznakowe

| Trójznak | Znak interpunkcyjny |
|----------|-----------------------|
| `??=` | `#` |
| `??(` | `[` |
| `??/` | `\` |
| `??)` | `]` |
| `??'` | `^` |
| `??<` | `{` |
| `??!` | `|` |
| `??>` | `}` |
| `??-` | `~` |

Trójznak jest zawsze traktowany jako pojedynczy znak źródłowy. Tłumaczenie trigraphs odbywa się w pierwszej [fazie tłumaczenia](../preprocessor/phases-of-translation.md)przed rozpoznawaniem znaków ucieczki w literałach ciągów i stałych znakach. Rozpoznawane jest tylko dziewięć trójznaków pokazanych w powyższej tabeli. Wszystkie inne sekwencje znaków są pozostawiane nieprzetłumaczone.

Sekwencja unikowa znaku, **`\?`** ,, zapobiega błędnej interpretacji sekwencji znaków trójznaków. (Aby uzyskać informacje na temat sekwencji unikowych, zobacz [Sekwencje ucieczki](../c-language/escape-sequences.md)). Na przykład, jeśli spróbujesz wydrukować ciąg `What??!` za pomocą tej `printf` instrukcji

```C
printf( "What??!\n" );
```

ciąg jest drukowany, `What|` ponieważ `??!` jest sekwencją trójznaków, która jest zastępowana `|` znakiem. Napisz instrukcję w następujący sposób, aby poprawnie wydrukować ciąg:

```C
printf( "What?\?!\n" );
```

W tej instrukcji `printf`, znak ucieczki ukośnika odwrotnego przed drugim znakiem zapytania zapobiega błędnej interpretacji `??!` jako trójznaku.

## <a name="see-also"></a>Zobacz także

[`/Zc:trigraphs`(Trigraphs podstawienia)](../build/reference/zc-trigraphs-trigraphs-substitution.md)<br/>
[Identyfikatory języka C](../c-language/c-identifiers.md)
