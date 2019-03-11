---
title: Visual C++, przenoszenie i uaktualnianie przewodnik
ms.date: 09/18/2018
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.openlocfilehash: 1b3f7142b5240d8b4a94040d5cda7d033e50e39d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752431"
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Visual C++, przenoszenie i uaktualnianie przewodnik

Ten temat zawiera wskazówki dotyczące uaktualniania kodu Visual C++. W tym wprowadzenie kodu, aby skompilować i uruchomić się poprawnie w nowszej wersji narzędzi, a także korzystając z zalet nowego języka i funkcje programu Visual Studio. Ten temat zawiera także informacje o Migrowanie starszych aplikacji na bardziej nowoczesnych platformach.

## <a name="reasons-to-upgrade-visual-c-code"></a>Ze względu na uaktualnianie kodu Visual C++

Należy rozważyć uaktualnienie kodu z następujących powodów:

- Kod szybciej, ze względu na optymalizacje kompilatora ulepszone.

- Szybsza kompilacja, ze względu na ulepszenia wydajności w kompilatorze, sam.

- Zgodność ze standardami ulepszone. Visual C++ implementuje są teraz wiele funkcji z najnowszymi standardami języka C++.

- Większe bezpieczeństwo. Funkcje zabezpieczeń, takie jak sprawdzanie guard.

### <a name="porting-your-code"></a>Przenoszenie kodu

Podczas uaktualniania, najpierw należy wziąć pod uwagę kod i projekty aplikacji. Twoja aplikacja powstała z programem Visual Studio? Jeśli tak, należy zidentyfikować projekty, które są zaangażowane.  Czy masz skrypty kompilacji niestandardowej Jeśli masz skrypty kompilacji niestandardowej zamiast systemu kompilacji programu Visual Studio, konieczne będzie więcej pracy do wykonania podczas uaktualniania, ponieważ nie można zaoszczędzić czas, przez Visual Studio ustawienia kompilacji i zaktualizuj pliki projektu.

Kompilacja systemu i projektu format pliku w programie Visual Studio zmieniła się z program vcbuild w wersji do programu Visual Studio 2008 do programu MSBuild w wersjach programu Visual Studio 2010 lub nowszy. Jeśli uaktualnianie jest w wersji wcześniejszej niż 2010 i masz system kompilacji wysoce dostosowany, Niewykluczone, że więcej pracy do uaktualnienia. Jeśli uaktualnianie z programu Visual Studio 2010 lub nowszej, Twoich projektów są już korzystanie z programu MSBuild, więc uaktualnianie projektu i kompilacja aplikacji powinno być łatwiejsze.

Jeśli nie używasz systemu kompilacji programu Visual Studio, należy rozważyć uaktualnienie za pomocą programu MSBuild. Jeśli uaktualniasz za pomocą programu MSBuild, użytkownik może teraz łatwiejsze w przyszłych uaktualnień i będzie łatwiejszy do korzystania z usług takich jak Visual Studio Online. Program MSBuild obsługuje wszystkich platform docelowych, które obsługuje program Visual Studio.

### <a name="porting-visual-studio-projects"></a>Przenoszenie projektów programu Visual Studio

Aby rozpocząć uaktualnianie projektu lub rozwiązania, po prostu otwórz rozwiązanie w nowej wersji programu Visual Studio i postępuj zgodnie z monitami, aby rozpocząć uaktualnianie go.  Kiedy uaktualniasz projekt, otrzymasz raport o uaktualnieniu, który również jest zapisywany w folderze projektu jako UpgradeLog.htm. Raport o uaktualnieniu przedstawia podsumowanie jakie problemy wystąpiły podczas procesu uaktualniania i pewne informacje o wprowadzone zmiany lub problemów, które nie może być automatycznie rozwiązany.

1. Właściwości projektu

2. Dołącz pliki

3. Kod, który nie jest już skompilowany bez błędów, z powodu imrovements zgodności kompilatora lub zmiany w standardzie

4. Kod, który wykorzystuje funkcje programu Visual Studio lub Windows, które nie są już dostępne lub pliki nagłówkowe, które nie są uwzględniane w domyślnej instalacji programu Visual Studio lub zostały usunięte z produktu

5. Kod, który już nie kompiluje z powodu zmian w interfejsach API takich jak zmienić nazwy interfejsów API, zmianę sygnatury funkcji lub przestarzałe funkcje

6. Kod, który już nie kompiluje się z powodu zmian w diagnostyce, takie jak ostrzeżenia, staje się błąd

7. Błędy konsolidatora z powodu bibliotek, które zostały zmienione, szczególnie w przypadku, gdy jest używany/nodefaultlib.

8. Błędy w czasie wykonywania lub nieoczekiwane wyniki z powodu zmian zachowania

