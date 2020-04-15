---
title: 'Wskazówki: umieszczanie formantów na paskach narzędzi'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 2a801e61c49301d9b8780bbf7eb77025990337ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360267"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Wskazówki: umieszczanie formantów na paskach narzędzi

W tym artykule opisano sposób dodawania przycisku paska narzędzi zawierającego kontrolkę systemu Windows do paska narzędzi. W MFC przycisk paska narzędzi musi być klasą [cmfctoolbutton](../mfc/reference/cmfctoolbarbutton-class.md)- klasa pochodna, na przykład [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton Class](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolButton Class](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)lub [CMFCToolBarMenuButton Class](../mfc/reference/cmfctoolbarmenubutton-class.md).

## <a name="adding-controls-to-toolbars"></a>Dodawanie kontrolek do pasków narzędzi

Aby dodać formant do paska narzędzi, wykonaj następujące czynności:

1. Zarezerwuj fikcyjny identyfikator zasobu dla przycisku w zasobie nadrzędnego paska narzędzi. Aby uzyskać więcej informacji na temat tworzenia przycisków przy użyciu **Edytora paska narzędzi** w programie Visual Studio, zobacz artykuł [Edytor paska narzędzi.](../windows/toolbar-editor.md)

1. Zarezerwuj obraz paska narzędzi (ikonę przycisku) dla przycisku we wszystkich mapach bitowych nadrzędnego paska narzędzi.

