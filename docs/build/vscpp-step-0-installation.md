---
title: Instalowanie obsługi języka C++ w programie Visual Studio
description: Instalowanie pomocy technicznej programu Visual Studio dla programu Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: d3018bef9254a8eab557057c035cde84310a2452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335363"
---
# <a name="install-c-support-in-visual-studio"></a>Instalowanie obsługi języka C++ w programie Visual Studio

Jeśli nie zostały pobrane i zainstalowane visual studio i narzędzia Visual C++jeszcze, oto jak rozpocząć.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Instalacja programu Visual Studio 2019

Witamy w programie Visual Studio 2019! W tej wersji łatwo jest wybrać i zainstalować tylko te funkcje, których potrzebujesz. A ze względu na zmniejszony minimalny zasięg instalacji, instaluje się szybko i przy mniejszym wpływie na system.

> [!NOTE]
> W tym temacie dotyczy instalacji programu Visual Studio w systemie Windows. [Visual Studio Code](https://code.visualstudio.com/) to lekkie, wieloplatformowe środowisko programistyczne, które działa w systemach Windows, Mac i Linux. Rozszerzenie Microsoft [C/C++ for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) obsługuje intellisense, debugowanie, formatowanie kodu, automatyczne uzupełnianie. Visual Studio dla komputerów Mac nie obsługuje microsoft C++, ale obsługuje języki platformy .NET i tworzenie wielu platform. Aby uzyskać instrukcje instalacji, zobacz [Instalowanie programu Visual Studio dla komputerów Mac](/visualstudio/mac/installation/).

Chcesz dowiedzieć się więcej o tym, co jeszcze jest nowe w tej wersji? Zobacz informacje [o wersji](/visualstudio/releases/2019/release-notes/)programu Visual Studio .

Gotowy do instalacji? Przejdziemy przez to krok po kroku.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1 - Upewnij się, że komputer jest gotowy do programu Visual Studio

Przed rozpoczęciem instalowania programu Visual Studio:

1. Sprawdź [wymagania systemowe](/visualstudio/releases/2019/system-requirements). Te wymagania pomagają sprawdzić, czy komputer obsługuje program Visual Studio 2019.

1. Zastosuj najnowsze aktualizacje systemu Windows. Te aktualizacje zapewniają, że komputer ma zarówno najnowsze aktualizacje zabezpieczeń, jak i wymagane składniki systemu dla programu Visual Studio.

1. Ponownie obuwać. Ponowne uruchomienie gwarantuje, że wszelkie oczekujące instalacje lub aktualizacje nie utrudniają instalacji programu Visual Studio.

1. Zwolnić miejsce. Usuń niepotrzebne pliki i aplikacje z %SystemDrive% na przykład przez uruchomienie aplikacji Oczyszczanie dysku.

Aby uzyskać pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok programu Visual Studio 2019, zobacz stronę [Kierowania i zgodność platformy programu Visual Studio 2019.](/visualstudio/releases/2019/compatibility/)

### <a name="step-2---download-visual-studio"></a>Krok 2 - Pobierz program Visual Studio

Następnie pobierz plik programu Visual Studio. Aby to zrobić, wybierz następujący przycisk, wybierz odpowiednią wersję programu Visual Studio, wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 - Instalowanie instalatora programu Visual Studio

Uruchom plik programu bootstrapper, aby zainstalować Instalatora programu Visual Studio. Ten nowy lekki instalator zawiera wszystko, czego potrzebujesz do instalowania i dostosowywania programu Visual Studio.

1. W folderze **Pobrane** kliknij dwukrotnie program uruchamiany, który pasuje lub jest podobny do jednego z następujących plików:

   - **vs_community.exe** dla społeczności programu Visual Studio
   - **vs_professional.exe** dla programu Visual Studio Professional
   - **vs_enterprise.exe** dla programu Visual Studio Enterprise

   Jeśli otrzymasz powiadomienie o kontroli konta użytkownika, wybierz opcję **Tak**.

1. Prosimy o uznanie [postanowień licencyjnych](https://visualstudio.microsoft.com/license-terms/) firmy Microsoft i [Zasad zachowania poufności informacji firmy](https://privacy.microsoft.com/privacystatement)Microsoft. Wybierz pozycję **Kontynuuj**.

### <a name="step-4---choose-workloads"></a>Krok 4 - Wybieranie obciążeń

Po zainstalowaniu instalatora można go użyć do dostosowania instalacji, wybierając *żądane obciążenia*lub zestawy funkcji. Oto jak to zrobić.

1. Znajdź żądane obciążenie na ekranie **Instalowanie programu Visual Studio.**

   ![Visual Studio 2019: instalowanie obciążenia](../get-started/media/vs-installer-workloads.png)

   W przypadku podstawowej obsługi języka C++ wybierz obciążenie "Tworzenie pulpitu z c++". Jest wyposażony w domyślny edytor rdzenia, który zawiera podstawową obsługę edycji kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności tworzenia projektu oraz zintegrowaną kontrolę kodu źródłowego.

   Dodatkowe obciążenia obsługują inne rodzaje programowania języka C++. Na przykład wybierz obciążenie "Tworzenie platformy uniwersalnej systemu Windows", aby utworzyć aplikacje korzystające ze środowiska wykonawczego systemu Windows dla sklepu Microsoft Store. Wybierz opcję "Tworzenie gier z C++", aby tworzyć gry korzystające z directx, unreal i cocos2d. Wybierz opcję "Rozwój Linuksa z C++", aby kierować reklamy na platformy Linux, w tym rozwój IoT.

   W okienku **Szczegóły instalacji** wymieniono dołączone i opcjonalne składniki zainstalowane przez każde obciążenie. Można zaznaczyć lub usunąć zaznaczenie składników opcjonalnych na tej liście. Na przykład do obsługi rozwoju przy użyciu visual studio 2017 lub 2015 kompilatora zestawy narzędzi, wybierz MSVC v141 lub MSVC w wersji 140 składników opcjonalnych. Można dodać obsługę MFC, eksperymentalne rozszerzenie języka modułów, IncrediBuild i więcej.

1. Po wybraniu żądanych obciążeń i składników opcjonalnych wybierz pozycję **Zainstaluj**.

   Następnie pojawiają się ekrany stanu, które pokazują postęp instalacji programu Visual Studio.

> [!TIP]
> W dowolnym momencie po instalacji można zainstalować obciążenia lub składniki, które nie zostały zainstalowane początkowo. Jeśli masz otwarty program Visual Studio, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje ...** który otwiera Instalatora programu Visual Studio. Lub otwórz **Instalatora programu Visual Studio** z menu Start. W tym miejscu można wybrać obciążenia lub składniki, które chcesz zainstalować. Następnie wybierz pozycję **Modyfikuj**.

### <a name="step-5---choose-individual-components-optional"></a>Krok 5 - Wybór poszczególnych komponentów (opcjonalnie)

Jeśli nie chcesz używać funkcji Obciążenia, aby dostosować instalację programu Visual Studio lub chcesz dodać więcej składników niż instaluje obciążenie, można to zrobić, instalując lub dodając poszczególne składniki z karty **Poszczególne składniki.**

  ![Visual Studio 2019 — instalowanie poszczególnych składników](../get-started/media/vs-installer-individual-components.png "Instalowanie poszczególnych składników programu Visual Studio")

### <a name="step-6---install-language-packs-optional"></a>Krok 6 - Instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje dopasować język systemu operacyjnego, gdy działa po raz pierwszy. Aby zainstalować program Visual Studio w wybranym języku, wybierz kartę **Pakiety językowe** z Instalatora programu Visual Studio, a następnie postępuj zgodnie z instrukcjami.

  ![Visual Studio 2019 — instalowanie pakietów językowych](../get-started/media/vs-installer-language-packs.png "Instalowanie pakietów językowych programu Visual Studio")

#### <a name="change-the-installer-language-from-the-command-line"></a>Zmienianie języka instalatora z wiersza polecenia

Innym sposobem zmiany języka domyślnego jest uruchomienie instalatora z wiersza polecenia. Na przykład można wymusić uruchomienie instalatora w języku angielskim `vs_installer.exe --locale en-US`za pomocą następującego polecenia: . Instalator zapamięta to ustawienie, gdy zostanie uruchomione następnym razem. Instalator obsługuje następujące tokeny językowe: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru i tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Krok 7 - Zmiana miejsca instalacji (opcjonalnie)

Można zmniejszyć rozmiar instalacji programu Visual Studio na dysku systemowym. Można przenieść pamięć podręczną pobierania, składniki udostępnione, zestawY SDK i narzędzia na różne dyski i zachować program Visual Studio na dysku, który uruchamia go najszybciej.

  ![Visual Studio 2019 — zmienianie lokalizacji instalacji](../get-started/media/vs-installer-installation-locations.png "Zmienianie lokalizacji instalacji")

> [!IMPORTANT]
> Inny dysk można wybrać tylko przy pierwszej instalacji programu Visual Studio. Jeśli masz już zainstalowany i chcesz zmienić dyski, należy odinstalować program Visual Studio, a następnie ponownie zainstalować go.

### <a name="step-8---start-developing"></a>Krok 8 - Rozpoczęcie tworzenia

1. Po zakończeniu instalacji programu Visual Studio wybierz przycisk **Uruchom,** aby rozpocząć tworzenie za pomocą programu Visual Studio.

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

1. W polu wyszukiwania wprowadź typ aplikacji, którą chcesz utworzyć, aby wyświetlić listę dostępnych szablonów. Lista szablonów zależy od obciążenia wybranego podczas instalacji. Aby wyświetlić różne szablony, wybierz różne obciążenia.

   Wyszukiwanie w poszukiwaniu określonego języka programowania można również filtrować za pomocą listy rozwijanej **Język.** Można filtrować przy użyciu **platformy** listy i listy **typu projektu,** zbyt.

1. Visual Studio otwiera nowy projekt i jesteś gotowy do kodu!

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Instalacja programu Visual Studio 2017

W programie Visual Studio 2017 można łatwo wybrać i zainstalować tylko te funkcje, których potrzebujesz. A ze względu na zmniejszony minimalny zasięg instalacji, instaluje się szybko i przy mniejszym wpływie na system.

### <a name="prerequisites"></a>Wymagania wstępne

- Szerokopasmowe połączenie internetowe. Instalator programu Visual Studio można pobrać kilka gigabajtów danych.

- Komputer z systemem Microsoft Windows 7 lub nowszymi wersjami. Firma Microsoft zaleca system Windows 10 dla najlepszego środowiska programowania. Przed zainstalowaniem programu Visual Studio upewnij się, że najnowsze aktualizacje są stosowane do systemu.

- Wystarczająco dużo wolnego miejsca na dysku. Program Visual Studio wymaga co najmniej 7 GB miejsca na dysku i może zająć 50 GB lub więcej, jeśli jest zainstalowanych wiele typowych opcji. Zalecamy zainstalowanie go na dysku C:.

Aby uzyskać szczegółowe informacje na temat miejsca na dysku i wymagań systemu operacyjnego, zobacz [Wymagania dotyczące rodziny produktów programu Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). Instalator raportuje, ile miejsca na dysku jest wymagane dla wybranych opcji.

### <a name="download-and-install"></a>Pobieranie i instalowanie

1. Pobierz najnowszy instalator programu Visual Studio 2017 dla systemu Windows.

   > [!div class="nextstepaction"]
   > [Instalowanie społeczności programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Edycja społeczności jest dla poszczególnych programistów, uczenia się w klasie, badań akademickich i rozwoju open source. Aby uzyskać inne zastosowania, zainstaluj [program Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) lub Visual Studio [2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Znajdź pobrany plik instalatora i uruchom go. Może być wyświetlany w przeglądarce lub można go znaleźć w folderze Pobrane. Instalator potrzebuje uprawnień administratora do uruchomienia. Może zostać wyświetlone okno dialogowe **Kontrola konta użytkownika** z prośbą o udzielenie zgody na zezwolenie instalatorowi na wprowadzanie zmian w systemie; wybierz **tak**. Jeśli masz problemy, znajdź pobrany plik w Eksploratorze plików, kliknij prawym przyciskiem myszy ikonę instalatora i wybierz polecenie **Uruchom jako administrator** z menu kontekstowego.

   ![Pobieranie i instalowanie instalatora programu Visual Studio](media/vscpp-concierge-run-installer.gif "Pobieranie i instalowanie instalatora programu Visual Studio")

1. Instalator przedstawia listę obciążeń, które są grupami powiązanych opcji dla określonych obszarów rozwoju. Obsługa języka C++ jest teraz częścią opcjonalnych obciążeń, które nie są domyślnie instalowane.

   ![Tworzenie pulpitu z obciążeniem języka C++](media/desktop-development-with-cpp.png "Programowanie aplikacji klasycznych w języku C++")

   W przypadku języka C++wybierz program rozwoju pulpitu z obciążeniem **języka C++,** a następnie wybierz pozycję **Zainstaluj**.

   ![Instalowanie programu rozwoju pulpitu z obciążeniem języka C++](media/vscpp-concierge-choose-workload.gif "Instalowanie programu rozwoju pulpitu z obciążeniem języka C++")

1. Po zakończeniu instalacji wybierz przycisk **Uruchom,** aby uruchomić program Visual Studio.

   Przy pierwszym uruchomieniu programu Visual Studio zostaniesz poproszony o zalogowanie się za pomocą konta Microsoft. Jeśli go nie masz, możesz go utworzyć za darmo. Musisz również wybrać motyw. Nie martw się, możesz go zmienić później, jeśli chcesz.

   Przygotowanie programu Visual Studio do użycia przy pierwszym uruchomieniu programu Visual Studio może potrwać kilka minut. Oto jak to wygląda w krótkim czasie:

   ![Logowanie do programu Visual Studio 2017](media/vscpp-quickstart-first-run.gif "Logowanie do programu Visual Studio 2017")

   Program Visual Studio uruchamia się znacznie szybciej po ponownym uruchomieniu.

1. Po otwarciu programu Visual Studio sprawdź, czy wyróżniona jest ikona flagi na pasku tytułu:

   ![Flaga powiadomienia programu Visual Studio 2017](media/vscpp-first-start-page-flag.png "Flaga powiadomienia programu Visual Studio 2017")

   Jeśli jest wyróżniony, wybierz go, aby otworzyć okno **Powiadomienia.** Jeśli są dostępne aktualizacje dla programu Visual Studio, zaleca się zainstalować je teraz. Po zakończeniu instalacji uruchom ponownie program Visual Studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Instalacja programu Visual Studio 2015

Aby zainstalować program Visual Studio 2015, przejdź do [pobierz starsze wersje programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Uruchom program instalacyjny i wybierz pozycję **Instalacja niestandardowa,** a następnie wybierz składnik C++. Aby dodać obsługę języka C++ do istniejącej instalacji programu Visual Studio 2015, kliknij przycisk Start systemu Windows i wpisz **Dodaj usuń programy**. Otwórz program z listy wyników, a następnie znajdź instalację programu Visual Studio 2015 na liście zainstalowanych programów. Kliknij go dwukrotnie, a następnie wybierz pozycję **Modyfikuj** i wybierz składniki Visual C++do zainstalowania.

Ogólnie rzecz biorąc zdecydowanie zaleca się, aby używać programu Visual Studio 2017, nawet jeśli trzeba skompilować kod przy użyciu kompilatora programu Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Używanie natywnego kierowania wielokrotnego w programie Visual Studio do tworzenia starych projektów.](../porting/use-native-multi-targeting.md)

::: moniker-end

Gdy program Visual Studio jest uruchomiony, można przystąpić do następnego kroku.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Tworzenie projektu języka C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
