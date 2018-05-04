---
title: dynamic_cast Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- dynamic_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a87105ad2d52ebbb7749deafadedcd510314038f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="dynamiccast-operator"></a>Operator dynamic_cast
Konwertuje argument `expression` do obiektu typu `type-id`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dynamic_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Uwagi  
 `type-id` Musi być wskaźnikiem lub odwołaniem do typu klasy uprzednio zdefiniowany lub "wskaźnik do typu void". Typ `expression` musi być wskaźnikiem, jeśli `type-id` jest wskaźnikiem lub l wartość, jeśli `type-id` to odwołanie.  
  
 Zobacz [static_cast](../cpp/static-cast-operator.md) opis różnicy między konwersje rzutowania statycznych i dynamicznych oraz gdy należy używać każdego.  
  
 Istnieją dwie istotne zmiany w zachowaniu `dynamic_cast` w zarządzanym kodzie:  
  
-   `dynamic_cast` na wskaźnik do podstawowego typu opakowanego wyliczenia zakończy się niepowodzeniem w czasie wykonywania, zwracanie wartości 0 zamiast przekonwertowanego wskaźnika.  
  
-   `dynamic_cast` nie spowoduje zgłoszenie wyjątku podczas `type-id` wewnętrznego wskaźnika do typu wartość z cast niepowodzeniem w czasie wykonywania.  Rzutowanie teraz zwraca wartość 0 wskaźnika zamiast Trwa zgłaszanie wyjątku.  
  
 Jeśli `type-id` wskaźnik do jednoznacznej dostępny bezpośredniej lub pośredniej klasy podstawowej z `expression`, wskaźnik do unikatowy podobiektów typu `type-id` jest wynikiem. Na przykład:  
  
```  
// dynamic_cast_1.cpp  
// compile with: /c  
class B { };  
class C : public B { };  
class D : public C { };  
  
void f(D* pd) {  
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class  
                                   // pc points to C subobject of pd   
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class  
                                   // pb points to B subobject of pd  
}  
```  
  
 Ten typ konwersji nazywa się "rozszerzające", ponieważ jego przesuwa kursor w górę hierarchii klas, z klasy pochodnej do klasy, która jest pochodną. Rozszerzające jest niejawnej konwersji.  
  
 Jeśli `type-id` jest void * środowiska wykonawczego dokonuje można określić rzeczywistego typu `expression`. Wynik jest wskaźnikiem do kompletnego obiektu wskazywana przez `expression`. Na przykład:  
  
```  
// dynamic_cast_2.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
  
void f() {  
   A* pa = new A;  
   B* pb = new B;  
   void* pv = dynamic_cast<void*>(pa);  
   // pv now points to an object of type A  
  
   pv = dynamic_cast<void*>(pb);  
   // pv now points to an object of type B  
}  
```  
  
 Jeśli `type-id` nie jest void * środowiska wykonawczego dokonuje aby zobaczyć, czy obiekt wskazywany przez `expression` można przekonwertować na typ wskazywana przez `type-id`.  
  
 Jeśli typ `expression` jest klasą podstawową typu `type-id`, czasu wykonywania dokonuje czy `expression` faktycznie wskazuje cały obiekt typu `type-id`. Jeśli to PRAWDA, wynikiem jest wskaźnikiem do kompletnego obiektu typu `type-id`. Na przykład:  
  
```  
// dynamic_cast_3.cpp  
// compile with: /c /GR  
class B {virtual void f();};  
class D : public B {virtual void f();};  
  
void f() {  
   B* pb = new D;   // unclear but ok  
   B* pb2 = new B;  
  
   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D  
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D  
}  
```  
  
 Konwersja tego typu jest nazywana "przypisanie elementu podrzędnego" ponieważ przesuwa wskaźnik w dół hierarchii klas, z danej klasy do klasy pochodzić od niego.  
  
 W przypadku dziedziczenie wielokrotne możliwości niejednoznaczności zostały wprowadzone. Należy wziąć pod uwagę hierarchii klas pokazano na poniższej ilustracji.  
  
 Na typy CLR `dynamic_cast` powoduje zerowa, jeśli konwersja może zostać wykonana niejawnie lub MSIL `isinst` instrukcji, która sprawdza dynamiczne i zwraca `nullptr` Jeśli konwersji nie powiedzie się.  
  
 Następujące przykładowe używa `dynamic_cast` ustalenie, jeśli klasa jest wystąpieniem obiektu określonego typu:  
  