1. W programie obsługi wiadomości, który przetwarza `AFX_WM_RESETTOOLBAR` wiadomość, wykonaj następujące kroki:

   1. Konstruuj formant `CMFCToolbarButton`przycisku przy użyciu klasy pochodnej.

   1. Zastąp przycisk manekina nowym formancie za pomocą [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Można skonstruować obiekt przycisku na `ReplaceButton` stosie, ponieważ kopiuje obiekt przycisku i utrzymuje kopię.

> [!NOTE]
> Jeśli w aplikacji włączono dostosowywanie, może być trzeba zresetować pasek narzędzi za pomocą przycisku **Reset na** **paskach narzędzi** w oknie dialogowym **Dostosowywanie,** aby zobaczyć zaktualizowany formant w aplikacji po ponownym skompilowaniu. Stan paska narzędzi jest zapisywany w rejestrze systemu Windows, `ReplaceButton` a informacje rejestru są ładowane i stosowane po wykonaniu metody podczas uruchamiania aplikacji.

## <a name="toolbar-controls-and-customization"></a>Kontrolki i dostosowywanie paska narzędzi

Karta **Polecenia** w oknie dialogowym **Dostosowywanie** zawiera listę poleceń dostępnych w aplikacji. Domyślnie okno dialogowe **Dostosowywanie** przetwarza menu aplikacji i tworzy listę standardowych przycisków paska narzędzi w każdej kategorii menu. Aby zachować rozszerzone funkcje, które zapewniają kontrolki paska narzędzi, należy zastąpić standardowy przycisk paska narzędzi formantem niestandardowym w oknie dialogowym **Dostosowywanie.**

Po włączeniu dostosowywania, należy utworzyć okno dialogowe `OnViewCustomize` **Dostosowywanie** w programie obsługi dostosowywania przy użyciu [CMFCToolBarsCustomizeDialog Class](../mfc/reference/cmfctoolbarscustomizedialog-class.md) klasy. Przed wyświetleniem okno dialogowe Dostosowywanie przez **wywołanie** [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), call [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) to replace the standard button with the new control.

## <a name="example-creating-a-find-combo-box"></a>Przykład: Tworzenie pola kombinacji znajdź

W tej sekcji opisano sposób tworzenia kontrolki pola kombi **Znajdź,** która pojawia się na pasku narzędzi i zawiera ostatnio używane ciągi wyszukiwania. Użytkownik może wpisać ciąg w formancie, a następnie nacisnąć klawisz enter, aby przeszukać dokument, lub nacisnąć klawisz escape, aby przywrócić fokus do ramki głównej. W tym przykładzie przyjęto założenie, że dokument jest wyświetlany w widoku pochodnym [klasy CEditView.](../mfc/reference/ceditview-class.md)

### <a name="creating-the-find-control"></a>Tworzenie formantu Znajdź

Najpierw utwórz kontrolkę Pola kombi **Znajdź:**

1. Dodaj przycisk i jego polecenia do zasobów aplikacji:

   1. W zasobach aplikacji dodaj nowy `ID_EDIT_FIND` przycisk z identyfikatorem polecenia do paska narzędzi w aplikacji i do wszystkich map bitowych skojarzonych z paskiem narzędzi.

   1. Utwórz nowy element `ID_EDIT_FIND` menu o identyfikatorze polecenia.

   1. Dodaj nowy ciąg "Znajdź tekst\nZnajduj" do `ID_EDIT_FIND_COMBO` tabeli ciągów i przypisz mu identyfikator polecenia. Ten identyfikator będzie używany jako identyfikator polecenia przycisku **Znajdź** pole kombi.

        > [!NOTE]
        > Ponieważ `ID_EDIT_FIND` jest to standardowe polecenie, `CEditView`które jest przetwarzane przez program , nie są wymagane do zaimplementowania specjalnego programu obsługi dla tego polecenia.  Należy jednak zaimplementować program `ID_EDIT_FIND_COMBO`obsługi dla nowego polecenia .

1. Utwórz nową `CFindComboBox`klasę, wywodzącą się z [klasy CComboBox](../mfc/reference/ccombobox-class.md).

1. W `CFindComboBox` klasie należy zastąpić `PreTranslateMessage` metodę wirtualną. Ta metoda umożliwi pole kombi do przetwarzania [wiadomości WM_KEYDOWN.](/windows/win32/inputdev/wm-keydown) Jeśli użytkownik trafi klawisz`VK_ESCAPE`ucieczki ( ), zwróć fokus do okna ramki głównej. Jeśli użytkownik trafi klawisz`VK_ENTER`Enter ( ), opublikuj `WM_COMMAND` w oknie `ID_EDIT_FIND_COMBO` ramki głównej komunikat zawierający identyfikator polecenia.

1. Utwórz klasę dla przycisku **Znajdź** pole kombi, pochodzące z [CMFCToolBarComboBoxButton Klasy](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). W tym przykładzie nosi `CFindComboButton`nazwę .

1. Konstruktor `CMFCToolbarComboBoxButton` przyjmuje trzy parametry: identyfikator polecenia przycisku, indeks obrazu przycisku i styl pola kombi. Ustaw następujące parametry w następujący sposób:

   1. Przekaż `ID_EDIT_FIND_COMBO` jako identyfikator polecenia.

   1. Użyj [CCommandManager::GetCmdImage](reference/internal-classes.md) z, `ID_EDIT_FIND` aby uzyskać indeks obrazu.

   1. Aby uzyskać listę dostępnych stylów pól kombi, zobacz [Style pola kombi](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

1. W `CFindComboButton` klasie należy zastąpić `CMFCToolbarComboBoxButton::CreateCombo` metodę. W tym `CFindComboButton` miejscu należy utworzyć obiekt i zwrócić do niego wskaźnik.

1. Użyj [makra IMPLEMENT_SERIAL,](../mfc/reference/run-time-object-model-services.md#implement_serial) aby przycisk kombi był trwały. Menedżer obszaru roboczego automatycznie ładuje i zapisuje stan przycisku w rejestrze systemu Windows.

1. Zaimplementuj `ID_EDIT_FIND_COMBO` program obsługi w widoku dokumentu. Użyj [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) z, `ID_EDIT_FIND_COMBO` aby pobrać wszystkie **Znajdź** przyciski pola kombi. Może istnieć kilka kopii przycisku o tym samym identyfikatorze polecenia z powodu dostosowania.

1. W `ID_EDIT_FIND` programie `OnFind`obsługi komunikatów użyj [polecenia CMFCToolBar::IsLastCommandFromButton,](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) aby ustalić, czy polecenie find zostało wysłane za pomocą **przycisku** Znajdź pole kombi. Jeśli tak, znajdź tekst i dodaj ciąg wyszukiwania do pola kombi.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Dodawanie formantu Znajdź do głównego paska narzędzi

Aby dodać przycisk pola kombi do paska narzędzi, wykonaj następujące czynności:

1. Zaimplementuj `AFX_WM_RESETTOOLBAR` program obsługi `OnToolbarReset` wiadomości w oknie ramki głównej.

    > [!NOTE]
    > Struktura wysyła ten komunikat do okna ramki głównej, gdy pasek narzędzi jest inicjowany podczas uruchamiania aplikacji lub gdy pasek narzędzi jest resetowany podczas dostosowywania. W obu przypadkach należy zastąpić standardowy przycisk paska narzędzi niestandardowym przyciskiem pola kombi **Znajdź.**

1. W `AFX_WM_RESETTOOLBAR` programie obsługi sprawdź identyfikator paska narzędzi, czyli *WPARAM* komunikatu AFX_WM_RESETTOOLBAR. Jeśli identyfikator paska narzędzi jest równy identyfikatorowi paska narzędzi zawierającego przycisk Pola kombi **Znajdź,** zadzwoń do [CMFCToolBar::ReplaceButton,](../mfc/reference/cmfctoolbar-class.md#replacebutton) aby `CFindComboButton` zastąpić przycisk **Znajdź** (czyli przycisk o identyfikatorze polecenia `ID_EDIT_FIND)` z obiektem.

    > [!NOTE]
    > Można skonstruować `CFindComboBox` obiekt na stosie, ponieważ `ReplaceButton` kopiuje obiekt przycisku i utrzymuje kopię.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Dodawanie formantu Znajdowanie do okna dialogowego Dostosowywanie

W programie obsługi `OnViewCustomize`dostosowywania , wywołać [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) zastąpić **Znajdź** przycisk (czyli `ID_EDIT_FIND`przycisk `CFindComboButton` z identyfikatorem polecenia ) z obiektem.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../mfc/hierarchy-chart.md)<br/>
[Klasy](../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Klasa CMFCToolBarsCustomizeDialog](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
