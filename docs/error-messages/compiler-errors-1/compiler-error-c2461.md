---
title: "C2461 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2461
dev_langs: C++
helpviewer_keywords: C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 18413443abb074d16c0d813de660555f8ba2b4c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2461"></a>C2461 błąd kompilatora
  
> "*klasy*": składni konstruktora brakuje parametrów formalnych  
  
 Konstruktor dla klasy nie określa żadnych parametrów formalnych. Deklaracja konstruktora musi określić formalnej listy parametrów. Lista może być pusta.  
  
Aby rozwiązać ten problem, Dodaj parę nawiasów po deklaracji *klasy*:: **klasy*.  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład przedstawia sposób naprawić C2461:  
  
```cpp  
// C2461.cpp  
// compile with: /c  
class C {  
   C::C;     // C2461  
   C::C();   // OK  
};  
```