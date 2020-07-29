---
title: Obsługa wyjątków  (C++/CLI i C++/CX)
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
ms.openlocfilehash: 23d65bb8056672d12e3d40f9fcab1e58bab65a3d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219706"
---
# <a name="exception-handling--ccli-and-ccx"></a>Obsługa wyjątków  (C++/CLI i C++/CX)

Aplikacje skompilowane przy użyciu `/ZW` opcji kompilatora lub `/clr` opcji kompilatora używają *wyjątków* do obsługi nieoczekiwanych błędów podczas wykonywania programu. W poniższych tematach omówiono obsługę wyjątków w aplikacjach C++/CX i C++/CLI.

## <a name="in-this-section"></a>W tej sekcji

[Podstawowe pojęcia związane z używaniem wyjątków zarządzanych](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Opisuje zgłaszanie wyjątków i używanie **`try`** / **`catch`** bloków.

[Różnice w zachowaniu obsługi wyjątków w/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
W tym artykule omówiono różnice między standardowym zachowaniem obsługi wyjątków języka C++.

[finally](../dotnet/finally.md)<br/>
W tym artykule omówiono sposób użycia słowa kluczowego finally.

[Instrukcje: Definiowanie i Instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Pokazuje, jak można przechwytywać Nieobsłużone wyjątki.

[Instrukcje: Przechwytywanie wyjątków w kodzie natywnym wygenerowanym z MSIL](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
W tym artykule omówiono sposób przechwytywania wyjątków CLR i C++ w kodzie natywnym.

[Instrukcje: Definiowanie i Instalowanie globalnego programu obsługi wyjątków](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Pokazuje, jak przechwytywać wszystkie Nieobsłużone wyjątki.

## <a name="related-sections"></a>Sekcje pokrewne

[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)<br/>
Opisuje obsługę wyjątków w standardowym języku C++.

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
