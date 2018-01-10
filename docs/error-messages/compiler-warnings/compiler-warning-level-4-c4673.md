---
title: "Kompilatora (poziom 4) ostrzeżenie C4673 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4673
dev_langs: C++
helpviewer_keywords: C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bff39a9045ba1543f42eb7e02b82565421969d8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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