---
title: "Porady: Określanie stanu interaktywności użytkownika (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++, user interactive state
- user interactive state
ms.assetid: 9f52323e-38b8-4a41-9b1d-052012ad839b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f65933a1cbd81c0794263dfe3fa2628f52599257
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-determine-the-user-interactive-state-ccli"></a>Porady: określanie stanu interaktywności użytkownika (C++/CLI)
Poniższy przykład kodu pokazuje sposób określania, czy kod jest uruchamiany w kontekście interakcji z użytkownikiem. Jeśli <xref:System.Environment.UserInteractive%2A> to false, a następnie kod jest uruchomiona jako proces usługi lub z wewnątrz aplikacji sieci Web, w którym to przypadku należy zrezygnować do interakcji z użytkownikiem.  
  
## <a name="example"></a>Przykład  
  
```  
// user_interactive.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   if ( Environment::UserInteractive )  
      Console::WriteLine("User interactive");  
   else  
      Console::WriteLine("Noninteractive");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje w systemie Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)