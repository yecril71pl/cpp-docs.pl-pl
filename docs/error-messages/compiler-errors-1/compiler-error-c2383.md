---
title: "C2383 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2383
dev_langs: C++
helpviewer_keywords: C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7f89545b9428bd5e901c72d895b5c23317646c26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2383"></a>C2383 błąd kompilatora
"*symbol*": argumenty domyślne są niedozwolone w tym symbolu  
  
 Kompilator języka C++ nie zezwala na wskaźniki do funkcji argumenty domyślne.  
  
 Ten kod został zaakceptowany przez kompilator języka Visual C++ w wersji sprzed programu Visual Studio 2005, ale teraz zwraca błąd. Kod, który działa we wszystkich wersjach programu Visual C++ nie należy przypisywać wartość domyślną do argumentu wskaźnika do funkcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie generuje C2383 i przedstawiono możliwe rozwiązania:  
  
```cpp  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```