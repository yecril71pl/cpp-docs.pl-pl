---
title: "Porady: ustalić, czy rozpoczęło się zamykanie systemu (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
ms.assetid: a8d39731-dea8-4f0a-96b7-2a5de09b21d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f4575f212752a43df2b130fbde9aa7264186d6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-determine-if-shutdown-has-started-ccli"></a>Porady: ustalanie, czy rozpoczęło się zamykanie systemu (C++/CLI)
Poniższy przykład kodu pokazuje sposób określania, czy jest obecnie przerywanie aplikacji lub programu .NET Framework. Jest to przydatne w przypadku uzyskiwania dostępu do elementów statycznych w programie .NET Framework, ponieważ podczas zamykania, tych konstrukcji sfinalizowaniu przez system i nie może być niezawodnie używany. Sprawdzając <xref:System.Environment.HasShutdownStarted%2A> właściwości, można uniknąć potencjalnych błędów przez nie dostępu do tych elementów.  
  
## <a name="example"></a>Przykład  
  
```  
// check_shutdown.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   if (Environment::HasShutdownStarted)  
      Console::WriteLine("Shutting down.");  
   else  
      Console::WriteLine("Not shutting down.");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje w systemie Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)