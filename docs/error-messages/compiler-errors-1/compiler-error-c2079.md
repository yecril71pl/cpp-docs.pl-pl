---
title: C2079 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2079
dev_langs:
- C++
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b29200be08c10dcfaeb178941309c6f3aec6ff9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168035"
---
# <a name="compiler-error-c2079"></a>C2079 błąd kompilatora
'Identyfikator' używa niezdefiniowanego klasy/struktury/Unii 'name'  
  
 Określony identyfikator jest niezdefiniowana klasy, struktury lub związku.  
  
 Ten błąd może być spowodowany przez inicjowanie związek anonimowy.  
  
 Poniższy przykład generuje C2079:  
  
```  
// C2079.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   std::ifstream g;   // C2079  
}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2079b.cpp  
// compile with: /EHsc  
#include <fstream>  
int main( ) {  
   std::ifstream g;  
}  
```  
  
 C2079 może również wystąpić, Jeśli spróbujesz deklarowanie obiektu na stosie typu, w których deklaracja przekazująca dalej znajduje się tylko w zakresie.  
  
```  
// C2079c.cpp  
class A;  
  
class B {  
   A a;   // C2079  
};  
  
class A {};  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2079d.cpp  
// compile with: /c  
class A;  
class C {};  
  
class B {  
   A * a;  
   C c;  
};  
  
class A {};  
```