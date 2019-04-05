---
title: Obsługa wyjątków (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
ms.openlocfilehash: b477f7355ee1f4f70a0ad3df8b85c4276c07d397
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037177"
---
# <a name="exception-handling--ccli-and-ccx"></a>Obsługa wyjątków (C + +/ CLI i C + +/ CX)

Aplikacje skompilowane z `/ZW` — opcja kompilatora lub `/clr` kompilator korzystać zarówno *wyjątki* do obsługi nieoczekiwanych błędów podczas wykonywania programu. W poniższych tematach omówiono obsługi wyjątków w dowolnym języku C + +/ CX lub C + +/ interfejsu wiersza polecenia aplikacji.

## <a name="in-this-section"></a>W tej sekcji

[Podstawowe pojęcia związane z używaniem wyjątków zarządzanych](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
W tym artykule opisano zgłaszanie wyjątków i przy użyciu **spróbuj**/**catch** bloków.

[Różnice w zachowaniu obsługi wyjątków w/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
W tym artykule omówiono różnice względem standardowe zachowanie programu obsługi wyjątków C++.

[finally](../dotnet/finally.md)<br/>
W tym artykule omówiono sposób używania finally — słowo kluczowe.

[Instrukcje: Definiowanie i instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Pokazuje, jak nieobsłużone wyjątki mogą być przechwytywane.

[Instrukcje: Przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Omawia, jak przechwytywać wyjątki środowiska CLR i C++ w kodzie natywnym.

[Instrukcje: Definiowanie i instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Pokazuje, jak przechwytywać wszystkie nieobsłużone wyjątki.

## <a name="related-sections"></a>Sekcje pokrewne

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
W tym artykule opisano obsługę wyjątków w standardowego języka C++.

## <a name="see-also"></a>Zobacz także

[Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)