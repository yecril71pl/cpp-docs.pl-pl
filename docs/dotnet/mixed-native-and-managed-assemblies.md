---
title: Mieszane (natywne i zarządzane) zestawy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 469e0429408e1b8afed65889539202650cd28413
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704792"
---
# <a name="mixed-native-and-managed-assemblies"></a>Zestawy mieszane (natywne i zarządzane)

Zestawy mieszane mogą zawierać zarówno niezarządzane instrukcje maszynowe, jak i instrukcje MSIL. Pozwala im to na wywołanie i bycie wywoływanym przez składniki .NET, przy zachowaniu zgodność ze składnikami, które są całkowicie niezarządzane. Używając zestawów mieszanych, deweloperzy mogą tworzyć aplikacje przy użyciu mieszanki funkcjonalności zarządzanej i niezarządzanej. Dzięki temu, zestawy mieszane są idealne do migrowania istniejących aplikacji Visual C++ do platformy .NET.

Na przykład składające się wyłącznie z funkcjami niezarządzanymi istniejącej aplikacji mogą być wprowadzane do platformy .NET przez kompilację tylko jeden moduł **/CLR** przełącznika kompilatora. Moduł ten będzie potem w stanie korzystać z funkcji .NET, ale pozostaje zgodny z pozostałą częścią aplikacji. W ten sposób można stopniowo konwertować aplikacje do platformy .NET, kawałek po kawałku. Istnieje nawet możliwość wybór między zarządzanymi i niezarządzanymi kompilacji na zasadach funkcja funkcji w ramach tego samego pliku (zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md)).

Visual C++ obsługuje tylko generowanie zestawów mieszanych zarządzanych za pomocą **/CLR** — opcja kompilatora. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r. Jeśli wymagane jest czysty i weryfikowalny zarządzanych zestawów, zaleca się tworzenie przy użyciu języka C#.

Generowanie trzy różne typy zarządzanych zestawów obsługiwane wcześniejszych wersji zestawu narzędzi kompilatora Visual C++: mieszanych, czystych i weryfikowalnych. Te ostatnie dwa omówiono w [czystej i weryfikowalny kod (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>W tej sekcji

[Porady: Migracja do/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
W tym artykule opisano zalecane kroki do wprowadzenia lub uaktualnienia funkcjonalności .NET w aplikacji.

[Porady: kompilowanie kodu MFC i ATL za pomocą opcji/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
W tym artykule omówiono sposób kompilowania istniejących programów MFC i ATL do elementu docelowego środowiska uruchomieniowego języka wspólnego.

[Inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md)<br/>
W tym artykule opisano problem „blokady modułu ładującego” i jego rozwiązania.

[Obsługa bibliotek dla zestawów mieszanych](../dotnet/library-support-for-mixed-assemblies.md)<br/>
W tym artykule omówiono sposób korzystać z natywnych bibliotek w **/CLR** kompilacji.

[Zagadnienia dotyczące wydajności](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
W tym artykule opisano wpływ zestawów mieszanych i przekazywania danych na wydajność.

[Domeny aplikacji i program Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
W tym artykule omówiono obsługę języka Visual C++ dla domen aplikacji.

[Podwójna konwersja bitowa adresów](../dotnet/double-thunking-cpp.md)<br/>
W tym artykule omówiono wpływ natywnego punktu wejścia dla funkcji zarządzanych na wydajność.

[Unikanie wyjątków CLR zamknięcia przypadku konsumowania obiektów COM skompilowanych z/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
W tym artykule omówiono sposób zapewnienia poprawnego zamknięcia aplikacji zarządzanej, który wykorzystuje obiektów COM skompilowanych z **/CLR**.

[Instrukcje: tworzenie aplikacji częściowo zaufanej przez usunięcie zależności od biblioteki DLL środowiska CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
W tym artykule omówiono sposób tworzenia aplikacji środowisko uruchomieniowe języka wspólnego częściowo zaufanej przez usunięcie zależności msvcm90.dll przy użyciu programu Visual C++.

Aby uzyskać więcej informacji o wytycznych programowania dla zestawów mieszanych, zobacz artykuł w witrynie MSDN [omówienie z zarządzanego/niezarządzany współdziałanie kodu](https://msdn.microsoft.com/en-us/library/ms973872.aspx).

## <a name="see-also"></a>Zobacz także

- [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
