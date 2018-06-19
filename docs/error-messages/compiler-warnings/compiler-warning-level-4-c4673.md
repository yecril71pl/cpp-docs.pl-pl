---
title: Kompilatora (poziom 4) ostrzeżenie C4673 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4673
dev_langs:
- C++
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aecb4b3590a3cb1a1b055cd1e3377d00c5d0e5bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295928"
---
# <a name="compiler-warning-level-4-c4673"></a>Kompilator C4673 ostrzegawcze (poziom 4)
wyrzucanie "identyfikator" następujących typów, nie zostanie uwzględniony w obszarze przechwytywania  
  
 Obiekt throw nie mogą być obsługiwane w **catch** bloku. Poszczególnych typów, które nie mogą być obsługiwane na liście błędów wyjścia bezpośrednio po wiersz zawierający to ostrzeżenie. Każdy nieobsługiwany typ ma własną ostrzeżenie. Przeczytaj ostrzeżenia dla każdego określonego typu, aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4673:  
  
```  
// C4673.cpp  
// compile with: /EHsc /W4  
class Base {  
private:  
   char * m_chr;  
public:  
   Base() {  
      m_chr = 0;  
   }  
  
   ~Base() {  
      if(m_chr)  
         delete m_chr;  
   }  
};  
  
class Derv : private Base {  
public:  
   Derv() {}  
   ~Derv() {}  
};  
  
int main() {  
   try {  
      Derv D1;  
      // delete previous line, uncomment the next line to resolve  
      // Base D1;  
      throw D1;   // C4673  
   }  
  
   catch(...) {}  
}  
```