9. Błędy z powodu błędów, które zostały wprowadzone w narzędziach. Jeśli wystąpi problem, zgłoś go do zespołu Visual C++, za pośrednictwem kanałów normalne pomocy technicznej lub za pomocą [Centrum opinii programu Visual Studio](http://connect.microsoft.com/VisualStudio/Feedback).

Oprócz zmian, których nie można uniknąć z powodu błędów kompilatora niektóre zmiany są opcjonalne w procesie uaktualniania, takich jak:

1. Nowe ostrzeżenia może oznaczać, że chcesz wyczyścić swój kod. W zależności od określonych diagnostyki może to poprawić przenośności, zgodność ze standardami i bezpieczeństwa kodu.

2. Możesz chcieć skorzystać z nowszych kompilatora funkcji takich jak [/GUARD: CF (Włącz przepływ sterowania ochronę)](../build/reference/guard-enable-control-flow-guard.md) — opcja kompilatora, który dodaje sprawdza, czy wykonywanie nieautoryzowanych kodu.

3. Być może chcesz zaktualizować niektóre kod, aby korzystać z nowych funkcji języka, które upraszcza kod, poprawić wydajność programów lub zaktualizować kod, aby korzystać z bibliotek nowoczesnych i być zgodna z nowoczesnych standardów i najlepsze rozwiązania.

Po uaktualnieniu i przetestowany projekt, możesz również chcieć należy wziąć pod uwagę poprawiania kodu w dalszych planowanie kierunek rozwoju kodu lub nawet ponowne rozpatrzenie architektury projektu. Będzie ona otrzymywać bieżących prac projektowych Czy będą ważne w przypadku wykonywania na innych platformach kodu?  Jeśli tak, jakie platformy?  Język C++ jest językiem standardowych, zaprojektowana z przenośność i programowanie dla wielu platform, pamiętaj, a jeszcze kodu dla wielu aplikacji Windows zdecydowanie jest powiązany z Windows platform. Czy chcesz wykonać refaktoryzację kodu, do oddzielenia tych elementów, które są bardziej powiązane z platformą Windows?

Jak wygląda interfejs użytkownika? Jeśli używasz biblioteki MFC, możesz chcieć zaktualizować interfejs użytkownika. Używasz dowolnego z nowszych funkcji MFC, które zostały wprowadzone w 2008 roku jako dodatek Feature Pack? Jeśli chcesz nadaj nowszej wygląd i działanie aplikacji bez konieczności ponownego zapisu całej aplikacji, można rozważyć za pomocą wstążki interfejsów API w MFC lub niektóre z nowych funkcji MFC.

Jeśli chcesz nadać swojemu programowi interfejs użytkownika XAML, ale nie chcesz utworzyć aplikację platformy uniwersalnej systemu Windows, służy C# przy użyciu platformy WPF do utworzenia warstwy Interfejsu i Refaktoryzacja logika standard C++ do bibliotek DLL. Utwórz warstwę współdziałanie w języku C + +/ interfejsu wiersza polecenia do łączenia z C# w kodzie macierzystym. Innym rozwiązaniem jest tworzenie aplikacji platformy uniwersalnej systemu Windows przy użyciu [C + +/ CX](https://msdn.microsoft.com/library/windows/apps/xaml/hh699871.aspx) lub [C + +/ WinRT](https://github.com/microsoft/cppwinrt). W systemie Windows 10, możesz użyć [Desktop App Converter](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) spakować swoją istniejącą aplikację pulpitu, jak aplikacja platformy uniwersalnej systemu Windows bez konieczności modyfikowania kodu.

Alternatywnie być może masz teraz nowe wymagania lub przewidujesz potrzebę przeznaczonych dla platform innych niż Windows desktop, na przykład Windows Phone lub urządzeń z systemem Android. Można przyłącz kod interfejsu użytkownika do biblioteki interfejsu użytkownika dla wielu platform. Za pomocą tych platform tworzenia interfejsu użytkownika można wiele urządzeń i nadal używać programu Visual Studio i debugerze programu Visual Studio jako środowiska deweloperskiego.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|W tym artykule omówiono sposób używania projekty utworzone we wcześniejszych wersjach programu Visual C++.|
|[What's New for kompilator języka C++ w programie Visual Studio 2017 RC](../what-s-new-for-visual-cpp-in-visual-studio.md)|Zmiany w środowisku IDE i narzędzia programu Visual Studio 2015 do programu Visual Studio 2017|
|[Ulepszenia zgodności języka C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md)|Ulepszenia zgodności standardów z programu Visual Studio 2015 do programu Visual Studio 2017|
|[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)|Lista wszystkich zmian bibliotek języka Visual C++ i narzędzia do kompilacji programu Visual Studio 2003 do 2015, które mogą wymagać zmian w kodzie.|
|[Visual C++ — co nowego od roku 2003 do 2015](visual-cpp-what-s-new-2003-through-2015.md)|Wszystkie "co nowego" informacje Visual c++ dla programu Visual Studio 2003 za pomocą programu Visual Studio 2015.|
|[Przenoszenie bibliotek innych firm](porting-third-party-libraries.md)|Jak używać **vcpkg** narzędzia wiersza polecenia do portu starsze bibliotek typu open source do wersji skompilowany przy użyciu nowszego zestawy narzędzi Visual C++.|
|[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](porting-and-upgrading-examples-and-case-studies.md)|W tej sekcji firma Microsoft przenoszone uaktualnia kilka przykładów i aplikacji i omówiono środowiska i wyników. Może się okazać, że odczytywanie te zapewnia możesz zorientować się, co jest zaangażowane w przenoszeniu i uaktualnianiu procesu. W całym procesie, możemy omówić porady i wskazówki dotyczące uaktualniania i pokazują, jak określone błędy zostały usunięte.|
|[Przenoszenie na platformę Windows Universal](porting-to-the-universal-windows-platform-cpp.md)|Zawiera informacje dotyczące przenoszenia kodu do systemu Windows 10|
|[Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX](introduction-to-visual-cpp-for-unix-users.md)|Zawiera informacje dla użytkowników systemu UNIX, którzy jesteś nowym użytkownikiem Visual C++ i chcesz stać się za pomocą go.|
|[Eksportowanie z systemu UNIX do Win32](porting-from-unix-to-win32.md)|W tym artykule omówiono opcje do migrowania aplikacji systemu UNIX do Windows.|

## <a name="see-also"></a>Zobacz także

[Visual C++](../visual-cpp-in-visual-studio.md)
