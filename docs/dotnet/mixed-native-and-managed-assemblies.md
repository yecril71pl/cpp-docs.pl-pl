---
title: "Mieszane (natywne i zarządzane) zestawy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c58f69057a7da709ec79c614fe60beef5a203f0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mixed-native-and-managed-assemblies"></a>Zestawy mieszane (natywne i zarządzane)
Zestawy mieszane mogą zawierać zarówno niezarządzane instrukcje maszynowe, jak i instrukcje MSIL. Pozwala im to na wywołanie i bycie wywoływanym przez składniki .NET, przy zachowaniu zgodność ze składnikami, które są całkowicie niezarządzane. Używając zestawów mieszanych, deweloperzy mogą tworzyć aplikacje przy użyciu mieszanki funkcjonalności zarządzanej i niezarządzanej. Dzięki temu, zestawy mieszane są idealne do migrowania istniejących aplikacji Visual C++ do platformy .NET.  
  
 Na przykład składające się wyłącznie z funkcjami niezarządzanymi istniejącej aplikacji mogą być wprowadzane do platformy .NET przez kompilację tylko jeden moduł **/CLR** przełącznika kompilatora. Moduł ten będzie potem w stanie korzystać z funkcji .NET, ale pozostaje zgodny z pozostałą częścią aplikacji. W ten sposób można stopniowo konwertować aplikacje do platformy .NET, kawałek po kawałku. Istnieje nawet możliwość wybór między zarządzanymi i niezarządzanymi kompilacji na zasadach funkcja funkcji w ramach tego samego pliku (zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md)).  
  
 Visual C++ obsługuje generację trzech różnych typów zestawów zarządzanych: mieszane, czyste i sprawdzalne. Te ostatnie dwa omówiono w [czystej i weryfikowalny kod (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Migracja do/CLR](../dotnet/how-to-migrate-to-clr.md)  
 W tym artykule opisano zalecane kroki do wprowadzenia lub uaktualnienia funkcjonalności .NET w aplikacji.  
  
 [Porady: kompilowanie kodu MFC i ATL za pomocą opcji/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)  
 W tym artykule omówiono sposób kompilowania istniejących programów MFC i ATL do elementu docelowego środowiska uruchomieniowego języka wspólnego.  
  
 [Inicjalizacja zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md)  
 W tym artykule opisano problem „blokady modułu ładującego” i jego rozwiązania.  
  
 [Obsługa bibliotek dla zestawów mieszanych](../dotnet/library-support-for-mixed-assemblies.md)  
 W tym artykule omówiono sposób korzystać z natywnych bibliotek w **/CLR** kompilacji.  
  
 [Zagadnienia dotyczące wydajności](../dotnet/performance-considerations-for-interop-cpp.md)  
 W tym artykule opisano wpływ zestawów mieszanych i przekazywania danych na wydajność.  
  
 [Domeny aplikacji i programu Visual C++](../dotnet/application-domains-and-visual-cpp.md)  
 W tym artykule omówiono obsługę języka Visual C++ dla domen aplikacji.  
  
 [Podwójna konwersja bitowa adresów](../dotnet/double-thunking-cpp.md)  
 W tym artykule omówiono wpływ natywnego punktu wejścia dla funkcji zarządzanych na wydajność.  
  
 [Unikanie wyjątków CLR zamknięcia przypadku konsumowania obiektów COM skompilowanych z/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)  
 W tym artykule omówiono sposób zapewnienia poprawnego zamknięcia aplikacji zarządzanej, który wykorzystuje obiektów COM skompilowanych z **/CLR**.  
  
 [Porady: tworzenie aplikacji częściowo zaufanej przez usunięcie zależności biblioteki DLL środowiska CRT](../dotnet/create-a-partially-trusted-application.md)  
 W tym artykule omówiono sposób tworzenia aplikacji środowisko uruchomieniowe języka wspólnego częściowo zaufanej przez usunięcie zależności msvcm90.dll przy użyciu programu Visual C++.  
  
 Aby uzyskać więcej informacji na temat wytycznych programowania dla zestawów mieszanych, zobacz artykuł w witrynie MSDN "Przegląd z zarządzanego/niezarządzany współdziałanie kodu" w [http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp](http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp).  
  
## <a name="see-also"></a>Zobacz też  
 [Macierzysty i współdziałaniu .NET](../dotnet/native-and-dotnet-interoperability.md)