---
title: "kontynuować Statement (C) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: continue
dev_langs: C++
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5d0fc645bdeec7ea9ec6df124279140fcd63f77d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="continue-statement-c"></a>continue — instrukcja (C)
`continue` Instrukcja przekazuje formantu do następnej iteracji najbliższej otaczającej `do`, `for`, lub `while` instrukcji, w którym zostanie wyświetlona, pomijanie wszelkie pozostałe instrukcje w `do`, `for`, lub `while` treść instrukcji.  
  
## <a name="syntax"></a>Składnia  
 `jump-statement`:  
 `continue;`  
  
 Następnej iteracji `do`, `for`, lub `while` instrukcji jest określane w następujący sposób:  
  
-   W ramach `do` lub `while` instrukcji następnej iteracji rozpoczyna się od wyrażenia reevaluating `do` lub `while` instrukcji.  
  
-   A `continue` instrukcji w `for` instrukcja powoduje, że wyrażenie pętli `for` instrukcji, które ma zostać obliczone. Następnie kompilator reevaluates wyrażenie warunkowe i, w zależności od wyniku albo kończy lub iteruje treść instrukcji. Zobacz [dla instrukcji](../c-language/for-statement-c.md) Aby uzyskać więcej informacji na temat `for` instrukcji i jego symboli nieterminalnych.  
  
 To jest przykład `continue` instrukcji:  
  
```  
while ( i-- > 0 )   
{  
    x = f( i );  
    if ( x == 1 )  
        continue;  
    y += x * x;  
}  
```  
  
 W tym przykładzie jest wykonywane w treści instrukcji podczas `i` jest większa niż 0. Pierwszy `f(i)` jest przypisany do `x`; następnie, jeśli `x` jest równa 1, `continue` instrukcja jest wykonywana. Pozostałe instrukcje w treści są ignorowane, a wykonanie wznawia w górnej części pętli z oceną testu pętli.  
  
## <a name="see-also"></a>Zobacz też  
 [Continue — instrukcja](../cpp/continue-statement-cpp.md)