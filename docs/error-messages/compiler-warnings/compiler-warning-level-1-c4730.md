---
title: Ostrzeżenie (poziom 1) C4730 kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4730
dev_langs:
- C++
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 467d9fd04e2fef78d480fc4db1417b6e4c8d5641
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285476"
---
# <a name="compiler-warning-level-1-c4730"></a>Ostrzeżenie C4730 kompilatora (poziom 1)
"main": połączenie typu _m64 i liczb zmiennoprzecinkowych wyrażenia może spowodować niepoprawny kod  
  
 Funkcja wykorzystuje [__m64](../../cpp/m64.md) i **float**/**podwójne** typów. Ponieważ MMX i rejestrów zmiennoprzecinkowych mają takie same fizycznych zarejestrować miejsca (nie można używać jednocześnie), za pomocą `__m64` i **float**/**podwójne** typy w tym samym funkcja może spowodować uszkodzenie danych, może doprowadzić do wyjątku.  
  
 Aby bezpiecznie korzystać `__m64` typy i typów zmiennoprzecinkowych w tej samej funkcji każdą instrukcję, która korzysta z jednego z typów powinny być oddzielone **_m_empty()** (dla MMX) lub **_m_femms()** (dla 3DNow!) wewnętrzne.  
  
 Poniższy przykład generuje C4730:  
  
```  
// C4730.cpp  
// compile with: /W1  
// processor: x86  
#include "mmintrin.h"  
  
void func(double)  
{  
}  
  
int main(__m64 a, __m64 b)  
{  
   __m64 m;  
   double f;  
   f = 1.0;  
   m = _m_paddb(a, b);  
   // uncomment the next line to resolve C4730  
   // _m_empty();  
   func(f * 3.0);   // C4730  
}  
```