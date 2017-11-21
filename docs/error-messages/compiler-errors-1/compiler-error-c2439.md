---
title: "C2439 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2439
dev_langs: C++
helpviewer_keywords: C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6aa5c0dcfd12be6979b0872f001bf0bf26a6e6e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2439"></a>C2439 błąd kompilatora
'Identyfikator': nie można zainicjować elementu członkowskiego  
  
 Nie można zainicjować klasy, struktury lub elementu członkowskiego typu union.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Próba zainicjowania pośredniej klasy podstawowej lub struktury.  
  
2.  Próba zainicjowania dziedziczonego elementu członkowskiego klasy lub struktury. Dziedziczony element członkowski musi zostać zainicjowany przez Konstruktor klasy lub struktury.