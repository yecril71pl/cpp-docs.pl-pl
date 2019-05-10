---
title: Wdrażanie aplikacji Visual C++ przy użyciu projektu instalacji
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 6829e917ed0a0e27bea7f42eb9bcfb2b9ad5d2e1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877380"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Przewodnik: Wdrażanie aplikacji Visual C++ przy użyciu projektu instalacji

W tym artykule opisano, jak wdrażanie aplikacji Visual C++ za pomocą projektu Instalatora.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Komputer z zainstalowanego programu Visual Studio.

- Dodatkowy komputer, który nie ma bibliotek języka Visual C++.

## <a name="create-the-setup-project"></a>Tworzenie projektu Instalatora

Instrukcje dotyczące tworzenia projektu Instalatora różnią się w zależności od zainstalowanej wersji programu Visual Studio. Upewnij się, że w selektorze wersja w prawym górnym lewym równa poprawnej wersji.

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Aby utworzyć projekt w programie Visual Studio 2019 r.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **Utwórz nowy projekt** okno dialogowe.

   ![Projekt aplikacji MFC](media/vs2019-mfc-app-new-project.png "MFC nowej aplikacji")

1. W górnej części okna dialogowego wpisz `MFC` w wyszukiwaniu pole, a następnie wybierz **aplikacji MFC** z listy wyników. Jeśli widzisz go, należy uruchomić program Instalatora programu Visual Studio w menu Windows Start, a następnie kliknij polecenie  **C++ obciążenie programowanie aplikacji klasycznych** kafelka. W obszarze **poszczególne składniki**, upewnij się, że składnik MFC jest zaznaczone.

1. Na następnej stronie podaj nazwę dla projektu, a następnie określ lokalizację projektu, w razie potrzeby.

1. Wybierz **Utwórz** przycisk, aby utworzyć projekt klienta. Gdy **Kreator aplikacji MFC** pojawi się, Zaakceptuj wszystkie ustawienia domyślne.

1. Zmień konfigurację aktywngo rozwiązania, aby **wersji**. Z **kompilacji** menu, wybierz opcję **programu Configuration Manager**. Z **programu Configuration Manager** okno dialogowe, wybierz opcję **wersji** z **Konfiguracja rozwiązania aktywnego** pole listy rozwijanej. Kliknij przycisk **Zamknij**.

1. Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania aplikacji. Lub na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Tworzenie aplikacji umożliwia projektu Instalatora, aby użyć danych wyjściowych tego projektu aplikacji MFC.

1. Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie programu Microsoft projektów Instalatora programu Visual Studio. Rozszerzenie jest bezpłatna dla deweloperów programu Visual Studio i dodaje funkcje instalacji i wdrażania szablonów projektu do programu Visual Studio. Po połączeniu się z Internetem, w programie Visual Studio, wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**. W obszarze **rozszerzenia i aktualizacje** okno dialogowe, wybierz opcję **Online** kartę i typ *projektów Instalatora programu Visual Studio Microsoft* w polu wyszukiwania. Naciśnij klawisz **Enter**, wybierz opcję **programu Microsoft Visual Studio \<wersji > Projekty Instalatora**i kliknij przycisk **Pobierz**. Możliwość uruchamiania i zainstaluj rozszerzenie, a następnie uruchom ponownie program Visual Studio.

   ![Projektu Instalatora programu Visual Studio](media/vs2019-extension-dialog-installer-project.png "nazwij projekt klienta")

1. Na pasku menu programu Visual Studio, wybierz **pliku** > **niedawne projekty i rozwiązania**, a następnie wybierz polecenie ponownie otworzyć projekt.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **Utwórz nowy projekt** okno dialogowe. W polu wyszukiwania wpisz "Setup", a z listy wyników wybierz **projektu Instalatora**.

1. Wprowadź nazwę dla projektu Instalatora w **nazwa** pole. W **rozwiązania** listy rozwijanej wybierz **Dodaj do rozwiązania**. Wybierz **OK** przycisk, aby utworzyć projekt Instalatora. A **Asystenta pliku (nazwa_projektu)** zostanie otwarta karta w oknie edytora.

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>Aby utworzyć projekt w programie Visual Studio 2017

