---
title: Uaktualnianie projektów C++ z wcześniejszych wersji programu Visual Studio
description: Jak uaktualnić projekty Microsoft C++ ze starszych wersji programu Visual Studio.
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: 7a4ab98c196d601bc458fe33bb1e2cb45ac30088
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505892"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Uaktualnianie projektów C++ z wcześniejszych wersji programu Visual Studio

Aby uaktualnić projekt utworzony we wcześniejszej wersji programu Visual Studio, po prostu otwórz projekt w najnowszej wersji programu Visual Studio. Program Visual Studio oferuje uaktualnienie projektu do bieżącego schematu.

Jeśli wybierzesz opcję **nie**, projekt nie zostanie uaktualniony. W przypadku projektów utworzonych w programie Visual Studio 2010 i nowszych można nadal używać projektu w nowszej wersji programu Visual Studio. Po prostu ustaw właściwości projektu, aby dalej korzystać ze starszego zestawu narzędzi. Jeśli opuścisz starszą wersję programu Visual Studio na komputerze, jego zestaw narzędzi będzie dostępny w nowszych wersjach. Na przykład jeśli projekt musi nadal działać w systemie Windows XP, można przeprowadzić uaktualnienie do programu Visual Studio 2019. Następnie należy określić zestaw narzędzi jako v141_xp lub wcześniej we właściwościach projektu. Aby uzyskać więcej informacji, zobacz [Używanie natywnego wielu elementów docelowych w programie Visual Studio do kompilowania starych projektów](use-native-multi-targeting.md).

Jeśli wybierzesz opcję **tak**, projekt zostanie uaktualniony w miejscu. Nie można go przekonwertować z powrotem do wcześniejszej wersji. Ze względu na scenariusze uaktualniania dobrym rozwiązaniem jest wykonanie kopii zapasowej istniejących plików projektu i rozwiązania.

## <a name="upgrade-reports"></a>Uaktualnianie raportów

Podczas uaktualniania projektu otrzymujesz Raport z uaktualnienia. Raport jest również zapisywany w folderze projektu jako UpgradeLog.htm. Raport o uaktualnieniu zawiera podsumowanie problemów znalezionych podczas konwersji. Zawiera on pewne informacje o wprowadzonych zmianach, w tym:

- Właściwości projektu.

- Pliki dołączane.

- Kod, który nie jest już kompilowany z powodu ulepszeń kompilatora lub zmian w standardzie.

- Kod, który korzysta z programu Visual Studio lub funkcji systemu Windows, które nie są już dostępne. Lub pliki nagłówkowe, które nie są uwzględnione w domyślnej instalacji programu Visual Studio lub zostały usunięte z produktu.

- Kod, który nie jest już kompilowany ze względu na zmiany w interfejsie API, takie jak interfejsy API nazw, zmienione podpisy funkcji lub funkcje przestarzałe.

- Kod, który nie jest już kompilowany ze względu na zmiany w diagnostyce, na przykład ostrzeżenie staje się błędem

- Błędy konsolidatora z powodu bibliotek, które zostały zmienione, szczególnie gdy jest używana/NODEFAULTLIB.

- Błędy środowiska uruchomieniowego lub nieoczekiwane wyniki spowodowane zmianami zachowania.

