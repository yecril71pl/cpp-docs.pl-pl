---
title: Opakowanie (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- boxing, C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
ms.openlocfilehash: 709754e8609406f635444937af93488060167ba9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172610"
---
# <a name="boxing--ccli-and-ccx"></a>Opakowanie (C++/CLI i C++/CX)

Konwersja typów wartości do obiektów jest nazywana *opakowaniem*, a Konwersja obiektów na typy wartości jest nazywana *rozpakowywaniem*.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie do wszystkich środowisk uruchomieniowych).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

C++/CX obsługuje skróconą składnię typów wartości opakowania i rozpakowywanie typów odwołań. Typ wartości jest opakowany, gdy jest przypisany do zmiennej typu `Object`. Zmienna `Object` jest oddzielona, gdy jest przypisana do zmiennej typu wartości, a nieopakowany typ jest określony w nawiasach; oznacza to, że gdy zmienna obiektu jest rzutowana na typ wartości.

```cpp
  Platform::Object^
  object_variable  = value_variable;
value_variable = (value_type) object_variable;
```

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

### <a name="examples"></a>Przykłady

Poniższy przykładowy kod dodaje pola i rozdzieli wartość `DateTime`. Najpierw przykład uzyskuje wartość `DateTime`, która reprezentuje bieżącą datę i godzinę, i przypisuje go do zmiennej `DateTime`. Następnie `DateTime` jest opakowany przez przypisanie do zmiennej `Object`. Na koniec, opakowana wartość jest niezaopakowana, przypisując ją do innej zmiennej `DateTime`.

Aby przetestować przykład, Utwórz projekt `BlankApplication`, Zastąp metodę `BlankPage::OnNavigatedTo()`, a następnie określ punkty przerwania w nawiasie zamykającym i przypisanie do zmiennej `str1`. Gdy przykład osiągnie nawias zamykający, należy zapoznać się `str1`.

```cpp
void BlankPage::OnNavigatedTo(NavigationEventArgs^ e)
{
    using namespace Windows::Globalization::DateTimeFormatting;

    Windows::Foundation::DateTime dt, dtAnother;
    Platform::Object^ obj1;

    Windows::Globalization::Calendar^ c =
        ref new Windows::Globalization::Calendar;
    c->SetToNow();
    dt = c->GetDateTime();
    auto dtf = ref new DateTimeFormatter(
                           YearFormat::Full,
                           MonthFormat::Numeric,
                           DayFormat::Default,
                           DayOfWeekFormat::None);
    String^ str1 = dtf->Format(dt);
    OutputDebugString(str1->Data());
    OutputDebugString(L"\r\n");

    // Box the value type and assign to a reference type.
    obj1 = dt;
    // Unbox the reference type and assign to a value type.
    dtAnother = (Windows::Foundation::DateTime) obj1;

    // Format the DateTime for display.
    String^ str2 = dtf->Format(dtAnother);
    OutputDebugString(str2->Data());
}
```

Aby uzyskać więcej informacji, zobacz [opakowanieC++(/CX)](../cppcx/boxing-c-cx.md).

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Pola kompilatora mają typy wartości do <xref:System.Object>. Jest to możliwe z powodu konwersji zdefiniowanej przez kompilator w celu przekonwertowania typów wartości na <xref:System.Object>.

Pakowanie i rozpakowywanie Włącz typy wartości, które mają być traktowane jako obiekty. Typy wartości, w tym typy struktury i typy wbudowane, takie jak int, można przekonwertować na i z typu <xref:System.Object>.

Aby uzyskać więcej informacji, zobacz:

- [Instrukcje: jawne żądanie konwersji boxing](../dotnet/how-to-explicitly-request-boxing.md)

- [Instrukcje: używanie funkcji gcnew do tworzenia typów wartości i korzystanie z niejawnej konwersji boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)

- [Instrukcje: rozpakowywanie](../dotnet/how-to-unbox.md)

- [Konwersje standardowe i niejawne konwersje boxing](../dotnet/standard-conversions-and-implicit-boxing.md)

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład pokazuje, jak działa niejawny opakowanie.

```cpp
// vcmcppv2_explicit_boxing2.cpp
// compile with: /clr
using namespace System;

ref class A {
public:
   void func(System::Object^ o){Console::WriteLine("in A");}
};

value class V {};

interface struct IFace {
   void func();
};

value class V1 : public IFace {
public:
   virtual void func() {
      Console::WriteLine("Interface function");
   }
};

value struct V2 {
   // conversion operator to System::Object
   static operator System::Object^(V2 v2) {
      Console::WriteLine("operator System::Object^");
      return (V2^)v2;
   }
};

void func1(System::Object^){Console::WriteLine("in void func1(System::Object^)");}
void func1(V2^){Console::WriteLine("in func1(V2^)");}

void func2(System::ValueType^){Console::WriteLine("in func2(System::ValueType^)");}
void func2(System::Object^){Console::WriteLine("in func2(System::Object^)");}

int main() {
   // example 1 simple implicit boxing
   Int32^ bi = 1;
   Console::WriteLine(bi);

   // example 2 calling a member with implicit boxing
   Int32 n = 10;
   Console::WriteLine("xx = {0}", n.ToString());

   // example 3 implicit boxing for function calls
   A^ a = gcnew A;
   a->func(n);

   // example 4 implicit boxing for WriteLine function call
   V v;
   Console::WriteLine("Class {0} passed using implicit boxing", v);
   Console::WriteLine("Class {0} passed with forced boxing", (V^)(v));   // force boxing

   // example 5 casting to a base with implicit boxing
   V1 v1;
   IFace ^ iface = v1;
   iface->func();

   // example 6 user-defined conversion preferred over implicit boxing for function-call parameter matching
   V2 v2;
   func1(v2);   // user defined conversion from V2 to System::Object preferred over implicit boxing
                // Will call void func1(System::Object^);

   func2(v2);   // OK: Calls "static V2::operator System::Object^(V2 v2)"
   func2((V2^)v2);   // Using explicit boxing: calls func2(System::ValueType^)
}
```

```Output
1

xx = 10

in A

Class V passed using implicit boxing

Class V passed with forced boxing

Interface function

in func1(V2^)

in func2(System::ValueType^)

in func2(System::ValueType^)
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
