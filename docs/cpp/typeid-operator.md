---
title: TypeID, Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9646678398ff1e18d0acf45c45bc931ce37cd54a
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37948271"
---
# <a name="typeid-operator"></a>typeid — operator
## <a name="syntax"></a>Składnia  
  
```  
  
typeid(type-id)  
typeid(expression)  
```  
  
## <a name="remarks"></a>Uwagi  
 **Typeid** operator zezwala na typ obiektu był ustalony w czasie wykonywania.  
  
 Wynik **typeid** jest `const type_info&`. Wartość jest odwołaniem do `type_info` obiekt, który reprezentuje *identyfikator typu* lub typ *wyrażenie*, zależnie od formy użycia **typeid** jest używany. Zobacz [type_info Class](../cpp/type-info-class.md) Aby uzyskać więcej informacji.  
  
 **Typeid** operator nie działa z typami zarządzanymi (abstrakcyjnymi deklaratorami lub wystąpieniami), zobacz [typeid](../windows/typeid-cpp-component-extensions.md) informacji na temat pobierania <xref:System.Type> określonego typu.  
  
 **Typeid** operator jest sprawdzenie czasu wykonywania, gdy jest stosowany do l wartością typu polimorficznej klasy, gdzie wartość true, typ obiektu nie można określić dostarczonymi informacjami statycznymi. Takie przypadki są:  
  
-   Odwołaniem do klasy  
  
-   Wskaźnikiem, wyłuskanym za pomocą *  
  
-   Indeksem wskaźnika (tj.) [ ]). (Należy zauważyć, że ogólnie nie jest bezpiecznie korzystać z indeksu dolnego ze wskaźnikiem do typu polimorficznego).  
  
 Jeśli *wyrażenie* wskazuje na typ klasy bazowej, obiekt jest rzeczywiście typu dziedziczonego z tej klasy bazowej `type_info` odwoływać się do klasy pochodnej jest wynikiem. *Wyrażenie* musi wskazywać typ polimorficzny (klasa funkcji wirtualnych). W przeciwnym razie wynikiem jest `type_info` dla klasy statycznej określonej w *wyrażenie*. Ponadto, wskaźnik musi być wyłuskany, aby wskazywany przez niego obiekt został użyty. Bez wyłuskania wskaźnika, wynik będzie `type_info` dla wskaźnika, nie jakie wskazuje. Na przykład:  
  
```cpp 
// expre_typeid_Operator.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <typeinfo.h>  
  
class Base {  
public:  
   virtual void vvfunc() {}  
};  
  
class Derived : public Base {};  
  
using namespace std;  
int main() {  
   Derived* pd = new Derived;  
   Base* pb = pd;  
   cout << typeid( pb ).name() << endl;   //prints "class Base *"  
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"  
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"  
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"  
   delete pd;  
}  
```  
  
 Jeśli *wyrażenie* jest wyłuskaniem wskaźnika i że jego wartość wynosi zero, **typeid** zgłasza [wyjątek bad_typeid](../cpp/bad-typeid-exception.md). Jeżeli wskaźnik nie wskazuje prawidłowego obiektu `__non_rtti_object` wyjątku, wskazując próbę analizy RTTI, która wyzwoliła taki błąd (np. naruszenie zasad dostępu), ponieważ obiekt jest z jakiegoś powodu nieprawidłowy (zły wskaźnik lub kod nie został skompilowany z [GR](../build/reference/gr-enable-run-time-type-information.md)).  
  
 Jeśli *wyrażenie* jest ani wskaźnikiem ani odwołaniem do klasy bazowej obiektu, wynik jest `type_info` odwołaniem typu statycznego *wyrażenie*. *Typu statycznego* wyrażenie odwołuje się do typu wyrażenia jaki jest znany w czasie kompilacji. Semantyka wykonania jest ignorowana przy ocenie typu statycznego wyrażenia. Ponadto, odwołania są ignorowane, gdy to możliwe przy określaniu typu statycznego wyrażenia:  
  
```cpp 
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **TypeID** można również w szablonach w celu określenia typu parametru szablonu:  
  
```cpp 
// expre_typeid_Operator_3.cpp  
// compile with: /c  
#include <typeinfo>  
template < typename T >   
T max( T arg1, T arg2 ) {  
   cout << typeid( T ).name() << "s compared." << endl;  
   return ( arg1 > arg2 ? arg1 : arg2 );  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje typu Run-Time](../cpp/run-time-type-information.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)