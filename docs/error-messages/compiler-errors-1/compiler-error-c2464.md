---
title: "C2464 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2464
dev_langs: C++
helpviewer_keywords: C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7e2600608ae490363d9042ad72ad91bf7cfe32d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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