```  
// dynamic_cast_clr.cpp  
// compile with: /clr  
using namespace System;  
  
void PrintObjectType( Object^o ) {  
   if( dynamic_cast<String^>(o) )  
      Console::WriteLine("Object is a String");  
   else if( dynamic_cast<int^>(o) )  
      Console::WriteLine("Object is an int");  
}  
  
int main() {  
   Object^o1 = "hello";  
   Object^o2 = 10;  
  
   PrintObjectType(o1);  
   PrintObjectType(o2);  
}  
```  
  
 ![Hierarchia zawiera wiele dziedziczenia klasy](../cpp/media/vc39011.gif "vc39011")  
Hierarchia klas przedstawiający dziedziczenie wielokrotne  
  
 Wskaźnik do obiektu typu `D` może być bezpiecznie rzutowany `B` lub `C`. Jednak jeśli `D` jest rzutowane na wskaż `A` obiektu, którego wystąpienia `A` spowoduje? Spowoduje to błędu niejednoznaczne rzutowania. Aby ominąć ten problem, można wykonywać dwa jednoznaczne rzutowania. Na przykład:  
  
```  
// dynamic_cast_4.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
class D : public B {virtual void f();};  
  
void f() {  
   D* pd = new D;  
   B* pb = dynamic_cast<B*>(pd);   // first cast to B  
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous  
}  
```  
  
 Mogą zostać wprowadzone dalsze niejednoznaczności, korzystając z wirtualnych klas podstawowych. Należy wziąć pod uwagę hierarchii klas pokazano na poniższej ilustracji.  
  
 ![Klasa hierarchii, która zawiera wirtualne klasy podstawowe](../cpp/media/vc39012.gif "vc39012")  
Hierarchia klas przedstawiający wirtualne klasy podstawowe  
  
 W tej hierarchii `A` jest wirtualna klasa podstawowa. Podane wystąpienie klasy `E` i wskaźnika do `A` podobiektu, `dynamic_cast` na wskaźnik do `B` zakończy się niepowodzeniem z powodu niejednoznaczności. Najpierw należy rzutować na pełną `E` obiekt, a następnie przechodzić Utwórz kopię zapasową hierarchii, jednoznacznie, aby osiągnąć poprawny `B` obiektu.  
  
 Należy wziąć pod uwagę hierarchii klas pokazano na poniższej ilustracji.  
  
 ![Klasa hierarchii, który zawiera zduplikowane klasy podstawowe](../cpp/media/vc39013.gif "vc39013")  
Hierarchia klas przedstawiający zduplikowane klasy podstawowe  
  
 Podany obiekt typu `E` i wskaźnika do `D` podobiektów, można przejść z `D` podobiektów do lewej `A` podobiektów trzy konwersje jest możliwe. Można wykonywać `dynamic_cast` konwersja z `D` wskaźnik do `E` wskaźnika, a następnie konwersji (albo `dynamic_cast` lub niejawna konwersja) z `E` do `B`, a na koniec niejawna konwersja z `B` do `A`. Na przykład:  
  