- Błędy wprowadzone w narzędziach. W przypadku znalezienia problemu zgłoś go do zespołu Visual C++ za pośrednictwem zwykłych kanałów pomocy technicznej lub na stronie [społeczności deweloperów programu Visual Studio C++](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Niektóre uaktualnione projekty i rozwiązania można skompilować pomyślnie bez modyfikacji. Jednak większość projektów będzie prawdopodobnie wymagała zmian w ustawieniach projektu i kodzie źródłowym. Nie istnieje pojedynczy prawidłowy sposób rozwiązania tych problemów, ale zalecamy użycie podejścia etapowego. Przed rozpoczęciem zapoznaj się [z omówieniem potencjalnych problemów z uaktualnianiem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) , aby uzyskać więcej informacji na temat wielu rodzajów typowych błędów.

1. Ustaw zestaw narzędzi platformy, Standard języka C++ i wersję Windows SDK (jeśli dotyczy) w preferowanych wersjach. (**Projekt**  >  **Właściwości**  >  **Właściwości konfiguracji**  >  **Ogólne**)

1. Jeśli masz wiele błędów, możesz tymczasowo wyłączyć niektóre opcje podczas ich rozwiązywania. Aby wyłączyć opcję [/permissive-](../build/reference/permissive-standards-conformance.md) , użyj właściwości konfiguracji **Project**  >  **Właściwości**projektu  >  **Configuration Properties**  >  **C/C++**  >  **Language**. Aby wyłączyć opcję [analizy kodu](../code-quality/code-analysis-for-c-cpp-overview.md) , użyj właściwości konfiguracji właściwości **projektu**  >  **Properties**  >  **Configuration Properties**  >  **Analiza kodu**.

1. Upewnij się, że wszystkie zależności są obecne i że ścieżki dołączania lub lokalizacje biblioteki są poprawne. (**Projekt**  >  **Właściwości**  >  **Właściwości konfiguracji**  >  **Katalogi VC + +**)

1. Identyfikowanie i rozwiązywanie błędów spowodowanych odwołaniami do interfejsów API, które już nie istnieją.

1. Popraw wszystkie pozostałe błędy, które uniemożliwiają kompilację. Zapoznaj się z [omówieniem potencjalnych problemów z uaktualnianiem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) dla poprawek w przypadku typowych błędów.

1. Włącz **/permissive-** i napraw wszelkie nowe błędy spowodowane przez niezgodny kod, który został wcześniej SKOMPILOWANY w MSVC.

1. Włącz analizę kodu, aby identyfikować potencjalne problemy lub nieaktualne wzorce kodowania, które nie są już uznawane za akceptowalne. Jeśli analiza kodu flaguje wiele błędów, można wyłączyć niektóre ostrzeżenia, aby skoncentrować się na najważniejszych pierwszych. Środowisko IDE może pomóc w szybkim rozwiązywaniu niektórych rodzajów problemów.

1. Rozważ inne możliwości modernizacji kodu. Na przykład Zastąp niestandardowe struktury danych i algorytmy tymi, które pochodzą z standardowej biblioteki C++, lub Zwiększ bibliotekę Open Source. Korzystając z funkcji standardowych, można ułatwić innym osobom zachowanie kodu. Możesz mieć pewność, że ten kod został dobrze przetestowany i sprawdzony przez wielu ekspertów w Komitecie standardowym i szerszej społeczności języka C++.

Aby usunąć błędy, spróbuj wyszukać lub opublikować pytanie w witrynie Developer Stack Overflow lub [społeczność deweloperów języka C++](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="in-this-section"></a>W tej sekcji

[Omówienie potencjalnych problemów z uaktualnianiem](overview-of-potential-upgrade-issues-visual-cpp.md)\
[Uaktualnianie kodu do uniwersalnej architektury CRT](upgrade-your-code-to-the-universal-crt.md)\
[Aktualizuj WINVER i _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[Popraw zależności od elementów wewnętrznych biblioteki](fix-your-dependencies-on-library-internals.md)\
[Problemy z migracją zmiennoprzecinkową](floating-point-migration-issues.md)\
[Funkcje języka C++ przestarzałe w programie Visual Studio 2019](features-deprecated-in-visual-studio.md)\
[VCBuild a MSBuild](build-system-changes.md)\
[Przenoszenie bibliotek innych firm](porting-third-party-libraries.md)

## <a name="see-also"></a>Zobacz też

[Co nowego w Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visual C++ historię zmian 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)\
[Przenoszenie aplikacji danych](../data/data-access-programming-mfc-atl.md)
