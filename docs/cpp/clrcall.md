---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: bc44feb97223de47f45734f75777ee040d0ebdd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534579"
---
# <a name="clrcall"></a>__clrcall

**Microsoft Specific**

Określa, że funkcja może zostać wywołana tylko z kodu zarządzanego.  Użyj **__clrcall** dla wszystkich funkcji wirtualnych, które będą wywoływane tylko z kodu zarządzanego. Jednak ta konwencja wywołania nie można użyć funkcji, które zostaną wywołane z kodu natywnego.

Użyj **__clrcall** aby poprawić wydajność podczas wywoływania funkcji zarządzanej funkcji wirtualnej zarządzanych lub funkcji zarządzanej funkcji zarządzanych za pomocą wskaźnika.

Punkty wejścia są oddzielne, generowane przez kompilator funkcje. Jeśli funkcja ma zarówno punkty wejścia natywnych i zarządzanych, jeden z nich będzie rzeczywiste funkcji z implementacją funkcji. Innych funkcji, będzie to oddzielna funkcja (wywołanie), wywołuje funkcję rzeczywiste, która umożliwia środowiska uruchomieniowego języka wspólnego wykonywania funkcji PInvoke. Kiedy oznaczanie funkcję jako **__clrcall**, wskazujesz, implementacja funkcji musi być MSIL i funkcję punktu wejścia natywne nie będą generowane.

Gdy przełącza adresu w funkcji natywnej, jeśli **__clrcall** nie zostanie określony, kompilator używa natywnego punktu wejścia. **Wywołanie __clrcall** wskazuje, że funkcja jest zarządzana i ma, nie trzeba przechodzić przez przejście z zarządzanego do kodu natywnego. W takim przypadku kompilator używa zarządzany punkt wejścia.

Gdy `/clr` (nie `/clr:pure` lub `/clr:safe`) jest używany i **__clrcall** jest nieużywane, biorąc adresu funkcji zawsze zwraca adres funkcję punktu wejścia natywnych. Gdy **__clrcall** jest używany, funkcja punktu wejścia natywne nie zostało utworzone, dzięki czemu możesz uzyskać adresu funkcji zarządzanej nie funkcję punktu wejścia thunk. Aby uzyskać więcej informacji, zobacz [podwójna](../dotnet/double-thunking-cpp.md). **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

[/ CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) oznacza, że wszystkie funkcje i wskaźniki funkcji mają **__clrcall** i kompilator nie pozwoli na funkcji wewnątrz compiland — był oznaczony jako coś innego niż **__clrcall**. Gdy **/CLR: pure** jest używany, **__clrcall** można określić tylko dla wskaźników funkcji i deklaracje zewnętrzne.

Można bezpośrednio wywoływać **__clrcall** funkcji z istniejącego kodu C++, który został skompilowany przy użyciu **/CLR** tak długo, jak ta funkcja zawiera implementację MSIL. **Wywołanie __clrcall** funkcji nie można wywołać bezpośrednio z funkcji, które mają wbudowanego asm i wywołać intrinisics specyficznych dla procesora CPU, na przykład, nawet jeśli te funkcje są kompilowane przy użyciu `/clr`.

**Wywołanie __clrcall** wskaźników funkcji są przeznaczone tylko do użycia w domenie aplikacji, w którym zostały utworzone.  Zamiast **__clrcall** wskaźniki funkcji w różnych domenach aplikacji, należy użyć <xref:System.CrossAppDomainDelegate>. Aby uzyskać więcej informacji, zobacz [domeny aplikacji i programu Visual C++](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Przykład

Należy pamiętać, że gdy funkcja jest zadeklarowana za pomocą **__clrcall**, kod zostanie wygenerowany, gdy potrzebne; na przykład, gdy funkcja jest wywoływana.

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, czy można zdefiniować wskaźnik funkcji tak, aby zadeklarować, że wskaźnik funkcji będzie można wywołać tylko z kodu zarządzanego. Dzięki temu kompilator, aby bezpośrednio wywołać funkcji zarządzanej i uniknąć natywnego punktu wejścia (podwójny thunk problem).

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
