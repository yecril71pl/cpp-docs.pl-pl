---
title: novtable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: novtable_cpp
dev_langs: C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26dc6677c6fcc7ab3834d3bb13d9e85dd0d8ede0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Jest to `__declspec` rozszerzonych atrybutów.  
  
 Ta forma `__declspec` mogą być stosowane do każdej deklaracji klasy, ale powinny być stosowane tylko do klasy czystego interfejsu, oznacza to, klasy, które nigdy nie będzie można utworzyć wystąpienia samodzielnie. `__declspec` Zatrzymuje kompilatora z generowania kodu zainicjować vfptr constructor(s) i destruktora klasy. W wielu przypadkach powoduje usunięcie tylko odwołania do vtable, które są skojarzone z klasą i w związku z tym konsolidator spowoduje jej usunięcia. Przy użyciu tej formy `__declspec` może spowodować znacznego zmniejszenia rozmiaru kodu.  
  
 Przy próbie utworzenia wystąpienia klasy oznaczonej jako `novtable` , a następnie uzyskiwanie dostępu do członka klasy, zostanie wyświetlony naruszenia zasad dostępu (AV).  
  
## <a name="example"></a>Przykład  
  
```  
// novtable.cpp  
#include <stdio.h>  
  
struct __declspec(novtable) X {  
   virtual void mf();  
};  
  
struct Y : public X {  
   void mf() {  
      printf_s("In Y\n");  
   }  
};  
  
int main() {  
   // X *pX = new X();  
   // pX->mf();   // Causes a runtime access violation.  
  
   Y *pY = new Y();  
   pY->mf();  
}  
```  
  
```Output  
In Y  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)