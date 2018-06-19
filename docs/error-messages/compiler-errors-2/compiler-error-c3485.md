---
title: C3485 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3485
dev_langs:
- C++
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cd9de6f300fed673d588df60d7acca15b104b61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258137"
---
# <a name="compiler-error-c3485"></a>C3485 błąd kompilatora
Definicja lambdy nie może mieć żadnych kwalifikatorów cv  
  
 Nie można użyć `const` lub `volatile` kwalifikator jako część definicji wyrażenia lambda.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń `const` lub `volatile` kwalifikator w definicji wyrażenia lambda.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3485, ponieważ używa on `const` kwalifikator jako część definicji wyrażenia lambda:  
  
```  
// C3485.cpp  
  
int main()  
{  
   auto x = []() const mutable {}; // C3485  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)