---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 6eb1a05eaf6669daa4cb7142ff16a57f7caf39cd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857609"
---
# <a name="__clrcall"></a>__clrcall

Określa, że funkcja może zostać wywołana tylko z kodu zarządzanego.  Użyj **__clrcall** dla wszystkich funkcji wirtualnych, które będą wywoływane tylko z kodu zarządzanego. Jednakże tej konwencji wywoływania nie można używać w przypadku funkcji, które będą wywoływane z kodu natywnego. Modyfikator **__clrcall** jest specyficzny dla firmy Microsoft.

Użyj **__clrcall** , aby zwiększyć wydajność podczas wywoływania funkcji zarządzanej przez wirtualną funkcję zarządzaną lub z funkcji zarządzanej do funkcji zarządzanej przez wskaźnik.

Punkty wejścia są oddzielnymi funkcjami wygenerowanymi przez kompilator. Jeśli funkcja ma natywne i zarządzane punkty wejścia, jedna z nich będzie rzeczywistą funkcją z implementacją funkcji. Druga funkcja będzie oddzielną funkcją (thunk), która wywołuje funkcję rzeczywistą i umożliwia wykonywanie w środowisku uruchomieniowym języka wspólnego PInvoke. Gdy oznaczasz funkcję jako **__clrcall**, oznacza to, że implementacja funkcji musi być MSIL i że funkcja natywnego punktu wejścia nie zostanie wygenerowana.

Podczas pobierania adresu funkcji natywnej, jeśli nie określono **__clrcall** , kompilator używa natywnego punktu wejścia. **__clrcall** wskazuje, że funkcja jest zarządzana i nie ma potrzeby przechodzenia przez przejście z zarządzanego do natywnego. W takim przypadku kompilator używa zarządzanego punktu wejścia.

Gdy jest używane `/clr` (nie `/clr:pure` lub `/clr:safe`) i **__clrcall** nie są używane, pobieranie adresu funkcji zawsze zwraca adres natywnej funkcji punktu wejścia. Gdy **__clrcall** jest używany, funkcja natywnego punktu wejścia nie zostanie utworzona, więc otrzymujesz adres funkcji zarządzanej, a nie funkcję thunk punktu wejścia. Aby uzyskać więcej informacji, zobacz [podwójny podwójna](../dotnet/double-thunking-cpp.md). **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

[/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../build/reference/clr-common-language-runtime-compilation.md) oznacza, że wszystkie funkcje i wskaźniki funkcji są **__clrcall** i kompilator nie zezwoli na użycie funkcji wewnątrz jednostka kompilacji jako innej niż **__clrcall**. Gdy jest używany **/CLR: Pure** , **__clrcall** można określić tylko dla wskaźników funkcji i deklaracji zewnętrznych.

Można bezpośrednio wywoływać **__clrcall** funkcje z istniejącego C++ kodu, który został skompilowany przy użyciu **/CLR** , o ile ta funkcja ma implementację MSIL. **__clrcall** funkcje nie mogą być wywoływane bezpośrednio z funkcji, które mają wbudowaną metodę ASM i wywołują intrinisics specyficzne dla procesora CPU, na przykład nawet jeśli te funkcje są kompilowane przy użyciu `/clr`.

**__clrcall** wskaźników funkcji można używać tylko w domenie aplikacji, w której zostały utworzone.  Zamiast przekazywać **__clrcall** wskaźniki funkcji w różnych domenach aplikacji, należy użyć <xref:System.CrossAppDomainDelegate>. Aby uzyskać więcej informacji, zobacz [domeny i wizualizacja C++aplikacji ](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Przykład

Należy pamiętać, że gdy funkcja jest zadeklarowana przy użyciu **__clrcall**, kod zostanie wygenerowany w razie konieczności; na przykład, gdy funkcja jest wywoływana.

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

Poniższy przykład pokazuje, że można zdefiniować wskaźnik funkcji, na przykład, deklaruje, że wskaźnik funkcji będzie wywoływany tylko z kodu zarządzanego. Dzięki temu kompilator może bezpośrednio wywołać funkcję zarządzaną i uniknąć natywnego punktu wejścia (podwójny thunk problemu).

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
