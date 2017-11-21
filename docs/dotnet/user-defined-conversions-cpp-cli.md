---
title: "Konwersje zdefiniowane przez użytkownika (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3515b9da7513080e825457d98aa06bccb63a1029
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="user-defined-conversions-ccli"></a>Konwersje zdefiniowane przez użytkownika (C++/CLI)
W tej sekcji omówiono konwersje zdefiniowane przez użytkownika (UDC), gdy jeden z typów w konwersji odwołania lub wystąpienia typu wartości lub typem referencyjnym.  
  
## <a name="implicit-and-explicit-conversions"></a>Konwersje jawne i niejawne  
 Konwersja zdefiniowana przez użytkownika może być jawnych ani niejawnych.  UDC powinna być niejawne, jeśli konwersja nie powoduje utraty informacji. W przeciwnym razie jawne UDC powinien być zdefiniowany.  
  
 Konstruktor klasy natywnej, można przekonwertować typu odwołanie lub wartość klasy natywnej.  
  
 Aby uzyskać więcej informacji na temat konwersji, zobacz [Boxing](../windows/boxing-cpp-component-extensions.md) i [konwersje standardowe](../cpp/standard-conversions.md).  
  
```  
// mcpp_User_Defined_Conversions.cpp  
// compile with: /clr  
#include "stdio.h"  
ref class R;  
class N;  
  
value class V {  
   static operator V(R^) {  
      return V();  
   }  
};  
  
ref class R {  
public:  
   static operator N(R^);  
   static operator V(R^) {  
      System::Console::WriteLine("in R::operator N");  
      return V();  
   }  
};  
  
class N {  
public:  
   N(R^) {  
      printf("in N::N\n");  
   }  
};  
  
R::operator N(R^) {  
   System::Console::WriteLine("in R::operator N");  
   return N(nullptr);  
}  
  
int main() {  
   // Direct initialization:  
   R ^r2;  
   N n2(r2);   // direct initialization, calls constructor  
   static_cast<N>(r2);   // also direct initialization  
  
   R ^r3;  
   // ambiguous V::operator V(R^) and R::operator V(R^)  
   // static_cast<V>(r3);     
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
in N::N  
in N::N  
```  
  
## <a name="convert-from-operators"></a>Konwersja z operatorów  
 Konwersja z operatorów utworzyć obiekt klasy, w którym jest zdefiniowany operator obiektu inna klasa.  
  
 Standard C++ nie obsługuje konwersja z operatorów; Standard C++ korzysta z konstruktorów w tym celu. Jednak przy użyciu typów CLR, Visual C++ zapewniają obsługę składni wywoływania konwersja z operatorów.  
  
 Współdziałanie z innymi językami zgodne ze specyfikacją CLS, warto zawijać każdego konstruktora jednoargumentowy zdefiniowane przez użytkownika dla danej klasy z odpowiadającego operatora konwersja z.  
  
 Konwersja z operatorów:  
  
-   Określa się jako statyczne funkcje.  
  
-   Albo można (dla konwersji, które nie tracić dokładność, takich jak krótko int) lub pośredniego, gdy mogą być utratę dokładności.  
  
-   Zwraca obiekt zawierający klasy.  
  
-   Ma typ "od" jako jedyny parametr typu.  
  
 Poniższy przykład przedstawia jawne i niejawne "Konwersja z", operator konwersji zdefiniowany przez użytkownika (UDC).  
  
```  
// clr_udc_convert_from.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
  
   MyDouble(int i) {  
      d = static_cast<double>(i);  
      System::Console::WriteLine("in constructor");  
   }  
  
   // Wrap the constructor with a convert-from operator.  
   // implicit UDC because conversion cannot lose precision  
   static operator MyDouble (int i) {  
      System::Console::WriteLine("in operator");  
      // call the constructor  
      MyDouble d(i);  
      return d;  
   }  
  
   // an explicit user-defined conversion operator  
   static explicit operator signed short int (MyDouble) {  
      return 1;  
   }  
};  
  
int main() {  
   int i = 10;  
   MyDouble md = i;  
   System::Console::WriteLine(md.d);  
  
   // using explicit user-defined conversion operator requires a cast    
   unsigned short int j = static_cast<unsigned short int>(md);  
   System::Console::WriteLine(j);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
in operator  
in constructor  
10  
1  
```  
  
