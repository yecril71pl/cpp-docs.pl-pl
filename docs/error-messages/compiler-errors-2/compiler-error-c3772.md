---
title: "C3772 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3772
dev_langs:
- C++
helpviewer_keywords:
- C3772
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3290a3be06ecc223bfc87e39ed068d187d4f95c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3772"></a>C3772 błąd kompilatora
"Nazwa": Nieprawidłowa deklaracja szablonu zaprzyjaźnionego  
  
Nie może deklarować elementu przyjaznego specjalizacji szablonu klasy. Nie można zadeklarować jawna lub częściowa specjalizacja szablonu klasy i w tej samej instrukcji deklarować elementu przyjaznego tego specjalizacji. *Nazwa* nieprawidłową deklaracją identyfikuje symbol zastępczy.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Nie deklaruj znajomego specjalizacji szablonu klasy.  
  
-   Jeśli odpowiedni dla aplikacji, deklarować elementu przyjaznego szablonu klasy lub deklarować elementu przyjaznego określonego jawnych ani częściowej specjalizacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu nie powiedzie się, ponieważ deklaruje on zaprzyjaźniona z częściowa specjalizacja szablonu klasy.  
  
```cpp  
// c3772.cpp  
// compile with: /c  
  
// A class template.  
    template<class T> class A {};  
  
// A partial specialization of the class template.  
    template<class T> class A<T*> {};  
  
// An explicit specialization.  
    template<> class A<char>;  
  
class X {  
// Invalid declaration of a friend of a partial specialization.  
    template<class T> friend class A<T*>; // C3772  
  
// Instead, if it is appropriate for your application, declare a   
// friend of the class template. Consequently, all specializations   
// of the class template are friends:  
//    template<class T> friend class A;  
// Or declare a friend of a particular partial specialization:  
//    friend class A<int*>;  
// Or declare a friend of a particular explicit specialization:  
//    friend class A<char>;  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
[Szablony](../../cpp/templates-cpp.md)   
[Specjalizacja szablonu](../../cpp/template-specialization-cpp.md)   
