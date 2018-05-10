---
title: Obsługa (C++ Component Extensions) wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling, managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- managed exceptions
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b6dcf8e844fbb2e8e133dc5dc6f0b98a3166ac6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="exception-handling--c-component-extensions"></a>Obsługa wyjątków (C++ Component Extensions)
Aplikacje skompilowane z **/ZW** — opcja kompilatora lub **/CLR** — opcja kompilatora oba rozwiązania używają *wyjątki* obsługi nieoczekiwane błędy podczas wykonywania programu. W poniższych tematach opisano obsługi wyjątków w obu C + +/ CX lub C + +/ CLI aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe pojęcia związane z używaniem wyjątków zarządzanych](../dotnet/basic-concepts-in-using-managed-exceptions.md)  
 W tym artykule opisano zgłaszanie wyjątków i przy użyciu `try` / `catch` bloków.  
  
 [Różnice w zachowaniu obsługi wyjątków w/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)  
 W tym artykule omówiono różnic od standardowego zachowania C++, obsługa wyjątków.  
  
 [finally](../dotnet/finally.md)  
 W tym artykule omówiono sposób użycia finally — słowo kluczowe.  
  
 [Instrukcje: definiowanie i instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
 Pokazuje, jak nieobsługiwanych wyjątków, można przechwycić.  
  
 [Instrukcje: przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)  
 Omówiono sposób przechwytywanie wyjątków CLR i C++ w kodzie natywnym.  
  
 [Instrukcje: definiowanie i instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
 Demonstracja catch wszystkie nieobsługiwane wyjątki.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)  
 W tym artykule opisano, obsługa wyjątków w języku C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)