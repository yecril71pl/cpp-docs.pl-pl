---
title: "Kompilatora (poziom 2 i 3) ostrzeżenie C4008 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afd45078ac75ec9da8343baa2c203e75b324fb6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Kompilator C4008 ostrzegawcze (poziom 2 i 3)
'Identyfikator': atrybutu ' atrybut ' ignorowane  
  
 Kompilator ignorowane `__fastcall`, **statycznych**, lub **wbudowanego** atrybutu dla funkcji (ostrzeżenia poziomu 3) lub danych (ostrzeżenie poziom 2).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  `__fastcall`atrybut z danymi.  
  
2.  **statyczne** lub **wbudowanego** atrybutem **głównego** funkcji.