---
title: Instalowanie obsługi języka C++ w programie Visual Studio
description: Zainstaluj obsługę programu Visual Studio dla Visual C++
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

Jeśli jeszcze nie pobrano i nie zainstalowano programu Visual Studio i narzędzi Visual C++, poniżej przedstawiono sposób rozpoczynania pracy.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Instalacja programu Visual Studio 2019

Witamy w programie Visual Studio 2019! W tej wersji można łatwo wybrać i zainstalować tylko te funkcje, które są potrzebne. I ze względu na obniżoną minimalną wartość, jest ona instalowana szybko i z mniejszym wpływem na system.

> [!NOTE]
> Ten temat dotyczy instalacji programu Visual Studio w systemie Windows. [Visual Studio Code](https://code.visualstudio.com/) to lekkie środowisko programistyczne dla wielu platform działające w systemach Windows, Mac i Linux. Rozszerzenie Microsoft [C/C++ for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) obsługuje funkcje IntelliSense, debugowanie, formatowanie kodu, Autouzupełnianie. Visual Studio dla komputerów Mac nie obsługuje języka Microsoft C++, ale obsługuje języki .NET i programowanie dla wielu platform. Instrukcje instalacji znajdują się w temacie [Install Visual Studio dla komputerów Mac](/visualstudio/mac/installation/).

Chcesz dowiedzieć się więcej na temat Nowości w tej wersji? Zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes/)programu Visual Studio.

Jesteś gotowy do instalacji? Przeprowadzimy Cię przez ten krok po kroku.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1. Upewnij się, że komputer jest gotowy do programu Visual Studio

Przed rozpoczęciem instalacji programu Visual Studio:

1. Sprawdź [wymagania systemowe](/visualstudio/releases/2019/system-requirements). Te wymagania pomagają sprawdzić, czy komputer obsługuje program Visual Studio 2019.

1. Zastosuj najnowsze aktualizacje systemu Windows. Te aktualizacje zapewniają, że komputer ma zarówno najnowsze aktualizacje zabezpieczeń, jak i wymagane składniki systemowe dla programu Visual Studio.

1. Ponowne uruchomienie. Ponowny rozruch zapewnia, że wszystkie oczekujące instalacje lub aktualizacje nie zakłócają instalacji programu Visual Studio.

1. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z dysku% SystemDrive%, na przykład uruchamiając aplikację Oczyszczanie dysku.

Pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok programu Visual Studio 2019 można znaleźć na stronie programu [Visual studio 2019 platformy docelowej i zgodności](/visualstudio/releases/2019/compatibility/) .

### <a name="step-2---download-visual-studio"></a>Krok 2. Pobieranie programu Visual Studio

Następnie Pobierz plik programu inicjującego Visual Studio. Aby to zrobić, wybierz poniższy przycisk, wybierz wersję programu Visual Studio, a następnie wybierz pozycję **Zapisz**, a następnie wybierz pozycję **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 — Instalowanie Instalatora programu Visual Studio

Uruchom plik programu inicjującego, aby zainstalować Instalator programu Visual Studio. Ten nowy Lightweight Installer zawiera wszystko, czego potrzebujesz do zainstalowania i dostosowania programu Visual Studio.

1. W folderze **pobierania** kliknij dwukrotnie program inicjujący pasujący do jednego z następujących plików lub jest podobny do następującego:

   - **vs_community. exe** dla programu Visual Studio Community
   - **vs_professional. exe** dla Visual Studio Professional
   - **vs_enterprise. exe** dla Visual Studio Enterprise

   Jeśli zostanie wyświetlony komunikat Kontrola konta użytkownika, wybierz opcję **tak**.

