---
title: czy-podczas Statement (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- do
- while
dev_langs: C++
helpviewer_keywords: do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40f86574e849bae8c1defafcfeab46fced2d77b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="do-while-statement-c"></a>do-while — instrukcja (C)
`do-while` Instrukcji umożliwia Powtórz instrukcji lub złożonej instrukcji określone wyrażenie staje się wartość false.  
  
## <a name="syntax"></a>Składnia  
 *instrukcji iteracji*:  
 **czy***instrukcji***podczas (***wyrażenie***);**   
  
 *Wyrażenie* w `do-while` instrukcji jest oceniane po wykonaniu treści pętli. W związku z tym treści pętli jest zawsze wykonywana co najmniej raz.  
  
 *Wyrażenie* musi mieć typ arytmetyczny lub wskaźnikowy. Wykonanie przebiega w następujący sposób:  
  
1.  Treść instrukcji jest wykonywana.  
  
2.  Następnie *wyrażenie* oceny. Jeśli *wyrażenie* ma wartość false, `do-while` kończy instrukcji i kontrola przechodzi do następnej instrukcji w programie. Jeśli *wyrażenie* ma wartość true, (niezerowej), proces jest powtarzany, poczynając od kroku 1.  
  
 `do-while` Instrukcji można również zakończyć kiedy **podziału**, `goto`, lub `return` instrukcja jest wykonywana w treści instrukcji.  
  
 To jest przykład `do-while` instrukcji:  
  
```  
do   
{  
    y = f( x );  
    x--;  
} while ( x > 0 );  
```  
  
 W tym `do-while` instrukcji, dwie instrukcje `y = f( x );` i `x--;` są wykonywane niezależnie od początkowej wartości `x`. Następnie `x > 0` oceny. Jeśli `x` jest większa niż 0, treść instrukcji jest wykonywane ponownie i `x > 0` jest ponownie oceniane. Treść instrukcji jest wykonywany wielokrotnie tak długo, jak `x` większe niż 0. Wykonywanie `do-while` kończy instrukcji, gdy `x` staje się 0 ani ujemna. Treści pętli jest wykonywane co najmniej raz.  
  
## <a name="see-also"></a>Zobacz też  
 [czy-while — instrukcja (C++)](../cpp/do-while-statement-cpp.md)