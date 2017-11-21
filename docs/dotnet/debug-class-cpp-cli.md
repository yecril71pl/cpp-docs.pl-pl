---
title: Klasa Debug (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 14354241c4e16e1177a5680b901a738f16036f96
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="debug-class-ccli"></a>Klasa Debug (C++/CLI)
Korzystając z <xref:System.Diagnostics.Debug> w aplikacji Visual C++, zachowanie nie zmienia się między debugowania i kompilacji wydania.  
  
## <a name="remarks"></a>Uwagi  
 Zachowanie <xref:System.Diagnostics.Trace> jest taka sama jak zachowanie dla klasy debugowania, ale jest zależna od symbolu definiowanego śledzenia. Oznacza to, że należy `#ifdef` żadnego kodu dotyczące śledzenia, aby zapobiec debugowania w kompilacji wydania.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład zawsze wykonuje instrukcje danych wyjściowych, niezależnie od tego, czy kompilacji z **/DDEBUG** lub **/DTRACE**.  
  
### <a name="code"></a>Kod  
  
```  
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
  
```  
    Entering Main  
Hello World.  
    Exiting Main  
test  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Aby uzyskać oczekiwane zachowanie (oznacza to, że żadne dane wyjściowe "test" drukowane dla kompilacji wydania), należy użyć `#ifdef` i `#endif` dyrektywy. W poprzednim przykładzie kodu zmienia się poniżej, aby zademonstrować tej poprawki:  
  
### <a name="code"></a>Kod  
  
```  
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
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)