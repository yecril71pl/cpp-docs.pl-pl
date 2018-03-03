---
title: "Wskazówki: Dodawanie obiektu CTaskDialog do aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3e9e75cb705bb4497cfefa350c2b34eca75cf2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Wskazówki: dodawanie obiektu CTaskDialog do aplikacji
W tym przewodniku przedstawiono [klasy obiektu CTaskDialog](../mfc/reference/ctaskdialog-class.md) i pokazuje, jak i dodaj je do aplikacji.  
  
 `CTaskDialog` Okno dialogowe zadania zastępujący pola wiadomości Windows w [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]. `CTaskDialog` Zwiększa oryginalnego pola wiadomości i dodaje funkcjonalność. W oknie komunikatu systemu Windows nadal jest obsługiwany w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Wersje systemu Windows starszych niż [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)] nie obsługują `CTaskDialog`. Jeśli chcesz wyświetlić komunikat do użytkownika, który uruchamia aplikację we wcześniejszej wersji systemu Windows należy zaprogramować opcji w oknie dialogowym alternatywnych. Można użyć metody statycznej [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) do określenia w czasie wykonywania, czy komputer użytkownika można wyświetlić `CTaskDialog`. Ponadto `CTaskDialog` jest dostępna tylko po utworzeniu aplikacji z biblioteką Unicode.  
  
 `CTaskDialog` Obsługuje kilka opcjonalne elementy do zbierania i wyświetlania informacji. Na przykład `CTaskDialog` można wyświetlać polecenia łącza, dostosowane przycisków ikon niestandardowych i stopki. `CTaskDialog` Ma również kilka metod, które pozwalają zbadać stanu zadania okno dialogowe, aby ustalić, jakie elementy opcjonalne wybrany przez użytkownika.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
- [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)]  
  
