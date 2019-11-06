---
title: Używanie natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów
ms.date: 10/25/2019
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: aff21121c181131b04ad22d75f03b7cbb222228a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627147"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Używanie natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów

Zwykle zalecamy zaktualizowanie projektów podczas instalacji najnowszej wersji programu Visual Studio. Koszt aktualizacji projektów i kodu jest zwykle wyższy niż przesunięty przez zalety nowego środowiska IDE, kompilatora, bibliotek i narzędzi. Jednak wiemy, że nie można zaktualizować niektórych projektów. Mogą istnieć pliki binarne, które są powiązane ze starszymi bibliotekami lub platformami, z powodów konserwacyjnych, których nie można uaktualnić. Kod może korzystać z niestandardowych konstrukcji językowych, które zostałyby przerwane w przypadku przeniesienia do nowszego kompilatora. Kod może zależeć od bibliotek innych firm skompilowanych dla określonej wersji wizualizacji C++. Lub można utworzyć biblioteki dla innych, które muszą wskazywać na określoną starszą wersję C++wizualizacji.

Na szczęście można użyć programu Visual Studio 2017 i programu Visual Studio 2015 do kompilowania projektów przeznaczonych dla starszych zestawów narzędzi i bibliotek kompilatora. Nie trzeba uaktualniać programu Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 ani programu Visual Studio 2015, aby korzystać z nowych funkcji środowiska IDE:

  - Nowe C++ możliwości refaktoryzacji i eksperymentalne funkcje edytora
  - Okno debugera narzędzi diagnostycznych i okno Lista błędów
  - Odnowionych punkty przerwania, okno wyjątków i nowy funkcja PerfTip
  - Nowe narzędzia do nawigacji i wyszukiwania kodu
  - Nowe C++ szybkie poprawki i rozszerzenia energooszczędnych narzędzi do produkcji.

Możesz również kierować projekty programu Visual Studio 2008, ale nie można ich używać bez zmian. Aby uzyskać szczegółowe informacje, zobacz sekcję **instrukcje dla programu Visual Studio 2008** .

Najnowsze wersje programu Visual Studio obsługują natywne, wielowymiarowe i dwukierunkowe projekty. Natywny cel wielowymiarowy to możliwość kompilowania przy użyciu zestawów narzędzi zainstalowanych przez poprzednie wersje programu Visual Studio. Funkcja okrężna jest funkcją najnowszego środowiska IDE do ładowania projektów utworzonych przez poprzednią wersję środowiska IDE bez wprowadzania jakichkolwiek zmian w projekcie. Jeśli zainstalujesz najnowszą wersję programu Visual Studio obok istniejącej wersji, możesz użyć nowej wersji środowiska IDE z kompilatorem i narzędziami z istniejącej wersji do kompilowania projektów. Inni członkowie zespołu mogą nadal używać projektów w starszej wersji programu Visual Studio.

W przypadku korzystania ze starszego zestawu narzędzi można korzystać z wielu najnowszych funkcji środowiska IDE, ale nie najnowszych zaliczeń w C++ kompilatorze, bibliotekach i narzędziach kompilacji. Na przykład nie będzie można korzystać z nowych ulepszeń związanych z zgodnością języka, nowych funkcji debugowania i analizy kodu ani uzyskać szybszej przepływności kompilacji najnowszego zestawu narzędzi. Istnieją także pewne funkcje IDE, które są niezgodne ze starszymi zestawami narzędzi. Na przykład w profilerze pamięci mogą znajdować się informacje o typie, a operacja refaktoryzacji **konwertuje do nieprzetworzonych literałów ciągu** , który generuje kod zgodny ze standardem C + +11, który nie zostanie skompilowany w przypadku korzystania z programu Visual Studio 2012 lub starszego zestawu narzędzi.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Jak używać natywnego wieloadresowania w programie Visual Studio

Po zainstalowaniu programu Visual Studio obok starszej wersji Otwórz istniejący projekt w nowej wersji programu Visual Studio. Po załadowaniu projektu program Visual Studio pyta, czy chcesz go uaktualnić do korzystania z najnowszego C++ kompilatora i bibliotek. Ponieważ projekt ma zachować starszy kompilator i biblioteki, wybierz przycisk **Anuluj** .

Program Visual Studio jest trwały w zakresie uaktualniania projektu. Aby uniknąć wyświetlania okna dialogowego uaktualniania przy każdym załadowaniu projektu, można zdefiniować następującą właściwość w projektach lub w importowanych plikach. props lub. targets:

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Należy usunąć tę właściwość, jeśli chcesz uaktualnić projekty.

W przypadku wybrania opcji Nie uaktualniaj program Visual Studio nie wprowadza żadnych zmian w plikach rozwiązania lub projektu. Podczas kompilowania projektu wygenerowane pliki binarne są w pełni zgodne z tymi, które zostały skompilowane przy użyciu starszej wersji programu Visual Studio. Wynika to z faktu, że program C++ Visual Studio używa tego samego kompilatora i łączy te same biblioteki, które zostały dostarczone przez starsze środowisko IDE. Dlatego też okno dialogowe uaktualniania ostrzega o zachowaniu starszej wersji programu Visual Studio, jeśli wybierzesz **przycisk Anuluj**.

## <a name="instructions-for-visual-studio-2008"></a>Instrukcje dla programu Visual Studio 2008

