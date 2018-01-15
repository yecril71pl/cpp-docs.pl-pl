---
title: "Rozpoznawanie przeciążenia wywołań szablonów funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64bc9371fcddad5f76f1474832a8d69188b60583
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="overload-resolution-of-function-template-calls"></a>Rozpoznawanie przeciążenia wywołań szablonów funkcji
Szablon funkcji można przeciążyć funkcji nieszablonu o takiej samej nazwie. W tym scenariuszu wywołania funkcji są rozpoznawane przy pierwszym przy użyciu Wnioskowanie argumentu szablonu do utworzenia wystąpienia szablonu funkcji z specjalizacji unikatowy. W przypadku niepowodzenia Wnioskowanie argumentu szablonu inne przeciążenia funkcji są traktowane jako wywołanie rozpoznawania. Te inne przeciążenia, tzw. zestaw candidate obejmują funkcje nieszablonu i innych szablonów funkcji wystąpień. Jeśli Wnioskowanie argumentu szablonu zakończy się powodzeniem, generowanej funkcji jest porównywany z innymi funkcjami, aby określić najlepsze dopasowanie, zgodnie z regułami Rozpoznanie przeciążenia. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](function-overloading.md).  
  
## <a name="example"></a>Przykład

 Jeśli funkcja nieszablonu jest równie dobrej dopasowany do funkcji szablonu, funkcja nieszablonu wybrano (chyba że jawnie zostały podane argumenty szablonu), ponieważ w wywołaniu `f(1, 1)` w poniższym przykładzie.  
  
```cpp
// template_name_resolution9.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void f(int, int) { cout << "f(int, int)" << endl; }  
void f(char, char) { cout << "f(char, char)" << endl; }  
  
template <class T1, class T2>  
void f(T1, T2)  
{  
   cout << "void f(T1, T2)" << endl;  
};  
  
int main()  
{  
   f(1, 1);   // Equally good match; choose the nontemplate function.  
   f('a', 1); // Chooses the template function.  
   f<int, int>(2, 2);  // Template arguments explicitly specified.  
}  
```  
  
```Output  
f(int, int)  
void f(T1, T2)  
void f(T1, T2)  
```  
  
## <a name="example"></a>Przykład

 Funkcja dokładnie zgodnego szablonu jest preferowana, jeśli funkcja nieszablonu wymaga konwersji pokazano w przykładzie dalej.  
  
```cpp
// template_name_resolution10.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void f(int, int) { cout << "f(int, int)" << endl; }  
  
template <class T1, class T2>  
void f(T1, T2)  
{  
   cout << "void f(T1, T2)" << endl;  
};  
  
int main()  
{  
   long l = 0;  
   int i = 0;  
   // Call the template function f(long, int) because f(int, int)  
   // would require a conversion from long to int.  
   f(l, i);  
}  
```  
  
```Output  
void f(T1, T2)  
```  
  
## <a name="see-also"></a>Zobacz też

 [Rozpoznawanie nazw](../cpp/templates-and-name-resolution.md)   
 [typename](../cpp/typename.md)   
 
