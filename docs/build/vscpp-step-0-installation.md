---
title: Instalowanie obsługi języka C++ w programie Visual Studio
description: Instalowanie obsługi programu Visual Studio dla języka Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 2c2bed4063194bdc3c0f3fbc405be6bf9a4031e7
ms.sourcegitcommit: 5fc76f5b3c4c3ee49f38f05b37261a324591530b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58870783"
---
# <a name="install-c-support-in-visual-studio"></a>Instalowanie obsługi języka C++ w programie Visual Studio

Jeśli jeszcze nie został pobrany i zainstalowany program Visual Studio i narzędzi Visual C++ jeszcze, Oto jak rozpocząć pracę.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Visual Studio 2019 Installation

Witamy w programie Visual Studio 2019 r! W tej wersji jest można łatwo wybrać i zainstalować tylko funkcje, których potrzebujesz. Ze względu na zmniejszenie rozmiaru minimalnej instalacji szybko i przy mniejszym wpływem na system i.

> [!NOTE]
> W tym temacie mają zastosowanie do instalacji programu Visual Studio na Windows. [Visual Studio Code](https://code.visualstudio.com/) jest uproszczone, Międzyplatformowe środowisko programistyczne, uruchamiany w systemach Windows, Mac i Linux. Microsoft [C/C++ dla Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) rozszerzenie obsługuje funkcję IntelliSense, debugowanie, formatowania i automatycznego uzupełniania kodu. Visual Studio dla komputerów Mac nie obsługuje Microsoft C++, ale obsługuje języki .NET i programowanie dla wielu platform. Aby uzyskać instrukcje dotyczące instalacji, zobacz [Zainstaluj program Visual Studio dla komputerów Mac](/visualstudio/mac/installation/).

Chcesz dowiedzieć się więcej na temat inne nowości w tej wersji? Zobacz programu Visual Studio [informacje o wersji](/visualstudio/releases/2019/release-notes/).

Gotowe do zainstalowania? Przeprowadzimy Cię przez nią krok po kroku.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Krok 1 — Upewnij się, że Twój komputer jest gotowy dla programu Visual Studio

Przed rozpoczęciem instalowania programu Visual Studio:

1. Sprawdź [wymagania systemowe](/visualstudio/releases/2019/system-requirements). Te wymagania ułatwiają określenie, czy komputer obsługuje program Visual Studio 2019 r.

1. Zastosowanie najnowszych aktualizacji Windows. Te aktualizacje upewnij się, że komputer ma najnowsze aktualizacje zabezpieczeń i wymagane składniki systemowe dla programu Visual Studio.

1. Ponowne uruchomienie komputera. Ponowne uruchomienie gwarantuje, że żadne oczekujące instalacje lub aktualizacje nie zakłócą instalacji programu Visual Studio.

1. Zwolnij miejsce. Usuń niepotrzebne pliki i aplikacje z usługi % SystemDrive %, na przykład uruchamianie aplikacji Oczyszczanie dysku.

Masz pytania dotyczące uruchamiania poprzednich wersji programu Visual Studio obok siebie przy użyciu programu Visual Studio 2019 r, zobacz [Visual Studio 2019 r i zgodności platformy](/visualstudio/releases/2019/compatibility/) strony.

### <a name="step-2---download-visual-studio"></a>Krok 2 — pobieranie programu Visual Studio

Następnie należy pobrać plik inicjujący programu Visual Studio. Aby to zrobić, kliknij poniższy przycisk, wybierz wydanie programu Visual Studio, której potrzebujesz, następnie wybierz **Zapisz**, a następnie wybierz **Otwórz folder**.

 > [!div class="button"]
 > [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Krok 3 — instalowanie Instalatora programu Visual Studio

Uruchom plik inicjujący, aby zainstalować Instalatora programu Visual Studio. Tego nowego, lekkiego Instalatora zawiera wszystko, co jest potrzebne do zainstalowania i Dostosuj program Visual Studio.

1. Z usługi **pliki do pobrania** folderu, kliknij dwukrotnie program inicjujący, który jest zgodny lub podobny do jednego z następujących plików:

   * **vs_community.exe** dla Visual Studio Community
   * **vs_professional.exe** for Visual Studio Professional
   * **vs_enterprise.exe** programu Visual Studio Enterprise

   Jeśli pojawi się powiadomienie Kontrola konta użytkownika, wybierz opcję **tak**.

1. Poprosimy Cię potwierdzić Microsoft [postanowienia licencyjne](https://visualstudio.microsoft.com/license-terms/) i Microsoft [zasady zachowania poufności informacji](https://privacy.microsoft.com/privacystatement). Wybierz **nadal**.

### <a name="step-4---choose-workloads"></a>Krok 4 — Wybieranie obciążeń

Po zainstalowaniu Instalatora, można go dostosować instalację, wybierając *obciążeń*, lub zestawy, które mają funkcji. Poniżej przedstawiono sposób.

1. Znajdź obciążenie w **Instalowanie programu Visual Studio** ekranu.

   ![Visual Studio 2019: Zainstaluj obciążenie](../get-started/media/vs-installer-workloads.png)

   Na potrzeby obsługi podstawowych C++ wybierz obciążenie "Programowanie aplikacji klasycznych w języku C++". Dołączono edytora podstawowych domyślny, który zawiera podstawowe obsługę edytowania kodu dla ponad 20 języków, możliwość otwierania i edytowania kodu z dowolnego folderu bez konieczności korzystania z projektu i zintegrowane kontroli kodu źródłowego.

   Dodatkowych obciążeń obsługuje inne rodzaje programowania w języku C++. Na przykład wybierz obciążenie "Programowanie aplikacji uniwersalnych platformy Windows", do tworzenia aplikacji, które używają środowiska uruchomieniowego Windows dla Microsoft Store. Wybierz pozycję "Programowanie gier w języku C++" do tworzenia gier korzystających z technologii DirectX, Unreal i Cocos2d. Wybierz pozycję "Programowanie dla systemu Linux przy użyciu języka C++" do platform Linux, łącznie z programowaniem IoT.

   **Szczegółowe informacje dotyczące instalacji** okienko zawiera listę dołączone i opcjonalne składniki zainstalowane przez każde obciążenie. Można wybrać, lub Anuluj wybór składników opcjonalnych na tej liście. Na przykład obsługi opracowywania aplikacji za pomocą programu Visual Studio 2017 lub 2015 kompilatora zestawy narzędzi, wybierz MSVC w wersji 141 lub MSVC w wersji 140 opcjonalnych składników. Możesz dodać obsługę MFC, eksperymentalne rozszerzenie języka modułów, IncrediBuild i nie tylko.

1. Po wybraniu workload(s) i opcjonalne składniki, które chcesz, aby wybrać **zainstalować**.

    Następnie ekranów statusu pojawiają się pokazujących postęp instalacji programu Visual Studio.

> [!TIP]
> W dowolnym momencie po zakończeniu instalacji można zainstalować obciążeń lub składników, które nie są początkowo zainstalowano. Jeśli masz program Visual Studio, Otwórz, przejdź do strony **narzędzia** > **Pobierz narzędzia i funkcje...**  która otwiera Instalatora programu Visual Studio. Lub Otwórz **Instalatora programu Visual Studio** z Start menu. Z tego miejsca możesz wybrać obciążeń lub składników, które chcesz zainstalować. Następnie wybierz **Modyfikuj**.

## <a name="step-5---choose-individual-components-optional"></a>Krok 5 — wybieranie poszczególnych składników (opcjonalnie)

Jeśli nie chcesz dostosować instalację programu Visual Studio za pomocą funkcji obciążeń lub chcesz dodać więcej składników nie instaluje obciążenia, możesz to zrobić poprzez zainstalowanie lub dodanie poszczególne składniki z **poszczególne składniki** kartę. Wybierz co, a następnie postępuj zgodnie z monitami.

  ![Visual Studio 2019 - instalacji poszczególnych składników](../get-started/media/vs-installer-individual-components.png "poszczególne składniki Zainstaluj program Visual Studio")

## <a name="step-6---install-language-packs-optional"></a>Krok 6 — instalowanie pakietów językowych (opcjonalnie)

Domyślnie program instalacyjny próbuje jest zgodny z językiem systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Aby zainstalować program Visual Studio w języku wybrane, wybierz opcję **pakiety językowe** kartę za pomocą Instalatora programu Visual Studio, a następnie postępuj zgodnie z monitami.

  ![Visual Studio 2019 - Zainstaluj pakiety językowe](../get-started/media/vs-installer-language-packs.png "pakiety językowe Zainstaluj program Visual Studio")

### <a name="change-the-installer-language-from-the-command-line"></a>Zmień język Instalatora z poziomu wiersza polecenia

Inny sposób, można zmienić domyślny język jest, uruchamiając Instalatora z poziomu wiersza polecenia. Na przykład, możesz wymusić Instalatora Aby uruchomić w języku angielskim, za pomocą następującego polecenia: `vs_installer.exe --locale en-US`. Instalator zapamięta to ustawienie po jej uruchomieniu następnym razem. Instalator obsługuje następujące generatory kodów języka: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru i tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Krok 7 — zmiana lokalizacji instalacji (opcjonalnie)

Możliwe jest zmniejszenie miejsca zajmowanego przez instalację programu Visual Studio na dysku systemowym. Można przenieść pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach i zachować programu Visual Studio na dysku, na której działa najszybszej.

  ![Visual Studio 2019 - Zmień lokalizacje instalacji](../get-started/media/vs-installer-installation-locations.png "zmiana lokalizacji instalacji")

> [!IMPORTANT]
> Możesz wybrać inny dysk tylko wtedy, gdy najpierw zainstalować program Visual Studio. Jeśli już został zainstalowany i chcesz zmienić dysków, należy odinstalować program Visual Studio i zainstaluj go ponownie.

## <a name="step-8---start-developing"></a>Krok 8 — zacznij programować

1. Po zakończeniu instalacji programu Visual Studio wybierz **Uruchom** przycisk, aby rozpocząć tworzenie aplikacji za pomocą programu Visual Studio.

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

1. W polu wyszukiwania wprowadź typ aplikacji, którą chcesz utworzyć, aby wyświetlić listę dostępnych szablonów. Na liście szablonów, zależy od workload(s), która została wybrana podczas instalacji. Aby wyświetlić różne szablony, wybierz różnych obciążeń.

   Można także filtrować wyszukiwania dla określonego języka programowania przy użyciu **języka** listy rozwijanej. Można filtrować przy użyciu **platformy** listy i **typ projektu** listy zbyt.

1. Visual Studio otwiera nowy projekt i wszystko jest gotowe do kodu.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Instalacja programu Visual Studio 2017

W programie Visual Studio 2017 jest można łatwo wybrać i zainstalować tylko funkcje, których potrzebujesz. Ze względu na zmniejszenie rozmiaru minimalnej instalacji szybko i przy mniejszym wpływem na system i.

### <a name="prerequisites"></a>Wymagania wstępne

- Połączenie szerokopasmowe. Instalator programu Visual Studio można pobrać kilku gigabajtów danych.

- Komputer z systemem Microsoft Windows 7 lub nowszy. Zalecamy systemu Windows 10 dla najlepszego komfortu programowania. Upewnij się, że najnowsze aktualizacje są stosowane do systemu, przed zainstalowaniem programu Visual Studio.

- Za mało wolnego miejsca na dysku. Visual Studio wymaga co najmniej 7 GB miejsca na dysku i może potrwać 50 GB lub więcej, jeśli zainstalowano wiele typowych opcji. Zaleca się, że masz zainstalowane na dysku C:.

Aby uzyskać szczegółowe informacje dotyczące miejsca na dysku i wymagania dotyczące systemu operacyjnego, zobacz [wymagania systemowe rodziny produktów Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). Instalator raporty, ilość miejsca na dysku jest wymagana dla wybranych opcji.

### <a name="download-and-install"></a>Pobierz i zainstaluj

1. Pobierz najnowszą wersję Instalatora programu Visual Studio 2017 for Windows.

   > [!div class="nextstepaction"]
   > [Install Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Wersja Community to dla indywidualnych deweloperów, edukacyjne, badań akademickich i programowania typu open source. Do innych celów, należy zainstalować [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) lub [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Znajdź plik Instalatora został pobrany i uruchom go. Może być wyświetlany w przeglądarce lub może okazać się w folderze pobrane. Instalator wymaga uprawnień administratora do uruchomienia. Może zostać wyświetlony **Kontrola konta użytkownika** okno dialogowe z monitem o nadanie uprawnień umożliwiających Instalatora, wprowadzić zmiany do systemu; wybierz **tak**. Jeśli występują problemy, Znajdź pobrany plik w Eksploratorze plików, kliknij prawym przyciskiem myszy na ikonie Instalatora, a następnie wybierz **Uruchom jako Administrator** z menu kontekstowego.

   ![Pobierz i zainstaluj Instalator programu Visual Studio](media/vscpp-concierge-run-installer.gif "pobranie i zainstalowanie Instalatora programu Visual Studio")

1. Instalator przedstawia listy obciążeń, powiązane opcje obszary rozwoju określonych grup. Podpora androidu Pro C++ jest teraz częścią opcjonalne obciążeń, które nie są instalowane domyślnie.

   ![Programowanie aplikacji klasycznych w języku C++](media/desktop-development-with-cpp.png "programowanie aplikacji klasycznych w języku C++")

   Dla języka C++, wybierz **programowanie aplikacji klasycznych w języku C++** obciążenia, a następnie wybierz **zainstalować**.

   ![Zainstaluj programowanie aplikacji klasycznych w języku C++](media/vscpp-concierge-choose-workload.gif "zainstalować programowanie aplikacji klasycznych w języku C++")

1. Po zakończeniu instalacji wybierz **Uruchom** przycisk, aby uruchomić program Visual Studio.

   Podczas pierwszego uruchomienia programu Visual Studio, pojawi się prośba o zalogowanie Account firmy Microsoft. Jeśli nie masz, możesz go utworzyć za darmo. Należy także wybrać motyw. Nie martw się, możesz go zmienić później, jeśli chcesz.

   Visual Studio może potrwać kilka minut w celu przygotowania do użycia przy pierwszym uruchomieniu. Poniżej przedstawiono, jak to wygląda w ujęć poklatkowych szybkie:

   ![Zaloguj się do niego programu Visual Studio 2017](media/vscpp-quickstart-first-run.gif "Zaloguj się do niego programu Visual Studio 2017")

   Program Visual Studio rozpoczyna się znacznie szybciej, gdy zostanie uruchomiony ponownie.

1. Po otwarciu programu Visual Studio, należy sprawdzić, jeśli zostanie wyróżniona ikonę flagi na pasku tytułu:

   ![Flaga powiadomienia w usłudze Visual Studio 2017](media/vscpp-first-start-page-flag.png "flagę powiadomienia programu Visual Studio 2017")

   Jeśli jest wyróżniona, zaznacz ją, aby otworzyć **powiadomienia** okna. Jeśli istnieją jakiekolwiek aktualizacje dostępne dla programu Visual Studio, zalecamy możesz zainstalować je teraz. Po zakończeniu instalacji uruchom ponownie program Visual Studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 Installation

Aby zainstalować program Visual Studio 2015, przejdź do [pobieranie starszych wersji programu Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Uruchom program instalacyjny, a następnie wybierz **Instalacja niestandardowa** , a następnie wybierz składnik C++. Aby dodać obsługę języka C++ do istniejącej instalacji programu Visual Studio 2015, kliknij przycisk Windows Start i typ **Dodaj/Usuń programy**. Otwórz program z listy wyników, a następnie znajdź instalacji programu Visual Studio 2015 na liście zainstalowanych programów. Kliknij go dwukrotnie, a następnie wybierz **Modyfikuj** i wybierz pozycję Visual C++ składniki do zainstalowania.

Ogólnie rzecz biorąc zdecydowanie zaleca się użycie programu Visual Studio 2017, nawet wtedy, gdy należy przeprowadzić kompilowanie kodu przy użyciu kompilatora Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Użyj natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów](../porting/use-native-multi-targeting.md).

::: moniker-end

Program Visual Studio jest uruchomiony, możesz przejść do następnego kroku.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Tworzenie projektu C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
