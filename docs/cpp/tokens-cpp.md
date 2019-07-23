---
title: TokenyC++()
ms.date: 11/04/2016
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
ms.openlocfilehash: cd104b7308716ca182374bbff2df61731c84d574
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376257"
---
# <a name="tokens-c"></a>TokenyC++()

Token jest najmniejszym elementem C++ programu, który jest zrozumiały dla kompilatora. C++ Analizator rozpoznaje te rodzaje tokenów: identyfikatory, słowa kluczowe, literały, operatory, przerywniki i inne separatory. Strumień tych tokenów stanowi jednostkę tłumaczenia.

Tokeny są zwykle oddzielane znakami *odstępu*. Biały znak może mieć jedną lub więcej:

- Puste wartości

- Karty poziome lub pionowe

- Nowe wiersze

- Źródła formularzy

- Komentarze

Analizator rozpoznaje słowa kluczowe, identyfikatory, literały, operatory i przerywniki. Aby uzyskać informacje na temat określonych typów tokenów, zobacz [słowa kluczowe](../cpp/keywords-cpp.md), [identyfikatory](../cpp/identifiers-cpp.md), [liczbowe, wartości logiczne i literały wskaźnika](../cpp/numeric-boolean-and-pointer-literals-cpp.md), literały [ciągów i znaków](../cpp/string-and-character-literals-cpp.md), [literały zdefiniowane przez użytkownika](../cpp/user-defined-literals-cpp.md), [ C++ operatory wbudowane, Pierwszeństwo i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)oraz [przerywniki](../cpp/punctuators-cpp.md). Biały znak jest ignorowany, z wyjątkiem sytuacji, gdy jest to wymagane do oddzielania tokenów.

Tokeny przetwarzania wstępnego są używane w fazach przetwarzania wstępnego w celu wygenerowania strumienia tokenu przesłanego do kompilatora. Wstępnie przetworzone kategorie tokenów to nazwy nagłówków, identyfikatory, numery przetwarzania wstępnego, literały znaków, literały ciągów, operatory przetwarzania wstępnego i przerywniki oraz pojedyncze znaki niebędące znakami odstępu, które nie pasują do jednej z innych kategorii. Literały znaku i ciągu mogą być literałami zdefiniowanymi przez użytkownika. Tokeny przetwarzania wstępnego mogą być oddzielone znakami odstępu lub komentarzem.

Parser oddziela tokeny ze strumienia wejściowego, tworząc najdłuższy token możliwy przy użyciu znaków wejściowych w skanowaniu od lewej do prawej. Rozważmy następujący fragment kodu:

```cpp
a = i+++j;
```

Programista, który napisał kod, może mieć zamierzoną jedną z następujących dwóch instrukcji:

```cpp
a = i + (++j)

a = (i++) + j
```

Ponieważ Analizator tworzy najdłuższy token możliwy ze strumienia wejściowego, wybiera drugą interpretację, tworząc tokeny `i++` `+`, i `j`.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)