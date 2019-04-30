---
title: Jawne przesłonięcia (C++sposób niezamierzony i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: 7d36793e4467f9454aca1eb207f3c3dfbd483bff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403966"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>Jawne przesłonięcia (C++sposób niezamierzony i C++/CX)

W tym temacie omówiono sposób jawnie przesłonić składowej klasy bazowej lub interfejsu. Nazwanego przesłaniania (jawne) należy używać tylko aby przesłonić metodę z metodą pochodnej, która ma inną nazwę.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Parametry

*overriding-function-declarator*<br/>
Zwracany typ, nazwa i argument lista przesłanianie funkcji.  Pamiętaj, że funkcja pomijania muszą mieć taką samą nazwę jak przesłaniana funkcja.

*type*<br/>
Typ podstawowy, zawierającego funkcję, aby zastąpić.

*— Funkcja*<br/>
Rozdzielana przecinkami lista co najmniej jedną nazwę funkcji do zastąpienia.

*overriding-function-definition*<br/>
Instrukcje treści funkcji, które definiują przesłanianie funkcji.

### <a name="remarks"></a>Uwagi

Używać jawnych zastąpień w utworzenie aliasu dla sygnatury metody lub dostarczać różne implementacje dla metod witht taki sam podpis.

Aby dowiedzieć się, jak modyfikowanie zachowania typy dziedziczone i członkowie typów dziedziczonych, zobacz [zastąpienie specyfikatorów](override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

W przypadku przesłania informacji na temat jawne, w kodzie natywnym lub kodu skompilowanego z `/clr:oldSyntax`, zobacz [jawne zastępowanie](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu pokazuje prosty, niejawne zastąpienia i implementacji elementu członkowskiego w interfejsie zgodnym podstawowego nie przy użyciu jawne przesłonięcia.

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

Poniższy przykład kodu pokazuje sposób implementacji wszystkich członków interfejsu za pomocą wspólnego podpisu przy użyciu składnia jawnego przesłaniania.

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

Poniższy przykład kodu pokazuje, jak zastąpienia funkcji może mieć inną nazwę funkcji, które implementuje.

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

Poniższy przykład kodu pokazuje implementacja interfejsu jawnego, który implementuje zbiór bezpiecznego typu.

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

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)