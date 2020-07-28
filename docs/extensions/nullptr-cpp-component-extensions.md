---
title: nullptr  (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 5e7a5d3f9a42968dee35f82d3f19d0fdb6da5d0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214233"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr  (C++/CLI i C++/CX)

**`nullptr`** Słowo kluczowe reprezentuje *wartość wskaźnika o wartości null*. Użyj wartości wskaźnika o wartości null, aby wskazać, że uchwyt obiektu, wskaźnik wewnętrzny lub typ wskaźnika natywnego nie wskazuje na obiekt.

Używany **`nullptr`** z kodem zarządzanym lub natywnym. Kompilator emituje odpowiednie, ale różne instrukcje dotyczące zarządzanych i natywnych wartości wskaźników wartości null. Aby uzyskać informacje na temat używania standardowej wersji ISO języka C++ tego słowa kluczowego, zobacz [nullptr](../cpp/nullptr.md).

Słowo kluczowe **__nullptr** jest słowem kluczowym specyficznym dla firmy Microsoft, który ma takie samo znaczenie jak **`nullptr`** , ale ma zastosowanie tylko do kodu natywnego. Jeśli używasz **`nullptr`** z natywnym kodem C/C++, a następnie kompilujesz przy użyciu opcji kompilatora [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , kompilator nie może określić, czy **`nullptr`** wskazuje natywną lub zarządzaną wartość wskaźnika o wartości null. Aby wyznaczać zamierzone dla kompilatora, użyj, **`nullptr`** Aby określić wartość zarządzaną lub **__nullptr** , aby określić wartość natywną.

**`nullptr`** Słowo kluczowe jest równoważne wartości **Nothing** w Visual Basic i **null** w języku C#.

## <a name="usage"></a>Sposób użycia

**`nullptr`** Słowo kluczowe może być używane wszędzie tam, gdzie dojście, wskaźnik natywny lub argument funkcji może być używany.

**`nullptr`** Słowo kluczowe nie jest typu i nie jest obsługiwane w przypadku:

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr`(chociaż `throw (Object^)nullptr;` będzie działała)

**`nullptr`** Słowo kluczowe może być używane podczas inicjowania następujących typów wskaźnika:

- Wskaźnik natywny

- Dojście środowisko wykonawcze systemu Windows

- Obsługa zarządzana

- Zarządzany wskaźnik wewnętrzny

**`nullptr`** Słowa kluczowego można użyć do sprawdzenia, czy odwołanie do wskaźnika lub dojścia ma wartość null przed użyciem odwołania.

Wywołania funkcji w różnych językach, które używają wartości wskaźnika wartości null do sprawdzania błędów, powinny być poprawnie interpretowane.

Nie można zainicjować dojścia do zera. **`nullptr`** można używać tylko. Przypisanie stałej 0 do dojścia do obiektu tworzy opakowane `Int32` i rzutowanie na `Object^` .

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **`nullptr`** słowo kluczowe może być używane wszędzie tam, gdzie można użyć uchwytu, wskaźnika natywnego lub argumentu funkcji. W przykładzie pokazano, że **`nullptr`** słowo kluczowe może służyć do sprawdzenia odwołania przed jego użyciem.

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **`nullptr`** i zero można użyć zamiennie na wskaźnikach natywnych.

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **`nullptr`** jest interpretowany jako dojście do dowolnego typu lub macierzystego wskaźnika do dowolnego typu. W przypadku przeciążania funkcji z dojściami do różnych typów zostanie wygenerowany błąd niejednoznaczności. **`nullptr`** Musi być jawnie rzutowany na typ.

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że rzutowanie **`nullptr`** jest dozwolone i zwraca wskaźnik lub uchwyt do typu rzutowania, który zawiera **`nullptr`** wartość.

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **`nullptr`** może być używany jako parametr funkcji.

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że gdy dojścia są zadeklarowane i nie są jawnie inicjowane, są one domyślnie inicjowane **`nullptr`** .

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **`nullptr`** można przypisać do macierzystego wskaźnika podczas kompilowania przy użyciu `/clr` .

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Wymagania

Opcja kompilatora: (niewymagane; obsługiwane przez wszystkie opcje generowania kodu, w tym `/ZW` i `/clr` )

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)
