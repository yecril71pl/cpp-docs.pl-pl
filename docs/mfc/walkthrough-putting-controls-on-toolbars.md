---
title: 'Wskazówki: Umieszczanie formantów na paskach narzędzi | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c134431500ed3e7b2b2229ea5b4b3da7cac6fa48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385086"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Wskazówki: umieszczanie formantów na paskach narzędzi
W tym temacie opisano sposób dodawania przycisku paska narzędzi, który zawiera kontrolki systemu Windows do paska narzędzi. W MFC, musi być przycisku paska narzędzi [klasy CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)-pochodnej klasy, na przykład [klasy CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [klasy CMFCToolBarEditBoxButton](../mfc/reference/cmfctoolbareditboxbutton-class.md), [Klasy CMFCDropDownToolbarButton](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), lub [CMFCToolBarMenuButton klasy](../mfc/reference/cmfctoolbarmenubutton-class.md).  
  
## <a name="adding-controls-to-toolbars"></a>Dodawanie formantów na paskach narzędzi  
 Aby dodać kontrolkę do paska narzędzi, wykonaj następujące kroki:  
  
1.  Zarezerwować Identyfikatora fikcyjnego zasobu dla przycisku w zasobie nadrzędnym paska narzędzi. Aby uzyskać więcej informacji na temat tworzenia przycisków w edytorze paska narzędzi w programie Visual Studio, zobacz [paska narzędzi edytora](../windows/toolbar-editor.md) tematu.  
  
2.  Zarezerwować obraz paska narzędzi (przycisk ikona) dla przycisku w wszystkich map bitowych nadrzędne paska narzędzi.  
  
3.  Programu obsługi wiadomości, który przetwarza `AFX_WM_RESETTOOLBAR` wiadomości, wykonaj następujące czynności:  
  
    1.  Skonstruować za pomocą formantu przycisku `CMFCToolbarButton`-klasy.  
  
    2.  Zamień przy użyciu nowego formantu zastępczego przycisk [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Można utworzyć obiektu przycisku na stosie, ponieważ `ReplaceButton` kopiuje obiekt przycisku i przechowuje kopię.  
  
> [!NOTE]
>  Włączenie dostosowania w aplikacji może być konieczne zresetować za pomocą narzędzi **zresetować** znajdującego się na **paski narzędzi** karcie **Dostosuj** okno dialogowe, aby wyświetlić zaktualizowany formant w aplikacji po ponownej kompilacji. Stan paska narzędzi jest zapisywany w rejestrze systemu Windows, a informacje rejestru jest załadowany i zastosowane po `ReplaceButton` metody jest wykonywany podczas uruchamiania aplikacji.  
  
## <a name="toolbar-controls-and-customization"></a>Dostosowywanie i formanty paska narzędzi  
 **Polecenia** karcie **Dostosuj** okno dialogowe zawiera listę poleceń, które są dostępne w aplikacji. Domyślnie **Dostosuj** okno dialogowe przetwarza menu aplikacji i tworzy listę przycisków standardowym pasku narzędzi w każdej kategorii menu. Aby zachować rozszerzoną funkcjonalność zapewniają formanty paska narzędzi, należy zastąpić przycisk standardowym pasku narzędzi kontrolki niestandardowej w **Dostosuj** okno dialogowe.  
  
 Po włączeniu dostosowania tworzenia **Dostosuj** okno dialogowe w obsłudze dostosowania `OnViewCustomize` za pomocą [klasy CMFCToolBarsCustomizeDialog](../mfc/reference/cmfctoolbarscustomizedialog-class.md) klasy. Przed wyświetleniem **Dostosuj** okno dialogowe, wywołując [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), wywołaj [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) zastąpić Standardowa przycisk Nowy formant.  
  
## <a name="example-creating-a-find-combo-box"></a>Przykład: Tworzenie pola kombi Znajdź  
 W tej sekcji opisano sposób tworzenia `Find` kontrolki pola kombi jest wyświetlana na pasku narzędzi i zawiera ciągi wyszukiwania ostatnio używane. Użytkownika można wpisać ciąg w formancie i następnie naciśnij klawisz enter, aby wyszukać dokument lub naciśnij klawisz ESC, aby powrócić do ramki głównej fokus. W tym przykładzie przyjęto założenie, że dokument jest wyświetlany w [klasy CEditView](../mfc/reference/ceditview-class.md)-pochodnych widoku.  
  
### <a name="creating-the-find-control"></a>Tworzenie formantu Znajdź  
 Najpierw utwórz `Find` kontrolki pola kombi:  
  
1.  Dodawanie przycisku i polecenia do zasobów aplikacji:  
  
    1.  W zasoby aplikacji, należy dodać nowy przycisk z `ID_EDIT_FIND` identyfikator polecenia do paska narzędzi w aplikacji i wszelkich map bitowych skojarzone z paska narzędzi.  
  
    2.  Utwórz nowy element menu identyfikatora id_edit_find — polecenie  
  
    3.  Dodaj nowy ciąg "Odnaleźć text\nFind" do tabeli ciągów i przypisz go `ID_EDIT_FIND_COMBO` polecenia identyfikatora. Ten identyfikator będzie używany jako identyfikator polecenia `Find` przycisk pola kombi.  
  
        > [!NOTE]
        >  Ponieważ `ID_EDIT_FIND` jest standardowe polecenia, które są przetwarzane przez `CEditView`, nie należy do implementacji specjalne obsługi dla tego polecenia.  Jednak należy zaimplementować obsługę nowego polecenia `ID_EDIT_FIND_COMBO`.  
  
2.  Utwórz nową klasę `CFindComboBox`, pochodną [ccombobox — klasa](../mfc/reference/ccombobox-class.md).  
  
3.  W `CFindComboBox` klasy, Zastąp `PreTranslateMessage` metoda wirtualna. Ta metoda umożliwi pole kombi, aby przetworzyć [WM_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280) wiadomości. Jeśli użytkownik naciśnie klawisz escape (`VK_ESCAPE`), zwraca fokus do głównego okna ramowego. Jeśli użytkownik naciśnie klawisz Enter (`VK_ENTER`), post do głównego okna ramowego `WM_COMMAND` komunikat, który zawiera `ID_EDIT_FIND_COMBO` polecenia identyfikatora.  
  
4.  Utwórz klasę dla `Find` przycisk pola kombi, pochodną [CMFCToolBarComboBoxButton klasy](../mfc/reference/cmfctoolbarcomboboxbutton-class.md). W tym przykładzie o nazwie `CFindComboButton`.  
  
5.  Konstruktor obiektu `CMFCToolbarComboBoxButton` przyjmuje trzy parametry: Identyfikator polecenia przycisku, indeks obrazu przycisku i styl pola kombi. Ustaw następujące parametry w następujący sposób:  
  
    1.  Przekaż `ID_EDIT_FIND_COMBO` jako identyfikator polecenia.  
  
    2.  Użyj [CCommandManager::GetCmdImage](http://msdn.microsoft.com/en-us/4094d08e-de74-4398-a483-76d27a742dca) z `ID_EDIT_FIND` uzyskać indeks obrazu.  
  
    3.  Lista style pola kombi dostępności, zobacz [style pola kombi](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).  
  
6.  W `CFindComboButton` klasy, Zastąp `CMFCToolbarComboBoxButton::CreateCombo` metody. W tym miejscu należy utworzyć `CFindComboButton` obiektu i zwraca wskaźnik do niego.  
  
7.  Użyj [implement_serial —](../mfc/reference/run-time-object-model-services.md#implement_serial) makra, aby przycisk kombi trwałych. Menedżer obszarów roboczych automatycznie ładuje i zapisuje stan przycisku w rejestrze systemu Windows.  
  
8.  Implementowanie `ID_EDIT_FIND_COMBO` obsługi w danym widoku dokumentu. Użyj [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) z `ID_EDIT_FIND_COMBO` pobranie wszystkich `Find` przyciski pola kombi. Z powodu dostosowania może istnieć wiele kopii przycisk o tym samym identyfikatorze polecenia.  
  
9. W obsłudze wiadomości id_edit_find — `OnFind`, użyj [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) ustalenie, czy polecenie find została wysłana z `Find` przycisk pola kombi. Jeśli tak, Znajdź tekst i dodaj ciąg wyszukiwania w polu kombi.  
  
### <a name="adding-the-find-control-to-the-main-toolbar"></a>Dodawanie formantu Znajdź na głównym pasku narzędzi  
 Aby dodać przycisk pola kombi na pasku narzędzi, wykonaj następujące kroki:  
  
1.  Implementowanie `AFX_WM_RESETTOOLBAR` obsługi wiadomości `OnToolbarReset` w głównego okna ramowego.  
  
    > [!NOTE]
    >  Platformę wysyła wiadomość do głównego okna ramowego podczas inicjowania podczas uruchamiania aplikacji paska narzędzi lub paska narzędzi jest resetowany podczas dostosowywania. W obu przypadkach należy zastąpić przycisk standardowym pasku narzędzi z niestandardowym `Find` przycisk pola kombi.  
  
2.  W `AFX_WM_RESETTOOLBAR` obsługi, Sprawdź identyfikator narzędzi, oznacza to, `WPARAM` z `AFX_WM_RESETTOOLBAR` wiadomości. Jeśli identyfikator narzędzi jest równa narzędzi, który zawiera `Find` przycisk pola kombi, wywołaj [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) zastąpić `Find` przycisk (to znaczy przycisk z poleceniem o identyfikatorze `ID_EDIT_FIND)` z `CFindComboButton` obiektu.  
  
    > [!NOTE]
    >  Można utworzyć `CFindComboBox` obiektu na stosie, ponieważ `ReplaceButton` kopiuje obiekt przycisku i przechowuje kopię.  
  
### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Dodawanie formantu Znajdź do okna dialogowego Dostosuj  
 W obsłudze dostosowania `OnViewCustomize`, wywołania [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) zastąpić `Find` przycisk (to znaczy przycisk z poleceniem o identyfikatorze `ID_EDIT_FIND)` z `CFindComboButton` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../mfc/hierarchy-chart.md)   
 [Klasy](../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCToolBarButton](../mfc/reference/cmfctoolbarbutton-class.md)   
 [Klasa CMFCToolBarComboBoxButton](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [Klasa CMFCToolBarsCustomizeDialog](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