## <a name="convert-to-operators"></a>Konwersja na operatory  
 Konwersja na operatory konwertować obiekt klasy, w którym zdefiniowano operator do innego obiektu. Poniższy przykład przedstawia pośrednie, konwersja na, operator konwersji zdefiniowany przez użytkownika:  
  
```  
// clr_udc_convert_to.cpp  
// compile with: /clr  
using namespace System;  
value struct MyInt {  
   Int32 i;  
  
   // convert MyInt to String^  
   static operator String^ ( MyInt val ) {  
      return val.i.ToString();  
   }  
  
   MyInt(int _i) : i(_i) {}  
};  
  
int main() {  
   MyInt mi(10);  
   String ^s = mi;  
   Console::WriteLine(s);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
10  
```  
  
 Operator konwersji jawnej zdefiniowane przez użytkownika konwersja na jest odpowiednie do konwersji, które może spowodować utratę danych w określony sposób. Aby wywołać operatora jawna konwersja na, muszą być używane rzutowanie.  
  
```  
// clr_udc_convert_to_2.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
   // convert MyDouble to Int32  
   static explicit operator System::Int32 ( MyDouble val ) {  
      return (int)val.d;  
   }  
};  
  
int main() {  
   MyDouble d;  
   d.d = 10.3;  
   System::Console::WriteLine(d.d);  
   int i = 0;  
   i = static_cast<int>(d);  
   System::Console::WriteLine(i);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
10.3  
10  
```  
  
## <a name="to-convert-generic-classes"></a>Aby przekonwertować klasy ogólne  
 Klasy ogólnej można przekonwertować na T.  
  
```  
// clr_udc_generics.cpp  
// compile with: /clr  
generic<class T>   
public value struct V {  
   T mem;  
   static operator T(V v) {  
      return v.mem;  
   }  
  
   void f(T t) {  
      mem = t;  
   }  
};  
  
int main() {  
   V<int> v;  
   v.f(42);  
   int i = v;  
   i += v;  
   System::Console::WriteLine(i == (42 * 2) );  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
True  
```  
  
 Konwertowanie Konstruktor ma typ i używa go do utworzenia obiektu.  Konwertowanie Konstruktor jest wywoływana z bezpośredniego inicjowania. rzutowania nie wywoła konwertowania konstruktorów. Domyślnie konwertowania konstruktory są jawne dla typów CLR.  
  
```  
// clr_udc_converting_constructors.cpp  
// compile with: /clr  
public ref struct R {  
   int m;  
   char c;  
  
   R(int i) : m(i) { }  
   R(char j) : c(j) { }  
};  
  
public value struct V {  
   R^ ptr;  
   int m;  
  
   V(R^ r) : ptr(r) { }  
   V(int i) : m(i) { }  
};  
  
int main() {   
   R^ r = gcnew R(5);  
  
   System::Console::WriteLine( V(5).m);  
   System::Console::WriteLine( V(r).ptr);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
5  
R  
```  
  
 W tym przykładowym kodzie niejawne statyczna funkcja konwersji jest odpowiednikiem konstruktora jawnej konwersji.  
  
```  
public value struct V {  
   int m;  
   V(int i) : m(i) {}  
   static operator V(int i) {  
      V v(i*100);  
      return v;  
   }  
};  
  
public ref struct R {  
   int m;  
   R(int i) : m(i) {}  
   static operator R^(int i) {  
      return gcnew R(i*100);  
   }  
};  
  
int main() {  
   V v(13);   // explicit  
   R^ r = gcnew R(12);   // explicit  
  
   System::Console::WriteLine(v.m);  
   System::Console::WriteLine(r->m);  
  
   // explicit ctor can't be called here: not ambiguous  
   v = 5;  
   r = 20;  
  
   System::Console::WriteLine(v.m);  
   System::Console::WriteLine(r->m);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
13  
12  
500  
2000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)