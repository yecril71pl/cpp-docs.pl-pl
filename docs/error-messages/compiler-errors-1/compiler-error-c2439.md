---
title: C2439 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33bfe8ebf00850a54020b2a3f21159daf28b7224
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2439"></a>C2439 błąd kompilatora
'Identyfikator': nie można zainicjować elementu członkowskiego  
  
 Nie można zainicjować klasy, struktury lub elementu członkowskiego typu union.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Próba zainicjowania pośredniej klasy podstawowej lub struktury.  
  
2.  Próba zainicjowania dziedziczonego elementu członkowskiego klasy lub struktury. Dziedziczony element członkowski musi zostać zainicjowany przez Konstruktor klasy lub struktury.