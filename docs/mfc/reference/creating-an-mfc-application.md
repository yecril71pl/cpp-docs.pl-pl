---
title: Tworzenie aplikacji MFC
ms.date: 08/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 5f3a24a46db1c9013e5458143812faa079ade013
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108508"
---
# <a name="creating-an-mfc-application"></a>Tworzenie aplikacji MFC

Aplikacja MFC jest aplikacją wykonywalną dla systemu Windows opartą na bibliotece Microsoft Foundation Class (MFC). Pliki wykonywalne MFC zazwyczaj mieszczą się w pięciu typach: standardowe aplikacje systemu Windows, okna dialogowe, aplikacje oparte na formularzach, aplikacje w stylu Eksploratora i aplikacje w stylu przeglądarki sieci Web. Aby uzyskać więcej informacji, zobacz:

- [Korzystanie z klas do zapisywania aplikacji systemu Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Tworzenie i wyświetlanie okien dialogowych](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Tworzenie aplikacji MFC opartej na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Tworzenie aplikacji MFC w stylu eksploratora plików](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Tworzenie aplikacji MFC w stylu przeglądarki internetowej](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

Kreator aplikacji MFC generuje odpowiednie klasy i pliki dla dowolnego z tych typów aplikacji, w zależności od opcji wybranych w kreatorze.


Najprostszym sposobem tworzenia aplikacji MFC jest użycie Kreatora aplikacji MFC (**projekt aplikacji MFC** w programie Visual Studio 2019). Aby utworzyć aplikację konsolową MFC (program wiersza polecenia, który używa bibliotek MFC, ale działa w oknie konsoli), użyj Kreatora pulpitu systemu Windows i wybierz opcję **Aplikacja konsolowa** i **nagłówki MFC** .

::: moniker range=">=vs-2019"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Aby utworzyć formularze MFC lub aplikację opartą na oknach dialogowych

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt**.
1. Wprowadź ciąg "MFC" w polu wyszukiwania, a następnie wybierz pozycję **aplikacja MFC** z listy wynik.
1. Zmodyfikuj wartości domyślne zgodnie z wymaganiami, a następnie naciśnij przycisk **Create (Utwórz** ), aby otworzyć **Kreatora aplikacji MFC**.
1. Zmodyfikuj wartości konfiguracyjne zgodnie z wymaganiami, a następnie naciśnij przycisk **Zakończ**.

Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji MFC opartej na formularzach](creating-a-forms-based-mfc-application.md).

![Kreator aplikacji MFC](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>Aby utworzyć aplikację konsolową MFC

Aplikacja konsolowa MFC jest programem wiersza polecenia, który korzysta z bibliotek MFC, ale działa w oknie konsoli.

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt**.
1. Wprowadź ciąg "Desktop" w polu wyszukiwania, a następnie wybierz pozycję **Kreator pulpitu systemu Windows** z listy wyników.
1. Zmodyfikuj odpowiednio nazwę projektu, a następnie naciśnij przycisk **dalej** , aby otworzyć **Kreatora pulpitu systemu Windows**.
1. Zaznacz pole **nagłówki MFC** i ustaw inne wartości zgodnie z wymaganiami, a następnie naciśnij przycisk **Zakończ**.

![Kreator aplikacji MFC](media/windows-desktop-wizard.png)

::: moniker-end

::: moniker range="=vs-2017"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Aby utworzyć formularze MFC lub aplikację opartą na oknach dialogowych

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt**.
1. W obszarze **zainstalowane** szablony wybierz pozycję **Visual C++**   >  **MFC/ATL**. Jeśli nie są one widoczne, użyj Instalator programu Visual Studio, aby je dodać.
1. Wybierz pozycję **aplikacja MFC** w środkowym okienku.
1. Zmodyfikuj wartości konfiguracyjne zgodnie z wymaganiami, a następnie naciśnij przycisk **Zakończ**.

Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji MFC opartej na formularzach](creating-a-forms-based-mfc-application.md).

![Kreator aplikacji MFC](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>Aby utworzyć aplikację konsolową MFC

Aplikacja konsolowa MFC jest programem wiersza polecenia, który korzysta z bibliotek MFC, ale działa w oknie konsoli.

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt**.
1. W obszarze **zainstalowane** szablony wybierz pozycję **Visual C++**  > **Windows Desktop**.
1. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows** .
1. Zmodyfikuj odpowiednio nazwę projektu, a następnie naciśnij przycisk **OK** , aby otworzyć **Kreatora pulpitu systemu Windows**.
1. Zaznacz pole **nagłówki MFC** i ustaw inne wartości zgodnie z wymaganiami, a następnie naciśnij przycisk **Zakończ**.

![Kreator aplikacji MFC](media/windows-desktop-wizard-2017.png)

::: moniker-end

::: moniker range="=vs-2015"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>Aby utworzyć formularze MFC lub aplikację opartą na oknach dialogowych

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt**.
1. W obszarze **zainstalowane** szablony wybierz pozycję **Visual C++**  > **MFC**.
1. Wybierz pozycję **aplikacja MFC** w środkowym okienku.
1. Kliknij przycisk **dalej** , aby uruchomić **Kreatora aplikacji MFC**.

Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji MFC opartej na formularzach](creating-a-forms-based-mfc-application.md).

![Kreator aplikacji MFC](media/mfc-app-wizard-2015.png)

## <a name="to-create-an-mfc-console-application"></a>Aby utworzyć aplikację konsolową MFC

Aplikacja konsolowa MFC jest programem wiersza polecenia, który korzysta z bibliotek MFC, ale działa w oknie konsoli.

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt**.
1. W obszarze **zainstalowane** szablony wybierz pozycję **Visual C++**  > **Win32**.
1. W środkowym okienku wybierz pozycję **aplikacja konsoli Win32** .
1. Zmodyfikuj nazwę projektu zgodnie z wymaganiami, a następnie naciśnij przycisk **OK**.
1. Na drugiej stronie kreatora zaznacz pole wyboru **Dodaj wspólne nagłówki dla MFC** i ustaw inne wartości zgodnie z wymaganiami, a następnie naciśnij przycisk **Zakończ**.

::: moniker-end

Po utworzeniu projektu można wyświetlić pliki utworzone w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji na temat plików tworzonych przez kreatora dla projektu, zobacz plik Readme. txt wygenerowany przez projekt. Aby uzyskać więcej informacji na temat typów plików, zobacz [typy plików utworzonych dla projektów C++ programu Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz także

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../build/reference/property-pages-visual-cpp.md)