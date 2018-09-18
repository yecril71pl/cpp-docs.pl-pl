---
title: Inicjowanie ciągów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e954fc417fb62d3bd08b1c37d445a3d7f2bc9ec9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034879"
---
# <a name="initializing-strings"></a>inicjowanie ciągów

Można zainicjować tablicy znaków (lub znaków dwubajtowych) za pomocą literału ciągu (lub szeroki literał ciągu). Na przykład:

```
char code[ ] = "abc";
```

Inicjuje `code` jako 4 elementowej tablicy znaków. Czwarty element jest znakiem zerowym, która kończy się wszystkich literałów ciągów.

Lista identyfikatorów można tylko tak długo, jak liczba identyfikatorów do zainicjowania. Jeśli określisz rozmiar tablicy, która ma mniej niż ciąg, dodatkowe znaki są ignorowane. Na przykład następująca deklaracja inicjuje `code` jako tablicy znaków trzech elementów:

```
char code[3] = "abcd";
```

Pierwsze trzy znaki inicjatora są przypisane do `code`. Znak `d` i znaku null zakończenie ciągu są odrzucane. Należy pamiętać, że spowoduje to utworzenie niezakończony ciąg (czyli jeden bez wartość 0, aby oznaczyć końca) i generuje komunikat diagnostyczny wskazujący tego warunku.

Deklaracja

```
char s[] = "abc", t[3] = "abc";
```

jest taka sama jak

```
char s[]  = {'a', 'b', 'c', '\0'},
     t[3] = {'a', 'b', 'c' };
```

Jeśli ciąg jest krótszy niż rozmiar określonej tablicy, pozostałe elementy tablicy są inicjowane na wartość 0.

**Microsoft Specific**

W Microsoft C literałów ciągów może być maksymalnie 2048 bajtów długości.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Inicjowanie](../c-language/initialization.md)