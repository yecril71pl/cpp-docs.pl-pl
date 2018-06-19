---
title: 2.6.4 konstrukcja niepodzielna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66f0dc8469d1d70b2697df1fe120f10142d90dbe
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688131"
---
# <a name="264-atomic-construct"></a>2.6.4 — konstrukcja niepodzielna
`atomic` Dyrektywy zapewnia atomowo, aktualizowanie lokalizacji pamięci zamiast ujawnienie go możliwości wielu równoczesnych zapisywania wątków. Składnia `atomic` dyrektywy wygląda następująco:  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 Instrukcja wyrażeń musi mieć jeden z następujących formatów:  
  
 *x binop*= *wyrażenie*  
  
 x ++  
  
 ++ x  
  
 x--  
  
 --x  
  
 W poprzednim wyrażenia:  
  
-   *x* wyrażenie l-wartością skalarną typu.  
  
-   *wyrażenie* wyrażenie skalarne, typ i nie odwołuje się obiekt wskazywany przez *x*.  
  
-   `binop` nie jest przeciążony operator i jest jednym z +, *, -, / &, ^, &#124;, <\<, lub >>.  
  
 Mimo że jest zdefiniowane w implementacji czy implementację zastępuje wszystkie `atomic` dyrektywy z **krytyczne** dyrektywy, które mają taki sam unikatowy *nazwa*, `atomic` — dyrektywa zezwala lepsze optymalizacji. Dostępne są często sprzętu instrukcjami który można wykonać aktualizacji atomic o najmniejszej obciążenie.  
  
 Tylko obciążenia i magazynu obiekt wskazywany przez *x* są atomic; oceny *wyrażenie* nie jest atomic. Aby uniknąć wyścigu, wszystkie aktualizacje lokalizacji równolegle powinien być chroniony za `atomic` dyrektywy, z wyjątkiem tych, które są znane wolnych wyścigu.  
  
 Ograniczenia `atomic` dyrektywy są następujące:  
  
-   Wszystkie atomic odwołania do lokalizacji magazynu x w programie muszą mieć zgodne z typem.  
  
## <a name="examples"></a>Przykłady:  
  
```  
extern float a[], *p = a, b;  
/* Protect against races among multiple updates. */  
#pragma omp atomic  
a[index[i]] += b;  
/* Protect against races with updates through a. */  
#pragma omp atomic  
p[i] -= 1.0f;  
  
extern union {int n; float x;} u;  
/* ERROR - References through incompatible types. */  
#pragma omp atomic  
u.n++;  
#pragma omp atomic  
u.x -= 1.0f;  
```