- [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Zastąpienie obiektu CTaskDialog okno komunikatu systemu Windows  
 W poniższej procedurze przedstawiono użycie najprostsze `CTaskDialog`, który ma zastąpić pole komunikatów systemu Windows. W tym przykładzie zmienia także ikon skojarzonych z zadań — okno dialogowe. Zmiana ikony sprawia, że `CTaskDialog` są wyświetlane takie same jak pole komunikatów systemu Windows.  
  
#### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Aby zastąpić obiektu CTaskDialog okno komunikatu systemu Windows  
  
1.  Utwórz nowy projekt aplikacji MFC z ustawieniami domyślnymi. Wywołać ją `MyProject`.  
  
2.  Użyj **Eksploratora rozwiązań** można otworzyć pliku MyProject.cpp.  
  
3.  Dodaj `#include "afxtaskdialog.h"` po zawiera listę.  
  
4.  Find — metoda `CMyProjectApp::InitInstance`. Wstaw następujące wiersze kodu przed `return TRUE;` instrukcji. Ten kod tworzy ciągów, których używamy w obu pola wiadomości Windows lub w `CTaskDialog`.  
  
 ```  
    CString message("My message to the user");

    CString dialogTitle("My Task Dialog title");

    CString emptyString;  
 ```  
  
5.  Dodaj następujący kod po kodzie z kroku 4. Ten kod gwarantuje, że na komputerze użytkownika obsługuje `CTaskDialog`. Okno dialogowe nie jest obsługiwana, aplikacja wyświetla komunikat Windows zamiast tego.  
  
 ```  
    if (CTaskDialog::IsSupported())  
 {  
 
 }  
    else 
 {  
    AfxMessageBox(message);

 }  
 ```  
  
6.  Wstaw następujący kod w nawiasie po `if` instrukcji z kroku 5. Ten kod tworzy `CTaskDialog`.  
  
 ```  
    CTaskDialog taskDialog(message,
    emptyString,
    dialogTitle,
    TDCBF_OK_BUTTON);

 ```  
  
7.  W następnym wierszu dodaj następujący kod. Ten kod ustawia ikonę ostrzeżenia.  
  
 ```  
    taskDialog.SetMainIcon(TD_WARNING_ICON);

 ```  
  
8.  W następnym wierszu dodaj następujący kod. Ten kod wyświetla okno dialogowe zadania.  
  
 ```  
    taskDialog.DoModal();

 ```  
  
 Krok 7 można pominąć, jeśli nie chcesz `CTaskDialog` do tego samego ikona jest wyświetlana jako pole komunikatów systemu Windows. W przypadku pominięcia tego kroku `CTaskDialog` ma bez ikony, gdy aplikacja wyświetla go.  
  
 Kompilowanie i uruchamianie aplikacji. Aplikacja wyświetla okno dialogowe zadania po jego uruchomieniu.  
  
## <a name="adding-functionality-to-the-ctaskdialog"></a>Dodawanie funkcji do obiektu CTaskDialog  
 Poniższa procedura przedstawia sposób dodawania funkcji do `CTaskDialog` utworzoną w poprzedniej procedurze. Przykładowy kod przedstawia sposób wykonywania szczegółowe instrukcje na podstawie wybranych przez użytkownika.  
  
#### <a name="to-add-functionality-to-the-ctaskdialog"></a>Dodawanie funkcji do obiektu CTaskDialog  
  
1.  Przejdź do **widok zasobów**. Jeśli nie widzisz **widok zasobów**, możesz otworzyć go z **widoku** menu.  
  
2.  Rozwiń węzeł **widok zasobów** do czasu możesz wybrać **tabeli ciągów** folderu. Rozwiń ją, a następnie kliknij dwukrotnie ikonę **tabeli ciągów** wpisu.  
  
3.  Przewiń w dół tabeli ciągów i Dodaj nowy wpis. Zmień identyfikator do `TEMP_LINE1`. Ustaw podpis **1 wiersz polecenia**.  
  
4.  Dodaj nowy wpis innego. Zmień identyfikator do `TEMP_LINE2`. Ustaw podpis **2 wiersza polecenia**.  
  
5.  Przejdź z powrotem do MyProject.cpp.  
  
6.  Po `CString emptyString;`, Dodaj następujący kod:  
  
 ```  
    CString expandedLabel("Hide extra information");

    CString collapsedLabel("Show extra information");

    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");

 ```  
  
7.  Znajdź `taskDialog.DoModal()` instrukcji i Zastąp następujący kod tej instrukcji. Ten kod aktualizuje okno dialogowe zadania i dodaje nowe kontrolki:  
  
 ```  
    taskDialog.SetMainInstruction(L"Warning");

 taskDialog.SetCommonButtons(TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);

    taskDialog.LoadCommandControls(TEMP_LINE1,
    TEMP_LINE2);

    taskDialog.SetExpansionArea(expansionInfo,
    collapsedLabel,
    expandedLabel);

    taskDialog.SetFooterText(L"This is the a small footnote to the user");

    taskDialog.SetVerificationCheckboxText(L"Remember your selection");

 ```  
  
8.  Dodaj następujący wiersz kodu, który wyświetla użytkownikowi okno dialogowe zadania i pobiera określonego przez użytkownika:  
  
 ```  
    INT_PTR result = taskDialog.DoModal();

 ```  
  
9. Wstaw następujący kod po wywołaniu `taskDialog.DoModal()`. Ta sekcja kod przetwarza dane wejściowe użytkownika:  
  
 ```  
    if (taskDialog.GetVerificationCheckboxState())  
 { *// PROCESS IF the user selects the verification checkbox   
 }  
 
    switch (result)  
 {  
    case TEMP_LINE1: *// PROCESS IF the first command line  
    break; 
    case TEMP_LINE2: *// PROCESS IF the second command line  
    break; 
    case IDYES: *// PROCESS IF the user clicks yes  
    break; 
    case IDNO: *// PROCESS IF the user clicks no  
    break; 
    case IDCANCEL: *// PROCESS IF the user clicks cancel  
    break; 
    default: *// This case should not be hit because closing the dialog box results in IDCANCEL  
    break; 
 }  
 ```  
  
 W kodzie w kroku 9 Zastąp komentarze zaczynające się z procesu, jeśli kod, który będzie wykonywany w określonych warunkach.  
  
 Kompilowanie i uruchamianie aplikacji. Aplikacja wyświetla okno dialogowe zadania, które są używane nowe formanty i dodatkowe informacje.  
  
## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Wyświetlanie obiektu CTaskDialog bez tworzenia obiektu obiektu CTaskDialog  
 Poniższa procedura przedstawia sposób wyświetlania `CTaskDialog` bez tworzenia `CTaskDialog` obiektu. W tym przykładzie nadal poprzedniej procedury.  
  
#### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Aby wyświetlić obiektu CTaskDialog bez tworzenia obiektu obiektu CTaskDialog  
  
1.  Otwórz plik MyProject.cpp, jeśli nie jest jeszcze otwarta.  
  
2.  Przejdź do nawiasu zamykającego dla `if (CTaskDialog::IsSupported())` instrukcji.  
  
3.  Wstaw następujący kod bezpośrednio przed zamykającym nawiasem `if` instrukcji (przed `else` blok):  
  
 ```  
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
    L"Error",
    L"New Title",
    TEMP_LINE1,
    TEMP_LINE2);

 ```  
  
 Kompilowanie i uruchamianie aplikacji. Aplikacja wyświetla okno dialogowe dwa zadania. Pierwszym oknie dialogowym jest od do dodawania funkcji do procedury obiektu CTaskDialog; drugie okno dialogowe pochodzi z poprzedniej procedurze.  
  
 W tych przykładach pokazano nie wszystkie opcje dostępne dla `CTaskDialog`, ale powinien ułatwiające rozpoczęcie pracy. Zobacz [klasy obiektu CTaskDialog](../mfc/reference/ctaskdialog-class.md) pełen opis klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Klasa obiektu CTaskDialog](../mfc/reference/ctaskdialog-class.md)   
 [CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)

