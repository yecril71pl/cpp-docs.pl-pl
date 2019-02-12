---
title: while — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: 4a789f248702f33342a19f95710a8ae313da1d94
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151900"
---
# <a name="while-statement-c"></a>while — instrukcja (C)

`while` Instrukcji umożliwia Powtórz instrukcji, dopóki określone wyrażenie przestaje być prawdziwy.

## <a name="syntax"></a>Składnia

*instrukcji iteracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**gdy (**  *wyrażenie*  **)**  *instrukcja*

*Wyrażenie* musi mieć typ arytmetyczny lub wskaźnika. Wykonanie działa w następujący sposób:

1. *Wyrażenie* jest oceniany.

1. Jeśli *wyrażenie* początkowo wartość false, treść `while` nigdy nie zostaje wykonana instrukcja i kontrola przechodzi z `while` instrukcji do następnej instrukcji w programie.

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

## <a name="see-also"></a>Zobacz także

[while, instrukcja (C++)](../cpp/while-statement-cpp.md)
