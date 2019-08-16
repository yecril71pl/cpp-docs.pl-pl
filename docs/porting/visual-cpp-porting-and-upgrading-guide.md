---
title: Wizualne C++ przenoszenie i uaktualnianie przewodnika
ms.date: 09/18/2018
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.openlocfilehash: cd74168419006388b8469086560452a8a99e05e2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511499"
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Wizualne C++ przenoszenie i uaktualnianie przewodnika

Ten temat zawiera Przewodnik uaktualniania kodu wizualnego C++ . Obejmuje to pobranie kodu do skompilowania i prawidłowego uruchomienia w nowszej wersji narzędzi, a także skorzystanie z nowych funkcji języka i programu Visual Studio. Ten temat zawiera również informacje o migrowaniu starszych aplikacji na bardziej nowoczesne platformy.

## <a name="reasons-to-upgrade-visual-c-code"></a>Przyczyny uaktualnienia kodu wizualnego C++

Należy rozważyć uaktualnienie kodu z następujących powodów:

- Szybszy kod, ze względu na udoskonalone optymalizacje kompilatora.

- Szybsze kompilacje ze względu na ulepszenia wydajności w kompilatorze.

- Ulepszone standardy zgodne. Wizualizacja C++ obecnie implementuje wiele funkcji z najnowszych C++ standardów.

- Lepsze zabezpieczenia. Funkcje zabezpieczeń, takie jak sprawdzanie Guard.

### <a name="porting-your-code"></a>Przenoszenie kodu

Podczas uaktualniania należy najpierw wziąć pod uwagę kod i projekty aplikacji. Czy Twoja aplikacja jest skompilowana przy użyciu programu Visual Studio? Jeśli tak, zidentyfikuj projekty, których to dotyczy.  Czy masz niestandardowe skrypty kompilacji? Jeśli masz niestandardowe skrypty kompilacji zamiast korzystania z systemu kompilacji programu Visual Studio, będziesz mieć więcej zadań do wykonania podczas uaktualniania, ponieważ nie możesz zaoszczędzić czasu, ponieważ program Visual Studio zaktualizuje pliki projektu i ustawienia kompilacji.

System kompilacji i format pliku projektu w programie Visual Studio uległy zmianie z vcbuild w wersjach do Visual Studio 2008 do MSBuild w wersjach programu Visual Studio z 2010 lub nowszym. Jeśli uaktualnienie pochodzi z wersji wcześniejszej niż 2010 i istnieje wysoce dostosowany system kompilacji, może być konieczne wykonanie większej ilości pracy w celu uaktualnienia. Jeśli uaktualniasz program Visual Studio 2010 lub nowszy, projekty już używają programu MSBuild, dlatego uaktualnianie projektu i kompilowanie aplikacji powinno być łatwiejsze.

Jeśli nie używasz systemu kompilacji programu Visual Studio, należy rozważyć uaktualnienie programu MSBuild. W przypadku uaktualnienia do korzystania z programu MSBuild może być łatwiejszy czas na kolejne uaktualnienia i będzie łatwiej używać usług takich jak Visual Studio Online. MSBuild obsługuje wszystkie platformy docelowe obsługiwane przez program Visual Studio.

### <a name="porting-visual-studio-projects"></a>Przenoszenie projektów programu Visual Studio

Aby rozpocząć uaktualnianie projektu lub rozwiązania, po prostu otwórz rozwiązanie w nowej wersji programu Visual Studio i postępuj zgodnie z monitami, aby rozpocząć uaktualnianie.  Podczas uaktualniania projektu otrzymujesz Raport z uaktualnienia, który jest również zapisywany w folderze projektu jako UpgradeLog. htm. Raport o uaktualnieniu zawiera podsumowanie problemów napotkanych podczas procesu uaktualniania oraz informacje o wprowadzonych zmianach lub problemy, których nie można rozwiązać automatycznie.

1. Właściwości projektu

2. Pliki dołączane

3. Kod, który nie jest już kompilowany w sposób czysty ze względu na zgodność kompilatora Imrovements lub zmiany w standardzie

4. Kod, który korzysta z programu Visual Studio lub funkcji systemu Windows, które nie są już dostępne lub nie są plikami nagłówka, które nie są dołączone do domyślnej instalacji programu Visual Studio lub zostały usunięte z produktu

5. Kod, który nie jest już kompilowany ze względu na zmiany w interfejsie API, takie jak interfejsy API nazw, zmienione podpisy funkcji lub funkcje przestarzałe

6. Kod, który nie jest już kompilowany ze względu na zmiany w diagnostyce, takie jak ostrzeżenie staje się błędem

7. Błędy konsolidatora wynikające z bibliotek, które zostały zmienione, szczególnie w przypadku używania/NODEFAULTLIB.

8. Błędy środowiska uruchomieniowego lub nieoczekiwane wyniki spowodowane zmianami zachowania

