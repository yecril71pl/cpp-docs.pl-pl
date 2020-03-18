---
title: do-while — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- do
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 3658fe7635ad77db6d6e08ff9d7c30e29d665721
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438588"
---
# <a name="do-while-statement-c"></a>do-while — instrukcja (C)

Instrukcja *do-while* umożliwia powtarzanie instrukcji lub złożonej instrukcji do momentu, gdy określone wyrażenie przyjmie wartość false.

## <a name="syntax"></a>Składnia

*iteracja-instrukcja*: &nbsp;&nbsp;&nbsp;&nbsp;**do***instrukcji***while (** *wyrażenie* **);**

*Wyrażenie* w instrukcji do *-while* jest oceniane po wykonaniu treści pętli. W związku z tym treść pętli jest zawsze wykonywana co najmniej raz.

*Wyrażenie* musi mieć typ arytmetyczny lub wskaźnikowy. Wykonanie przebiega w następujący sposób:

1. Treść instrukcji jest wykonywana.

1. Następnie *wyrażenie* jest oceniane. Jeśli *wyrażenie* ma wartość false, instrukcja *do-while* kończy działanie i kontrola przechodzi do następnej instrukcji w programie. Jeśli *wyrażenie* jest prawdziwe (niezerowe), proces jest powtarzany, zaczynając od kroku 1.

Instrukcja *do-while* może również kończyć się, gdy instrukcja **Break**, **goto**lub **Return** jest wykonywana w treści instrukcji.

Jest to przykładowa instrukcja do *-while* :

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

W tej instrukcji *do-while* są wykonywane dwie instrukcje `y = f( x );` i `x--;`, niezależnie od początkowej wartości `x`. Następnie `x > 0` jest oceniane. Jeśli `x` jest większa niż 0, treść instrukcji jest wykonywana ponownie i `x > 0` zostanie przeszacowana. Treść instrukcji jest wykonywana wielokrotnie, o ile `x` pozostanie większa niż 0. Wykonywanie instrukcji *do-while* kończy się, gdy `x` stanie się 0 lub ujemny. Treść pętli jest wykonywana co najmniej raz.

## <a name="see-also"></a>Zobacz też

[do-while, instrukcja (C++)](../cpp/do-while-statement-cpp.md)
