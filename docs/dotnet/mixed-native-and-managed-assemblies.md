---
title: Zestawy mieszane (natywne i zarządzane)
ms.date: 09/18/2018
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
ms.openlocfilehash: eee54a6101a83a64c221ae016f69931e7fd7829b
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403702"
---
# <a name="mixed-native-and-managed-assemblies"></a>Zestawy mieszane (natywne i zarządzane)

Zestawy mieszane mogą zawierać zarówno niezarządzane instrukcje maszynowe, jak i instrukcje MSIL. Umożliwia to wywoływanie i wywoływanie przez składniki platformy .NET, zachowując zgodność z natywnymi bibliotekami C++. Korzystając z zestawów mieszanych, deweloperzy mogą tworzyć aplikacje przy użyciu kombinacji programu .NET i natywnego kodu C++.

Na przykład istniejąca Biblioteka składająca się w całości z natywnego kodu języka C++ może zostać przeprowadzona do platformy .NET przez ponowne skompilowanie tylko jednego modułu z przełącznikiem kompilatora **/CLR** . Moduł ten będzie potem w stanie korzystać z funkcji .NET, ale pozostaje zgodny z pozostałą częścią aplikacji. Istnieje nawet możliwość podejmowania decyzji między kompilacją zarządzaną i natywną w ramach funkcji po funkcji w ramach tego samego pliku (zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md)).

Visual C++ obsługuje generowanie mieszanych zestawów zarządzanych przy użyciu opcji kompilatora **/CLR** . **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017. Jeśli wymagane są czyste lub możliwe do zweryfikowania zarządzane zestawy, zalecamy utworzenie ich przy użyciu języka C#.

Wcześniejsze wersje zestawu narzędzi kompilatora języka Microsoft C++ obsługiwały generowanie trzech różnych typów zestawów zarządzanych: mieszanych, czystych i możliwych do zweryfikowania. Te ostatnie dwie zostały omówione w [kodzie czystym i możliwym do zweryfikowania (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: migracja do/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
W tym artykule opisano zalecane kroki do wprowadzenia lub uaktualnienia funkcjonalności .NET w aplikacji.

[Instrukcje: kompilowanie kodu MFC i ATL za pomocą/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
W tym artykule omówiono sposób kompilowania istniejących programów MFC i ATL do elementu docelowego środowiska uruchomieniowego języka wspólnego.

[Inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md)<br/>
W tym artykule opisano problem „blokady modułu ładującego” i jego rozwiązania.

[Obsługa bibliotek dla zestawów mieszanych](../dotnet/library-support-for-mixed-assemblies.md)<br/>
W tym artykule omówiono sposób używania bibliotek natywnych w kompilacjach **/CLR** .

[Zagadnienia dotyczące wydajności](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
W tym artykule opisano wpływ zestawów mieszanych i przekazywania danych na wydajność.

[Domeny aplikacji i Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
W tym artykule omówiono obsługę języka Visual C++ dla domen aplikacji.

[Podwójny podwójna](../dotnet/double-thunking-cpp.md)<br/>
W tym artykule omówiono wpływ natywnego punktu wejścia dla funkcji zarządzanych na wydajność.

[Unikanie wyjątków przy zamykaniu środowiska CLR podczas używania obiektów COM skompilowanych przy użyciu opcji/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
W tym artykule omówiono sposób zapewnienia prawidłowego zamknięcia aplikacji zarządzanej, która korzysta z obiektu COM skompilowanego z **/CLR**.

[Instrukcje: Tworzenie częściowo zaufanej aplikacji przez usunięcie zależności od biblioteki DLL z biblioteką CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
W tym artykule omówiono sposób tworzenia częściowo zaufanej aplikacji środowiska uruchomieniowego języka wspólnego przy użyciu Visual C++, usuwając zależność od msvcm90.dll.

Aby uzyskać więcej informacji na temat wytycznych dotyczących kodowania dla zestawów mieszanych, zobacz [Omówienie współdziałania kodu zarządzanego/niezarządzanego](/previous-versions/dotnet/articles/ms973872(v=msdn.10)).

## <a name="see-also"></a>Zobacz też

- [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