Program Visual Studio 2008 ma swój własny dedykowany system C++ kompilacji dla wywołanego **vcbuild**. Począwszy od programu Visual Studio 2010, projekty C++ programu Visual Studio zostały zmienione w celu użycia programu **MSBuild**. Oznacza to, że bez względu na to, czy proces uaktualniania ma być trwały, czy wiele elementów docelowych, należy wykonać krok aktualizacji, aby skompilować projekty programu Visual Studio 2008 w najnowszej wersji programu Visual Studio. Zaktualizowany projekt nadal generuje pliki binarne, które są w pełni zgodne z plikami binarnymi utworzonymi przy użyciu środowiska IDE programu Visual Studio 2008.

Po pierwsze, oprócz bieżącej wersji programu Visual Studio, należy zainstalować program Visual Studio 2010 na tym samym komputerze co program Visual Studio 2008. Tylko program Visual Studio 2010 instaluje skrypty **MSBuild** , które są wymagane do celów projektów programu Visual Studio 2008.

Następnie należy zaktualizować rozwiązanie programu Visual Studio 2008 i projekty do bieżącej wersji programu Visual Studio. Zalecamy utworzenie kopii zapasowej projektów i plików rozwiązań przed uaktualnieniem. Aby rozpocząć proces uaktualniania, Otwórz rozwiązanie w bieżącej wersji programu Visual Studio. Po otrzymaniu monitu o uaktualnienie Przejrzyj wyświetlone informacje, a następnie wybierz przycisk **OK** , aby rozpocząć uaktualnianie. Jeśli w rozwiązaniu istnieje więcej niż jeden projekt, należy zaktualizować Kreator tworzy nowe pliki projektu. vcxproj obok istniejących plików. vcproj. Jeśli masz również kopię oryginalnego pliku. sln, uaktualnienie nie ma żadnego wpływu na istniejące projekty programu Visual Studio 2008.

> [!NOTE]
> Poniższe kroki dotyczą tylko scenariuszy obejmujących wiele celów. Jeśli zamierzasz trwale uaktualnić projekt do nowszej wersji zestawu narzędzi, następnym krokiem jest zapisanie projektu, otwarcie go w programie Visual Studio 2019 i rozwiązanie problemów dotyczących kompilacji, które pojawiły się w tym miejscu.

Po zakończeniu uaktualniania, jeśli raport dziennika zawiera błędy lub ostrzeżenia dla dowolnego z projektów, należy uważnie przejrzeć te elementy. Konwersja z **vcbuild** na **MSBuild** może powodować problemy. Upewnij się, że rozumiesz i zaimplementowano wszystkie elementy akcji wymienione w raporcie. Aby uzyskać więcej informacji na temat raportu dziennika uaktualniania i problemów, które mogą wystąpić podczas konwertowania **vcbuild** na **MSBuild**, zobacz ten [ C++ natywny](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) wpis w blogu z wieloma docelowymi informacjami.

Po zakończeniu uaktualniania projektu, a wszystkie problemy w pliku dziennika, Twoje rozwiązanie rzeczywiście odwołuje się do najnowszego zestawu narzędzi. Ostatnim krokiem jest zmiana właściwości dla każdego projektu w rozwiązaniu, aby użyć zestawu narzędzi programu Visual Studio 2008. W przypadku rozwiązania załadowanego w bieżącej wersji programu Visual Studio dla każdego projektu w rozwiązaniu Otwórz okno dialogowe **strony właściwości** projektu: kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie wybierz polecenie **Właściwości**. W oknie dialogowym **strony właściwości** Zmień **wartość w polu listy** rozwijanej na **wszystkie konfiguracje**. W obszarze **Właściwości konfiguracji**wybierz opcję **Ogólne**, a następnie Zmień zestaw **narzędzi platformy** do **programu Visual Studio 2008 (v90)** .

Po tej zmianie kompilator i biblioteki programu Visual Studio 2008 są używane do generowania plików binarnych projektu podczas kompilowania rozwiązania w bieżącej wersji programu Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Instalowanie starszego zestawu narzędzi programu Visual Studio

Może istnieć stary projekt programu Visual Studio C++ , którego nie można uaktualnić, ale nie jest to wersja zestawu narzędzi platformy zgodna z projektem. W tym przypadku, aby uzyskać zestaw narzędzi, możesz zainstalować bezpłatną wersję Visual Studio Community lub Express Edition, której potrzebujesz. Każda wersja programu Visual Studio z programu Visual Studio 2008 w systemie może zainstalować kompilator, narzędzia i biblioteki potrzebne do tej wersji z bieżącego programu Visual Studio. Przeszukaj centrum pobierania Microsoft, aby znaleźć i pobrać określoną wersję programu Visual Studio. Upewnij się, C++ że wybrano opcje instalacji podczas instalacji. Po zakończeniu instalacji uruchom tę wersję programu Visual Studio, aby zainstalować wszystkie aktualizacje. Sprawdź również, czy istnieją Windows Update zmiany, które mogą być wymagane. Aby można było pobrać wszystkie aktualizacje, może być konieczne powtórzenie tego procesu sprawdzania aktualizacji.

Aby uzyskać dostęp do aktualnie dostępnych plików do pobrania, zobacz [pobieranie starszego oprogramowania Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

Gdy te produkty są zainstalowane, w oknie dialogowym **strony właściwości** zostanie automatycznie zaktualizowana właściwość zestawu **narzędzi platformy** , aby pokazać dostępne zestawy narzędzi. Teraz można używać najnowszej wersji programu Visual Studio do kompilowania projektów dla tych starszych wersji zestawu narzędzi bez konieczności ich konwertowania ani uaktualniania.

## <a name="see-also"></a>Zobacz także

[Uaktualnianie projektów ze starszych wersji wizualizacjiC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)
