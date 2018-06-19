---
title: C2626 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2626
dev_langs:
- C++
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b7b2ea1473b4226382e9aa3bd17b0bfc092f5cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232428"
---
# <a name="compiler-error-c2626"></a>C2626 błąd kompilatora
"identyfikator": elementu członkowskiego prywatnych lub chronionych danych nie jest dozwolona w anonimowym struktury lub związku  
  
 Członek anonimowe struktura lub związek musi mieć publicznego dostępu.  
  
 Poniższy przykład generuje C2626:  
  
```  
// C2626.cpp  
int main() {  
   union {  
   protected:  
      int j;     // C2626, j is protected  
   private:  
      int k;     // C2626, k is private  
   };  
}  
```  
  
 Aby rozwiązać ten problem, Usuń wszystkie znaczniki prywatne lub chronione:  
  
```  
// C2626b.cpp  
int main() {  
   union {  
   public:  
      int i;   // OK, i is public  
   };  
}  
```