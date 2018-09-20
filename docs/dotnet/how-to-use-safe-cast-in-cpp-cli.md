---
title: 'Porady: Korzystanie z polecenia safe_cast w języku C + +/ interfejsu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a0adec10db22c9793ebdd44add76945ade803ca7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444440"
---
# <a name="how-to-use-safecast-in-ccli"></a>Porady: korzystanie z polecenia safe_cast w języku C++/interfejsie wiersza polecenia

W tym artykule pokazano, jak korzystanie z polecenia safe_cast w języku C + +/ interfejsu wiersza polecenia aplikacji. Aby uzyskać informacje dotyczące polecenia safe_cast w języku C + +/ CX, zobacz [safe_cast](../windows/safe-cast-cpp-component-extensions.md).

## <a name="upcasting"></a>Rzutowanie rozszerzające

Rozszerzające jest rzutowanie z typem pochodnym do jednej z jej klas podstawowych. To rzutowanie jest bezpieczna i nie wymaga jawnego rzutowania notacji. Poniższy przykład pokazuje, jak wykonać rozszerzające za pomocą `safe_cast` i bez niego.

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>Rzutowanie

Rzutowania jest rzutowanie z klasy bazowej do klasy, która pochodzi od klasy bazowej.  Rzutowania jest bezpieczne, tylko wtedy, gdy obiekt, który jest opisany w czasie wykonywania jest faktycznie odnoszący się do obiektu klasy pochodnej.  W odróżnieniu od `static_cast`, `safe_cast` przeprowadza sprawdzanie dynamiczne i zgłasza <xref:System.InvalidCastException> Jeśli konwersja nie powiedzie się.

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safecast-with-user-defined-conversions"></a>safe_cast z konwersje zdefiniowane przez użytkownika

Następny przykład pokazuje, jak można użyć `safe_cast` do wywołania konwersje zdefiniowane przez użytkownika.

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safecast-and-boxing-operations"></a>operacje polecenia safe_cast i pakowania

### <a name="boxing"></a>Boxing

OPAKOWYWANIE jest zdefiniowany jako konwersji wprowadzony przez kompilator, zdefiniowane przez użytkownika.  W związku z tym, można użyć `safe_cast` do pola wartość na stosie CLR.

Poniższy przykład pokazuje boxing z typami wartości prostego i zdefiniowane przez użytkownika.  A `safe_cast` pola zmienną typu wartości, która znajduje się na macierzystym stosu tak, że może ona zostać przypisana do zmiennej na stercie zebranych elementów bezużytecznych.

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

Następny przykład pokazuje, że pakowania ma priorytet nad konwersja zdefiniowana przez użytkownika, w `safe_cast` operacji.

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>Rozpakowywanie

Rozpakowywanie jest zdefiniowany jako konwersji wprowadzony przez kompilator, zdefiniowane przez użytkownika.  W związku z tym, można użyć `safe_cast` do rozpakowania wartością na stosie CLR.

Rozpakowywanie to konwersja zdefiniowana przez użytkownika, ale w przeciwieństwie do pakowanie, rozpakowywanie musi jawnie — czyli muszą być wykonywane przez `static_cast`, stylu C cast lub `safe_cast`; Rozpakowywanie nie może zostać wykonana niejawnie.

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

Ilustruje poniższy przykład rozpakowywania typów wartości i typami pierwotnymi.

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safecast-and-generic-types"></a>polecenia safe_cast i typów ogólnych

Następny przykład pokazuje, jak można użyć `safe_cast` przeprowadzić rzutowania z typu ogólnego.

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>Zobacz też

[przedstawienie operacji safe_cast](../windows/safe-cast-cpp-component-extensions.md)