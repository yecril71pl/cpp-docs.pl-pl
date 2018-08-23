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
ms.openlocfilehash: 566ed55df84accef0c3e5308e750a2684c36b91c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606797"
---
# <a name="exception-handling--c-component-extensions"></a>Obsługa wyjątków (C++ Component Extensions)

Aplikacje skompilowane z `/ZW` — opcja kompilatora lub `/clr` kompilator korzystać zarówno *wyjątki* do obsługi nieoczekiwanych błędów podczas wykonywania programu. W poniższych tematach omówiono obsługi wyjątków w dowolnym języku C + +/ CX lub C + +/ interfejsu wiersza polecenia aplikacji.

## <a name="in-this-section"></a>W tej sekcji

[Podstawowe pojęcia związane z używaniem wyjątków zarządzanych](../dotnet/basic-concepts-in-using-managed-exceptions.md)  
W tym artykule opisano zgłaszanie wyjątków i przy użyciu **spróbuj**/**catch** bloków.

[Różnice w zachowaniu obsługi wyjątków w/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)  
W tym artykule omówiono różnice względem standardowe zachowanie programu obsługi wyjątków C++.

[finally](../dotnet/finally.md)  
W tym artykule omówiono sposób używania finally — słowo kluczowe.

[Instrukcje: definiowanie i instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
Pokazuje, jak nieobsłużone wyjątki mogą być przechwytywane.

[Instrukcje: przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)  
Omawia, jak przechwytywać wyjątki środowiska CLR i C++ w kodzie natywnym.

[Instrukcje: definiowanie i instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
Pokazuje, jak przechwytywać wszystkie nieobsłużone wyjątki.

## <a name="related-sections"></a>Sekcje pokrewne

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)  
W tym artykule opisano obsługę wyjątków w języku C++.

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)