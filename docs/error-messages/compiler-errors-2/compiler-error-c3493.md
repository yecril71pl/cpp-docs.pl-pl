---
title: C3493 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3aec62bfff59396ec73141746193e4e3f16d84fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257319"
---
# <a name="compiler-error-c3493"></a>C3493 błąd kompilatora
"var" nie może być niejawnie przechwycone, ponieważ nie podano żadnego domyślnego trybu przechwytywania  
  
 Przechwytywanie wyrażenia lambda pusta, `[]`, określa jawnie nie jest wyrażeniem lambda lub niejawnie przechwytywania żadnych zmiennych.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Podaj domyślny tryb przechwytywania, lub  
  
-   Jawnie przechwycić co najmniej jedną zmienną.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3493, ponieważ modyfikuje zmienną zewnętrznych, ale określa klauzuli pusty przechwytywania:  
  
```  
// C3493a.cpp  
  
int main()  
{  
   int m = 55;  
   [](int n) { m = n; }(99); // C3493  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rozpoznaje C3493, określając-reference jako domyślny tryb przechwytywania.  
  
```  
// C3493b.cpp  
  
int main()  
{  
   int m = 55;  
   [&](int n) { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)