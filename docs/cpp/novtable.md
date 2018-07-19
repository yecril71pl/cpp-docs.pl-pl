---
title: novtable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- novtable_cpp
dev_langs:
- C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ad0c50330d174a6139ce6e588b278e03cd99562
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947888"
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Jest to **__declspec** atrybutów rozszerzonych.  
  
 Ta forma **__declspec** mogą być stosowane do dowolnej deklaracji klasy, ale tylko stosuje się do klasy interfejsu czystego, oznacza to, klas, które nigdy nie zostać utworzone samodzielnie. **__Declspec** zatrzymuje kompilator generuje kod, aby zainicjować vfptr constructor(s) i destruktor klasy. W wielu przypadkach spowoduje to usunięcie tylko odwołania do vtable, które są skojarzone z klasy i w związku z tym, konsolidator spowoduje usunięcie go. Przy użyciu tej formy **__declspec** może doprowadzić do znacznego zmniejszenia rozmiaru kodu.  
  
 Jeśli użytkownik podejmie próbę utworzenia wystąpienia klasy oznaczone `novtable` i następnie uzyskać dostęp do składowej klasy, zostanie wyświetlony naruszenie zasad dostępu (pliki audio i wideo).  
  
## <a name="example"></a>Przykład  
  
```cpp 
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
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)