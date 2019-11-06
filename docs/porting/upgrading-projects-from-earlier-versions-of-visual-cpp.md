---
title: Uaktualnianie C++ projektów ze starszych wersji programu Visual Studio
description: Jak uaktualnić projekty firmy C++ Microsoft ze starszych wersji programu Visual Studio.
ms.date: 10/29/2019
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: b317271a9cd0873e60a6dd9acd1b73a766aaea19
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627165"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Uaktualnianie C++ projektów ze starszych wersji programu Visual Studio

Aby uaktualnić projekt utworzony w programie Visual Studio 2008 lub starszym, musisz najpierw użyć programu Visual Studio 2010 do przekonwertowania projektu z formatu VCBuild (. vcproj) na format MSBuild (. vcxproj). Aby uzyskać więcej informacji, zobacz [instrukcje dla programu Visual Studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

Aby uaktualnić projekt utworzony w programie Visual Studio 2010 lub nowszym, wystarczy otworzyć projekt w najnowszej wersji programu Visual Studio. Program Visual Studio oferuje uaktualnienie projektu do bieżącego schematu. Jeśli wybierzesz opcję **nie**, a masz starszą wersję programu Visual Studio na komputerze, możesz rozpocząć pracę nad projektem w nowszej wersji programu Visual Studio i nadal korzystać ze starszego zestawu narzędzi. Na przykład jeśli projekt musi nadal działać w systemie Windows XP, można go uaktualnić do programu Visual Studio 2019, ale należy określić zestaw narzędzi jako najnowsze 141 lub starszy. Aby uzyskać więcej informacji, zobacz [Używanie natywnego wielu elementów docelowych w programie Visual Studio do kompilowania starych projektów](use-native-multi-targeting.md). Jeśli wybierzesz opcję **tak**, projekt zostanie przekonwertowany i nie można go przekonwertować z powrotem do wcześniejszej wersji. W związku z tym w scenariuszach uaktualniania dobrym rozwiązaniem jest tworzenie kopii istniejących plików projektu i rozwiązania.

## <a name="upgrade-reports"></a>Uaktualnianie raportów

Podczas uaktualniania projektu otrzymujesz Raport z uaktualnienia, który jest również zapisywany w folderze projektu jako UpgradeLog. htm. Raport o uaktualnieniu zawiera podsumowanie dotyczące napotkanych problemów oraz informacje o wprowadzonych zmianach, w tym:

1. Właściwości projektu

2. Pliki dołączane

3. Kod, który nie jest już kompilowany z powodu ulepszeń kompilatora lub zmian w standardzie

4. Kod, który korzysta z programu Visual Studio lub funkcji systemu Windows, które nie są już dostępne lub nie są plikami nagłówka, które nie są dołączone do domyślnej instalacji programu Visual Studio lub zostały usunięte z produktu

5. Kod, który nie jest już kompilowany ze względu na zmiany w interfejsie API, takie jak interfejsy API nazw, zmienione podpisy funkcji lub funkcje przestarzałe

6. Kod, który nie jest już kompilowany ze względu na zmiany w diagnostyce, na przykład ostrzeżenie staje się błędem

7. Błędy konsolidatora wynikające z bibliotek, które zostały zmienione, szczególnie w przypadku używania/NODEFAULTLIB.

8. Błędy środowiska uruchomieniowego lub nieoczekiwane wyniki spowodowane zmianami zachowania

9. Błędy wprowadzone w narzędziach. W przypadku wystąpienia problemu zgłoś go do zespołu wizualnego C++ za pośrednictwem zwykłych kanałów pomocy technicznej lub strony [społeczności deweloperów programu Visual C++ Studio](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Niektóre uaktualnione projekty i rozwiązania można skompilować pomyślnie bez modyfikacji. Jednak większość projektów będzie prawdopodobnie wymagała wprowadzenia zmian w ustawieniach projektu, a także kodu źródłowego. Nie ma żadnego poprawnego sposobu, aby go rozwiązać, ale zalecane jest pewne podejście etapowe. Przed rozpoczęciem zapoznaj się [z omówieniem potencjalnych problemów z uaktualnianiem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) , aby uzyskać więcej informacji na temat wielu rodzajów typowych błędów.

 1. Ustaw zestaw narzędzi platformy, C++ Standard języka i wersję Windows SDK (jeśli ma zastosowanie) do żądanych wersji. ( **Właściwości** > **projektu** > **Właściwości konfiguracji** > **Ogólne**)
 1. Jeśli masz wiele błędów, wyłącz opcję [ograniczającą](../build/reference/permissive-standards-conformance.md) ( **Właściwości** > **projektu** > **Właściwości konfiguracji** > **języku** **C++ C/**  > ) i [Analiza kodu ](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)( **Właściwości** > **projektu** > **Właściwości konfiguracji** > **Analiza kodu**) tymczasowo, aby zmniejszyć liczbę błędów.
 1. Upewnij się, że wszystkie zależności są obecne i że ścieżki dołączania lub lokalizacje biblioteki są poprawne. ( **Właściwości** > **projektu** > **Właściwości konfiguracji** > **katalogów VC + +** )
 1. Identyfikować i naprawiać błędy ze względu na odwołania do interfejsów API, które już nie istnieją.
 1. Popraw wszystkie pozostałe błędy, które uniemożliwiają kompilację. Zapoznaj się z [omówieniem potencjalnych problemów z uaktualnianiem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) dla poprawek w przypadku typowych błędów.
 1. Włącz przynależność i rozwiąż wszelkie nowe błędy, które pojawiają się z powodu niezgodnego kodu, który został wcześniej SKOMPILOWANY w MSVC.
 1. Włącz analizę kodu, aby identyfikować potencjalne problemy lub nieaktualne wzorce kodowania, które nie są już uznawane za akceptowalne. Jeśli analiza kodu flaguje wiele błędów, można wyłączyć niektóre ostrzeżenia, aby skoncentrować się na najważniejszych pierwszych. Środowisko IDE może pomóc w szybkim rozwiązywaniu niektórych rodzajów problemów.
 1. Rozważ inne możliwości modernizacji kodu, na przykład przez zastąpienie niestandardowych struktur danych i algorytmów z zastosowaniem biblioteki C++ standardowej lub podwyższenie poziomu biblioteki Open Source. Dzięki funkcjom standardowym można ułatwić innym osobom zachowanie kodu i mieć silny stopień pewności, że kod został dobrze przetestowany i sprawdzony przez wielu ekspertów w Komitecie standardowym i szerszej C++ społeczności.

Aby usunąć błędy, spróbuj wyszukać lub opublikować pytanie w witrynie Stack Overflow lub [ C++ społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="in-this-section"></a>W tej sekcji

[Omówienie potencjalnych problemów z uaktualnianiem](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Uaktualnienie kodu do Universal CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[Aktualizuj WINVER i _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[Naprawianie zależności w bibliotece wewnętrznej](fix-your-dependencies-on-library-internals.md)<br/>
[Problemy przy migracji liczb zmiennoprzecinkowych](floating-point-migration-issues.md)<br/>
[C++funkcje przestarzałe w programie Visual Studio 2019](features-deprecated-in-visual-studio.md)<br/>
[VCBuild a MSBuild](build-system-changes.md)<br/>
[Porty innych firm](porting-third-party-libraries.md)<br/>

## <a name="see-also"></a>Zobacz także

[Co nowego w wizualizacji C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual C++ — historia zmian w latach 2003–2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)<br/>
[Porty — aplikacje](../data/data-access-programming-mfc-atl.md)<br/>
