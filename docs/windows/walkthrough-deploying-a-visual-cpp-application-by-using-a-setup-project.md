---
title: Wdrażanie aplikacji visual c++ przy użyciu projektu instalacji
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 8a1242140154c5a0123d71b83983fae20cab5d7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374363"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Wskazówki: wdrażanie aplikacji Visual C++ przy użyciu instalacji projektu

W tym artykule opisano, jak za pomocą projektu instalacji do wdrażania aplikacji Visual C++.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Zainstalowany komputer z programem Visual Studio.

- Dodatkowy komputer, który nie ma bibliotek języka Visual C++.

## <a name="create-the-setup-project"></a>Tworzenie projektu instalacji

Instrukcje dotyczące tworzenia projektu instalacji różnią się w zależności od zainstalowanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Aby utworzyć projekt w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe Tworzenie nowego **projektu.**

   ![Projekt aplikacji MFC](media/vs2019-mfc-app-new-project.png "Nowa aplikacja MFC")

1. W górnej części okna `MFC` dialogowego wpisz pole wyszukiwania, a następnie wybierz aplikację **MFC** z listy wyników. Jeśli go nie widzisz, musisz uruchomić program Instalatora programu Visual Studio z menu Start systemu Windows i kliknąć kafelek **obciążenia deweloperskie w języku C++.** W obszarze **Poszczególne składniki**upewnij się, że składnik MFC jest sprawdzany.

1. Na następnej stronie wprowadź nazwę projektu i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt klienta. Po **wyświetleniu Kreatora aplikacji MFC** zaakceptuj wszystkie wartości domyślne.

1. Zmień konfigurację aktywnego rozwiązania na **Zwolnij**. Z menu **Kompilacja** wybierz polecenie **Menedżer konfiguracji**. W oknie **dialogowym Menedżer konfiguracji** wybierz pozycję **Zwolnij** z listy rozwijanej **Konfiguracja rozwiązania Active.** Kliknij przycisk **Zamknij**.

1. Naciśnij **klawisze Ctrl**+**Shift**+**B,** aby utworzyć aplikację. W menu **Kompilacja** kliknij polecenie **Buduj rozwiązanie**. Tworzenie aplikacji umożliwia projektowi instalacji użycie danych wyjściowych tego projektu aplikacji MFC.

1. Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie Microsoft Visual Studio Installer Projects. Rozszerzenie jest bezpłatne dla deweloperów programu Visual Studio i dodaje funkcje szablonów projektu instalacji i wdrażania do programu Visual Studio. Po nawiązaniu połączenia z Internetem w programie Visual Studio wybierz pozycję **Zarządzanie rozszerzeniami rozszerzeń** > **Manage Extensions**. W oknie dialogowym **Rozszerzenia i aktualizacje** wybierz kartę **Online** i wpisz w polu wyszukiwania pozycję *Projekty instalatora programu Microsoft Visual Studio.* Naciśnij **klawisz Enter**, wybierz pozycję Microsoft Visual Studio ** \<version> Installer Projects**, a następnie kliknij przycisk **Pobierz**. Wybierz, aby uruchomić i zainstalować rozszerzenie, a następnie uruchom ponownie program Visual Studio.

   ![Projekt instalacji programu Visual Studio](media/vs2019-extension-dialog-installer-project.png "Nadawanie nazwy projektowi klienta")

1. Na pasku menu programu Visual Studio wybierz pozycję **File** > **Recent Projects and Solutions**, a następnie wybierz opcję ponownego otwarcia projektu.

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe Tworzenie nowego **projektu.** W polu wyszukiwania wpisz "Ustawienia", a z listy wyników wybierz pozycję **Setup Project**.

1. Wprowadź nazwę projektu instalacji w polu **Nazwa.** Z listy rozwijanej **Rozwiązanie** wybierz pozycję **Dodaj do rozwiązania**. Wybierz przycisk **OK,** aby utworzyć projekt instalacji. W oknie edytora zostanie otwarta karta **Asystent plików (ProjectName).**

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>Aby utworzyć projekt w programie Visual Studio 2017

1. Tworzenie nowego projektu. W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.

