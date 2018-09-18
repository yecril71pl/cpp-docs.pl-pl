---
title: podczas gdy Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- while
dev_langs:
- C++
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dfda5807aab0c9930780b8374ffc934dde001c0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096811"
---
# <a name="while-statement-c"></a>while — instrukcja (C)

`while` Instrukcji umożliwia Powtórz instrukcji, dopóki określone wyrażenie przestaje być prawdziwy.

## <a name="syntax"></a>Składnia

*instrukcji iteracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**gdy (***wyrażenie***)***— instrukcja*

*Wyrażenie* musi mieć typ arytmetyczny lub wskaźnika. Wykonanie działa w następujący sposób:

1. *Wyrażenie* jest oceniany.

2. Jeśli *wyrażenie* początkowo wartość false, treść `while` nigdy nie zostaje wykonana instrukcja i kontrola przechodzi z `while` instrukcji do następnej instrukcji w programie.

   Jeśli *wyrażenie* jest wartość true (niezerową), zostaje wykonana instrukcji i proces jest powtarzany, zaczynając od kroku 1.

`while` Instrukcji można także zakończyć, gdy **podziału**, `goto`, lub `return` w ramach instrukcja zostaje wykonana. Użyj **nadal** instrukcję, aby zakończyć iterację bez zamykania `while` pętli. **Nadal** instrukcji przekazuje kontrolę do następnej iteracji `while` instrukcji.

Jest to przykład `while` instrukcji:

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

W tym przykładzie kopiuje znaków ze zbioru `string2` do `string1`. Jeśli `i` jest większa niż lub równa 0, `string2[i]` jest przypisany do `string1[i]` i `i` zostanie zmniejszony. Gdy `i` osiągnie lub spadnie poniżej 0, wykonywanie `while` kończy się.

## <a name="see-also"></a>Zobacz też

[while, instrukcja (C++)](../cpp/while-statement-cpp.md)