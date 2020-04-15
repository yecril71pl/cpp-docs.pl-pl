---
title: Używanie natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów
ms.date: 10/25/2019
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: 70acf3b5b78e0bc58555ef3f1f8e72e8aed74dd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353263"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Używanie natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów

Zwykle zaleca się aktualizowanie projektów podczas instalowania najnowszej wersji programu Visual Studio. Koszt aktualizacji projektów i kodu jest zwykle więcej niż kompensowane przez korzyści z nowego IDE, kompilator, biblioteki i narzędzia. Wiemy jednak, że aktualizacja niektórych projektów może być niedyskusi. Możesz mieć pliki binarne, które są powiązane ze starszymi bibliotekami lub platformami, których ze względów konserwacyjnych nie można uaktualnić. Kod może używać niestandardowych konstrukcji języka, które mogłyby zostać przerwane, jeśli zostanie przeniesiony do kompilatora nowszego. Kod może polegać na bibliotekach innych firm skompilowanych dla określonej wersji programu Visual C++. Możesz też tworzyć biblioteki dla innych osób, które muszą być przeznaczone dla określonej starszej wersji programu Visual C++.

Na szczęście można użyć visual studio 2017 i Visual Studio 2015 do tworzenia projektów, które są przeznaczone dla starszych zestawów narzędzi kompilatora i bibliotek. Nie trzeba uaktualniać visual studio 2010, Visual Studio 2012, Visual Studio 2013 lub Visual Studio 2015 projektu, aby skorzystać z nowych funkcji w IDE:

- Nowe funkcje refaktoryzacji języka C++ i funkcje eksperymentalne edytora
- Okno debugera nowych narzędzi diagnostycznych i okno lista błędów
- Przebudowane punkty przerwania, okno wyjątków i nowe porady dotyczące punktów procentowych
- Nowe narzędzia do nawigacji i wyszukiwania kodu
- Nowe szybkie poprawki języka C++ i rozszerzenia narzędzi zwiększających produktywność.

Można również kierować projekty programu Visual Studio 2008, ale nie można ich używać bez zmian. Aby uzyskać szczegółowe informacje, zobacz **instrukcje dotyczące programu Visual Studio 2008** sekcji.

Najnowsze wersje programu Visual Studio obsługują natywne multi-targeting i round-tripping projektów. Natywne kierowanie na wiele jest możliwość najnowszego IDE do tworzenia przy użyciu zestawów narzędzi zainstalowanych przez poprzednie wersje programu Visual Studio. Round-tripping jest możliwość najnowszych IDE załadować projekty utworzone przez poprzednią wersję IDE bez wprowadzania żadnych zmian w projekcie. Jeśli zainstalujesz najnowszą wersję programu Visual Studio obok istniejącej wersji, można użyć nowej wersji IDE z kompilatorem i narzędziami z istniejącej wersji do tworzenia projektów. Inni członkowie zespołu mogą nadal używać projektów w starszej wersji programu Visual Studio.

Korzystając ze starszego zestawu narzędzi, można korzystać z wielu najnowszych funkcji IDE, ale nie najnowsze osiągnięcia w kompilatorze C++, biblioteki i narzędzia kompilacji. Na przykład nie będzie można użyć nowych ulepszeń zgodności języka, nowe funkcje debugowania i analizy kodu lub uzyskać szybszą przepływność kompilacji najnowszego zestawu narzędzi. Istnieją również pewne funkcje IDE, które są niezgodne ze starszymi zestawami narzędzi. Na przykład informacje o typie mogą brakować w programie Profiler pamięci, a operacja refaktoryzacji **Konwersja na nieprzetworzone literały ciągów** generuje kod zgodny z C++ 11, który nie będzie kompilowany podczas korzystania z programu Visual Studio 2012 lub starszych zestawów narzędzi.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Jak używać natywnego kierowania wielokrotnego w programie Visual Studio

Po zainstalowaniu programu Visual Studio obok starszej wersji otwórz istniejący projekt w nowej wersji programu Visual Studio. Po załadowaniu projektu visual studio pyta, czy chcesz go uaktualnić, aby użyć najnowszego kompilatora języka C++ i bibliotek. Ponieważ chcesz, aby projekt zachował starszy kompilator i biblioteki, wybierz przycisk **Anuluj.**

Visual Studio jest trwałe o uaktualnianie projektu. Aby uniknąć wyświetlania okna dialogowego uaktualniania przy każdym załadowaniu projektu, można zdefiniować następującą właściwość w projektach lub w plikach .props lub .targets, które importują:

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Należy usunąć tę właściwość, jeśli chcesz uaktualnić swoje projekty.

Jeśli nie zdecydujesz się na uaktualnienie, visual studio wprowadza żadnych zmian do rozwiązania lub plików projektu. Podczas tworzenia projektu wygenerowane pliki binarne są w pełni zgodne z tymi, które zostały utworzone przy starszej wersji programu Visual Studio. Dzieje się tak, ponieważ program Visual Studio używa tego samego kompilatora Języka C++ i łączy te same biblioteki, z którymi dostarczany jest starszy ide. Dlatego też okno dialogowe uaktualniania ostrzega, aby zachować starszą wersję programu Visual Studio zainstalowaną, jeśli wybierzesz **opcję Anuluj**.

## <a name="instructions-for-visual-studio-2008"></a>Instrukcje dotyczące programu Visual Studio 2008

