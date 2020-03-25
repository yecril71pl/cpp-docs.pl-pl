---
title: Obsługa wyjątków (C++/CLI i C++/CX)
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
ms.openlocfilehash: 9f5662bb9e744b5db3b0ab25ac4230b2f67016bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182126"
---
# <a name="exception-handling--ccli-and-ccx"></a>Obsługa wyjątków (C++/CLI i C++/CX)

Aplikacje skompilowane przy użyciu opcji kompilatora `/ZW` lub `/clr` opcji kompilatora używają *wyjątków* do obsługi nieoczekiwanych błędów podczas wykonywania programu. W poniższych tematach omówiono obsługę wyjątków w C++aplikacjach/CX C++lub/CLI.

## <a name="in-this-section"></a>W tej sekcji

[Podstawowe pojęcia związane z używaniem wyjątków zarządzanych](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Opisuje zgłaszanie wyjątków i używanie bloków **try**/**catch** .

[Różnice w zachowaniu obsługi wyjątków w/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Omawia różnice między standardowym zachowaniem obsługi C++ wyjątków.

[finally](../dotnet/finally.md)<br/>
W tym artykule omówiono sposób użycia słowa kluczowego finally.

[Instrukcje: definiowanie i instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Pokazuje, jak można przechwytywać Nieobsłużone wyjątki.

[Instrukcje: przechwytywanie wyjątków w kodzie natywnym wygenerowanym w języku MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Omawia sposób przechwytywania środowiska CLR i C++ wyjątków w kodzie natywnym.

[Instrukcje: definiowanie i instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Pokazuje, jak przechwytywać wszystkie Nieobsłużone wyjątki.

## <a name="related-sections"></a>Sekcje pokrewne

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
Opisuje obsługę wyjątków w standardowym C++.

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
