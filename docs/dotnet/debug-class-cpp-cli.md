---
title: Klasa Debug (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 47e1b949cb6e998508a3bd362b1c74961cf4cc23
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414155"
---
# <a name="debug-class-ccli"></a>Klasa Debug (C++/CLI)

W przypadku używania <xref:System.Diagnostics.Debug> w aplikacji Visual C++ zachowanie nie zmienia się między debugowaniem a kompilacją wydania.

## <a name="remarks"></a>Uwagi

Zachowanie <xref:System.Diagnostics.Trace> jest identyczne z zachowaniem dla klasy Debug, ale jest zależne od zdefiniowanego śladu symbolu. Oznacza to, że należy `#ifdef` każdy kod związany ze śledzeniem, aby zapobiec zachowaniem debugowania w kompilacji wydania.

## <a name="example-always-executes-output-statements"></a>Przykład: zawsze wykonuje instrukcje wyjściowe

### <a name="description"></a>Opis

Poniższy przykład zawsze wykonuje instrukcje wyjściowe, niezależnie od tego, czy kompilujesz przy użyciu **/DDEBUG** czy **/DTrace**.

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

## <a name="example-use-ifdef-and-endif-directives"></a>Przykład: Użyj dyrektyw #ifdef i #endif

### <a name="description"></a>Opis

Aby uzyskać oczekiwane zachowanie (to oznacza, że dane wyjściowe "testowe" są drukowane dla kompilacji wydania), należy użyć `#ifdef` dyrektyw i `#endif` . Poprzedni przykład kodu został zmodyfikowany poniżej, aby przedstawić tę poprawkę:

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
