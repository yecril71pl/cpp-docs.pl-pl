---
title: Pimpl hermetyzacji w czasie kompilacji (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e80c4bd86cd4c7400e3937fcb8d164fe6b14106
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404658"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Mechanizm pimpl hermetyzacji w czasie kompilacji (Modern C++)
*Pimpl idiom* to technika nowoczesnego języka C++ do ukrywania implementacji, aby zminimalizować sprzężenia i do oddzielnych interfejsów. Pimpl jest skrót od "wskaźnik do implementacji." Może być już można zapoznać się z pojęciem, ale wiedzieć, przy użyciu innych nazw, takich jak idiom Cheshire Cat lub kompilatora zapory.  
  
## <a name="why-use-pimpl"></a>Dlaczego warto używać pimpl?  
 Poniżej przedstawiono, jak poprawić pimpl idiom życia tworzenia oprogramowania:  
  
-   Minimalizacji zależności kompilacji.  
  
-   Oddzielenie interfejsu i implementacji.  
  
-   Przenośność.  
  
## <a name="pimpl-header"></a>Nagłówek Pimpl  
  
```cpp  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
```  
  
 Pimpl idiom pozwala uniknąć kaskady ponownej kompilacji i kruchy obiektu układów. Dobrze nadaje się dla (przechodnio) popularnych typów.  
  
## <a name="pimpl-implementation"></a>Implementacja Pimpl  
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
  
## <a name="best-practices"></a>Najlepsze rozwiązania  
 Należy rozważyć dodanie obsługi niezgłaszające specjalizacji wymiany.  
  
## <a name="see-also"></a>Zobacz także  
 [Witamy z powrotem w C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)