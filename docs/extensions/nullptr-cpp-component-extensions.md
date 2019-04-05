---
title: nullptr (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 05aaaa8a0d0056e0f5318f5e9329d90824760728
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040827"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C + +/ CLI i C + +/ CX)

**Nullptr** — słowo kluczowe reprezentuje *wartość wskaźnika null*. Aby wskazać, że dojście do obiektu, posługiwanie się nimi wskaźnika lub typu wskaźnik natywny nie wskazuje obiektu, należy użyć wartości wskaźnika o wartości null.

Użyj **nullptr** przy użyciu kodu zarządzanego lub natywnego. Kompilator generuje instrukcje odpowiednie, ale różnych wartości zarządzanego i natywnego wskaźnika o wartości null. Aby dowiedzieć się, jak za pomocą ISO standard C++ wersję to słowo kluczowe, zobacz [nullptr](../cpp/nullptr.md).

**__Nullptr** — słowo kluczowe jest słowem kluczowym specyficzne dla firmy Microsoft, która ma takie samo znaczenie jak **nullptr**, ale dotyczą tylko kodu natywnego. Jeśli używasz **nullptr** za pomocą natywnego języka C/C++ kodu i następnie skompilować z [/CLR](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora, kompilator nie może określić, czy **nullptr** wskazuje natywny lub zarządzane wartość pustego wskaźnika. Aby zamiaru wyczyść w kompilatorze, użyj **nullptr** określić wartość zarządzanych lub **__nullptr** określić wartość natywnych.

**Nullptr** — słowo kluczowe jest odpowiednikiem **nic** w języku Visual Basic i **null** w języku C#.

## <a name="usage"></a>Użycie

**Nullptr** — słowo kluczowe może używane wszędzie, gdzie można użyć uchwytu, wskaźnik natywny lub argumentu funkcji.

**Nullptr** — słowo kluczowe nie jest typem i nie jest obsługiwane do użytku z programem:

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (mimo że `throw (Object^)nullptr;` będzie działać)

**Nullptr** — słowo kluczowe może być używana w inicjowania następujących typów wskaźników:

- Wskaźnik natywny

- Dojście do środowiska wykonawczego Windows

- Dojście do zarządzanego

- Zarządzane wskaźnika wewnętrznego

**Nullptr** — słowo kluczowe może służyć do testowania, jeśli wskaźnik lub uchwyt odwołanie ma wartość null, zanim zostaną użyte odwołania.

Wywołania funkcji spośród języków, które używają wartości wskaźnika o wartości null sprawdzania błędów powinny były prawidłowo interpretowane.

Nie można zainicjować dojścia do zero. tylko **nullptr** mogą być używane. Przypisanie stałej 0 na uchwyt obiektu tworzy spakowany `Int32` i rzutowania `Object^`.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **nullptr** — słowo kluczowe może służyć wszędzie tam, gdzie uchwytu, wskaźnik natywny lub argumentu funkcji, które mogą być używane. A w przykładzie pokazano, że **nullptr** — słowo kluczowe może służyć do sprawdzania odwołania, zanim zostaną one użyte.

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

Poniższy przykład kodu pokazuje, że **nullptr** i zero mogą być używane zamiennie w natywnymi wskaźnikami.

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

Poniższy przykład kodu pokazuje, że **nullptr** jest interpretowany jako uchwyt do dowolnego typu lub wskaźnik natywny do dowolnego typu. W przypadku przeciążania funkcji za pomocą uchwytów na różne typy, zostanie wygenerowany błąd niejednoznaczności. **Nullptr** , musi być jawnie rzutowane na typ.

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

Poniższy przykład kodu pokazuje tego rzutowania **nullptr** jest dozwolone, a następnie zwraca wskaźnik lub uchwyt do typu rzutowania, który zawiera **nullptr** wartości.

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

Poniższy przykład kodu pokazuje, że **nullptr** mogą być używane jako parametru funkcji.

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

Poniższy przykład kodu pokazuje, że gdy uchwyty są deklarowane i nie zostały jawnie zainicjowana, są one domyślnie zainicjowane, aby **nullptr**.

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

Poniższy przykład kodu pokazuje, że **nullptr** można przypisać na wskaźnik natywny podczas kompilowania z `/clr`.

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Wymagania

— Opcja kompilatora: (Nie jest wymagane; obsługiwane przez wszystkie opcje generowania kodu, w tym `/ZW` i `/clr`)

## <a name="see-also"></a>Zobacz także

[Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)