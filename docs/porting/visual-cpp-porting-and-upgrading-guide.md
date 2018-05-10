---
title: Visual C++, przenoszenie i uaktualnianie przewodnik | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 084c689ad7720e36670130d552522aa2f593218e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Visual C++, przenoszenie i uaktualnianie przewodnik
Ten temat zawiera przewodnik uaktualniania kodu Visual C++. Dotyczy to również pobierania kod, aby skompilować i poprawnie uruchomić na nowszą wersją narzędzia, a także korzystanie z nowego języka i funkcje programu Visual Studio. Ten temat zawiera także informacje o Migrowanie starszych aplikacji na platformach nowoczesnych więcej.  
  
## <a name="reasons-to-upgrade-visual-c-code"></a>Ze względu na uaktualnienie kodu języka Visual C++  
 Należy rozważyć uaktualnienie kodu z następujących powodów:  
  
-   Kod szybszy, z powodu optymalizacji kompilatora ulepszone.  
  
-   Szybsze kompilacje, ze względu na ulepszenia wydajności kompilatora samej siebie.  
  
-   Ulepszone standardów zgodności. Visual C++ teraz implementuje wiele funkcji z najnowszych standardów języka C++.  
  
-   Większe bezpieczeństwo. Funkcje zabezpieczeń, takich jak sprawdzanie guard.  
  
### <a name="porting-your-code"></a>Przenoszenie kodu  
 Podczas uaktualniania, najpierw należy wziąć pod uwagę kod i projekty aplikacji. Jest aplikacji skompilowanej za pomocą programu Visual Studio?  Jeśli tak, zidentyfikuj zaangażowany projektów.  Masz skrypty niestandardowej kompilacji?  Jeśli masz skrypty niestandardowej kompilacji zamiast system kompilacji programu Visual Studio, konieczne będzie więcej pracy w uaktualniania, ponieważ nie można zapisać czas dzięki użyciu programu Visual Studio, zaktualizuj pliki projektu oraz ustawienia kompilacji.  
  
 Kompilacja systemu i projektu format pliku w Visual Studio zmieniła się z program vcbuild w programie Visual Studio 2008 do wersji programu MSBuild w wersjami programu Visual Studio 2010 lub nowszej. Jeśli jest uaktualnienie z wersji przed 2010 i korzystasz z systemu kompilacji wysoce dostosowane, może być konieczne uaktualnienie kontynuować pracę.  W przypadku uaktualniania z programu Visual Studio 2010 lub nowszej, projekty są już przy użyciu programu MSBuild, więc uaktualniania projektu i kompilacja aplikacji powinno być łatwiejsze.  
  
 Jeśli system kompilacji programu Visual Studio nie jest używany, należy rozważyć uaktualnienie do Użyj programu MSBuild. Użyj programu MSBuild w przypadku uaktualniania łatwiejsze czasu może być w przyszłych uaktualnień i będzie łatwiejszy do korzystania z usług takich jak Visual Studio Online. MSBuild obsługuje wszystkich platformach docelowych, które obsługuje program Visual Studio.  
  
### <a name="porting-visual-studio-projects"></a>Eksportowanie projektów programu Visual Studio  
  Aby rozpocząć uaktualnianie projekt lub rozwiązanie, po prostu otwórz rozwiązanie w nowej wersji programu Visual Studio i postępuj zgodnie z monitami, aby rozpocząć uaktualnianie go.  Podczas uaktualniania projektu, możesz uzyskać uaktualnienia raport, który również jest zapisywany w folderze projektu jako UpgradeLog.htm. Uaktualnienia raport zawiera podsumowanie jakie problemy wystąpiły podczas procesu uaktualniania, a niektóre informacje na temat zmiany lub problemów, które nie może być automatycznie rozwiązany.  
  
1.  Właściwości projektu  
  
2.  Pliki dołączane  
  
3.  Kod, który nie jest już skompilowany bez błędów, z powodu imrovements zgodność kompilatora lub zmiany w standardzie  
  
4.  Kod, który wykorzystuje funkcje programu Visual Studio lub systemu Windows, które nie są już dostępne lub pliki nagłówkowe, które nie są uwzględniane w domyślnej instalacji programu Visual Studio lub zostały usunięte z produktu  
  
5.  Kod, który nie jest już kompiluje z powodu zmian w interfejsów API takie jak zmienione interfejsy API, zmienić sygnatury funkcji lub przestarzałe funkcje  
  
6.  Kod, który nie jest już kompiluje z powodu zmian w diagnostyce, takie jak ostrzeżenia, staje się błąd  
  
7.  Błędy konsolidatora z powodu bibliotek, które zostały zmienione, szczególnie w przypadku, gdy jest używany/nodefaultlib.  
  
8.  Błędy środowiska wykonawczego lub nieoczekiwane wyniki z powodu zmian zachowania  
  
