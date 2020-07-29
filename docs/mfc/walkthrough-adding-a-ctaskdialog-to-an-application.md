---
title: 'Wskazówki: dodawanie obiektu CTaskDialog do aplikacji'
ms.date: 04/25/2019
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
ms.openlocfilehash: 3a970df4911fed643045a1c6b59fcda1a853dbcf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222774"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Wskazówki: dodawanie obiektu CTaskDialog do aplikacji

W tym instruktażu przedstawiono [klasę obiektu CTaskDialog](../mfc/reference/ctaskdialog-class.md) i pokazano, jak dodać ją do aplikacji.

`CTaskDialog`To zadanie okno dialogowe, które zastępuje okno komunikatu systemu Windows w systemie Windows Vista lub nowszym. `CTaskDialog`Poprawi oryginalny komunikat i dodaje funkcję. Okno komunikatu systemu Windows jest nadal obsługiwane w programie Visual Studio.

> [!NOTE]
> Wersje systemu Windows starsze niż Windows Vista nie obsługują programu `CTaskDialog` . Należy zaprogramować alternatywną opcję okna dialogowego, jeśli chcesz wyświetlić komunikat dla użytkownika uruchamiającego aplikację w starszej wersji systemu Windows. Możesz użyć statycznej metody [obiektu CTaskDialog:: Issupportd](../mfc/reference/ctaskdialog-class.md#issupported) , aby określić w czasie wykonywania, czy komputer użytkownika może wyświetlać `CTaskDialog` . Ponadto `CTaskDialog` jest dostępna tylko wtedy, gdy aplikacja jest skompilowana przy użyciu biblioteki Unicode.

Program `CTaskDialog` obsługuje kilka opcjonalnych elementów, które umożliwiają zbieranie i wyświetlanie informacji. Na przykład `CTaskDialog` można wyświetlić linki poleceń, niestandardowe przyciski, dostosowane ikony i stopkę. `CTaskDialog`Ma także kilka metod, które umożliwiają badanie stanu okna dialogowego zadania w celu określenia elementów opcjonalnych wybranych przez użytkownika.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2010 lub w nowszej wersji

- System Windows Vista lub nowszy

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Zamienianie okna komunikatu systemu Windows na obiektu CTaskDialog

Poniższa procedura przedstawia najbardziej podstawowe użycie programu `CTaskDialog` , który polega na zastępowaniu okna komunikatu systemu Windows. Ten przykład zmienia również ikonę skojarzoną z oknem dialogowym zadania. Zmiana ikony powoduje, że `CTaskDialog` pojawia się ona tak samo jak w przypadku okna komunikatu systemu Windows.

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Aby zamienić okno komunikatu systemu Windows na obiektu CTaskDialog

1. Użyj **Kreatora aplikacji MFC** , aby utworzyć aplikację MFC ze wszystkimi ustawieniami domyślnymi. Zobacz [Przewodnik: używanie nowych formantów powłoki MFC](walkthrough-using-the-new-mfc-shell-controls.md) w celu uzyskania instrukcji dotyczących sposobu otwierania Kreatora dla używanej wersji programu Visual Studio.

1. Wywołaj element *WebProject*.

1. Użyj **Eksplorator rozwiązań** , aby otworzyć plik. cpp.

1. Dodaj `#include "afxtaskdialog.h"` po liście zawiera.

1. Znajdź metodę `CMyProjectApp::InitInstance` . Wstaw następujące wiersze kodu przed `return TRUE;` instrukcją. Ten kod tworzy ciągi używane w oknie komunikatu systemu Windows lub w `CTaskDialog` .

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

1. Dodaj następujący kod po kodzie z kroku 4. Ten kod gwarantuje, że komputer użytkownika obsługuje `CTaskDialog` . Jeśli okno dialogowe nie jest obsługiwane, aplikacja wyświetli okno komunikatu systemu Windows.

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

1. Wstaw następujący kod między nawiasami po **`if`** instrukcji z kroku 5. Ten kod tworzy `CTaskDialog` .

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

1. W następnym wierszu Dodaj następujący kod. Ten kod ustawia ikonę ostrzeżenia.

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

1. W następnym wierszu Dodaj następujący kod. Ten kod wyświetla okno dialogowe zadanie.

    ```cpp
    taskDialog.DoModal();
    ```

Możesz uniknąć kroku 7, jeśli nie chcesz, `CTaskDialog` Aby wyświetlać tę samą ikonę co okno komunikatu systemu Windows. W przypadku uniknięcia tego kroku `CTaskDialog` nie ma ikony, gdy aplikacja zostanie wyświetlona.

Skompiluj i uruchom aplikację. Po rozpoczęciu aplikacja wyświetli okno dialogowe zadania.

## <a name="adding-functionality-to-the-ctaskdialog"></a>Dodawanie funkcji do obiektu CTaskDialog

Poniższa procedura przedstawia sposób dodawania funkcji do programu `CTaskDialog` , który został utworzony w poprzedniej procedurze. Przykładowy kod przedstawia sposób wykonywania określonych instrukcji na podstawie wybranych opcji użytkownika.

### <a name="to-add-functionality-to-the-ctaskdialog"></a>Aby dodać funkcjonalność do obiektu CTaskDialog

1. Przejdź do **Widok zasobów**. Jeśli nie widzisz **Widok zasobów**, możesz otworzyć ją z menu **Widok** .

1. Rozwiń **Widok zasobów** do momentu wybrania folderu **tabeli ciągów** . Rozwiń go i kliknij dwukrotnie wpis **tabeli ciągów** .

1. Przewiń w dół tabeli ciągów i Dodaj nowy wpis. Zmień identyfikator na `TEMP_LINE1` . Ustaw podpis na **wiersz polecenia 1**.

1. Dodaj kolejny nowy wpis. Zmień identyfikator na `TEMP_LINE2` . Ustaw podpis na **wiersz polecenia 2**.

1. Przejdź wstecz do projektu. cpp.

1. Po `CString emptyString;` Dodaj następujący kod:

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

1. Znajdź `taskDialog.DoModal()` instrukcję i Zastąp tę instrukcję poniższym kodem. Ten kod aktualizuje okno dialogowe zadania i dodaje nowe kontrolki:

    ```cpp
    taskDialog.SetMainInstruction(L"Warning");
    taskDialog.SetCommonButtons(
        TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);
    taskDialog.LoadCommandControls(TEMP_LINE1, TEMP_LINE2);
    taskDialog.SetExpansionArea(
        expansionInfo, collapsedLabel, expandedLabel);
    taskDialog.SetFooterText(L"This is the a small footnote to the user");
    taskDialog.SetVerificationCheckboxText(L"Remember your selection");
    ```

1. Dodaj następujący wiersz kodu, który wyświetla okno dialogowe zadanie dla użytkownika i pobiera wybór użytkownika:

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

1. Wstaw następujący kod po wywołaniu metody `taskDialog.DoModal()` . Ta sekcja kodu przetwarza dane wejściowe użytkownika:

    ```cpp
    if (taskDialog.GetVerificationCheckboxState())
    {
        // PROCESS IF the user selects the verification checkbox
    }

    switch (result)
    {
    case TEMP_LINE1:
        // PROCESS IF the first command line
        break;
    case TEMP_LINE2:
        // PROCESS IF the second command line
        break;
    case IDYES:
        // PROCESS IF the user clicks yes
        break;
    case IDNO:
        // PROCESS IF the user clicks no
        break;
    case IDCANCEL:
        // PROCESS IF the user clicks cancel
        break;
    default:
        // This case should not be hit because closing
        // the dialog box results in IDCANCEL
        break;
    }
    ```

W kodzie w kroku 9 Zastąp komentarze, które zaczynają się od `PROCESS IF` kodu, który ma zostać wykonany w określonych warunkach.

Skompiluj i uruchom aplikację. Aplikacja wyświetli okno dialogowe zadania, w którym są używane nowe kontrolki i dodatkowe informacje.

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Wyświetlanie obiektu CTaskDialog bez tworzenia obiektu obiektu CTaskDialog

Poniższa procedura pokazuje, jak wyświetlić a `CTaskDialog` bez wcześniejszego utworzenia `CTaskDialog` obiektu. Ten przykład kontynuuje poprzednią procedurę.

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Aby wyświetlić obiektu CTaskDialog bez tworzenia obiektu obiektu CTaskDialog

1. Otwórz plik moje Project. cpp, jeśli nie jest jeszcze otwarty.

1. Przejdź do nawiasu zamykającego `if (CTaskDialog::IsSupported())` instrukcji.

1. Wstaw poniższy kod bezpośrednio przed nawiasem zamykającym **`if`** instrukcji (przed **`else`** blokiem):

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

Skompiluj i uruchom aplikację. Aplikacja wyświetla dwa okna dialogowe zadań. Pierwsze okno dialogowe pochodzi z programu w **celu dodania funkcji do procedury obiektu CTaskDialog** . drugie okno dialogowe pochodzi z ostatniej procedury.

Te przykłady nie demonstrują wszystkich dostępnych opcji dla `CTaskDialog` , ale powinny pomóc Ci rozpocząć pracę. Aby uzyskać pełny opis klasy, zobacz [obiektu CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) .

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Klasa obiektu CTaskDialog](../mfc/reference/ctaskdialog-class.md)<br/>
[Obiektu CTaskDialog:: obiektu CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
