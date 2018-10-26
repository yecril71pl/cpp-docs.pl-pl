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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d8c5188cccceb0c09de95c43a72a645ded0e6a9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077522"
---
# <a name="desktop-applications-visual-c"></a>Aplikacje klasyczne (Visual C++)

A *aplikacja komputerowa* w języku C++ jest natywna aplikacja, które ma dostęp do pełnego zestawu interfejsów API Windows i albo działa w oknie lub w konsoli programu system. Aplikacji klasycznych w języku C++ uruchomić na Windows XP do systemu Windows 10 (chociaż Windows XP nie jest już oficjalnie obsługiwany wiąże się z wielu interfejsów API Windows, które zostały wprowadzone od tego czasu).

Aplikacja komputerowa różni się od aplikacji uniwersalnych platformy Windows (UWP), które mogą być uruchamiane na komputerach z systemem Windows 10, a także na konsoli XBox, Windows Phone, urządzeniu Surface Hub i innych urządzeń. Aby uzyskać więcej informacji na temat klasycznych programu vs. Aplikacje platformy uniwersalnej systemu Windows, zobacz [wybierz swoją technologię](https://msdn.microsoft.com/library/windows/desktop/dn614993).

### <a name="desktop-bridge"></a>Desktop Bridge

W systemie Windows 10 można pakietu istniejących aplikacji pulpitu lub obiektu COM jako aplikację platformy uniwersalnej systemu Windows i Dodaj funkcje platformy uniwersalnej systemu Windows, takie jak touch lub wywoływać interfejsy API z nowoczesnych zestawu Windows API. Aplikacja platformy uniwersalnej systemu Windows można również dodać do pulpitu rozwiązania w programie Visual Studio i pakiet je razem w jednym pakietu i komunikować się między nimi za pomocą interfejsów API Windows.

W Visual Studio 2017 w wersji 15.4 lub nowszy można utworzyć projekt pakietu aplikacji Windows, do znacznego uproszczenia pracy pakowania swoją istniejącą aplikację pulpitu. Kilka ograniczenia mają zastosowanie w odniesieniu do rejestru, które wywołuje lub korzysta z interfejsów API aplikacji pulpitu, ale w wielu przypadkach można utworzyć ścieżki alternatywnej kodu do osiągnięcia podobne funkcje podczas uruchamiania w pakiecie aplikacji. Aby uzyskać więcej informacji, zobacz [Desktop Bridge](/windows-uwp/porting/desktop-to-uwp-root).

### <a name="terminology"></a>Terminologia

- A *Win32* aplikacja jest Windows, aplikacji klasycznych w języku C++, który może zgłaszać korzystać z natywnych [interfejsów API języka C Windows i/lub interfejsów API modelu COM](https://msdn.microsoft.com/library/windows/desktop/ff818516) CRT i standardowe biblioteki interfejsów API i 3 bibliotek innych firm. Aplikacja Win32, który działa w oknie wymaga deweloperowi jawnie pracować Windows komunikaty wewnątrz funkcji procedury Windows. Niezależnie od nazwy jest aplikacją systemu Win32 może być kompilowane jako (x86) 32-bitowy lub 64-bitowych (x64) binarny. W programie Visual Studio IDE to samo warunków x86 i Win32.

- [Component Object Model (COM)](/windows/desktop/com/the-component-object-model) jest specyfikacja, która umożliwia programom napisane w różnych językach, aby komunikować się ze sobą. Windows wiele składników są implementowane jako obiekty COM i postępuj zgodnie z standardowe zasady modelu COM do tworzenia obiektów interfejsu zniszczenie odnajdywania i obiektu.  Obiekty COM z aplikacji klasycznych w języku C++ jest stosunkowo prosta, ale zapisywania obiektu COM jest bardziej zaawansowane. [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) zawiera makra i funkcje pomocnicze, które upraszczają programowanie COM.

- Aplikacja MFC jest używanego przez aplikację pulpitu Windows [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) do tworzenia interfejsu użytkownika. Aplikacja MFC umożliwia również składników COM, a także CRT i standardowych interfejsów API w bibliotece. Biblioteka MFC zawiera alokowania elastycznego otok obiektowy C++ przez API Windows i pętli komunikatów okien. MFC jest opcją domyślną dla aplikacji — zwłaszcza aplikacji typu korporacyjnego — które mają wiele formantów interfejsu użytkownika lub niestandardowych formantów użytkownika. MFC udostępnia wygodne klasy pomocnika do zarządzania systemem Windows, serializacji, operacji na tekście, drukowania i elementy interfejsu użytkownika modern, takie jak wstążki. Zaczęła obowiązywać z MFC, należy zapoznać się z systemu Win32.

- W języku C + +/ interfejsu wiersza polecenia aplikacji lub składnika używa rozszerzeń do składni języka C++ (zgodnie ze specyfikacją języka C++) umożliwiające interakcje między kodu .NET i natywnego języka C ++.  W języku C + +/ interfejsu wiersza polecenia aplikacji mogą mieć części, które działa natywnie i części, działających w .NET Framework z dostępem do Biblioteka klasy podstawowej platformy .NET. C + +/ interfejsu wiersza polecenia jest preferowaną opcją, gdy masz macierzystego kodu C++, który musi współpracować przy użyciu kodu napisanego w języku C# lub Visual Basic. Jest przeznaczona głównie do użytku w bibliotekach DLL platformy .NET, a nie w kodzie interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [programowania .NET w języku C + +/ interfejsu wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Można użyć dowolnej aplikacji klasycznych w języku C++, C Runtime (CRT) i standardową bibliotekę klas i funkcji, obiektów COM i funkcji Windows publicznych, które są łącznie znane jako interfejsu API Windows. Aby zapoznać się z wprowadzeniem do Windows aplikacji klasycznych w języku C++, zobacz [Naucz się Program dla Windows w języku C++](http://go.microsoft.com/fwlink/p/?LinkId=262281).

## <a name="in-this-section"></a>W tej sekcji

|Tytuł|Opis|
|-----------|-----------------|
|[Aplikacje konsoli](../windows/console-applications-in-visual-cpp.md)|Zawiera informacje o aplikacjach konsoli. Aplikacja konsoli Win32 (lub Win64) ma, nie własnego okna ani pętli komunikatów. Działa w oknie konsoli, a dane wejściowe i wyjściowe są obsługiwane za pośrednictwem wiersza polecenia.|
|[Aplikacje pulpitu Windows](../windows/windows-desktop-applications-cpp.md)|Jak utworzyć aplikacje klasyczne, które są uruchamiane w systemie windows, w przeciwieństwie do konsoli programu.|
|[Zasoby służące do tworzenia gier za pomocą programu DirectX (C++)](../windows/resources-for-creating-a-game-using-directx.md)|Zawiera łącza do zawartości do tworzenia gier w języku C++.|
|[Wskazówki: Tworzenie i używanie biblioteki statycznej](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Jak utworzyć plik binarny lib.|
|[Instrukcje: używanie zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Zawiera instrukcje dotyczące konfigurowania projektu kompilować przy użyciu zestawu SDK systemu Windows 10.|

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie aplikacji dla systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=262282)|Zawiera informacje o interfejsie Windows API i modelu COM. (Niektóre interfejsy API Windows i biblioteki DLL innych firm, są implementowane jako obiekty COM.)|
|[Hilo: Projektowanie aplikacji Windows 7 w języku C++](http://go.microsoft.com/fwlink/p/?LinkId=262284)|Opisuje sposób tworzenia aplikacji klasycznych Windows wzbogaconego klienta używającej animacji Windows i Direct2D do utworzenia interfejsu użytkownika opartego na karuzeli.  W tym samouczku nie został jeszcze zaktualizowany od Windows 7, ale nadal zapewnia szczegółowe wprowadzenie do programowania systemu Win32.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|W tym artykule opisano kluczowe funkcje programu Visual C++ w Visual Studio i łącza do pozostałej części dokumentacji języka Visual C++.|

## <a name="see-also"></a>Zobacz też

[Visual C++](../visual-cpp-in-visual-studio.md)