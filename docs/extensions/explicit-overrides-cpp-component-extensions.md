---
title: Jawne zastąpienia (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: c199301794daaa140ede2fd99b0ae755cea70f97
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172376"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>Jawne zastąpienia (C++/CLI i C++/CX)

W tym temacie omówiono sposób jawnego przesłaniania elementu członkowskiego klasy bazowej lub interfejsu. Zastępowanie nazwane (jawne) powinno być używane tylko w celu przesłaniania metody z użyciem metody pochodnej, która ma inną nazwę.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Parametry

*przesłanianie-funkcja-deklarator*<br/>
Typ zwracany, nazwa i lista argumentów funkcji przesłaniania.  Należy zauważyć, że funkcja przesłaniania nie musi mieć takiej samej nazwy jak zastępowana funkcja.

*type*<br/>
Typ podstawowy, który zawiera funkcję, która ma zostać przesłonięta.

*funkcyjn*<br/>
Rozdzielana przecinkami lista nazw jednej lub więcej funkcji, które mają zostać przesłonięte.

*Zastępowanie-funkcja-definicja*<br/>
Instrukcje treści funkcji, które definiują funkcję zastępującą.

### <a name="remarks"></a>Uwagi

Użyj jawnych zastąpień, aby utworzyć alias dla sygnatury metody lub podać różne implementacje metod o tej samej sygnaturze.

Aby uzyskać informacje o modyfikowaniu zachowania dziedziczonych typów i dziedziczonych elementów członkowskich typu, zobacz [specyfikatory przesłonięć](override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o jawnych zastąpień w kodzie natywnym lub kodzie skompilowanym za pomocą `/clr:oldSyntax`, zobacz [jawne zastąpienia](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu pokazuje proste, niejawne przesłonięcie i implementację elementu członkowskiego w interfejsie podstawowym, a nie używa jawnych zastąpień.

```cpp
// explicit_override_1.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
}
```

```Output
X::f override of I1::f
```

Poniższy przykład kodu pokazuje, jak zaimplementować wszystkie elementy członkowskie interfejsu ze wspólnym podpisem przy użyciu składni jawnego przesłaniania.

```cpp
// explicit_override_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

interface struct I2 {
   virtual void f();
};

ref struct X : public I1, I2 {
   virtual void f() = I1::f, I2::f {
      System::Console::WriteLine("X::f override of I1::f and I2::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   I2 ^ MyI2 = gcnew X;
   MyI -> f();
   MyI2 -> f();
}
```

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

Poniższy przykład kodu pokazuje, jak przesłonięcie funkcji może mieć inną nazwę niż implementująca funkcja.

```cpp
// explicit_override_3.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void g() = I1::f {
      System::Console::WriteLine("X::g");
   }
};

int main() {
   I1 ^ a = gcnew X;
   a->f();
}
```

```Output
X::g
```

Poniższy przykład kodu pokazuje jawną implementację interfejsu implementującą bezpieczną kolekcję typów.

```cpp
// explicit_override_4.cpp
// compile with: /clr /LD
using namespace System;
ref class R : ICloneable {
   int X;

   virtual Object^ C() sealed = ICloneable::Clone {
      return this->Clone();
   }

public:
   R() : X(0) {}
   R(int x) : X(x) {}

   virtual R^ Clone() {
      R^ r = gcnew R;
      r->X = this->X;
      return r;
   }
};
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