1. Kreator **aplikacji MFC** służy do tworzenia nowego rozwiązania programu Visual Studio. Aby znaleźć kreatora, w oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C++,** wybierz pozycję **MFC**, wybierz **pozycję Aplikacja MFC**, wprowadź nazwę projektu, a następnie kliknij przycisk **OK**. Kliknij przycisk **Zakończ**.

   > [!NOTE]
   > Jeśli brakuje typu **aplikacji MFC,** wybierz **otwórz Instalatora programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.** Zainstaluj opcję znajdującą się w obszarze **Tworzenie pulpitu z c++** w sekcji **Składniki opcjonalne,** o nazwie **Visual C++ MFC dla x86 i x64**.

1. Zmień konfigurację aktywnego rozwiązania na **Zwolnij**. Z menu **Kompilacja** wybierz polecenie **Menedżer konfiguracji**. W oknie **dialogowym Menedżer konfiguracji** wybierz pozycję **Zwolnij** z listy rozwijanej **Konfiguracja rozwiązania Active.** Kliknij przycisk **Zamknij**.

1. Naciśnij **klawisze Ctrl**+**Shift**+**B,** aby utworzyć aplikację. W menu **Kompilacja** kliknij polecenie **Buduj rozwiązanie**. Tworzenie aplikacji umożliwia projektowi instalacji użycie danych wyjściowych tego projektu aplikacji MFC.

1. Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie Microsoft Visual Studio Installer Projects. Rozszerzenie jest bezpłatne dla deweloperów programu Visual Studio i dodaje funkcje szablonów projektu instalacji i wdrażania do programu Visual Studio. Po nawiązaniu połączenia z Internetem w programie Visual Studio wybierz pozycję**Rozszerzenia i aktualizacje** **narzędzi** > . W oknie dialogowym **Rozszerzenia i aktualizacje** wybierz kartę **Online** i wpisz w polu wyszukiwania pozycję *Projekty instalatora programu Microsoft Visual Studio.* Naciśnij **klawisz Enter**, wybierz pozycję Microsoft Visual Studio ** \<version> Installer Projects**, a następnie kliknij przycisk **Pobierz**. Wybierz, aby uruchomić i zainstalować rozszerzenie, a następnie uruchom ponownie program Visual Studio.

1. Na pasku menu wybierz pozycję **File** > **Recent Projects and Solutions**, a następnie wybierz opcję ponownego otwarcia projektu.

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe **Nowy projekt.** Następnie w lewym okienku okna dialogowego rozwiń węzły **Zainstalowane** > **inne typy projektów** i wybierz pozycję Instalator programu Visual **Studio**. W środkowym okienku wybierz pozycję **Projekt instalacji**.

1. Wprowadź nazwę projektu instalacji w polu **Nazwa.** Z listy rozwijanej **Rozwiązanie** wybierz pozycję **Dodaj do rozwiązania**. Wybierz przycisk **OK,** aby utworzyć projekt instalacji. W oknie edytora zostanie otwarta karta **Asystent plików (ProjectName).**

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>Aby utworzyć projekt w programie Visual Studio 2015

1. Tworzenie nowego projektu. W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.

1. Kreator **aplikacji MFC** służy do tworzenia nowego rozwiązania programu Visual Studio. Aby znaleźć kreatora, w oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C++,** wybierz pozycję **MFC**, wybierz **pozycję Aplikacja MFC**, wprowadź nazwę projektu, a następnie kliknij przycisk **OK**. Kliknij przycisk **Zakończ**.

   > [!NOTE]
   > Jeśli brakuje typu **aplikacji MFC,** kliknij przycisk Start systemu Windows i wpisz **Dodaj usuń programy**. Otwórz program z listy wyników, a następnie znajdź instalację programu Microsoft Visual Studio 2015 na liście zainstalowanych programów. Kliknij go dwukrotnie, a następnie wybierz pozycję **Modyfikuj** i wybierz składnik **Microsoft Foundation Classes** w obszarze Visual **C++**.

1. Zmień konfigurację aktywnego rozwiązania na **Zwolnij**. Z menu **Kompilacja** wybierz pozycję **Menedżer konfiguracji**. W oknie **dialogowym Menedżer konfiguracji** wybierz pozycję **Zwolnij** z listy rozwijanej **Konfiguracja rozwiązania Active.** Kliknij przycisk **Zamknij**.

