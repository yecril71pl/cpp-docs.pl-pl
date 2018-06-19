---
title: Kompilatora (poziom 2 i 3) ostrzeżenie C4008 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cdc88f222f9e5ce3829a63c131c955ce2abdd7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294261"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Kompilator C4008 ostrzegawcze (poziom 2 i 3)
'Identyfikator': atrybutu ' atrybut ' ignorowane  
  
 Kompilator ignorowane `__fastcall`, **statycznych**, lub **wbudowanego** atrybutu dla funkcji (ostrzeżenia poziomu 3) lub danych (ostrzeżenie poziom 2).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  `__fastcall` atrybut z danymi.  
  
2.  **statyczne** lub **wbudowanego** atrybutem **głównego** funkcji.