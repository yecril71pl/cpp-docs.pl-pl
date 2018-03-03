---
title: Mechanizm pimpl hermetyzacji kompilacji (Modern C++) w czasie | Dokumentacja firmy Microsoft
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
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a109015f3d30b04eaf89e769e1265c49663599f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Mechanizm pimpl hermetyzacji w czasie kompilacji (Modern C++)
*Idiom mechanizm pimpl w czasie* to technika C++ nowoczesnych, aby ukryć implementacji, aby zminimalizować sprzężenia, a do oddzielania interfejsów. Mechanizm pimpl w czasie jest skrót od "wskaźnik do implementacji." Może już należy zapoznać się z pojęciem, ale o tym przez inne nazwy, takie jak idiom Cheshire Cat lub Zapora kompilatora.  
  
## <a name="why-use-pimpl"></a>Dlaczego warto używać mechanizm pimpl w czasie?  
 Oto, jak poprawić idiom mechanizm pimpl w czasie cyklu tworzenia oprogramowania:  
  
-   Minimalizacja zależności kompilacji.  
  
-   Rozdzielenie interfejsu i implementacji.  
  
-   Przenośność.  
  
## <a name="pimpl-header"></a>Mechanizm pimpl w czasie nagłówka  
  
```cpp  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 Mechanizm pimpl w czasie idiom pozwala uniknąć kaskady Odbuduj i układy łamliwa obiektu. Nadaje się również do (przechodnie) popularnych typów.  
  
## <a name="pimpl-implementation"></a>Mechanizm pimpl w czasie wykonania  
 Zdefiniuj `impl` klasy w pliku .cpp.  
  
```cpp  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Należy rozważyć, czy dodać obsługę-zgłaszanie specjalizacji wymiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)