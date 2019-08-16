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
ms.openlocfilehash: 11bdfc98c64b2612129e10c002c68ee243bec7da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501141"
---
# <a name="mixed-native-and-managed-assemblies"></a>Zestawy mieszane (natywne i zarządzane)

Zestawy mieszane mogą zawierać zarówno niezarządzane instrukcje maszynowe, jak i instrukcje MSIL. Umożliwia to wywoływanie i wywoływanie przez składniki platformy .NET, zachowując zgodność z natywnymi C++ bibliotekami. Korzystając z zestawów mieszanych, deweloperzy mogą tworzyć aplikacje przy użyciu kombinacji kodu .NET C++ i natywnego.

Na przykład istniejąca Biblioteka składająca się wyłącznie z C++ kodu natywnego może zostać przeprowadzona do platformy .NET przez ponowne skompilowanie tylko jednego modułu z przełącznikiem kompilatora **/CLR** . Moduł ten będzie potem w stanie korzystać z funkcji .NET, ale pozostaje zgodny z pozostałą częścią aplikacji. Istnieje nawet możliwość podejmowania decyzji między kompilacją zarządzaną i natywną w ramach funkcji po funkcji w ramach tego samego pliku (zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md)).

Wizualizacja C++ obsługuje tylko generowanie mieszanych zestawów zarządzanych przy użyciu opcji kompilatora **/CLR** . **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017. Jeśli wymagane są czyste lub możliwe do zweryfikowania zarządzane zestawy, zalecamy utworzenie ich przy C#użyciu programu.

Wcześniejsze wersje zestawu narzędzi kompilatora C++ firmy Microsoft obsługują generowanie trzech różnych typów zestawów zarządzanych: mieszanych, czystych i możliwych do zweryfikowania. Te ostatnie dwa zostały omówione w [czystym i możliwymC++do zweryfikowaniu kodzie (/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: Migruj do/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
W tym artykule opisano zalecane kroki do wprowadzenia lub uaktualnienia funkcjonalności .NET w aplikacji.

[Instrukcje: Kompiluj kod MFC i ATL za pomocą opcji/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
W tym artykule omówiono sposób kompilowania istniejących programów MFC i ATL do elementu docelowego środowiska uruchomieniowego języka wspólnego.

[Inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md)<br/>
W tym artykule opisano problem „blokady modułu ładującego” i jego rozwiązania.

[Obsługa bibliotek dla zestawów mieszanych](../dotnet/library-support-for-mixed-assemblies.md)<br/>
W tym artykule omówiono sposób używania bibliotek natywnych w kompilacjach **/CLR** .

[Zagadnienia dotyczące wydajności](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
W tym artykule opisano wpływ zestawów mieszanych i przekazywania danych na wydajność.

[Domeny aplikacji i program Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
W tym artykule omówiono obsługę języka Visual C++ dla domen aplikacji.

[Podwójny podwójna](../dotnet/double-thunking-cpp.md)<br/>
W tym artykule omówiono wpływ natywnego punktu wejścia dla funkcji zarządzanych na wydajność.

[Unikanie wyjątków przy zamykaniu środowiska CLR podczas używania obiektów COM skompilowanych przy użyciu opcji/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
W tym artykule omówiono sposób zapewnienia prawidłowego zamknięcia aplikacji zarządzanej, która korzysta z obiektu COM skompilowanego z **/CLR**.

[Instrukcje: tworzenie aplikacji częściowo zaufanej przez usunięcie zależności od biblioteki DLL środowiska CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
Omawia, jak utworzyć częściowo zaufaną aplikację środowiska uruchomieniowego języka wspólnego przy C++ użyciu wizualizacji, usuwając zależność od Msvcm90. dll.

Aby uzyskać więcej informacji na temat wytycznych dotyczących kodowania dla zestawów mieszanych, zobacz artykuł MSDN [Omówienie współdziałania kodu zarządzanego/](/previous-versions/dotnet/articles/ms973872(v=msdn.10))niezarządzanego.

## <a name="see-also"></a>Zobacz także

- [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