9. Błędy z powodu błędów, które zostały wprowadzone w narzędziach. Jeśli wystąpi problem, zgłoś go do zespołu Visual C++ przez inne kanały pomocy technicznej normalnym lub za pomocą [Centrum opinii programu Visual Studio](http://connect.microsoft.com/VisualStudio/Feedback).  
  
 Oprócz zmian, których nie można pominąć z powodu błędów kompilatora, niektóre zmiany są opcjonalne w procesie uaktualniania, takich jak:  
  
1.  Nowe ostrzeżenia może oznaczać, że chcesz wyczyścić kodu. W zależności od określonych diagnostyki może to poprawić przenośność, standardów zgodności i zabezpieczeń kodu.  
  
2.  Warto skorzystać z nowszej kompilatora funkcji takich jak [/GUARD: CF (Włącz kontroli ochronę przepływu)](../build/reference/guard-enable-control-flow-guard.md) opcję kompilatora, która dodaje sprawdza, czy wykonywanie nieautoryzowanego kodu.  
  
3.  Może chcesz zaktualizować niektóre kod, aby korzystać z nowych funkcji języka, które uprościć kod, poprawić wydajność programy lub zaktualizuj kod, aby korzystać z nowoczesnymi bibliotek i są zgodne z nowoczesnych standardów i najlepsze rozwiązania.  
  
 Po uaktualnieniu i przetestowany projekt, również warto wziąć pod uwagę poprawiania kodu w dalszych planowanie przyszłych kierunek kodu lub nawet rozważenia architektura projektu. Zostanie wyświetlony bieżących prac projektowych? Czy będą ważne w przypadku wykonywania na innych platformach kodu?  Jeśli tak, jakie platformy?  C++ jest langauge standardowych, zaprojektowany z przenośnością i programowanie wieloplatformowych pamiętać i jeszcze kodu dla wielu aplikacji systemu Windows jest silnie związany z platformy systemu Windows. Czy chcesz zrefaktoryzuj kod, aby rozdzielić tych elementów, które są bardziej powiązane z platformy Windows?  
  
 Co interfejsu użytkownika?  Jeśli używasz MFC, można zaktualizować interfejsu użytkownika.  Używasz dowolnej nowsze funkcje MFC, które zostały wprowadzone w 2008 jako Feature Pack?  Jeśli chcesz zapewnić nowszej wygląd i działanie aplikacji bez ponownego tworzenia całej aplikacji, można rozważyć za pomocą wstążki interfejsów API w MFC lub niektóre z nowych funkcji MFC.  
  
 Jeśli chcesz nadać program interfejs użytkownika XAML, ale nie chcesz utworzyć aplikację platformy uniwersalnej systemu Windows, korzystając C# z użyciem WPF do tworzenia warstwy interfejsu użytkownika i zrefaktoryzuj logiki standard C++ do biblioteki dll. Tworzenie warstwy współdziałanie w języku C + +/ CLI nawiązać C# w kodzie macierzystym. Innym rozwiązaniem jest tworzenie aplikacji platformy uniwersalnej systemu Windows przy użyciu [C + +/ CX](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh699871.aspx) lub [C + +/ WinRT](https://github.com/microsoft/cppwinrt). W systemie Windows 10 można użyć [konwertera aplikacji pulpitu](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) do pakietu istniejących aplikacji pulpitu w aplikacji platformy uniwersalnej systemu Windows bez konieczności modyfikowania kodu.   
 Alternatywnie istnieje teraz nowe wymagania lub przewidujesz potrzebę przeznaczonych dla platformy innych niż system Windows desktop, takie jak Windows Phone lub urządzeń z systemem Android. Można portu kodu interfejsu użytkownika do biblioteki interfejsu użytkownika i platform. Z tych platform interfejsu użytkownika można wiele urządzeń i nadal używać programu Visual Studio i debuger programu Visual Studio jako środowiska deweloperskiego.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|W tym artykule omówiono sposób korzystania z projektów utworzonych w starszych wersjach programu Visual C++.|  
|[What's New dla kompilatora języka C++ w programie Visual Studio RC 2017 r](../what-s-new-for-visual-cpp-in-visual-studio.md)|Zmiany w IDE i narzędzi Visual Studio 2015 do programu Visual Studio 2017 r.|  
|[Ulepszenia zgodności języka C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md)|Ulepszenia zgodność standardów z programu Visual Studio 2015 Visual Studio 2017 r.|  
|[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)|Lista wszystkich zmian w bibliotek języka Visual C++ i narzędzia kompilacji programu Visual Studio 2003 za pośrednictwem 2015, które mogą wymagać zmian w kodzie.|  
|[Visual C++ — co nowego od roku 2003 do 2015](visual-cpp-what-s-new-2003-through-2015.md)|Wszystkie "nowości" informacje w języku Visual C++ z programu Visual Studio 2003 za pomocą programu Visual Studio 2015.|  
|[Przenoszenie bibliotek innych firm](porting-third-party-libraries.md)|Jak używać **vcpkg** narzędzie wiersza polecenia do portu starsze biblioteki open source do wersji skompilowane z nowszą procesami Visual C++.|  
|[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](porting-and-upgrading-examples-and-case-studies.md)|Dla tej sekcji możemy przenieść i uaktualnia kilka przykładów i aplikacji i omówione uruchomień oraz wyniki. Może się okazać, że odczytywania zapewnia te można zorientować się, co jest objętego przenoszenie i uaktualnianie procesu. W trakcie procesu, możemy omówienia porady i wskazówki dotyczące uaktualniania i Pokaż jak określone błędy zostały usunięte.|  
|[Przenoszenie na platformę uniwersalną systemu Windows](porting-to-the-universal-windows-platform-cpp.md)|Zawiera informacje o eksportowaniu kodu do systemu Windows 10|  
|[Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX](introduction-to-visual-cpp-for-unix-users.md)|Zawiera informacje dla użytkowników systemu UNIX, które są nowe w programie Visual C++ i chcesz wydajność z nim.|  
|[Eksportowanie z systemu UNIX do Win32](porting-from-unix-to-win32.md)|Omówienie opcji migrowania aplikacji systemu UNIX do systemu Windows.|  
|[Podręcznik migracji C++/CLI](../dotnet/cpp-cli-migration-primer.md)|Przedstawia szczegółowo sposób uaktualnienia programu rozszerzeń zarządzanych dla składni języka C++ Użyj nowej składni. Aby uzyskać więcej informacji, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual C++](../visual-cpp-in-visual-studio.md)
