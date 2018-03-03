---
title: "Przenośność na granicach ABI (Modern C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 06cb6c97580b4c4c9a6c961cb76f2c4d84d841ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="portability-at-abi-boundaries-modern-c"></a>Przenośność na granicach ABI (Modern C++)
Użyj typów wystarczająco przenośnych i konwencje na granicach binarny interfejsu. "Typ portable" jest typem wbudowanym C lub struktury, która zawiera tylko typy wbudowane C. Typy klas można użyć tylko, gdy obiekt wywołujący i wywoływany uzgodnić układu, wywoływanie Konwencji, np. Jest to możliwe tylko wtedy, gdy oba są kompilowane przy użyciu tego samego kompilatora i ustawienia kompilatora.  
  
## <a name="how-to-flatten-a-class-for-c-portability"></a>Jak spłaszczanie klasy przenośności C  
 Podczas wywoływania może być kompilowana przy użyciu innego kompilatora/języka, a następnie "spłaszczanie", aby **zewnętrzne "C"** interfejsu API za pomocą określonego konwencja wywołania:  
  
```cpp  
// class widget {  
//   widget();  
//   ~widget();  
//   double method( int, gadget& );  
// };  
extern "C" {        // functions using explicit "this"  
   struct widget;   // opaque type (forward declaration only)  
   widget* STDCALL widget_create();      // constructor creates new "this"  
   void STDCALL widget_destroy(widget*); // destructor consumes "this"  
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)