---
title: "Kompilatora (poziom 1) ostrzeżenie C4556 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- xml
- C4556
dev_langs:
- C++
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a55e969849a3f13464e372c1dcfe0aa0956a564d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4556"></a>Kompilator C4556 ostrzegawcze (poziom 1)
wartość wewnętrznego argumentu natychmiastowego "wartość" jest poza zakresem "ich - górnej granicy"  
  
 Wewnętrznie odpowiada instrukcji sprzętu. Instrukcja sprzętu ma stałą liczbę bitów do kodowania stała. Jeśli ***wartość*** jest poza zakresem, jego będzie Koduj poprawnie. Kompilator obcina dodatkowe bity.  
  
 Poniższy przykład generuje C4556:  
  
```  
// C4556.cpp  
// compile with: /W1  
// processor: x86 IPF  
#include <xmmintrin.h>  
void test()  
{  
   __m64 m;  
   _m_pextrw(m, 5);   // C4556  
}  
int main()  
{  
}  
```