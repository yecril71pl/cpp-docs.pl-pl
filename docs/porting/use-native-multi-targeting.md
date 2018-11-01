---
title: Użyj natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów
ms.date: 11/04/2016
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: a4bb059b13f2001c6691e8d051106aa5e11eccbd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429170"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Użyj natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów

Normalnie firma Microsoft zaleca, zaktualizuj swoje projekty, po zainstalowaniu najnowszej wersji programu Visual Studio. Koszt aktualizacji projektów i kodu jest zazwyczaj bardziej niż przesunięcie przez zalet nowego środowiska IDE, kompilatora, bibliotek i narzędzi. Jednak wiemy, że nie można zaktualizować niektórych projektów. Masz plików binarnych, które są powiązane z starsze bibliotek i platform, ze względów konserwacji nie można uaktualnić. Twój kod może używać konstrukcji językowych niestandardowych, które zaburzyłaby, jeśli został przeniesiony do kompilatora nowszą. Twój kod może polegać na 3 bibliotek innych firm dla określonej wersji programu Visual C++. Lub może generować biblioteki dla innych osób, które musi być przeznaczony dla określonego starszej wersji programu Visual C++.

Na szczęście można użyć programu Visual Studio 2017 i Visual Studio 2015 do tworzenia projektów, że zestawy narzędzi kompilatora starszych docelowych i bibliotek. Uaktualnienie programu Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 lub projektu programu Visual Studio 2015 z zalet nowych funkcji w środowisku IDE nie jest konieczne:

  - Nowe możliwości refaktoryzacji C++ i funkcji eksperymentalnych edytora
  - Nowe narzędzia diagnostyczne jest debugera okno i okno Lista błędów
  - Całkiem nowe punkty przerwania, okno wyjątków i nowych funkcji PerfTips
  - Nowe narzędzia nawigacji i wyszukiwanie kodu
  - Nowe C++ szybkich poprawek i rozszerzenia Productivity Power Tools.

Można również przeznaczać projektów programu Visual Studio 2008, ale nie można ich używać bez zmian. Aby uzyskać więcej informacji, zobacz **instrukcje dotyczące programu Visual Studio 2008** sekcji.

Najnowsze wersje programu Visual Studio obsługuje natywna wielowersyjność i obustronne konwertowanie projektów. Natywna wielowersyjność jest możliwość tworzenia, za pomocą zestawów narzędzi zainstalowanych przez poprzednie wersje programu Visual Studio IDE najnowszych. Pełna zgodnooć wersji jest możliwość ładowania projektów utworzonych za pomocą poprzedniej wersji środowiska IDE bez wprowadzania żadnych zmian w projekcie najnowsze środowisko IDE. Po zainstalowaniu najnowszej wersji programu Visual Studio side-by-side przy użyciu istniejącej wersji umożliwia nową wersję środowiska IDE przy użyciu kompilatora i narzędzi z istniejącej wersji kompilowanie projektów. Inni członkowie zespołu mogą w dalszym ciągu używać projektów w starszej wersji programu Visual Studio.

Gdy używasz starszej zestawu narzędzi, możesz korzystać z zalet wiele z najnowszych funkcji środowiska IDE, ale nie najnowszych rozwiązań w menu Narzędzia kompilatora, biblioteki i kompilacji języka C++. Na przykład nie będzie mógł użyć nowe ulepszenia zgodności języka nowe debugowania i funkcji analizy kodu lub pobrać szybciej przepływność kompilacji najnowszy zestaw narzędzi. Dostępne są także niektóre funkcje środowiska IDE, które są niezgodne z starsze zestawy narzędzi. Na przykład typ może brakować informacji w Profiler pamięci i operacji refaktoryzacji **przekonwertować surowe Literały ciągu** generuje C ++ 11 zgodne kod, który nie będzie kompilacji podczas korzystania z programu Visual Studio 2012 lub starszy zestawy narzędzi.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Jak używać natywnej wielowersyjności kodu w programie Visual Studio

Po zainstalowaniu programu Visual Studio side-by-side przy użyciu starszej wersji, otwórz istniejący projekt w nowej wersji programu Visual Studio. Po załadowaniu projektu programu Visual Studio pyta, czy chcesz uaktualnić go do korzystania z najnowszą wersję kompilatora C++ i bibliotek. Ponieważ projektu, aby zachować starszy kompilator i biblioteki należy wybrać **anulować** przycisku.

Program Visual Studio jest trwały o uaktualnianiu projektu. Aby uniknąć wyświetlania okno dialogowe uaktualniania za każdym razem, gdy ładowanie projektu, można zdefiniować następującą właściwość w projekcie lub w plikach .props i .targets zaimportowali:

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Należy usunąć tę właściwość, jeśli chcesz uaktualnić swoje projekty.

Jeśli wybierzesz nie uaktualnić program Visual Studio nie wprowadza żadnych zmian w plikach rozwiązania lub projektu. Podczas tworzenia projektu, wygenerowane pliki binarne są w pełni zgodne z tymi, które są wbudowane ze starszą wersją programu Visual Studio. Jest to spowodowane programu Visual Studio używa tego samego kompilatora C++ i łączy ten sam bibliotek, które starsze zintegrowanego środowiska Projektowego dostarczane z programem. Jest to Dlaczego okno dialogowe uaktualniania wyświetli ostrzeżenie, aby zachować starszą wersję programu Visual Studio zainstalowany, wybranie opcji **anulować**.

