---
title: Uaktualnianie C++ projektów ze starszych wersji programu Visual Studio
description: Jak uaktualnić projekty firmy C++ Microsoft ze starszych wersji programu Visual Studio.
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: bc9fb5628c1a628b91f306c346f2bbb1dea13de8
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416107"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Uaktualnianie C++ projektów ze starszych wersji programu Visual Studio

Aby uaktualnić projekt utworzony we wcześniejszej wersji programu Visual Studio, po prostu otwórz projekt w najnowszej wersji programu Visual Studio. Program Visual Studio oferuje uaktualnienie projektu do bieżącego schematu.

Jeśli wybierzesz opcję **nie**, projekt nie zostanie uaktualniony. W przypadku projektów utworzonych w programie Visual Studio 2010 i nowszych można nadal używać projektu w nowszej wersji programu Visual Studio. Po prostu ustaw właściwości projektu, aby dalej korzystać ze starszego zestawu narzędzi. Jeśli opuścisz starszą wersję programu Visual Studio na komputerze, jego zestaw narzędzi będzie dostępny w nowszych wersjach. Na przykład jeśli projekt musi nadal działać w systemie Windows XP, można przeprowadzić uaktualnienie do programu Visual Studio 2019. Następnie należy określić zestaw narzędzi jako v141_xp lub wcześniej we właściwościach projektu. Aby uzyskać więcej informacji, zobacz [Używanie natywnego wielu elementów docelowych w programie Visual Studio do kompilowania starych projektów](use-native-multi-targeting.md).

Jeśli wybierzesz opcję **tak**, projekt zostanie uaktualniony w miejscu. Nie można go przekonwertować z powrotem do wcześniejszej wersji. Ze względu na scenariusze uaktualniania dobrym rozwiązaniem jest wykonanie kopii zapasowej istniejących plików projektu i rozwiązania.

## <a name="upgrade-reports"></a>Uaktualnianie raportów

Podczas uaktualniania projektu otrzymujesz Raport z uaktualnienia. Raport jest również zapisywany w folderze projektu jako UpgradeLog. htm. Raport o uaktualnieniu zawiera podsumowanie problemów znalezionych podczas konwersji. Zawiera on pewne informacje o wprowadzonych zmianach, w tym:

- Właściwości projektu.

- Pliki dołączane.

- Kod, który nie jest już kompilowany z powodu ulepszeń kompilatora lub zmian w standardzie.

- Kod, który korzysta z programu Visual Studio lub funkcji systemu Windows, które nie są już dostępne. Lub pliki nagłówkowe, które nie są uwzględnione w domyślnej instalacji programu Visual Studio lub zostały usunięte z produktu.

- Kod, który nie jest już kompilowany ze względu na zmiany w interfejsie API, takie jak interfejsy API nazw, zmienione podpisy funkcji lub funkcje przestarzałe.

- Kod, który nie jest już kompilowany ze względu na zmiany w diagnostyce, na przykład ostrzeżenie staje się błędem

- Błędy konsolidatora z powodu bibliotek, które zostały zmienione, szczególnie gdy jest używana/NODEFAULTLIB.

- Błędy środowiska uruchomieniowego lub nieoczekiwane wyniki spowodowane zmianami zachowania.

- Błędy wprowadzone w narzędziach. W przypadku znalezienia problemu zgłoś go do zespołu wizualnego C++ za pośrednictwem zwykłych kanałów pomocy technicznej lub strony [społeczności deweloperów programu Visual C++ Studio](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Niektóre uaktualnione projekty i rozwiązania można skompilować pomyślnie bez modyfikacji. Jednak większość projektów będzie prawdopodobnie wymagała zmian w ustawieniach projektu i kodzie źródłowym. Nie istnieje pojedynczy prawidłowy sposób rozwiązania tych problemów, ale zalecamy użycie podejścia etapowego. Przed rozpoczęciem zapoznaj się [z omówieniem potencjalnych problemów z uaktualnianiem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) , aby uzyskać więcej informacji na temat wielu rodzajów typowych błędów.

1. Ustaw zestaw narzędzi platformy, C++ Standard języka i wersję Windows SDK (jeśli dotyczy) w preferowanych wersjach. ( **Właściwości** > **projektu** > **Właściwości konfiguracji** > **Ogólne**)

1. Jeśli masz wiele błędów, możesz tymczasowo wyłączyć niektóre opcje podczas ich rozwiązywania. Aby wyłączyć opcję [/permissive-](../build/reference/permissive-standards-conformance.md) , użyj **Właściwości** > **projektu** > **Właściwości konfiguracji** > **języku** **C++ C/**  > . Aby wyłączyć opcję [analizy kodu](/cpp/code-quality/code-analysis-for-c-cpp-overview) , użyj **właściwości** > **projektu** > **Właściwości konfiguracji** > **Analiza kodu**.

1. Upewnij się, że wszystkie zależności są obecne i że ścieżki dołączania lub lokalizacje biblioteki są poprawne. ( **Właściwości** > **projektu** > **Właściwości konfiguracji** > **katalogów VC + +** )

1. Identyfikowanie i rozwiązywanie błędów spowodowanych odwołaniami do interfejsów API, które już nie istnieją.

1. Popraw wszystkie pozostałe błędy, które uniemożliwiają kompilację. Zapoznaj się z [omówieniem potencjalnych problemów z uaktualnianiem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) dla poprawek w przypadku typowych błędów.

1. Włącz **/permissive-** i napraw wszelkie nowe błędy spowodowane przez niezgodny kod, który został wcześniej SKOMPILOWANY w MSVC.

1. Włącz analizę kodu, aby identyfikować potencjalne problemy lub nieaktualne wzorce kodowania, które nie są już uznawane za akceptowalne. Jeśli analiza kodu flaguje wiele błędów, można wyłączyć niektóre ostrzeżenia, aby skoncentrować się na najważniejszych pierwszych. Środowisko IDE może pomóc w szybkim rozwiązywaniu niektórych rodzajów problemów.

1. Rozważ inne możliwości modernizacji kodu. Na przykład Zastąp niestandardowe struktury danych i algorytmy tymi samymi C++ z biblioteki standardowej lub Zwiększ bibliotekę Open Source. Korzystając z funkcji standardowych, można ułatwić innym osobom zachowanie kodu. Możesz mieć pewność, że ten kod został dobrze przetestowany i sprawdzony przez wielu ekspertów w Komitecie standardowym i szerszej C++ społeczności.

Aby usunąć błędy, spróbuj wyszukać lub opublikować pytanie w witrynie Stack Overflow lub [ C++ społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="in-this-section"></a>W tej sekcji

[Omówienie potencjalnych problemów z uaktualnianiem](overview-of-potential-upgrade-issues-visual-cpp.md)\
[Uaktualnij kod do uniwersalnej\ CRT](upgrade-your-code-to-the-universal-crt.md)
[Zaktualizuj winver i _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[Napraw zależności od wewnętrznych bibliotek](fix-your-dependencies-on-library-internals.md)\
[Problemy z migracją zmiennoprzecinkową](floating-point-migration-issues.md)\
[funkcje przestarzałe w programie Visual Studio 2019\ C++ ](features-deprecated-in-visual-studio.md)
[Vcbuild a MSBuild](build-system-changes.md)\
[Porty innych firm](porting-third-party-libraries.md)

## <a name="see-also"></a>Zobacz też

[Co nowego w wizualizacji C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Historia C++ zmian wizualnych 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
\ [zachowanie niestandardowe](../cpp/nonstandard-behavior.md)
[Porty — aplikacje](../data/data-access-programming-mfc-atl.md)
