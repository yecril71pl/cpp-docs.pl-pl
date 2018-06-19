---
title: C3803 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3803
dev_langs:
- C++
helpviewer_keywords:
- C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d720e2f94cc4a480122413e31b897ec1718ebc15
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269260"
---
# <a name="compiler-error-c3803"></a>C3803 błąd kompilatora
"właściwość": właściwość ma typ, który jest niezgodny z jednym z jego akcesorów "akcesor"  
  
 Typ właściwości zdefiniowane z [właściwości](../../cpp/property-cpp.md) jest niezgodny z typem zwracanym dla jednej z jego funkcji dostępu.  
  
 Poniższy przykład generuje C3803:  
  
```  
// C3803.cpp  
struct A  
{  
   __declspec(property(get=GetIt)) int i;  
   char GetIt()  
   {  
      return 0;  
   }  
  
   /*  
   // try the following definition instead  
   int GetIt()  
   {  
      return 0;  
   }  
   */  
}; // C3803  
  
int main()  
{  
}  
```