---
title: "Porady: Pobieranie czasu, jaki upłynął od uruchomienia (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
ms.assetid: a31fdecc-099e-4dd1-a176-f682289c5dd0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 56f73aec78af0fe34d8c3881911a6ae1d7f26501
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-retrieve-time-elapsed-since-startup-ccli"></a>Porady: pobieranie czasu, jaki upłynął od uruchomienia systemu (C++/CLI)
W poniższym przykładzie pokazano, jak określić liczbę cykli lub wyrażony w milisekundach czas, które upłynęły od systemu Windows została uruchomiona. Ta wartość jest przechowywana w <xref:System.Environment.TickCount%2A?displayProperty=fullName> elementu członkowskiego i, ponieważ jest 32-bitową wartość przywraca zero co 24,9 dni.  
  
## <a name="example"></a>Przykład  
  
```  
// startup_time.cpp  
// compile with: /clr  
using namespace System;  
  
int main( )   
{  
   Int32 tc = Environment::TickCount;  
   Int32 seconds = tc / 1000;  
   Int32 minutes = seconds / 60;  
   float hours = static_cast<float>(minutes) / 60;  
   float days = hours / 24;  
  
   Console::WriteLine("Milliseconds since startup: {0}", tc);  
   Console::WriteLine("Seconds since startup: {0}", seconds);  
   Console::WriteLine("Minutes since startup: {0}", minutes);  
   Console::WriteLine("Hours since startup: {0}", hours);  
   Console::WriteLine("Days since startup: {0}", days);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje w systemie Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)