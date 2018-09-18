---
title: czy-while Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do
- while
dev_langs:
- C++
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef670aca60b2e3156ea70480a1dafc315ae60624
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061479"
---
# <a name="do-while-statement-c"></a>do-while — instrukcja (C)

*Czy — gdy* instrukcji umożliwia Powtórz instrukcji lub instrukcji złożonej, na którym określone wyrażenie przestaje być prawdziwy.

## <a name="syntax"></a>Składnia

*instrukcji iteracji*: &nbsp; &nbsp; &nbsp; &nbsp; **czy***instrukcji***podczas (** *wyrażenie***);** 

*Wyrażenie* w *czy-podczas* instrukcji jest oceniane, po wykonaniu treść pętli. W związku z tym treść pętli jest zawsze wykonywana co najmniej raz.

*Wyrażenie* musi mieć typ arytmetyczny lub wskaźnika. Wykonanie działa w następujący sposób:

1. Instrukcja zostaje wykonana.

2. Następnie *wyrażenie* jest oceniany. Jeśli *wyrażenie* ma wartość FAŁSZ, *czy — gdy* kończy się i przekazuje kontrolę do następnej instrukcji w programie. Jeśli *wyrażenie* jest prawdziwe (niezerowe), proces jest powtarzany, zaczynając od kroku 1.

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

## <a name="see-also"></a>Zobacz też

[do-while, instrukcja (C++)](../cpp/do-while-statement-cpp.md)