```  
// dynamic_cast_5.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B : public A {virtual void f();};  
class C : public A { };  
class D {virtual void f();};  
class E : public B, public C, public D {virtual void f();};  
  
void f(D* pd) {  
   E* pe = dynamic_cast<E*>(pd);  
   B* pb = pe;   // upcast, implicit conversion  
   A* pa = pb;   // upcast, implicit conversion  
}  
```  
  
 `dynamic_cast` Operatora można używać do wykonywania "cast krzyżowego". Przy użyciu tej samej hierarchii klas, istnieje możliwość rzutowania wskaźnik, na przykład z `B` podobiektów do `D` podobiektów, jak długo cały obiekt jest typu `E`.  
  
 Biorąc pod uwagę cross rzutowania, jest faktycznie można wykonać konwersji ze wskaźnika do `D` na wskaźnik do lewej `A` podobiektów w dwóch krokach. Można wykonać rzutowania z krzyżyk `D` do `B`, następnie niejawna konwersja z `B` do `A`. Na przykład:  
  
```  
// dynamic_cast_6.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B : public A {virtual void f();};  
class C : public A { };  
class D {virtual void f();};  
class E : public B, public C, public D {virtual void f();};  
  
void f(D* pd) {  
   B* pb = dynamic_cast<B*>(pd);   // cross cast  
   A* pa = pb;   // upcast, implicit conversion  
}  
```  
  
 Wartość wskaźnika o wartości null jest konwertowana na wartość pustego wskaźnika typu docelowego przez `dynamic_cast`.  
  
 Jeśli używasz `dynamic_cast < type-id > ( expression )`, jeśli `expression` nie może być bezpiecznie przekonwertować na typ `type-id`, rzutowania niepowodzenie powoduje wyboru środowiska wykonawczego. Na przykład:  
  
```  
// dynamic_cast_7.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
  
void f() {  
   A* pa = new A;  
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;  
   // B not derived from A  
}  
```  
  
 Wartość nie powiodło się Rzutowanie na typ wskaźnika jest pustego wskaźnika. Nie powiodło się rzutowania do odwołania typu zgłasza [bad_cast — wyjątek](../cpp/bad-cast-exception.md).   Jeśli `expression` wskaż lub nie odwołuje się do obiektu prawidłowy, `__non_rtti_object` wyjątku.  
  
 Zobacz [typeid](../cpp/typeid-operator.md) wyjaśnienie `__non_rtti_object` wyjątku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie tworzone wskaźnika klasy podstawowej (struktura A), do obiektu (struktura C).  To, a także fakt, że funkcje wirtualne, umożliwia polimorfizm środowiska wykonawczego.  
  
 Przykład wywołuje również funkcją wirtualną z systemem innym niż w hierarchii.  
  
```  
// dynamic_cast_8.cpp  
// compile with: /GR /EHsc  
#include <stdio.h>  
#include <iostream>  
  
struct A {  
    virtual void test() {  
        printf_s("in A\n");  
   }  
};  
  
struct B : A {  
    virtual void test() {  
        printf_s("in B\n");  
    }  
  
    void test2() {  
        printf_s("test2 in B\n");  
    }  
};  
  
struct C : B {  
    virtual void test() {  
        printf_s("in C\n");  
    }  
  
    void test2() {  
        printf_s("test2 in C\n");  
    }  
};  
  
void Globaltest(A& a) {  
    try {  
        C &c = dynamic_cast<C&>(a);  
        printf_s("in GlobalTest\n");  
    }  
    catch(std::bad_cast) {  
        printf_s("Can't cast to C\n");  
    }  
}  
  
int main() {  
    A *pa = new C;  
    A *pa2 = new B;  
  
    pa->test();  
  
    B * pb = dynamic_cast<B *>(pa);  
    if (pb)  
        pb->test2();  
  
    C * pc = dynamic_cast<C *>(pa2);  
    if (pc)  
        pc->test2();  
  
    C ConStack;  
    Globaltest(ConStack);  
  
   // will fail because B knows nothing about C  
    B BonStack;  
    Globaltest(BonStack);  
}  
```  
  
```Output  
in C  
test2 in B  
in GlobalTest  
Can't cast to C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory rzutowania](../cpp/casting-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)