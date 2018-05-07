---
title: Błąd narzędzi konsolidatora LNK2020 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2020
dev_langs:
- C++
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33dd1b381d36a90f2e9b144e690e364ac512c081
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2020"></a>Błąd narzędzi konsolidatora LNK2020
Nierozpoznany token 'token'  
  
 Podobnie jak niezdefiniowany błąd zewnętrzny, z tą różnicą, że odwołanie jest za pośrednictwem metadanych. W metadanych muszą być zdefiniowane wszystkie dane i funkcje.  
  
 Aby rozwiązać:  
  
-   Zdefiniuj Brak funkcję lub dane, lub  
  
-   Dołączyć plik obiektu lub biblioteki, w którym brak funkcji lub danych jest już zdefiniowany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje LNK2020.  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## <a name="example"></a>Przykład  
 LNK2020 zostanie również wystąpić, jeśli można utworzyć zmiennej typu zarządzanego szablonu, ale nie również utworzyć wystąpienia typu.  
  
 Poniższy przykład generuje LNK2020.  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```