1. Poprosimy o potwierdzenie [postanowień licencyjnych](https://visualstudio.microsoft.com/license-terms/) firmy Microsoft oraz [zasad zachowania poufności informacji](https://privacy.microsoft.com/privacystatement)firmy Microsoft. Wybierz pozycję **Kontynuuj**.

### <a name="step-4---choose-workloads"></a>Krok 4. Wybieranie obciążeń

Po zainstalowaniu Instalatora można go użyć do dostosowania instalacji, wybierając odpowiednie *obciążenia*lub zestawy funkcji. Oto jak to zrobić.

1. Znajdź żądane obciążenie na ekranie **Instalowanie programu Visual Studio** .

   ![Visual Studio 2019: Instalowanie obciążenia](../get-started/media/vs-installer-workloads.png)

   W przypadku podstawowej obsługi języka C++ wybierz obciążenie "Programowanie aplikacji klasycznych w języku C++". Jest on dostarczany z domyślnym edytorem podstawowym, który obejmuje podstawową obsługę edycji kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności stosowania projektu i zintegrowanej kontroli kodu źródłowego.

   Dodatkowe obciążenia obsługują inne rodzaje programowania w języku C++. Na przykład wybierz obciążenie "platforma uniwersalna systemu Windows Development", aby utworzyć aplikacje używające środowisko wykonawcze systemu Windows do Microsoft Store. Wybierz pozycję "Programowanie gier w języku C++", aby utworzyć gry korzystające z technologii DirectX, Unreal i Cocos2d. Wybierz pozycję "Programowanie dla systemu Linux w języku C++", aby wskazać platformy dla systemu Linux, w tym rozwój IoT.

   Okienko **szczegóły instalacji** zawiera listę składników dołączonych i opcjonalnych zainstalowanych przez każde obciążenie. Możesz wybrać lub usunąć zaznaczenie składników opcjonalnych na tej liście. Na przykład aby obsługiwać Programowanie przy użyciu zestawu narzędzi kompilatora programu Visual Studio 2017 lub 2015, wybierz składniki opcjonalne MSVC najnowsze 141 lub MSVC wersji 140. Można dodać obsługę MFC, rozszerzenie języka dla modułów eksperymentalnych, IncrediBuild i inne.

1. Po wybraniu żądanych obciążeń i składników opcjonalnych wybierz pozycję **Zainstaluj**.

   Następnie wyświetlane są ekrany stanu pokazujące postęp instalacji programu Visual Studio.

> [!TIP]
> W dowolnym momencie po zakończeniu instalacji można zainstalować obciążenia lub składniki, które nie zostały wcześniej zainstalowane. Jeśli masz otwarty program Visual Studio, przejdź do pozycji **Narzędzia** > **Pobierz narzędzia i funkcje...** , co spowoduje otwarcie Instalator programu Visual Studio. Lub Otwórz **Instalator programu Visual Studio** z menu Start. W tym miejscu możesz wybrać obciążenia lub składniki, które chcesz zainstalować. Następnie wybierz **Modyfikuj**.

### <a name="step-5---choose-individual-components-optional"></a>Krok 5. Wybierz poszczególne składniki (opcjonalnie)

Jeśli nie chcesz używać funkcji obciążeń do dostosowywania instalacji programu Visual Studio lub chcesz dodać więcej składników niż w przypadku instalacji obciążeń, możesz to zrobić, instalując lub dodając poszczególne składniki z karty **poszczególne składniki** . Wybierz, co chcesz zrobić, a następnie postępuj zgodnie z instrukcjami.

  ![Visual Studio 2019 — Zainstaluj poszczególne składniki](../get-started/media/vs-installer-individual-components.png "Zainstaluj poszczególne składniki programu Visual Studio")

### <a name="step-6---install-language-packs-optional"></a>Krok 6. Instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje dopasować język systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Aby zainstalować program Visual Studio w wybranym języku, wybierz kartę **pakiety językowe** z Instalator programu Visual Studio, a następnie postępuj zgodnie z monitami.

  ![Visual Studio 2019 — Zainstaluj pakiety językowe](../get-started/media/vs-installer-language-packs.png "Zainstaluj pakiety językowe programu Visual Studio")

#### <a name="change-the-installer-language-from-the-command-line"></a>Zmiana języka Instalatora z wiersza polecenia

Innym sposobem zmiany języka domyślnego jest uruchomienie Instalatora z wiersza polecenia. Na przykład można wymusić uruchomienie Instalatora w języku angielskim przy użyciu następującego polecenia: `vs_installer.exe --locale en-US`. Instalator zapamiętaje to ustawienie, gdy zostanie uruchomione następnym razem. Instalator obsługuje następujące tokeny języka: zh-CN, zh-TW, CS-Czechy, en-us, es-ES, fr-fr, de-de, IT-JP, ko-kr, pl-pl, pt-br, ru-RU i TR-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Krok 7. zmiana lokalizacji instalacji (opcjonalnie)

Możesz zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym. Możesz przenieść pamięć podręczną pobierania, składniki współużytkowane, zestawy SDK i narzędzia na inne dyski i pozostawić program Visual Studio na dysku, na którym jest on uruchomiony najszybciej.

  ![Visual Studio 2019 — Zmień lokalizacje instalacji](../get-started/media/vs-installer-installation-locations.png "Zmień lokalizację instalacji")

> [!IMPORTANT]
> Inny dysk można wybrać tylko podczas pierwszej instalacji programu Visual Studio. Jeśli został już zainstalowany i chcesz zmienić dyski, należy odinstalować program Visual Studio, a następnie zainstalować go ponownie.

### <a name="step-8---start-developing"></a>Krok 8. Rozpoczynanie tworzenia

1. Po zakończeniu instalacji programu Visual Studio wybierz przycisk **Uruchom** , aby rozpocząć programowanie przy użyciu programu Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

1. W polu wyszukiwania wprowadź typ aplikacji, którą chcesz utworzyć, aby wyświetlić listę dostępnych szablonów. Lista szablonów zależy od obciążeń, które zostały wybrane podczas instalacji. Aby wyświetlić różne szablony, wybierz różne obciążenia.

   Wyszukiwanie w określonym języku programowania można również filtrować za pomocą listy rozwijanej **Język** . Można również filtrować za pomocą listy **platform** i listy **Typ projektu** .

1. Program Visual Studio otwiera nowy projekt i wszystko jest gotowe do kodu!

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Instalacja programu Visual Studio 2017

W programie Visual Studio 2017 można łatwo wybrać i zainstalować tylko te funkcje, które są potrzebne. I ze względu na obniżoną minimalną wartość, jest ona instalowana szybko i z mniejszym wpływem na system.

### <a name="prerequisites"></a>Wymagania wstępne

- Szerokopasmowe połączenie internetowe. Instalator programu Visual Studio może pobrać kilka gigabajtów danych.

- Komputer z systemem Microsoft Windows 7 lub nowszym. Zalecamy użycie systemu Windows 10 w celu uzyskania najlepszego środowiska programistycznego. Przed zainstalowaniem programu Visual Studio upewnij się, że do systemu zastosowano najnowsze aktualizacje.

- Wystarczająca ilość wolnego miejsca na dysku. Program Visual Studio wymaga co najmniej 7 GB miejsca na dysku i może trwać 50 GB lub więcej, jeśli są zainstalowane wiele typowych opcji. Zalecamy zainstalowanie go na dysku C:.

Aby uzyskać szczegółowe informacje o wymaganiach dotyczących miejsca na dysku i systemu operacyjnego, zobacz [wymagania systemowe rodziny produktów Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). Instalator raportuje ilość miejsca na dysku wymaganą dla wybranych opcji.

### <a name="download-and-install"></a>Pobieranie i instalowanie

1. Pobierz najnowszą wersję Instalatora programu Visual Studio 2017 dla systemu Windows.

   > [!div class="nextstepaction"]
   > [Zainstaluj społeczność programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Wersja Community jest przeznaczony dla indywidualnych deweloperów, uczenia klasowego, badań akademickich i opracowywania rozwiązań open source. Aby uzyskać inne zastosowania, zainstaluj [program Visual studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) lub [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Znajdź pobrany plik Instalatora i uruchom go. Może być wyświetlana w przeglądarce lub może znajdować się w folderze pobierania. Instalator wymaga uprawnień administratora do uruchomienia. Może zostać wyświetlone okno dialogowe **Kontrola konta użytkownika** z prośbą o przyznanie uprawnień, aby Instalator mógł wprowadzać zmiany w systemie. Wybierz opcję **tak**. Jeśli występują problemy, Znajdź pobrany plik w Eksploratorze plików, kliknij prawym przyciskiem myszy ikonę Instalatora i wybierz polecenie **Uruchom jako administrator** z menu kontekstowego.

   ![Pobierz i zainstaluj Instalator programu Visual Studio](media/vscpp-concierge-run-installer.gif "Pobierz i zainstaluj Instalator programu Visual Studio")

1. Instalator przedstawia listę obciążeń, które są grupami powiązanych opcji dla określonych obszarów deweloperskich. Obsługa języka C++ jest teraz częścią opcjonalnych obciążeń, które nie są instalowane domyślnie.

   ![Programowanie aplikacji klasycznych w języku C++](media/desktop-development-with-cpp.png "Programowanie aplikacji klasycznych w języku C++")

   W przypadku języka C++ wybierz pozycję **Programowanie aplikacji klasycznych w języku c++** , a następnie wybierz pozycję **Zainstaluj**.

   ![Instalowanie programu Desktop Development przy użyciu obciążenia C++](media/vscpp-concierge-choose-workload.gif "Instalowanie programu Desktop Development przy użyciu obciążenia C++")

1. Po zakończeniu instalacji wybierz przycisk **Uruchom** , aby uruchomić program Visual Studio.

   Przy pierwszym uruchomieniu programu Visual Studio zostanie wyświetlony monit o zalogowanie się przy użyciu konta Microsoft. Jeśli nie masz takiego konta, możesz je utworzyć bezpłatnie. Należy również wybrać motyw. Nie martw się, możesz ją zmienić później, jeśli chcesz.

   Przygotowanie się do korzystania z programu Visual Studio w ciągu kilku minut może być możliwe dopiero po pierwszym uruchomieniu. Oto, co wygląda jak w krótkim czasie:

   ![Logowanie do programu Visual Studio 2017](media/vscpp-quickstart-first-run.gif "Logowanie do programu Visual Studio 2017")

   Program Visual Studio uruchamia się znacznie szybciej po ponownym uruchomieniu.

1. Po otwarciu programu Visual Studio Sprawdź, czy ikona flagi na pasku tytułu jest wyróżniona:

   ![Flaga powiadomienia programu Visual Studio 2017](media/vscpp-first-start-page-flag.png "Flaga powiadomienia programu Visual Studio 2017")

   Jeśli zostanie on wyróżniony, wybierz go, aby otworzyć okno **powiadomienia** . Jeśli dla programu Visual Studio są dostępne jakieś aktualizacje, zalecamy ich zainstalowanie teraz. Po zakończeniu instalacji uruchom ponownie program Visual Studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Instalacja programu Visual Studio 2015

Aby zainstalować program Visual Studio 2015, przejdź do [pozycji Pobierz starsze wersje programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Uruchom program instalacyjny i wybierz pozycję **Instalacja niestandardowa** , a następnie wybierz składnik C++. Aby dodać obsługę języka C++ do istniejącej instalacji programu Visual Studio 2015, kliknij przycisk Start systemu Windows i wpisz polecenie **Dodaj Usuń programy**. Otwórz program z listy wyników, a następnie Znajdź instalację programu Visual Studio 2015 na liście zainstalowanych programów. Kliknij go dwukrotnie, a następnie wybierz polecenie **Modyfikuj** i wybierz składniki Visual C++, które mają zostać zainstalowane.

Ogólnie rzecz biorąc, zdecydowanie zalecamy użycie programu Visual Studio 2017, nawet jeśli trzeba skompilować kod przy użyciu kompilatora programu Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Używanie natywnego wielu elementów docelowych w programie Visual Studio do kompilowania starych projektów](../porting/use-native-multi-targeting.md).

::: moniker-end

Gdy program Visual Studio jest uruchomiony, możesz przejść do następnego kroku.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Tworzenie projektu w języku C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
