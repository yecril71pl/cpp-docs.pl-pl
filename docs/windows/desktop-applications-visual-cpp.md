---
title: Aplikacje klasyczne (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e7d3612cd306dc2235b9fb4e6051415cba699c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569797"
---
# <a name="desktop-applications-visual-c"></a>Aplikacje klasyczne (Visual C++)
A *aplikacją* w języku C++ jest aplikacji natywnej dostępnej pełny zestaw interfejsów API systemu Windows i albo działa w oknie lub w konsoli systemowej. Aplikacje w języku C++ można uruchomić w systemie Windows XP do systemu Windows 10 (chociaż systemu Windows XP jest już oficjalnie obsługiwana i istnieje wiele interfejsów API systemu Windows, które zostały wprowadzone od tego czasu).

Aplikacja różni się od aplikacji systemu Windows platformy Uniwersalnej, które można uruchomić na komputerach z systemem Windows 10, a także na konsoli XBox, Windows Phone, Surface Hub i innych urządzeniach. Aby uzyskać więcej informacji na temat pulpitu vs. Aplikacji platformy uniwersalnej systemu Windows, zobacz [Wybierz technologię](https://msdn.microsoft.com/en-us/library/windows/desktop/dn614993\(v=vs.85\).aspx).  


**Mostek pulpitu** systemu Windows 10 można spakować istniejących aplikacji pulpitu lub obiektu modelu COM jako aplikację platformy uniwersalnej systemu Windows, a także dodać funkcje platformy uniwersalnej systemu Windows, takich jak touch lub wywoływać interfejsy API z nowoczesny interfejs API systemu Windows ustaw. Można również dodać aplikacji platformy uniwersalnej systemu Windows do rozwiązania pulpitu w Visual Studio i pakiet je razem w jednym pakietu i komunikować się między nimi przy użyciu interfejsów API systemu Windows.  
   
W Visual Studio 2017 wersji 15,4 i nowszych można utworzyć projekt pakietu aplikacji systemu Windows do znacznego uproszczenia pracy pakowania istniejącej aplikacji klasycznych. Kilka ograniczenia są stosowane względem wywołuje jakie rejestru lub korzysta z interfejsów API aplikacji pulpitu, ale w wielu przypadkach można utworzyć ścieżki alternatywnego kodu do osiągnięcia podobne funkcje podczas uruchamiania w pakiecie aplikacji. Aby uzyskać więcej informacji, zobacz [Mostek pulpitu](/windows-uwp/porting/desktop-to-uwp-root).  
  
 **Terminologia**  
  
-   A *Win32* aplikacja jest aplikacją w języku C++, który może zgłaszać użycie macierzystego systemu Windows [interfejsów API systemu Windows C i/lub interfejsów API modelu COM.](https://msdn.microsoft.com/en-us/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT i standardowej biblioteki interfejsów API i 3 bibliotek strony. Aplikacji Win32, która działa w oknie wymaga deweloperowi jawnie współpracować komunikatów systemu Windows w funkcji procedury systemu Windows. Niezależnie od nazwy aplikacji Win32 mogą być kompilowane jako (x86) 32-bitowy lub 64-bitowych (x64) binarnego. W programie Visual Studio IDE warunków x86 i Win32 to samo.  
  
-   [Składnik modelu COM.](https://msdn.microsoft.com/en-us/library/windows/desktop/ms694363\(v=vs.85\).aspx) jest specyfikacją, która umożliwia programom napisane w różnych językach do komunikowania się ze sobą. Wiele okien składniki są zaimplementowane jako obiekty COM i wykonaj standardowe zasady Tworzenie obiektów COM interfejs zniszczenie odnajdywania i obiektu.  Przy użyciu obiektów COM z aplikacjami klasycznymi C++ jest stosunkowo prosta, ale zapisywanie obiektu modelu COM jest bardziej zaawansowane. [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) zawiera makra i funkcje pomocnicze, które upraszczają programowanie COM.  
  
-   Użyj aplikacją pulpitu systemu Windows jest aplikacji MFC [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) do tworzenia interfejsu użytkownika. Aplikacji MFC można również użyć składniki COM oraz CRT i standardowej biblioteki interfejsów API. MFC udostępnia cienką otoką zorientowane obiektowo C++ w porównaniu z pętli komunikatów okna i interfejsów API systemu Windows. MFC jest domyślnie wybierana aplikacje — szczególnie aplikacje typu enterprise —, która ma wiele formantów interfejsu użytkownika lub kontrolki użytkownika niestandardowego. MFC udostępnia klasy pomocy wygodny do zarządzania systemem Windows, serializacji, manipulowanie tekstu, drukowania i elementy interfejsu użytkownika modern, takie jak wstążki. Efektywność z MFC, należy zapoznać się z systemu Win32.  
  
-   C + +/ CLI aplikację lub składnik używa rozszerzeń składni języka C++ (dozwolone przez specyfikację języka C++) umożliwiające interakcje między .NET i kod natywny C ++.  C + +/ CLI aplikacji może mieć elementy, które są uruchamiane w sposób macierzysty i części systemem w programie .NET Framework z dostępem do Biblioteka klas programu .NET Base. C + +/ CLI jest preferowaną opcję w przypadku kodu natywnego języka C++ potrzebne do pracy z kod napisany w języku C# lub Visual Basic. Jest przeznaczone głównie do użytku w bibliotekach DLL .NET, a nie w kodzie interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [.NET Programowanie w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
 C Runtime (CRT) i bibliotekę standardową klasy i funkcje, obiekty COM i publicznego funkcje systemu Windows, które są nazywane zbiorczo interfejsu API systemu Windows, można użyć dowolnego aplikacją w języku C++. Aby obejrzeć wprowadzenie do aplikacji pulpitu systemu Windows w języku C++, zobacz [więcej informacji o programie dla systemu Windows w języku C++](http://go.microsoft.com/fwlink/p/?LinkId=262281).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Aplikacje konsoli](../windows/console-applications-in-visual-cpp.md)|Zawiera informacje o aplikacji konsoli. Aplikacji konsoli Win32 (lub Win64) ma żadnego okna własnych i Brak pętli komunikatów. Działa w oknie konsoli, a dane wejściowe i wyjściowe są obsługiwane za pośrednictwem wiersza polecenia.|  
|[Aplikacje systemu Windows](../windows/windows-desktop-applications-cpp.md)|Jak tworzyć aplikacje działające w systemie windows, w przeciwieństwie do konsoli.|  
|[Zasoby służące do tworzenia gier za pomocą programu DirectX (C++)](../windows/resources-for-creating-a-game-using-directx.md)|Linki do zawartości do tworzenia gier w języku C++.|  
|[Wskazówki: Tworzenie i używanie biblioteki statycznej](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Jak utworzyć plik binarny lib.|  
|[Instrukcje: używanie zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zawiera instrukcje dotyczące konfigurowania projektu kompilować przy użyciu zestawu SDK systemu Windows 10.|  
  
## <a name="related-articles"></a>Powiązane artykuły  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Tworzenie aplikacji dla systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=262282)|Zawiera informacje na temat interfejsu API systemu Windows i modelu COM. (Niektóre interfejsów API systemu Windows i bibliotek DLL innych firm, są zaimplementowane jako obiekty COM.)|  
|[Hilo: Tworzenie aplikacji C++ dla systemu Windows 7](http://go.microsoft.com/fwlink/p/?LinkId=262284)|Opisuje sposób tworzenia wzbogaconego klienta Windows aplikacją, która używa do tworzenia interfejsu użytkownika opartego na Karuzela animacji systemu Windows i programem Direct2D.  W tym samouczku nie został zaktualizowany od systemu Windows 7, ale nadal zawiera dokładne wprowadzenie do programowania w języku systemu Win32.|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|W tym artykule opisano najważniejsze funkcje programu Visual C++ w Visual Studio i łącza do pozostałej części dokumentacji Visual C++.|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual C++](../visual-cpp-in-visual-studio.md)
