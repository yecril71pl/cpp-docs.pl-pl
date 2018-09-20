---
title: 'Wskazówki: Dodawanie obiektu CTaskDialog do aplikacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f803af896c1bb2a0e5f58e45f4ef9f588f4e66d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420487"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Wskazówki: dodawanie obiektu CTaskDialog do aplikacji

Ten przewodnik stanowi wprowadzenie [klasa CTaskDialog](../mfc/reference/ctaskdialog-class.md) i dowiesz się, jak je dodać do swojej aplikacji.

`CTaskDialog` To okno dialogowe zadań, która zastępuje okno komunikatu Windows w systemie Windows Vista lub nowszym. `CTaskDialog` Zwiększa oryginalnego okno komunikatu i dodaje funkcjonalność. Okno komunikatu Windows nadal jest obsługiwany w programie Visual Studio.

> [!NOTE]
> Wersje Windows wcześniejsze niż Windows Vista nie obsługują `CTaskDialog`. Należy programu opcji w oknie dialogowym alternatywnego, jeśli chcesz wyświetlić komunikat dla użytkownika, który uruchomił aplikację w starszej wersji programu Windows. Można użyć statycznej metody [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) do określenia w czasie wykonywania, czy na komputerze użytkownika może wyświetlać `CTaskDialog`. Ponadto `CTaskDialog` jest dostępna tylko podczas kompilacji aplikacji za pomocą biblioteki Unicode.

`CTaskDialog` Obsługuje kilka opcjonalnych elementów do gromadzenia i wyświetlania informacji. Na przykład `CTaskDialog` może wyświetlać polecenia łącza, przyciski niestandardowe, dostosowane ikon i stopki. `CTaskDialog` Ma również kilka metod, które umożliwiają Wyślij zapytanie o stan okno dialogowe zadania, aby określić elementy opcjonalne wybranego użytkownika.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2010 lub w nowszej wersji

- Windows Vista lub nowszy

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Zastępowanie okno komunikatu Windows za pomocą obiektu CTaskDialog

W poniższej procedurze przedstawiono najbardziej podstawowe zastosowanie `CTaskDialog`, który ma zastąpić Windows okno komunikatu. W tym przykładzie zmienia się również ikon skojarzonych z okno dialogowe zadania. Zmiana ikony sprawia, że `CTaskDialog` pojawiają się taka sama jak okno komunikatu Windows.

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Aby zastąpić okno komunikatu Windows obiektu CTaskDialog

1. Utwórz nowy projekt aplikacji MFC, przy użyciu ustawień domyślnych. Wywołaj go *MyProject*.

2. Użyj **Eksploratora rozwiązań** można otworzyć pliku MyProject.cpp.

3. Dodaj `#include "afxtaskdialog.h"` po zawiera listę.

4. Znajdź metodę `CMyProjectApp::InitInstance`. Wstaw następujące wiersze kodu przed `return TRUE;` instrukcji. Ten kod tworzy ciągów, których używa w dowolnym oknie komunikatu Windows lub w `CTaskDialog`.

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

5. Dodaj następujący kod po kodzie z kroku 4. Ten kod gwarantuje, że na komputerze użytkownika obsługuje `CTaskDialog`. Okno dialogowe nie jest obsługiwana, aplikacja wyświetla okno komunikatu, Windows zamiast tego.

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

6. Wstaw następujący kod w nawiasach kwadratowych po `if` instrukcji z kroku 5. Ten kod tworzy `CTaskDialog`.

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

7. W następnym wierszu dodaj następujący kod. Ten kod ustawia ikonę ostrzeżenia.

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

8. W następnym wierszu dodaj następujący kod. Ten kod wyświetla okno dialogowe zadania.

    ```cpp
    taskDialog.DoModal();
    ```

Krok 7 można pominąć, jeśli nie chcesz `CTaskDialog` do tego samego ikona jest wyświetlana jako okno komunikatu Windows. Jeśli pominiesz ten krok `CTaskDialog` ma żadnej ikony, gdy aplikacja wyświetla je.

Skompilować i uruchomić aplikację. Aplikacja wyświetla okno dialogowe zadania po jego uruchomieniu.

## <a name="adding-functionality-to-the-ctaskdialog"></a>Dodawanie funkcji do obiektu CTaskDialog

Poniższa procedura pokazuje sposób dodawania funkcjonalności do `CTaskDialog` utworzoną w poprzedniej procedurze. Przykładowy kod przedstawia sposób wykonywania szczegółowych instrukcji, w zależności od wyborów użytkownika.

### <a name="to-add-functionality-to-the-ctaskdialog"></a>Aby dodać funkcje do obiektu CTaskDialog

1. Przejdź do **widok zasobów**. Jeśli nie widzisz **widok zasobów**, możesz go otworzyć **widoku** menu.

2. Rozwiń **widok zasobów** do momentu wybrania **tabeli ciągów** folderu. Rozwiń ją, a następnie kliknij dwukrotnie **tabeli ciągów** wpisu.

3. Przewiń w dół tabeli ciągów i Dodaj nowy wpis. Zmień identyfikator, który ma `TEMP_LINE1`. Ustaw podpis **1 wiersz polecenia**.

4. Dodaj inny nowy wpis. Zmień identyfikator, który ma `TEMP_LINE2`. Ustaw podpis **2 wiersza polecenia**.

5. Przejdź z powrotem do MyProject.cpp.

6. Po `CString emptyString;`, Dodaj następujący kod:

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

7. Znajdź `taskDialog.DoModal()` instrukcji i Zastąp następujący kod w tej instrukcji. Ten kod aktualizuje okno dialogowe zadania i dodaje nowe kontrolki:

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

8. Dodaj następujący wiersz kodu, który wyświetla okno dialogowe zadania użytkownika oraz pobiera wybranych przez użytkownika:

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

9. Wstaw następujący kod po wywołaniu `taskDialog.DoModal()`. Ta sekcja kodu przetwarza dane wejściowe użytkownika:

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

W kodzie w kroku 9 Zastąp komentarzy rozpoczynających się Jeśli proces z kodem, który ma zostać wykonany w określonych warunkach.

Skompilować i uruchomić aplikację. Aplikacja wyświetla okno dialogowe zadania, który korzysta z nowych kontrolek i dodatkowe informacje.

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Wyświetlanie obiektu CTaskDialog bez tworzenia obiektu CTaskDialog

Poniższa procedura pokazuje sposób wyświetlania `CTaskDialog` bez tworzenia `CTaskDialog` obiektu. Ten przykład jest kontynuacją poprzednich procedur.

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Aby wyświetlić obiektu CTaskDialog bez tworzenia obiektu CTaskDialog

1. Otwórz plik MyProject.cpp, jeśli nie jest już otwarty.

2. Przejdź do nawiasu zamykającego dla `if (CTaskDialog::IsSupported())` instrukcji.

3. Wstaw następujący kod bezpośrednio przed zamykającym nawiasem `if` — instrukcja (przed `else` bloku):

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

Skompilować i uruchomić aplikację. Aplikacja wyświetla dwa zadania, okno dialogowe. Pierwsze okno dialogowe obejmuje adresy od z do dodawania funkcji do procedury CTaskDialog; drugie okno dialogowe pochodzi z poprzedniej procedurze.

Przykłady te pokazują nie wszystkie dostępne opcje `CTaskDialog`, ale powinny pomóc Ci rozpocząć pracę. Zobacz [klasa CTaskDialog](../mfc/reference/ctaskdialog-class.md) pełny opis klasy.

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Klasa CTaskDialog](../mfc/reference/ctaskdialog-class.md)<br/>
[CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