1. Utwórz nowy projekt. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

1. Użyj **Kreator aplikacji MFC** do tworzenia nowego rozwiązania programu Visual Studio. Można znaleźć kreatora z **nowy projekt** okna dialogowego rozwiń **Visual C++** węzeł **MFC**, wybierz opcję **aplikacji MFC**, wprowadź Nazwa projektu, a następnie kliknij przycisk **OK**. Kliknij przycisk **Zakończ**.

   > [!NOTE]
   > Jeśli **aplikacji MFC** brakuje typu, wybierz **Otwórz Instalator programu Visual Studio** w lewym okienku **nowy projekt** okno dialogowe. Opcję znajdujący się w folderze instalacji **programowanie aplikacji klasycznych w języku C++** w **opcjonalnie** składniki sekcji o nazwie **Visual C++ MFC dla x86 i x64**.

1. Zmień konfigurację aktywngo rozwiązania, aby **wersji**. Z **kompilacji** menu, wybierz opcję **programu Configuration Manager**. Z **programu Configuration Manager** okno dialogowe, wybierz opcję **wersji** z **Konfiguracja rozwiązania aktywnego** pole listy rozwijanej. Kliknij przycisk **Zamknij**.

1. Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania aplikacji. Lub na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Tworzenie aplikacji umożliwia projektu Instalatora, aby użyć danych wyjściowych tego projektu aplikacji MFC.

1. Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie programu Microsoft projektów Instalatora programu Visual Studio. Rozszerzenie jest bezpłatna dla deweloperów programu Visual Studio i dodaje funkcje instalacji i wdrażania szablonów projektu do programu Visual Studio. Po połączeniu się z Internetem, w programie Visual Studio, wybierz **narzędzia** > **rozszerzenia i aktualizacje**. W obszarze **rozszerzenia i aktualizacje** okno dialogowe, wybierz opcję **Online** kartę i typ *projektów Instalatora programu Visual Studio Microsoft* w polu wyszukiwania. Naciśnij klawisz **Enter**, wybierz opcję **programu Microsoft Visual Studio \<wersji > Projekty Instalatora**i kliknij przycisk **Pobierz**. Możliwość uruchamiania i zainstaluj rozszerzenie, a następnie uruchom ponownie program Visual Studio.

1. Na pasku menu wybierz **pliku** > **niedawne projekty i rozwiązania**, a następnie wybierz polecenie ponownie otworzyć projekt.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **nowy projekt** okno dialogowe. Następnie w okienku po lewej stronie okna dialogowego rozwiń **zainstalowane** > **inne typy projektów** węzłów, a następnie wybierz **Instalatora programu Visual Studio**. W środkowym okienku wybierz **projektu Instalatora**.

1. Wprowadź nazwę dla projektu Instalatora w **nazwa** pole. W **rozwiązania** listy rozwijanej wybierz **Dodaj do rozwiązania**. Wybierz **OK** przycisk, aby utworzyć projekt Instalatora. A **Asystenta pliku (nazwa_projektu)** zostanie otwarta karta w oknie edytora.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>Aby utworzyć projekt w programie Visual Studio 2015

1. Utwórz nowy projekt. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

1. Użyj **Kreator aplikacji MFC** do tworzenia nowego rozwiązania programu Visual Studio. Można znaleźć kreatora z **nowy projekt** okna dialogowego rozwiń **Visual C++** węzeł **MFC**, wybierz opcję **aplikacji MFC**, wprowadź Nazwa projektu, a następnie kliknij przycisk **OK**. Kliknij przycisk **Zakończ**.

   > [!NOTE]
   > Jeśli **aplikacji MFC** brakuje typu, kliknij przycisk Windows Start i typ **Dodaj/Usuń programy**. Otwórz program z listy wyników, a następnie znajdź instalacji programu Microsoft Visual Studio 2015 na liście zainstalowanych programów. Kliknij go dwukrotnie, a następnie wybierz **Modyfikuj** i wybierz **Microsoft Foundation Classes** składnika w obszarze **Visual C++**.

