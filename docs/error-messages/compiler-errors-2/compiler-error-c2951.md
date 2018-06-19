---
title: C2951 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2951
dev_langs:
- C++
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0883b0942fdfbe3d55a540fbed35a0affc73be5b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241539"
---
# <a name="compiler-error-c2951"></a>C2951 błąd kompilatora
Typ deklaracji są dozwolone tylko w globalnej, przestrzeni nazw lub zakresie klasy  
  
 Nie można zadeklarować ogólne lub szablonu klasy poza globalnych lub zakresie przestrzeni nazw. Jeśli Twoje deklaracje ogólne lub szablonu w pliku dołączenia, upewnij się, że plik dołączania jest w zakresie globalnym.  
  
 Poniższy przykład generuje C2951:  
  
```  
// C2951.cpp  
template <class T>  
class A {};  
  
int main() {  
   template <class T>   // C2951  
   class B {};  
}  
```  
  
 C2951 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2951b.cpp  
// compile with: /clr /c  
  
// OK  
generic <class T>   
ref class GC { };  
  
int main() {  
   generic <class T> ref class GC2 {};   // C2951  
}  
```