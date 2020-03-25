---
title: zapieczętowane (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: ab5d5b32ceb87a3b1ccf08d170889dd4825f6c17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181801"
---
# <a name="sealed--ccli-and-ccx"></a>zapieczętowane (C++/CLI i C++/CX)

**Sealed** to kontekstowe słowo kluczowe dla klas referencyjnych, które wskazują, że nie można przesłonić wirtualnego elementu członkowskiego lub że typ nie może być używany jako typ podstawowy.

> [!NOTE]
> Język standardowy ISO C++ 11 wprowadził słowo kluczowe [Final](../cpp/final-specifier.md) . Używaj **wersji Final** dla klas standardowych i **zapieczętowanych** w klasach ref.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

## <a name="syntax"></a>Składnia

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>Parametry

*identyfikatora*<br/>
Nazwa funkcji lub klasy.

*Typ zwracany*<br/>
Typ, który jest zwracany przez funkcję.

## <a name="remarks"></a>Uwagi

W pierwszej składni, Klasa jest zapieczętowana. W drugim przykładzie funkcja wirtualna jest zapieczętowana.

Używaj **zapieczętowanego** słowa kluczowego dla klas referencyjnych i ich wirtualnych funkcji składowych. Aby uzyskać więcej informacji, zobacz [specyfikatory przesłonięcia i kompilacje natywne](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Możesz wykryć w czasie kompilacji, niezależnie od tego, czy typ jest zapieczętowany przy użyciu cech typu `__is_sealed(type)`. Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](compiler-support-for-type-traits-cpp-component-extensions.md).

**zapieczętowany** jest kontekstowym słowem kluczowym.  Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Zobacz [klasy referencyjne i struktury](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie tylko do środowiska uruchomieniowego języka wspólnego).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu przedstawia efekt **zapieczętowanego** elementu członkowskiego.

```cpp
// sealed_keyword.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
   virtual void g();
};

ref class X : I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }

   virtual void g() sealed {
      System::Console::WriteLine("X::f override of I1::g");
   }
};

ref class Y : public X {
public:
   virtual void f() override {
      System::Console::WriteLine("Y::f override of I1::f");
   }

   /*
   // the following override generates a compiler error
   virtual void g() override {
      System::Console::WriteLine("Y::g override of I1::g");
   }
   */
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
   MyI -> g();

   I1 ^ MyI2 = gcnew Y;
   MyI2 -> f();
}
```

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

Następny przykład kodu pokazuje, jak oznaczyć klasę jako Sealed.

```cpp
// sealed_keyword_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X sealed : I1 {
public:
   virtual void f() override {}
};

ref class Y : public X {   // C3246 base class X is sealed
public:
   virtual void f() override {}
};
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
