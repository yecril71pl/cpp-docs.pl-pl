---
title: C2461 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47aee3122dad3e875cf58d5a41bcadda297e1463
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197640"
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