---
title: Klasa Debug (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: eecda10f2fd88b902a54fe9f4dc4de8edc4bc1b0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413565"
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

## <a name="see-also"></a>Zobacz też

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)