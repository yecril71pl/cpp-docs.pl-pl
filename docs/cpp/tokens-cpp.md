---
title: Tokeny (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba2e1a6cc36e4e5f2f785c1e5dff03c6fb5e392d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="tokens-c"></a>Tokeny (C++)
Token jest najmniejszy element programu C++, który jest przydatny do kompilatora. Analizator C++ rozpoznaje rodzaju tokenów: identyfikatory, słowa kluczowe literały, operatory, znaki interpunkcyjne i innych separatorów. Strumień tokeny te tworzą jednostce tłumaczenia.  
  
 Tokeny są zwykle rozdzielone *biały znak*. Biały znak może być jeden lub więcej:  
  
-   Puste  
  
-   Karty poziomej lub pionowej  
  
-   Nowe wiersze  
  
-   Formfeeds  
  
-   Komentarze  
  
 Analizator rozpoznaje słów kluczowych, identyfikatory literały, Operatorzy i znaki interpunkcyjne. Informacje o określonych typach tokenów, zobacz [słowa kluczowe](../cpp/keywords-cpp.md), [identyfikatory](../cpp/identifiers-cpp.md), [liczbowe, Boolean i literały wskaźnika](../cpp/numeric-boolean-and-pointer-literals-cpp.md), [literały ciągów i znakowe ](../cpp/string-and-character-literals-cpp.md), [Literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md), [operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md), i [znaki interpunkcyjne](../cpp/punctuators-cpp.md). Biały znak jest ignorowany, z wyjątkiem zgodnie z wymaganiami do oddzielania tokenów.  
  
 Tokeny przetwarzania wstępnego są używane w fazy wstępnego przetwarzania do generowania tokenu strumienia przekazanego do kompilatora. Wstępnego przetwarzania tokenu kategorie są nazwy nagłówka, identyfikatory, numery przetwarzania wstępnego, literały znaków, literałów ciągów, operatory przetwarzania wstępnego i znaki interpunkcyjne i jednego z systemem innym niż białe znaki, które nie pasują do jednego z innych kategorii. Literały znaków i ciąg może być literały definiowane przez użytkownika. Przetwarzanie wstępne tokeny mogą być oddzielone biały znak lub komentarzy.  
  
 Analizator oddziela tokeny ze strumienia wejściowego, tworząc najdłuższy możliwe tokenu przy użyciu znaków wejściowych skanowania od lewej do prawej. Należy wziąć pod uwagę fragmentu kodu:  
  
```  
a = i+++j;  
```  
  
 Programisty, autorze kod było zamierzone jednej z tych dwóch instrukcji:  
  
```  
a = i + (++j)  
  
a = (i++) + j  
```  
  
 Ponieważ analizator tworzy token najdłuższym możliwe ze strumienia wejściowego, wybiera interpretacji drugiego, co tokeny `i++`, `+`, i `j`.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje leksykalne](../cpp/lexical-conventions.md)