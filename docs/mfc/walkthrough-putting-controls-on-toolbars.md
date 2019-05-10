---
title: 'Przewodnik: Umieszczanie formantów na paskach narzędzi'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: f3e4653d1be2f4a1830288ba724d20ddb7610958
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558156"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Przewodnik: Umieszczanie formantów na paskach narzędzi

W tym artykule opisano sposób dodawania przycisku paska narzędzi, który zawiera formant Windows, na pasku narzędzi. W MFC, musi być przycisku paska narzędzi [klasa CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)-pochodne klasy, na przykład [klasa CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [klasa CMFCToolBarEditBoxButton](../mfc/reference/cmfctoolbareditboxbutton-class.md), [Klasa CMFCDropDownToolbarButton](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), lub [klasa CMFCToolBarMenuButton](../mfc/reference/cmfctoolbarmenubutton-class.md).

## <a name="adding-controls-to-toolbars"></a>Dodawanie formantów na paskach narzędzi

Aby dodać formant do paska narzędzi, wykonaj następujące kroki:

1. Zarezerwuj identyfikator zasobu fikcyjnego przycisku w nadrzędnej zasób paska narzędzi. Aby uzyskać więcej informacji o tym, jak utworzyć przyciski, za pomocą **Edytor paska narzędzi** w programie Visual Studio, zobacz [Edytor paska narzędzi](../windows/toolbar-editor.md) artykułu.

1. Zarezerwuj obraz paska narzędzi (ikonę przycisku) przycisku w wszystkich map bitowych paska narzędzi nadrzędnej.

1. Programu obsługi wiadomości, która przetwarza `AFX_WM_RESETTOOLBAR` wiadomości, wykonaj następujące czynności:

   1. Utworzyć formant przycisku przy użyciu `CMFCToolbarButton`-klasy pochodnej.

   1. Zamień zastępczy przycisk nowego formantu za pomocą [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Można skonstruować obiekt przycisku na stosie, ponieważ `ReplaceButton` kopiuje obiekt przycisku, a następnie przechowuje kopię.

> [!NOTE]
>  Włączenie dostosowania w aplikacji może być konieczne zresetować na pasku narzędzi, za pomocą **resetowania** znajdujący się na **pasków narzędzi** karcie **Dostosuj** okno dialogowe, aby zobaczyć Zaktualizowano kontrolki w aplikacji po ponownej kompilacji. Stan paska narzędzi jest zapisywany w rejestrze systemu Windows i informacje rejestru jest ładowany i stosowane po `ReplaceButton` metody jest wykonywane podczas uruchamiania aplikacji.

## <a name="toolbar-controls-and-customization"></a>Dostosowywanie i formanty paska narzędzi

**Polecenia** karcie **Dostosuj** okno dialogowe zawiera listę poleceń, które są dostępne w aplikacji. Domyślnie **Dostosuj** okno dialogowe przetwarza menu aplikacji i tworzy listę przycisków na pasku narzędzi Standardowy w każdej kategorii menu. Aby zachować rozszerzone funkcje, które zapewniają formanty paska narzędzi, należy zastąpić przycisk na pasku narzędzi Standardowy kontrolki niestandardowej w **Dostosuj** okno dialogowe.

Po włączeniu dostosowywania, Utwórz **Dostosuj** okno dialogowe programu obsługi dostosowywania `OnViewCustomize` przy użyciu [klasa CMFCToolBarsCustomizeDialog](../mfc/reference/cmfctoolbarscustomizedialog-class.md) klasy. Przed wyświetleniem **Dostosuj** okno dialogowe, wywołując [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), wywołaj [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) zastąpić przycisk standardowy nowego formantu.

## <a name="example-creating-a-find-combo-box"></a>Przykład: Tworzenie pola kombi Znajdź

W tej sekcji opisano sposób tworzenia **znaleźć** formant pola kombi, pojawi się na pasku narzędzi, który zawiera ciągi wyszukiwania ostatnio używane. Użytkownik może wpisać ciąg w kontrolce a następnie naciśnij klawisz enter, aby wyszukać dokument lub naciśnij klawisz ESC, aby ponownie ustawić fokus na głównej ramki. W tym przykładzie założono, że dokument jest wyświetlany w [klasa CEditView](../mfc/reference/ceditview-class.md)-pochodnych widoku.

### <a name="creating-the-find-control"></a>Tworzenie kontrolki wyszukiwania

Najpierw utwórz **znaleźć** formant pola kombi:

1. Dodaj przycisk i polecenia do zasobów aplikacji:

   1. Zasoby aplikacji, należy dodać nowy przycisk za pomocą `ID_EDIT_FIND` identyfikator polecenia do paska narzędzi aplikacji i mapy bitowe, wszelkie skojarzone z na pasku narzędzi.

   1. Utwórz nowy element menu przy użyciu `ID_EDIT_FIND` polecenia identyfikatora.

   1. Dodaj nowy ciąg "Wyszukiwanie text\nFind" do tabeli ciągów i przypisz mu `ID_EDIT_FIND_COMBO` polecenia identyfikatora. Ten identyfikator będzie używany jako identyfikator polecenia **znaleźć** przycisk pola kombi.

        > [!NOTE]
        > Ponieważ `ID_EDIT_FIND` jest standardowe polecenie, które są przez nią przetwarzane `CEditView`, nie należy implementować specjalne Obsługa tego polecenia.  Jednak należy zaimplementować funkcję obsługi nowego polecenia `ID_EDIT_FIND_COMBO`.

1. Utwórz nową klasę `CFindComboBox`, pochodzącej z [klasa CComboBox](../mfc/reference/ccombobox-class.md).

1. W `CFindComboBox` klasy, Zastąp `PreTranslateMessage` metodę wirtualną. Ta metoda umożliwi pole kombi, aby przetworzyć [przetłumaczyła](/windows/desktop/inputdev/wm-keydown) wiadomości. Jeśli użytkownik naciśnie klawisz ESC (`VK_ESCAPE`), ponowne Ustawianie fokusa w oknie głównym ramki. Jeśli użytkownik naciśnie klawisz Enter (`VK_ENTER`), wpis w oknie głównym ramki `WM_COMMAND` wiadomość, która zawiera `ID_EDIT_FIND_COMBO` polecenia identyfikatora.

1. Utwórz klasę dla **znaleźć** przycisk pola kombi, pochodzące z [klasa CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). W tym przykładzie jest on nazwany `CFindComboButton`.

1. Konstruktor obiektu `CMFCToolbarComboBoxButton` przyjmuje trzy parametry: Identyfikator polecenia przycisku, indeks obrazu przycisku i style pola kombi. Ustaw następujące parametry w następujący sposób:

   1. Przekaż `ID_EDIT_FIND_COMBO` jako identyfikator polecenia.

   1. Użyj [CCommandManager::GetCmdImage](reference/internal-classes.md) z `ID_EDIT_FIND` uzyskać indeks obrazu.

   1. Aby uzyskać listę style pola kombi dostępne, zobacz [style pola kombi](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

1. W `CFindComboButton` klasy, Zastąp `CMFCToolbarComboBoxButton::CreateCombo` metody. W tym miejscu należy utworzyć `CFindComboButton` obiektu i zwraca wskaźnik do niego.

1. Użyj [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) makra w celu uzyskania trwałego przycisk kombi. Menedżer obszar roboczy ładuje i automatycznie zapisuje stan przycisku w rejestrze systemu Windows.

1. Implementowanie `ID_EDIT_FIND_COMBO` obsługi w danym widoku dokumentu. Użyj [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) z `ID_EDIT_FIND_COMBO` pobranie wszystkich **znaleźć** przyciskami pola kombi. Ze względu na dostosowanie może być kilka kopii przycisk za pomocą tego samego Identyfikatora polecenia.

1. W `ID_EDIT_FIND` obsługi wiadomości `OnFind`, użyj [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) do określenia, czy polecenie find została wysłana z **znaleźć** przycisk pola kombi. Jeśli tak, Znajdź tekst i dodaj ciąg wyszukiwania do pola kombi.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Dodawanie kontrolki wyszukiwania do głównego paska narzędzi

Aby dodać przycisk pola kombi na pasku narzędzi, wykonaj następujące kroki:

1. Implementowanie `AFX_WM_RESETTOOLBAR` obsługi wiadomości `OnToolbarReset` w oknie głównym ramki.

    > [!NOTE]
    > Struktura wysyła tę wiadomość w oknie głównym ramki, gdy pasek narzędzi jest inicjowany podczas uruchamiania aplikacji lub pasek narzędzi jest resetowany podczas dostosowywania. W obu przypadkach należy zastąpić przycisk na pasku narzędzi Standardowy z niestandardowym **znaleźć** przycisk pola kombi.

1. W `AFX_WM_RESETTOOLBAR` obsługi, Sprawdź identyfikator narzędzi, to znaczy, *WPARAM* AFX_WM_RESETTOOLBAR wiadomości. Jeśli identyfikator narzędzi jest równa pasek narzędzi, który zawiera **znaleźć** przycisk pola kombi, wywołanie [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) zastąpić **znaleźć** przycisku (oznacza to, przycisk z poleceniem o identyfikatorze `ID_EDIT_FIND)` z `CFindComboButton` obiektu.

    > [!NOTE]
    > Można skonstruować `CFindComboBox` obiektów na stosie, ponieważ `ReplaceButton` kopiuje obiekt przycisku, a następnie przechowuje kopię.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Dodawanie kontrolki wyszukiwania do okna dialogowego Dostosowywanie

W obsłudze dostosowywania `OnViewCustomize`, wywołaj [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) zastąpić **znaleźć** przycisku (oznacza to, że przycisk z poleceniem o identyfikatorze `ID_EDIT_FIND`) z `CFindComboButton` obiektu.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../mfc/hierarchy-chart.md)<br/>
[Klasy](../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Klasa CMFCToolBarsCustomizeDialog](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
