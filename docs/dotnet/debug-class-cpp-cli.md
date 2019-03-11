---
title: Klasa Debug (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 3a262a0d2ef429cb94f4648eb7c7180e7b130279
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743618"
---
# <a name="debug-class-ccli"></a>Klasa Debug (C++/CLI)

Korzystając z <xref:System.Diagnostics.Debug> w aplikacji Visual C++, zachowanie nie zmienił się od debugowania, jak i kompilację wydania.

## <a name="remarks"></a>Uwagi

Zachowanie <xref:System.Diagnostics.Trace> jest taka sama jak zachowanie dla klasy debugowania, ale jest zależny od symbolu śledzenia, które zostały zdefiniowane. Oznacza to, że musisz `#ifdef` żadnego kodu dotyczące śledzenia, aby zapobiec debugowanie kompilacji wydania.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład wykonuje zawsze oświadczeń danych wyjściowych, niezależnie od tego, czy kompilujesz z **/DDEBUG** lub **/DTRACE**.

### <a name="code"></a>Kod

```cpp
// mcpp_debug_class.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
   Trace::Unindent();

   Debug::WriteLine("test");
}
```

### <a name="output"></a>Dane wyjściowe

```Output
    Entering Main
Hello World.
    Exiting Main
test
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Aby uzyskać oczekiwane zachowanie (oznacza to, że żadne dane wyjściowe "test" druk dla wersji kompilacji), należy użyć `#ifdef` i `#endif` dyrektywy. W poprzednim przykładzie kodu zmienia się poniżej, aby zademonstrować tę poprawkę:

### <a name="code"></a>Kod

```cpp
// mcpp_debug_class2.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();

#ifdef TRACE   // checks for a debug build
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
#endif
   Trace::Unindent();

#ifdef DEBUG   // checks for a debug build
   Debug::WriteLine("test");
#endif   //ends the conditional block
}
```

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
