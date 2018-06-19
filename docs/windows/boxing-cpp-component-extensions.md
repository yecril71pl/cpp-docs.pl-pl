---
title: OPAKOWYWANIE (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f689255af653e5dfdf69250e4988aa809393461
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861360"
---
# <a name="boxing--c-component-extensions"></a>Boxing (C++ Component Extensions)
Kompilatora Visual C++ można przekonwertować wartości typów obiektów w procesie nazywanym *boxing*i konwersji obiektów na typy wartości w procesie nazywanym *rozpakowującej*.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych.)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 C + +/ CX obsługuje składni skrótu dla typów wartości opakowywanie i rozpakowywanie typy referencyjne. Typ wartości jest opakowany, gdy jest przypisany do zmiennej typu `Object`. `Object` Zmienna jest rozpakowany, gdy jest przypisany do zmiennej typu wartości i rozpakowany typ jest określony w nawiasy; oznacza to, gdy zmienna obiektu jest Rzutowanie na typ wartości.  
  
```  
  
  Platform::Object^  
  object_variable  = value_variable;  
value_variable = (value_type) object_variable;  
  
```  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
### <a name="examples"></a>Przykłady  
 Następujący kod przykładowy pola i unboxes `DateTime` wartość. Po pierwsze przykładzie uzyskuje wartość daty/godziny, która reprezentuje bieżącą datę i godzinę, a następnie przypisuje go do zmiennej typu DateTime. Następnie element DateTime jest opakowany przez przypisanie go do zmiennej obiektu. Na koniec wartości spakowanej jest rozpakowany przez przypisanie go do innej zmiennej typu DateTime.  
  
 W celu przetestowania przykładu, Utwórz projekt BlankApplication, Zastąp metodę BlankPage::OnNavigatedTo(), a następnie określ punkty przerwania w nawias i przypisanie do zmiennej str1. W przypadku przykładzie osiągnie zamykający nawias kwadratowy, należy sprawdzić str1.  
  
```  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Boxing (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh969554.aspx).  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 Kompilator Visual C++ teraz typów do wartości pola <xref:System.Object>.  Jest to możliwe z powodu konwersji zdefiniowanej przez kompilator do konwersji typów wartości do <xref:System.Object>.  
  
 Konwersja boxing i rozpakowywanie Włącz typy wartości powinien być traktowany jako obiekty. Typy wartości, w tym zarówno typy struktur i typy wbudowane, takie jak int, mogą być konwertowane do i z typem <xref:System.Object>.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Instrukcje: jawne żądanie konwersji boxing](../dotnet/how-to-explicitly-request-boxing.md)  
  
-   [Instrukcje: używanie funkcji gcnew do tworzenia typów wartości i korzystanie z niejawnej konwersji boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)  
  
-   [Instrukcje: rozpakowywanie](../dotnet/how-to-unbox.md)  
  
-   [Konwersje standardowe i niejawne konwersje boxing](../dotnet/standard-conversions-and-implicit-boxing.md)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład przedstawia sposób niejawna konwersja boxing działa.  
  
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
  
 **Output**  
  
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
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)