9. Błędy spowodowane błędami wprowadzonymi w narzędziach. W przypadku wystąpienia problemu zgłoś go do zespołu wizualnego C++ za pośrednictwem zwykłych kanałów pomocy technicznej lub strony [społeczności deweloperów programu Visual C++ Studio](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Oprócz zmian, których nie można uniknąć z powodu błędów kompilatora, niektóre zmiany są opcjonalne w procesie uaktualniania, na przykład:

1. Nowe ostrzeżenia mogą oznaczać, że chcesz wyczyścić swój kod. W zależności od konkretnej diagnostyki może to poprawić przenośność, zgodność ze standardami oraz bezpieczeństwo kodu.

2. Możesz chcieć skorzystać z nowszych funkcji kompilatora, takich jak [/Guard: CF (Enable Flow Control Guard)](../build/reference/guard-enable-control-flow-guard.md) , która dodaje sprawdzenia dla nieautoryzowanego wykonania kodu.

3. Możesz chcieć zaktualizować kod, aby używać nowych funkcji języka, które upraszczają kod, poprawiają wydajność programów lub aktualizować kod w celu korzystania z nowoczesnych bibliotek i są zgodne z nowoczesnymi standardami i najlepszymi rozwiązaniami.

Po uaktualnieniu i przetestowaniu projektu warto również rozważyć polepszenie kodu lub zaplanowanie przyszłego kierunku kodu, a nawet ponowne rozważenie architektury projektu. Czy otrzymasz trwającą prace programistyczne? Czy będzie ważne, aby kod był uruchamiany na innych platformach?  Jeśli tak, jakie platformy?  C++to standardowy język zaprojektowany z myślą o przenośności i opracowywaniu wielu platform, a jednak kod dla wielu aplikacji systemu Windows jest silnie powiązany z platformą systemu Windows. Czy chcesz reejść swój kod, aby oddzielić te części, które są bardziej powiązane z platformą systemu Windows?

Co z Twoim interfejsem użytkownika? Jeśli używasz MFC, możesz chcieć zaktualizować interfejs użytkownika. Czy używasz dowolnych nowszych funkcji MFC, które zostały wprowadzone w 2008 jako pakiet funkcji? Jeśli chcesz, aby Twoja aplikacja była nowsza, bez konieczności ponownego pisania całej aplikacji, możesz rozważyć użycie interfejsów API wstążki w MFC lub przy użyciu niektórych nowych funkcji MFC.

Jeśli chcesz nadać programowi interfejs użytkownika języka XAML, ale nie chcesz tworzyć aplikacji platformy UWP, możesz użyć C# with WPF do utworzenia warstwy interfejsu użytkownika i refaktoryzacji standardowej C++ logiki do bibliotek DLL. Utwórz warstwę współdziałania C++w programie/CLI C# , aby połączyć się z kodem natywnym. Innym rozwiązaniem jest utworzenie aplikacji platformy UWP przy użyciu [ C++/CX](../cppcx/visual-c-language-reference-c-cx.md) lub [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/). W systemie Windows 10 można użyć konwertera [aplikacji klasycznej](/windows/msix/desktop/desktop-to-uwp-run-desktop-app-converter) do spakowania istniejącej aplikacji klasycznej jako aplikacji platformy UWP bez konieczności modyfikowania kodu.

Alternatywnie, prawdopodobnie masz nowe wymagania lub można przewidzieć potrzeby dla platform docelowych innych niż komputery z systemem Windows, takie jak Windows Phone czy urządzenia z systemem Android. Kod interfejsu użytkownika można przenieść do biblioteki interfejsów użytkownika dla wielu platform. Dzięki tym architekturom interfejsu użytkownika można kierować wiele urządzeń, a nadal używać programu Visual Studio i debugera programu Visual Studio jako środowiska deweloperskiego.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|W tym artykule omówiono sposób używania projektów utworzonych we wcześniejszych wersjach programu Visual Studio.|
|[Co nowego w C++ kompilatorze w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)|Zmiany środowiska IDE i narzędzi do bieżącej wersji programu Visual Studio|
|[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)|Ulepszenia zgodności ze standardami z programu Visual Studio 2015 do programu Visual Studio|
|[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)|Lista wszystkich zmian w bibliotekach wizualnych C++ i narzędziach kompilacji z programu Visual Studio 2003 do 2015, które mogą wymagać zmian w kodzie.|
|[Visual C++ — co nowego od roku 2003 do 2015](visual-cpp-what-s-new-2003-through-2015.md)|Wszystkie informacje "co nowego" dotyczące wizualizacji C++ z programu visual Studio 2003 za pośrednictwem programu visual Studio 2015.|
|[Przenoszenie bibliotek innych firm](porting-third-party-libraries.md)|Jak używać narzędzia wiersza polecenia **vcpkg** do portów starszych bibliotek Open Source z wersjami skompilowanymi przy użyciu najnowszych zestawów narzędzi C++ wizualnych.|
|[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](porting-and-upgrading-examples-and-case-studies.md)|W tej sekcji zostały przewoźny i uaktualniony kilka przykładów i aplikacji oraz omówione zostały środowiska i wyniki. Może się okazać, że odczyty te dają Ci sensie, co obejmuje proces przenoszenia i uaktualniania. W trakcie całego procesu omówiono porady i wskazówki dotyczące uaktualniania oraz pokazujące, jak określone błędy zostały naprawione.|
|[Przenoszenie do platforma uniwersalna systemu Windows](porting-to-the-universal-windows-platform-cpp.md)|Zawiera informacje na temat przenoszenia kodu do systemu Windows 10|
|[Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX](introduction-to-visual-cpp-for-unix-users.md)|Zawiera informacje dla użytkowników systemu UNIX, którzy są nowością w programie Visual C++ i chcą pracować z nią.|
|[Eksportowanie z systemu UNIX do Win32](porting-from-unix-to-win32.md)|W tym artykule omówiono opcje migrowania aplikacji systemu UNIX do systemu Windows.|

## <a name="see-also"></a>Zobacz także

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)
