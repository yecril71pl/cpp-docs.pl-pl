---
title: C2464 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2464
dev_langs:
- C++
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98949ba463f432666753cb39de37bb4bf8f7276f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226029"
---
# <a name="compiler-error-c2464"></a>C2464 błąd kompilatora
'Identyfikator': nie można użyć "new", aby przydzielić odwołanie  
  
 Identyfikator odniesienia przydzielony przy `new` operatora. Odwołania nie są obiekty pamięci, dlatego `new` nie może zwracać wskaźnik do nich. Deklarowanie odwołania, należy użyć składni standardowe deklaracja zmiennej.  
  
 Poniższy przykład generuje C2464:  
  
```  
// C2464.cpp  
int main() {  
   new ( int& ir );   // C2464  
}  
```