1. Zmień konfigurację aktywngo rozwiązania, aby **wersji**. Z **kompilacji** menu, wybierz opcję **programu Configuration Manager**. Z **programu Configuration Manager** okno dialogowe, wybierz opcję **wersji** z **Konfiguracja rozwiązania aktywnego** pole listy rozwijanej. Kliknij przycisk **Zamknij**.

1. Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania aplikacji. Lub na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Tworzenie aplikacji umożliwia projektu Instalatora, aby użyć danych wyjściowych tego projektu aplikacji MFC.

1. Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie programu Microsoft projektów Instalatora programu Visual Studio. Rozszerzenie jest bezpłatna dla deweloperów programu Visual Studio i dodaje funkcje instalacji i wdrażania szablonów projektu do programu Visual Studio. Po połączeniu się z Internetem, w programie Visual Studio, wybierz **narzędzia** > **rozszerzenia i aktualizacje**. W obszarze **rozszerzenia i aktualizacje** okno dialogowe, wybierz opcję **Online** kartę i typ *projektów Instalatora programu Visual Studio Microsoft* w polu wyszukiwania. Naciśnij klawisz **Enter**, wybierz opcję **programu Microsoft Visual Studio \<wersji > Projekty Instalatora**i kliknij przycisk **Pobierz**. Możliwość uruchamiania i zainstaluj rozszerzenie, a następnie uruchom ponownie program Visual Studio.

1. Na pasku menu wybierz **pliku** > **niedawne projekty i rozwiązania**, a następnie wybierz polecenie ponownie otworzyć projekt.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **nowy projekt** okno dialogowe. Następnie w okienku po lewej stronie okna dialogowego rozwiń **zainstalowane** > **inne typy projektów** węzłów, a następnie wybierz **Instalatora programu Visual Studio**. W środkowym okienku wybierz **projektu Instalatora**.

1. Wprowadź nazwę dla projektu Instalatora w **nazwa** pole. W **rozwiązania** listy rozwijanej wybierz **Dodaj do rozwiązania**. Wybierz **OK** przycisk, aby utworzyć projekt Instalatora. A **Asystenta pliku (nazwa_projektu)** zostanie otwarta karta w oknie edytora.

::: moniker-end

## <a name="add-items-to-the-project"></a>Dodawanie elementów do projektu

1. Kliknij prawym przyciskiem myszy **folderu aplikacji** a następnie wybierz węzeł **Dodaj** > **dane wyjściowe projektu** otworzyć **Dodaj grupę wyjściową projektu**okno dialogowe. W oknie dialogowym wybierz **podstawowe wyjście** i kliknij przycisk **OK**. Nowy element o nazwie **główny wynik ProjectName (aktywny)** pojawia się.

1. Kliknij prawym przyciskiem myszy **folderu aplikacji** a następnie wybierz węzeł **Dodaj** > **zestawu** otworzyć **wybierz składnik** okna dialogowego pole. Wybierz i Dodaj wszystkie wymagane biblioteki DLL wymaganej przez program, zgodnie z opisem w artykule [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).

1. Wybierz element, który **główny wynik ProjectName (aktywny)**, kliknij prawym przyciskiem myszy i wybierz polecenie **Utwórz skrót podstawowe wyjście z ProjectName (aktywny)**. Nowy element o nazwie **skrót do podstawowe wyjście z ProjectName (aktywny)** pojawia się. Może zmienić nazwę elementu skrótów, a następnie przeciągnij i upuść element do **Menu programy użytkownika** węzła w lewej części okna.

1. Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**. W **projektu** tabeli, w obszarze **kompilacji** kolumny, zaznacz pole projektu wdrożenia. Kliknij przycisk **Zamknij**.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie** Tworzenie projektu MFC i wdrażaniu projektu.

1. W folderze rozwiązania zlokalizuj program setup.exe, który został zbudowany z projektu wdrożenia. Możesz skopiować ten plik (i plik msi) do zainstalowania aplikacji i jej wymagane pliki biblioteki na innym komputerze. Uruchom program instalacyjny na drugim komputerze, który nie ma bibliotek języka Visual C++.

## <a name="see-also"></a>Zobacz także

[Przykłady wdrożeń](deployment-examples.md)<br/>
