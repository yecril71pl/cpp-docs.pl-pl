---
title: "C2439 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79b6ef4b6182a525bb8c8fc5e7e9fc7bd541f870
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2439"></a>C2439 błąd kompilatora
'Identyfikator': nie można zainicjować elementu członkowskiego  
  
 Nie można zainicjować klasy, struktury lub elementu członkowskiego typu union.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Próba zainicjowania pośredniej klasy podstawowej lub struktury.  
  
2.  Próba zainicjowania dziedziczonego elementu członkowskiego klasy lub struktury. Dziedziczony element członkowski musi zostać zainicjowany przez Konstruktor klasy lub struktury.