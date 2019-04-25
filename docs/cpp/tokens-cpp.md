---
title: Tokeny (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
ms.openlocfilehash: 1606df56191ec00ffea543dedd3fd4eda98d01c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330443"
---
# <a name="tokens-c"></a>Tokeny (C++)

Token jest najmniejszy element program w języku C++, która ma znaczenie dla kompilatora. Analizator składni języka C++ rozpoznaje tych rodzajów tokenów: identyfikatory, słowa kluczowe, literały, operatory, przerywniki języka i innych separatorów. Tworzy strumień tokeny te jednostki translacji.

Tokeny są zwykle rozdzielone *biały*. Biały znak może być jeden lub więcej:

- Puste

- Poziomą lub pionową karty

- Nowe wiersze

- Formfeeds

- Komentarze

Analizator rozpoznaje słów kluczowych, identyfikatory, literały, operatorów i przerywniki języka. Informacje o określonych typach tokenu, zobacz [słowa kluczowe](../cpp/keywords-cpp.md), [identyfikatory](../cpp/identifiers-cpp.md), [numeryczne, wartości logicznych i literały wskaźnika](../cpp/numeric-boolean-and-pointer-literals-cpp.md), [literały ciągów i znakowe ](../cpp/string-and-character-literals-cpp.md), [Literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md), [C++ wbudowane operatory, pierwszeństwo i kojarzenie](../cpp/cpp-built-in-operators-precedence-and-associativity.md), i [przerywniki języka](../cpp/punctuators-cpp.md). Biały znak jest ignorowany, z wyjątkiem zgodnie z potrzebami do oddzielania tokenów.

Tokeny wstępnego przetwarzania są używane w fazy przetwarzania wstępnego w celu wygenerowania strumień tokenu przekazywane do kompilator. Przetwarzania wstępnego kategorie tokenu są nazwy nagłówków, identyfikatory, numery przetwarzania wstępnego, literały znakowe, literałów ciągów, operatory przetwarzania wstępnego i przerywniki języka i pojedyncze znaki inne niż odstępu, które nie pasują do jednej z innych kategorii. Literały znakowe i może być literały definiowane przez użytkownika. Przetworzone wstępnie tokeny mogą być oddzielone biały znak lub komentarzy.

Analizator oddziela tokenów ze strumienia wejściowego, tworząc najdłużej możliwe tokenu przy użyciu wprowadzonych znaków podczas skanowania od lewej do prawej. Należy wziąć pod uwagę fragmentu kodu:

```cpp
a = i+++j;
```

Programisty, który napisał kod było zamierzone jednej z tych dwóch instrukcji:

```cpp
a = i + (++j)

a = (i++) + j
```

Ponieważ analizator tworzy token najdłuższy możliwe ze strumienia wejściowego, wybiera ona drugi interpretacji, dzięki czemu tokenów `i++`, `+`, i `j`.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)