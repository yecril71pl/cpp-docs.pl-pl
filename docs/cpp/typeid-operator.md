---
title: "TypeID — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b27f3bcb7358b3ea05907df1a4372c107538dfb4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="typeid-operator"></a>typeid — operator
## <a name="syntax"></a>Składnia  
  
```  
  
      typeid(   
      type-id  
       )  
typeid( expression )  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator `typeid` pozwala, aby typ obiektu był ustalony w czasie wykonywania.  
  
 Wynik `typeid` jest **const type_info — &**. Wartość jest odwołaniem do **type_info —** obiekt, który reprezentuje albo *identyfikator typu* lub typ *wyrażenie*w oparciu o który formę `typeid` jest używany . Zobacz [type_info — klasa](../cpp/type-info-class.md) Aby uzyskać więcej informacji.  
  
 `typeid` Operator nie działa z typy zarządzane (deklaratory abstrakcyjne języka lub wystąpień), zobacz [typeid](../windows/typeid-cpp-component-extensions.md) informacji na temat pobierania <xref:System.Type> określonego typu.  
  
 Operator `typeid` wykonuje sprawdzanie w czasie wykonania po zastosowaniu l-wartości do typu polimorficznej klasy, gdzie prawidłowego typu obiektu nie można określić dostarczonymi informacjami statycznymi. Takie przypadki są:  
  
-   Odwołaniem do klasy  
  
-   Wskaźnikiem, wyłuskanym za pomocą *  
  
-   Indeksem wskaźnika (tj.) [ ]). (Należy zauważyć, że ogólnie nie jest bezpiecznie korzystać z indeksu dolnego ze wskaźnikiem do typu polimorficznego).  
  
 Jeśli *wyrażenie* wskazuje typ klasy podstawowej, jeszcze obiektu w rzeczywistości była typu pochodnego od tej klasy podstawowej **type_info —** odwołania do klasy pochodnej jest wynikiem. *Wyrażenie* musi wskazywać na typie polimorficznym (klasa funkcji wirtualnych). W przeciwnym razie wynikiem jest **type_info —** statycznej klasy określonej w *wyrażenia*. Ponadto, wskaźnik musi być wyłuskany, aby wskazywany przez niego obiekt został użyty. Bez usuwania odwołania wskaźnik, wynikiem będzie **type_info —** wskaźnika, wskazuje nie które it. Na przykład:  
  
```  
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
  
 Jeśli *wyrażenie* jest dereferencji wskaźnik, i że jego wartość wynosi zero, **typeid** zgłasza [bad_typeid — wyjątek](../cpp/bad-typeid-exception.md). Jeśli wskaźnik nie wskazuje prawidłowego obiektu `__non_rtti_object` wyjątku, wskazującą próba analizowanie RTTI, która wyzwoliła błąd (np. naruszenia zasad dostępu), ponieważ obiekt jest z jakiegoś powodu nieprawidłowe (nieprawidłowy wskaźnik lub kod nie został skompilowany z [GR](../build/reference/gr-enable-run-time-type-information.md)).  
  
 Jeśli *wyrażenie* nie jest wskaźnikiem ani odwołaniem do obiektu, klasa podstawowa jest wynik **type_info —** odwołania reprezentujący typ statyczny *wyrażenie*. *Statycznego typu* wyrażeń odwołuje się do typu wyrażenia są znane w czasie kompilacji. Semantyka wykonania jest ignorowana przy ocenie typu statycznego wyrażenia. Ponadto, odwołania są ignorowane, gdy to możliwe przy określaniu typu statycznego wyrażenia:  
  
```  
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **TypeID** można również w szablonach można określić typu parametru szablonu:  
  
```  
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