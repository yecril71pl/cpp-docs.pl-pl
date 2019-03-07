---
title: Edytor menu (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: 0681cc0a0d93d78633dd5488defaa0e9db55b1c6
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563137"
---
# <a name="menu-editor-c"></a>Edytor menu (C++)

Menu umożliwiają organizuje polecenia w sposób logiczny i łatwe do znalezienia. Za pomocą **Edytor Menu**, możesz utworzyć i menu edycji, przez który ściśle współpracuje bezpośrednio z paska menu podobny do jednego, gotowych aplikacji.

> [!TIP]
> Podczas korzystania z **Edytor Menu**, w wielu przypadkach możesz kliknąć prawym przyciskiem myszy, aby wyświetlić menu rozwijane z najczęściej używanymi poleceniami. Dostępne polecenia zależą od tego, wskaźnik wskazuje na.

## <a name="how-to"></a>Instrukcje

**Edytor Menu** umożliwia:

### <a name="to-create-a-standard-menu"></a>Aby utworzyć menu standardowe

1. Przejdź do menu **widoku** > **widok zasobów** i kliknij prawym przyciskiem myszy **Menu** nagłówka. Wybierz **Dodaj zasób**, następnie **Menu**.

1. Wybierz **nowy element** pole (prostokąt, który zawiera *typu w tym miejscu*) na pasku menu.

   ![Pole nowego elementu w edytorze menu](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **Nowy element** okno

1. Na przykład, wpisz nazwę nowego menu, *pliku*.

   Można wpisać tekst, który jest dostępny w **Edytor Menu** i **podpis** pole w [okno właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości nowego menu w jednej z tych lokalizacji.

   Po wyrażono nowe menu nazwę na pasku menu, okno nowy element przenosi się z prawej strony (co pozwala innym menu dodawania), a inny nowy element zostanie otwarte okno poniżej pierwszej menu, polecenia menu można dodać do niego.

   ![Rozwinięty okno nowy element](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   **Nowy element** pole z fokusem przesunięte po wpisaniu nazwy menu

   > [!NOTE]
   > Aby utworzyć pojedynczą pozycją menu na pasku menu, ustaw **okno podręczne** właściwości **False**.

### <a name="to-create-a-submenu"></a>Aby utworzyć podmenu

1. Wybierz polecenie menu, dla której chcesz utworzyć podmenu.

1. W **nowy element** pole, które pojawia się po prawej stronie, wpisz nazwę nowego polecenia menu. To nowe polecenie pojawią się najpierw z menu podmenu.

1. Dodawanie dodatkowych poleceń do menu podmenu.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>Aby wstawić nowego menu między istniejącymi menu

Wybierz istniejące nazwy menu i naciśnij klawisz **Wstaw** klucza, lub kliknij prawym przyciskiem myszy pasek menu i wybierz pozycję **Wstaw nowy**.

   **Nowy element** pole jest wstawiany przed wybranego elementu.

### <a name="to-add-commands-to-a-menu"></a>Aby dodać polecenia do menu

1. Tworzenie menu. Następnie wybierz nazwę menu, na przykład **pliku**.

   Każde menu będzie Rozwiń i udostępnić pole nowego elementu w przypadku poleceń. Na przykład można dodać polecenia **New**, **Otwórz**, i **Zamknij** do **pliku** menu.

1. W polu Nowy element wpisz nazwę nowego polecenia menu.

   > [!NOTE]
   > Można wpisać tekst, który jest dostępny w **Edytor Menu** i **podpis** pole w [okno właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości nowego menu w jednej z tych lokalizacji.

   > [!TIP]
   > Można zdefiniować mnemoników klucza (klawisz dostępu), który umożliwia użytkownikowi wybranie polecenia menu. Wpisz znak (`&`) przed literę, aby określić, że mnemonik. Użytkownik może wybrać polecenie menu, wpisując tę literę.

1. W **właściwości** okna, wybierz opcję menu polecenie Właściwości, które są stosowane. Aby uzyskać więcej informacji, zobacz [właściwości poleceń Menu](../windows/menu-command-properties.md).

1. W **wiersza** pole w **właściwości** okna, wpisz ciąg monitu mają być wyświetlane na pasku stanu aplikacji.

   W tym kroku tworzy wpis w tabeli ciągów za pomocą tego samego identyfikatora zasobu jako polecenia menu, który został utworzony.

   > [!NOTE]
   > Monity można stosować tylko do elementów menu za pomocą **okno podręczne** właściwość **True**. Na przykład elementy menu najwyższego poziomu może mieć monitów, jeśli mają one elementy menu podrzędne. Celem **monitu** jest wskazanie, co się stanie, jeśli użytkownik wybierze element menu.

1. Naciśnij klawisz **Enter** można ukończyć polecenia menu.

   Nowe pole elementu jest zaznaczone, aby można było utworzyć menu dodatkowych poleceń.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>Aby wybrać wiele polecenia menu, aby uruchomić operacje zbiorcze, takie jak usuwanie lub zmiana właściwości

Przytrzymując naciśnięty **Ctrl** klucza, wybierz menu lub poleceń z podmenu ma.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Przenoszenie i kopiowanie menu i poleceń menu

- Użyj metody przeciągania i upuszczania:

   1. Przeciągnij lub skopiuj element, który chcesz przenieść do:

      - Nowa lokalizacja bieżącego menu.

      - Inne menu. Możesz przejść do innych menu, przeciągając wskaźnik myszy nad nimi.

   1. Pomijać polecenia menu, gdy prowadnicę wstawiania pokazuje pozycji, które chcesz.

- Użyj polecenia menu skrótów:

   1. Kliknij prawym przyciskiem myszy jeden lub więcej menu lub poleceń menu, a następnie wybierz **Wytnij** (Aby przenieść) lub **kopiowania**.

   1. Jeśli przenosisz elementy do menu inny zasób lub pliku skryptu zasobu, [otwórz go w innym oknie](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. Wybierz pozycję menu lub polecenia menu, który chcesz przenieść lub skopiować do.

   1. Z menu skrótów wybierz polecenie **Wklej**. Element przenoszone lub kopiowane jest umieszczany przed elementem, którą wybierzesz.

> [!NOTE]
> Można również przeciągnąć, skopiuj i Wklej do innych menu w innych oknach menu.

### <a name="to-delete-a-menu-or-menu-command"></a>Aby usunąć menu lub poleceń menu

Kliknij prawym przyciskiem myszy polecenie lub nazwy menu, a następnie wybierz **Usuń**.

> [!NOTE]
> Podobnie można użyć menu skrótów do wykonywania innych akcji, takich jak kopiowanie, wycinanie, wklejanie, Wstaw nowy, Wstaw Separator edycji identyfikatorów Pokaż jako okno podręczne, sprawdź mnemonik itp.

## <a name="pop-up-menus"></a>Menu wyskakujące

[Menu wyskakujące](../mfc/menus-mfc.md) wyświetlania często używanych poleceń. Mogą to być kontekstowo lokalizacji wskaźnika. Używanie wyskakujących menu w aplikacji wymaga tworzenia samo menu, a następnie nawiąż połączenie z kodu aplikacji.

Po utworzeniu zasobu menu, kod aplikacji musi załadować zasobu menu i używać [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) aby spowodować, że są wyświetlane w menu. Po użytkownik został odrzucony wyskakujących menu, wybierając poza nim lub została wybrana polecenie, funkcja zwróci. Jeśli użytkownik wybierze polecenie, komunikat tego polecenia będą wysyłane do okna, w których uchwyt został przekazany.

> [!NOTE]
> W przypadku programów biblioteki Microsoft Foundation Class (MFC) i programy, ATL, użyj **kreatorów kodu** można dołączyć poleceń menu do kodu. Aby uzyskać więcej informacji, zobacz [Dodawanie zdarzenia](../ide/adding-an-event-visual-cpp.md) i [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

- Aby utworzyć menu rozwijane, utworzyć menu z pustym tytułem, a nie zapewniają *podpis*. Następnie należy dodać polecenie menu do menu Nowy, Przenieś do pierwszego polecenia menu poniżej tytułu pustego menu z podpisem tymczasowe *typu w tym miejscu* i wpisz *podpis* i inne informacje.

   Powtórz ten proces dla innych poleceń menu w menu podręcznym i pamiętaj zapisać zasobu menu.

- Aby połączyć z menu podręcznego do aplikacji, na przykład dodać program obsługi komunikatów dla WM_CONTEXTMENU, a następnie dodaj następujący kod do obsługi komunikatów:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) przekazywane przez komunikat program obsługi jest we współrzędnych ekranu.

Zwykle podczas pracy **Edytor Menu**, zasobu menu jest wyświetlana jako pasek menu. Jednak może być zasobów menu, które są dodawane do paska menu aplikacji, podczas gdy program jest uruchomiony.

- Aby wyświetlić menu zasobu jako menu podręczne, kliknij prawym przyciskiem myszy menu, a następnie wybierz **Pokaż jako menu podręczne**.

   Ta opcja jest tylko preferencji wyświetlania i nie umożliwia modyfikowania menu.

> [!TIP]
> Aby zmienić widok paska menu, wybierz **Pokaż jako menu podręczne** ponownie. Ta akcja spowoduje usunięcie znacznika wyboru i zwraca widok paska menu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Polecenia menu](../windows/menu-command-properties.md)<br/>

<!--
[User-Interface Objects and Command IDs](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menus](../mfc/menus-mfc.md)<br/>
[Menus](https://msdn.microsoft.com/library/windows/desktop/ms646977.aspx)-->