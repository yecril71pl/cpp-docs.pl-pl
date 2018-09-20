---
title: Zestawy mieszane (natywne i zarządzane) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/18/2018
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
ms.openlocfilehash: 4ee94905bc4c40f6d080e34098e24bd71d495141
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494494"
---
# <a name="mixed-native-and-managed-assemblies"></a>Zestawy mieszane (natywne i zarządzane)

Zestawy mieszane mogą zawierać zarówno niezarządzane instrukcje maszynowe, jak i instrukcje MSIL. Umożliwi to wywołanie i bycie wywoływanym przez składniki .NET, przy zachowaniu zgodności z natywnych bibliotek C++. Używając zestawów mieszanych, deweloperzy mogą tworzyć aplikacje przy użyciu kombinacji kodu .NET i natywnego języka C++.

Na przykład istniejącej biblioteki składające się wyłącznie z macierzystego kodu C++ może być przeniesiona do platformy .NET przez ponowną kompilację tylko jednego modułu z **/CLR** przełącznika kompilatora. Moduł ten będzie potem w stanie korzystać z funkcji .NET, ale pozostaje zgodny z pozostałą częścią aplikacji. Istnieje nawet możliwość decydowania między zarządzanego i natywnego kompilacji na podstawie funkcji przez funkcję w obrębie tego samego pliku (zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md)).

Visual C++ obsługuje tylko generowanie zestawów mieszanych zarządzanych przy użyciu **/CLR** — opcja kompilatora. **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017. Jeśli wymagana jest czysty i weryfikowalny zestawów zarządzanych, zalecamy tworzenie przy użyciu języka C#.

Wcześniejsze wersje zestawu narzędzi kompilatora Visual C++ obsługuje generację trzech różnych typów zestawów zarządzanych: mieszanych, czystych i weryfikowalnych. Te ostatnie dwa są omówione w [czystej i możliwe do zweryfikowania kodu (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>W tej sekcji

[Porady: Migracja do/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
W tym artykule opisano zalecane kroki do wprowadzenia lub uaktualnienia funkcjonalności .NET w aplikacji.

[Porady: kompilowanie MFC i ATL kodu za pomocą/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
W tym artykule omówiono sposób kompilowania istniejących programów MFC i ATL do elementu docelowego środowiska uruchomieniowego języka wspólnego.

[Inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md)<br/>
W tym artykule opisano problem „blokady modułu ładującego” i jego rozwiązania.

[Obsługa bibliotek dla zestawów mieszanych](../dotnet/library-support-for-mixed-assemblies.md)<br/>
W tym artykule omówiono sposób użycia bibliotek natywnych w **/CLR** kompilacje.

[Zagadnienia dotyczące wydajności](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
W tym artykule opisano wpływ zestawów mieszanych i przekazywania danych na wydajność.

[Domeny aplikacji i program Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
W tym artykule omówiono obsługę języka Visual C++ dla domen aplikacji.

[Podwójna konwersja bitowa](../dotnet/double-thunking-cpp.md)<br/>
W tym artykule omówiono wpływ natywnego punktu wejścia dla funkcji zarządzanych na wydajność.

[Unikanie wyjątków przy CLR zamykania przypadku konsumowania obiektów COM skompilowanych z/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
W tym artykule omówiono sposób zapewnienia prawidłowego zamknięcia zarządzanej aplikacji, która przetwarza obiekt COM skompilowany przy użyciu **/CLR**.

[Instrukcje: tworzenie aplikacji częściowo zaufanej przez usunięcie zależności od biblioteki DLL środowiska CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
W tym artykule omówiono sposób tworzenia częściowo zaufanych aplikacji środowiska uruchomieniowego języka wspólnego przy użyciu języka Visual C++ przez usunięcie zależności od msvcm90.dll.

Aby uzyskać więcej informacji dotyczących wytycznych kodowania zestawów mieszanych, zobacz artykuł w witrynie MSDN [przegląd z zarządzanego/niezarządzanego kodu współdziałanie](https://msdn.microsoft.com/library/ms973872.aspx).

## <a name="see-also"></a>Zobacz także

- [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
