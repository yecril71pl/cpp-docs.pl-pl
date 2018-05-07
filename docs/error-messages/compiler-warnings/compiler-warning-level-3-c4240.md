---
title: Kompilatora (poziom 3) ostrzeżenie C4240 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4240
dev_langs:
- C++
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f0691230454ffd935d67c99f58b857cdc1ce0f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4240"></a>Kompilator C4240 ostrzegawcze (poziom 3)
użyto niestandardowego rozszerzenia: dostęp do "classname" teraz zdefiniowany jako "specyfikator dostępu", poprzednio został zdefiniowany jako "specyfikator dostępu"  
  
 W obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), nie można zmienić dostęp do klasy zagnieżdżonej. W obszarze rozszerzenia Microsoft domyślne (/Ze) można z tego ostrzeżenia.  
  
## <a name="example"></a>Przykład  
  
```  
// C4240.cpp  
// compile with: /W3  
class X  
{  
private:  
   class N;  
public:  
   class N  
   {   // C4240  
   };  
};  
  
int main()  
{  
}  
```