1. Naciśnij **klawisze Ctrl**+**Shift**+**B,** aby utworzyć aplikację. W menu **Kompilacja** kliknij polecenie **Buduj rozwiązanie**. Tworzenie aplikacji umożliwia projektowi instalacji użycie danych wyjściowych tego projektu aplikacji MFC.

1. Jeśli jeszcze tego nie zrobiono, pobierz rozszerzenie Microsoft Visual Studio Installer Projects. Rozszerzenie jest bezpłatne dla deweloperów programu Visual Studio i dodaje funkcje szablonów projektu instalacji i wdrażania do programu Visual Studio. Po nawiązaniu połączenia z Internetem w programie Visual Studio wybierz pozycję**Rozszerzenia i aktualizacje** **narzędzi** > . W oknie dialogowym **Rozszerzenia i aktualizacje** wybierz kartę **Online** i wpisz w polu wyszukiwania pozycję *Projekty instalatora programu Microsoft Visual Studio.* Naciśnij **klawisz Enter**, wybierz pozycję Microsoft Visual Studio ** \<version> Installer Projects**, a następnie kliknij przycisk **Pobierz**. Wybierz, aby uruchomić i zainstalować rozszerzenie, a następnie uruchom ponownie program Visual Studio.

1. Na pasku menu wybierz pozycję **File** > **Recent Projects and Solutions**, a następnie wybierz opcję ponownego otwarcia projektu.

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe **Nowy projekt.** Następnie w lewym okienku okna dialogowego rozwiń węzły **Zainstalowane** > **inne typy projektów** i wybierz pozycję Instalator programu Visual **Studio**. W środkowym okienku wybierz pozycję **Projekt instalacji**.

1. Wprowadź nazwę projektu instalacji w polu **Nazwa.** Z listy rozwijanej **Rozwiązanie** wybierz pozycję **Dodaj do rozwiązania**. Wybierz przycisk **OK,** aby utworzyć projekt instalacji. W oknie edytora zostanie otwarta karta **Asystent plików (ProjectName).**

::: moniker-end

## <a name="add-items-to-the-project"></a>Dodawanie elementów do projektu

1. Kliknij prawym przyciskiem myszy węzeł **Folder aplikacji** i wybierz polecenie **Dodaj** > **dane wyjściowe projektu,** aby otworzyć okno dialogowe **Dodawanie grupy wyjściowej projektu.** W oknie dialogowym wybierz pozycję **Wyjście główne** i kliknij przycisk **OK**. Zostanie wyświetlony nowy element o nazwie **Wyjście podstawowe z elementu ProjectName (Active).**

1. Kliknij prawym przyciskiem myszy węzeł **Folder aplikacji** i wybierz polecenie **Dodaj** > **złożenie,** aby otworzyć okno dialogowe **Wybieranie komponentu.** Wybierz i dodaj wymagane biblioteki DLL potrzebne przez program, zgodnie z opisem w artykule [Określanie, które biblioteki DLL mają być redystrybucyjne.](determining-which-dlls-to-redistribute.md)

1. Wybierz element **Wyjście podstawowe z ProjectName (Active),** kliknij prawym przyciskiem myszy i wybierz polecenie **Utwórz skrót do danych wyjściowych podstawowego z ProjectName (Active)**. Zostanie wyświetlony nowy element o nazwie **Skrót do danych wyjściowych podstawowych z elementu ProjectName (Active).** Można zmienić nazwę elementu skrótu, a następnie przeciągnąć i upuścić element do **węzła Menu programy użytkownika** po lewej stronie okna.

1. Na pasku menu wybierz pozycję **Build** > **Configuration Manager**. W tabeli **Projekt** w kolumnie **Kompilacja** zaznacz pole wyboru dla projektu wdrożeniowego. Kliknij przycisk **Zamknij**.

1. Na pasku menu wybierz pozycję Build Build Solution to build the MFC project and the deployment project.On the menu bar, choose **Build** > **Build Solution** to build the MFC project and the deployment project.

1. W folderze rozwiązania znajdź program setup.exe utworzony na podstawie projektu wdrożenia. Możesz skopiować ten plik (i plik msi), aby zainstalować aplikację i jej wymagane pliki biblioteki na innym komputerze. Uruchom program instalacyjny na drugim komputerze, na który nie ma bibliotek visual c++.

## <a name="see-also"></a>Zobacz też

[Przykłady wdrożeń](deployment-examples.md)<br/>
