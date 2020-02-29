---
title: Synchronizacja zmian między środowiskiem XCode a programem Visual Studio
ms.date: 10/17/2019
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.openlocfilehash: ab941551c519acee49f658d8a8ff1b9fe0e4ba49
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177536"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchronizacja zmian między środowiskiem XCode a programem Visual Studio

Tworzenie aplikacji mobilnych za C++ pomocą składników w programie Visual Studio obejmuje zdalne możliwości synchronizacji pracy między komputerem i komputerem Mac. Gdy komputery z programem Visual Studio i komputerów Mac są sparowane, nowe opcje są dostępne dla projektów aplikacji dla systemu iOS w programie Visual Studio, których można użyć do otwierania projektu w Xcode, przenoszenia kodu między Xcode i Visual Studio oraz czyszczenia tymczasowego katalogu projektu Xcode.

Aby użyć opcji komputer zdalny, projekt musi być projektu aplikacji systemu iOS, a Visual Studio muszą być skojarzone z Twojego komputera Mac. Aby uzyskać wymagania wstępne i instrukcje dotyczące parowania z komputerem Mac, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>W menu maszyny zdalnej

W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby wyświetlić menu kontekstowe. Wybierz element **maszyny zdalnej** , aby wyświetlić dostępne opcje zdalne.

![Element menu maszyny zdalnej w Eksplorator rozwiązań](../cross-platform/media/cppmdd-u2-remotemachine-menu.jpg "Element menu maszyny zdalnej w Eksplorator rozwiązań")

Te polecenia umożliwiają otwieranie projektu w programie Xcode, przenoszenie lokalnych zmian lub całego projektu między programem Visual Studio i Xcode, a także czyszczenie plików tymczasowych na maszynie zdalnej.

## <a name="open-in-xcode"></a>Otwórz w Xcode

Aby otworzyć projekt w programie Xcode z poziomu programu Visual Studio, w podmenu **komputer zdalny** wybierz polecenie **Otwórz w Xcode** , aby otworzyć wybrany projekt na sparowanym komputerze zdalnym. Serwer `vcremote` jest używany do otwierania Xcode na komputerze Mac i przechodzenia do katalogu tymczasowego utworzonego na komputerze Mac, który zawiera kopię projektu. Program Visual Studio pojawia się okno dialogowe, które zawiera katalog tymczasowy używany dla projektu. Akcje wykonywane na maszynie zdalnej są również wyświetlane w oknie **danych wyjściowych** w programie Visual Studio. Aby je wyświetlić, w górnej części okna **danych wyjściowych** może być konieczne wybranie opcji  **C++ Wizualizacja maszyna zdalna** .

![W oknie dane wyjściowe są wyświetlane akcje maszyny zdalnej.](../cross-platform/media/cppmdd-u2-remotemachine-output.png "W oknie dane wyjściowe są wyświetlane akcje maszyny zdalnej")

Na komputerze Mac możesz użyć wszystkich narzędzi Xcode, aby edytować swój kod i zasoby, Scenorysy i akcje. W programie Visual Studio projekt aplikacji systemu iOS jest oznaczony adnotacją "otwarty w Xcode", aby wskazać, że zmiany mogą zostać wprowadzone na komputerze zdalnym. Po zakończeniu edycji ściąganie z lokalizacji zdalnej lub przyrostowe ściąganie z poleceń zdalnych można użyć do skopiowania zmiany do projektu programu Visual Studio.

## <a name="push-to-remote-and-incremental-push-to-remote"></a>Wypchnij do zdalnego i przyrostowe Wypychanie do lokalizacji zdalnej

Jeśli zostały wprowadzone zmiany do projektu aplikacji systemu iOS w programie Visual Studio, Wypychanie do zdalnego i przyrostowe Wypychanie do poleceń zdalnych może służyć do przenoszenia plików projektu zmienione na sparowanym komputerze zdalnym. Wypychanie do polecenia zdalnego kopiuje wszystkie pliki projektu do maszyny zdalnej. Tylko przyrostowe Wypychanie do polecenia zdalnego kopiuje zmienionych plików do maszyny zdalnej. W przypadku dużych projektów z niewielkich zmian przyrostowych polecenie pozwala zaoszczędzić czas i przepustowości.

Aby skopiować pliki projektu na komputer Mac, w programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz pozycję **maszyna zdalna** i wybierz opcję **wypychania do zdalnego** lub **przyrostowego wypychania do zdalnego** , aby skopiować pliki projektu z programu Visual Studio na komputer Mac.

## <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Korzystaj z zdalnego i przyrostowe ściąganie z lokalizacji zdalnej

Po wprowadzeniu zmian w projekcie w programie Xcode Przenieś zmiany z powrotem do programu Visual Studio, aby zachować synchronizację projektów.

Aby skopiować pliki projektu z komputera Mac, w programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz pozycję **maszyna zdalna** , a następnie wybierz pozycję **ściąganie** lub **przyrostowe ściąganie z dysku zdalnego** , aby skopiować pliki projektu z komputera Mac do programu Visual Studio.

## <a name="clean-remote"></a>Wyczyść maszynę zdalną

Polecenia Wyczyść zdalnego służy do usuwania plików w katalogu projektu tymczasowego na komputerze zdalnym. Zawartość katalogu, w tym wszystkie pliki źródłowe lub produktów kompilacji, są usuwane na komputerze Mac. Upewnij się, że zostały zsynchronizowane wszelkie zmiany, które chcesz zachować powrót do programu Visual Studio przy użyciu ściągnięcia ze zdalnej lub przyrostowe ściąganie ze zdalnej, zanim użyjesz polecenia Wyczyść zdalnego.

Aby wyczyścić tymczasowy katalog projektu na komputerze zdalnym, w programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz pozycję **maszyna zdalna** i wybierz polecenie **Oczyść zdalnie** , aby usunąć pliki katalogu projektu z komputera Mac.
