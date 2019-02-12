---
title: do-while — instrukcja (C)
ms.date: 11/04/2016
f1_keywords:
- do
- while
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 052b02beca49f5de19c6f68cc475edb5f5daf6e2
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147506"
---
# <a name="do-while-statement-c"></a>do-while — instrukcja (C)

*Czy — gdy* instrukcji umożliwia Powtórz instrukcji lub instrukcji złożonej, na którym określone wyrażenie przestaje być prawdziwy.

## <a name="syntax"></a>Składnia

*instrukcji iteracji*: &nbsp; &nbsp; &nbsp; &nbsp; **czy***instrukcji***podczas (** *wyrażenie***);**

*Wyrażenie* w *czy-podczas* instrukcji jest oceniane, po wykonaniu treść pętli. W związku z tym treść pętli jest zawsze wykonywana co najmniej raz.

*Wyrażenie* musi mieć typ arytmetyczny lub wskaźnika. Wykonanie działa w następujący sposób:

1. Instrukcja zostaje wykonana.

1. Następnie *wyrażenie* jest oceniany. Jeśli *wyrażenie* ma wartość FAŁSZ, *czy — gdy* kończy się i przekazuje kontrolę do następnej instrukcji w programie. Jeśli *wyrażenie* jest prawdziwe (niezerowe), proces jest powtarzany, zaczynając od kroku 1.

*Czy — podczas* instrukcji można także zakończyć, gdy **podziału**, **goto**, lub **zwracają** instrukcja jest wykonywana w treści instrukcji.

Jest to przykład *czy-podczas* instrukcji:

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

W tym *czy — gdy* instrukcji, dwie instrukcje `y = f( x );` i `x--;` są wykonywane, bez względu na wartość początkową `x`. Następnie `x > 0` jest oceniany. Jeśli `x` jest większa niż 0, instrukcja zostaje wykonana ponownie i `x > 0` jest ponownie oceniane. Instrukcja zostaje wykonana wielokrotnie tak długo, jak `x` większe niż 0. Wykonywanie *czy — gdy* instrukcji skończy się, gdy `x` staje się 0 ani ujemna. Treść pętli jest wykonywane co najmniej raz.

## <a name="see-also"></a>Zobacz także

[do-while, instrukcja (C++)](../cpp/do-while-statement-cpp.md)