## <a name="instructions-for-visual-studio-2008"></a>Instrukcje dotyczące programu Visual Studio 2008

Program Visual Studio 2008 ma swój własny system kompilacji dedykowane dla języka C++ o nazwie **program VCBuild**. Począwszy od programu Visual Studio 2010 projektów Visual C++ zostały zmienione, aby użyć **MSBuild**. Oznacza to, należy przejść do kroku aktualizacji do tworzenia projektów programu Visual Studio 2008 w najnowszej wersji programu Visual Studio. Zaktualizowano projekt nadal generuje pliki binarne, które są w pełni zgodne z plikami binarnymi utworzone za pomocą programu Visual Studio 2008 IDE.

Najpierw oprócz bieżącej wersji programu Visual Studio, Visual Studio 2010 należy zainstalować na tym samym komputerze co program Visual Studio 2008. Instaluje tylko program Visual Studio 2010 **MSBuild** skrypty, które są wymagane do projektów docelowych programu Visual Studio 2008.

Następnie należy zaktualizować program Visual Studio 2008 rozwiązanie i projekty do bieżącej wersji programu Visual Studio. Zaleca się, że utworzono kopię zapasową swoich projektach i plikach rozwiązania przed uaktualnieniem. Aby rozpocząć proces uaktualniania, otwórz rozwiązanie w bieżącej wersji programu Visual Studio. Po otrzymaniu monitu uaktualnienia, zapoznaj się z informacjami, a następnie wybierz **OK** uruchomiony w celu uaktualnienia. Jeśli masz więcej niż jednego projektu w rozwiązaniu, należy zaktualizować Kreator utworzy nowy .vcxproj projektu pliki side-by-side z istniejącymi plikami .vcproj. Tak długo, jak również zainstalowany kopię oryginalnego pliku .sln, uaktualnienie nie ma innych wpływu na istniejących projektów programu Visual Studio 2008.

Po zakończeniu uaktualniania, jeśli raport dziennika zawiera błędy lub ostrzeżenia dla żadnego z projektów, dokładne zapoznanie się z nimi. Konwersja z **program VCBuild** do **MSBuild** mogą powodować problemy. Upewnij się, zrozumieć i zaimplementować żadnych czynności do wykonania wymienione w raporcie. Aby uzyskać więcej informacji na temat raportu dziennika uaktualniania i problemów, które mogą występować podczas konwertowania **program VCBuild** do **MSBuild**, zobacz ten [C++ natywna Wielowersyjność](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) wpis w blogu.

Po zakończeniu procesu uaktualniania projektu, i zostały skorygowane problemy w pliku dziennika, rozwiązania faktycznie jest przeznaczony dla najnowszych narzędzi. Ostatni krok Zmień właściwości dla każdego projektu w rozwiązaniu, aby użyć zestawu narzędzi programu Visual Studio 2008. Dzięki rozwiązaniu załadowane w bieżącej wersji programu Visual Studio dla każdego projektu w rozwiązaniu, otwórz projekt **stron właściwości** okno dialogowe: kliknij prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** a Wybierz **właściwości**. W **stron właściwości** okno dialogowe, zmiana **konfiguracji** wartość listy rozwijanej **wszystkie konfiguracje**. W **właściwości konfiguracji**, wybierz opcję **ogólne**, a następnie zmień **zestawu narzędzi platformy** do **programu Visual Studio 2008 (v90)**.

Po tej zmianie kompilator programu Visual Studio 2008 i biblioteki są używane do generowania dane binarne projektu podczas kompilowania rozwiązania w bieżącej wersji programu Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Instalowanie starszej zestawu narzędzi Visual Studio

Może być starego projektu Visual C++, który nie może lub nie chcesz uaktualnić, ale nie wersję zestawu narzędzi platformy zgodną z projektu. W takim przypadku można pobrać zestawu narzędzi, można zainstalować bezpłatnego programu Visual Studio Community i Express edition w wersji, których potrzebujesz. Każda wersja programu Visual Studio z programu Visual Studio 2008 na można zainstalować kompilator, narzędzia i biblioteki należy pod kątem tej wersji z bieżącego programu Visual Studio. Wyszukaj Microsoft Download Center, aby znaleźć i pobrać określonej wersji programu Visual Studio. Upewnij się, że wybrane opcje instalacji C++ podczas instalacji. Po zakończeniu instalacji uruchom tej wersji programu Visual Studio i zainstaluj wszystkie aktualizacje. Sprawdź także wszelkie zmiany w aktualizacji Windows, które mogą być wymagane. Ten proces sprawdzania aktualizacji może być konieczne powtórzenie więcej niż jeden raz do każdej zaktualizowania.

Aby uzyskać aktualnie dostępne pliki do pobrania, zobacz [starsze oprogramowania Visual Studio można pobrać](https://visualstudio.microsoft.com/vs/older-downloads/).

Po zainstalowaniu tych produktów **zestawu narzędzi platformy** właściwości listy rozwijanej w **stron właściwości** okno dialogowe jest automatycznie aktualizowana, aby wyświetlić dostępne zestawy narzędzi. Najnowszą wersję programu Visual Studio umożliwia teraz tworzenie projektów w przypadku starszych wersji zestawu narzędzi bez konieczności konwertowania lub jej uaktualnienie.

## <a name="see-also"></a>Zobacz też

[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md)