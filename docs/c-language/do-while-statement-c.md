---
title: do-while — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- do
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 4a10b9df9f7276eb8e241d76726bca26f2c0cb75
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218874"
---
# <a name="do-while-statement-c"></a>do-while — instrukcja (C)

Instrukcja *do-while* umożliwia powtarzanie instrukcji lub złożonej instrukcji do momentu, gdy określone wyrażenie przyjmie wartość false.

## <a name="syntax"></a>Składnia

*iteracji-instrukcji*: &nbsp; &nbsp; &nbsp; &nbsp; **`do`** *instrukcja***while (***wyrażenie***);**        

*Wyrażenie* w instrukcji do *-while* jest oceniane po wykonaniu treści pętli. W związku z tym treść pętli jest zawsze wykonywana co najmniej raz.

*Wyrażenie* musi mieć typ arytmetyczny lub wskaźnikowy. Wykonanie przebiega w następujący sposób:

1. Treść instrukcji jest wykonywana.

1. Następnie *wyrażenie* jest oceniane. Jeśli *wyrażenie* ma wartość false, instrukcja *do-while* kończy działanie i kontrola przechodzi do następnej instrukcji w programie. Jeśli *wyrażenie* jest prawdziwe (niezerowe), proces jest powtarzany, zaczynając od kroku 1.

Instrukcja *do-while* może również kończyć się, gdy **`break`** **`goto`** instrukcja,, lub **`return`** jest wykonywana w treści instrukcji.

Jest to przykładowa instrukcja do *-while* :

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

W tej instrukcji do *-while* dwie instrukcje `y = f( x );` i `x--;` są wykonywane niezależnie od wartości początkowej `x` . Następnie `x > 0` jest oceniane. Jeśli `x` jest większa niż 0, treść instrukcji jest wykonywana ponownie i `x > 0` zostanie przeszacowana. Treść instrukcji jest wykonywana wielokrotnie, o ile `x` pozostanie większa niż 0. Wykonywanie instrukcji *do-while* kończy `x` się, gdy przyjmie wartość 0 lub ujemną. Treść pętli jest wykonywana co najmniej raz.

## <a name="see-also"></a>Zobacz także

[do-While — Instrukcja (C++)](../cpp/do-while-statement-cpp.md)