Visual Studio 2008 miał własny dedykowany system kompilacji dla języka C++ o nazwie **VCBuild**. Począwszy od programu Visual Studio 2010, visual studio C++ projekty zostały zmienione w celu korzystania z **MSBuild**. Oznacza to, że niezależnie od tego, czy uaktualnianie trwale lub multi-targeting należy przejść przez krok aktualizacji do tworzenia projektów programu Visual Studio 2008 w najnowszej wersji programu Visual Studio. Zaktualizowany projekt nadal generuje pliki binarne, które są w pełni zgodne z plikami binarnymi utworzonymi przy użyciu środowiska IDE programu Visual Studio 2008.

Po pierwsze, oprócz bieżącej wersji programu Visual Studio należy zainstalować program Visual Studio 2010 na tym samym komputerze co program Visual Studio 2008. Tylko visual studio 2010 instaluje skrypty **MSBuild,** które są wymagane do kierowania projektów programu Visual Studio 2008.

Następnie należy zaktualizować rozwiązanie programu Visual Studio 2008 i projekty do bieżącej wersji programu Visual Studio. Przed uaktualnieniem zaleca się utworzenie kopii zapasowej projektów i plików rozwiązań. Aby rozpocząć proces uaktualniania, otwórz rozwiązanie w bieżącej wersji programu Visual Studio. Po wyświetleniu monitu o uaktualnienie przejrzyj prezentowane informacje, a następnie wybierz przycisk **OK,** aby rozpocząć uaktualnienie. Jeśli w rozwiązaniu jest więcej niż jeden projekt, należy zaktualizować Kreator tworzy nowe pliki projektu .vcxproj obok istniejących plików .vcproj. Tak długo, jak masz również kopię oryginalnego pliku .sln, uaktualnienie nie ma innego wpływu na istniejące projekty programu Visual Studio 2008.

> [!NOTE]
> Poniższe kroki dotyczą tylko scenariuszy z wieloma celami. Jeśli zamierzasz trwale uaktualnić projekt do późniejszego zestawu narzędzi, następnym krokiem jest zapisanie projektu, otwarcie go w programie Visual Studio 2019 i rozwiązanie problemów z kompilacją, które się tam pojawiają.

Po zakończeniu uaktualniania, jeśli raport dziennika zawiera błędy lub ostrzeżenia dla każdego z projektów, należy je dokładnie przejrzeć. Konwersja z **VCBuild** do **MSBuild** może powodować problemy. Upewnij się, że rozumiesz i implementujesz wszystkie elementy akcji wymienione w raporcie. Aby uzyskać więcej informacji na temat raportu dziennika uaktualnienia i problemów, które mogą wystąpić podczas konwersji **VCBuild** do **MSBuild,** zobacz ten [c++ natywne multi-targeting](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) blogu.

Po zakończeniu uaktualniania projektu i rozwiązano wszelkie problemy w pliku dziennika, rozwiązanie faktycznie jest przeznaczone dla najnowszego zestawu narzędzi. W ostatnim kroku zmień właściwości dla każdego projektu w rozwiązaniu, aby użyć zestawu narzędzi Visual Studio 2008. Po załadowaniu rozwiązania w bieżącej wersji programu Visual Studio dla każdego projektu w rozwiązaniu otwórz okno dialogowe **Strony właściwości** projektu: Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Właściwości**. W oknie dialogowym **Strony właściwości** zmień wartość rozwijaną **Konfiguracja** na **Wszystkie konfiguracje**. W **obszarze Właściwości konfiguracji**wybierz pozycję **Ogólne**, a następnie zmień zestaw **narzędzi platformy** na program Visual **Studio 2008 (wersja 90)**.

Po tej zmianie visual studio 2008 kompilator i biblioteki są używane do generowania plików binarnych projektu podczas tworzenia rozwiązania w bieżącej wersji programu Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Instalowanie starszego zestawu narzędzi programu Visual Studio

Być może masz stary projekt Visual Studio C++, którego nie można lub nie chcesz uaktualnić, ale nie jest to wersja zestawu narzędzi platformy, która pasuje do projektu. W takim przypadku, aby uzyskać zestaw narzędzi, można zainstalować bezpłatną wersję visual studio społeczności lub express wersji potrzebnej wersji. Każda wersja programu Visual Studio z programu Visual Studio 2008 na można zainstalować kompilator, narzędzia i biblioteki, które należy kierować tej wersji z bieżącego programu Visual Studio. Przeszukaj Centrum pobierania firmy Microsoft, aby znaleźć i pobrać określoną wersję programu Visual Studio. Upewnij się, że podczas instalacji zostały wybrani opcje instalacji języka C++. Po zakończeniu instalacji uruchom tę wersję programu Visual Studio, aby zainstalować wszystkie aktualizacje. Sprawdź również, czy nie ma zmian w usłudze Windows Update, które mogą być wymagane. Ten proces sprawdzania aktualizacji może wymagać powtórzenia więcej niż jeden raz, aby uzyskać każdą aktualizację.

Aby uzyskać aktualnie dostępne pliki do pobrania, zobacz [Pobieranie starszego oprogramowania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

Po zainstalowaniu tych produktów z listy rozwijanej Właściwości **platform Toolset** w oknie dialogowym **Strony właściwości** są automatycznie aktualizowane w celu wyświetlenia dostępnych zestawów narzędzi. Teraz można użyć najnowszej wersji programu Visual Studio do tworzenia projektów dla tych starszych wersji zestawu narzędzi bez ich konwertowania lub uaktualniania.

## <a name="see-also"></a>Zobacz też

[Uaktualnianie projektów z wcześniejszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)
