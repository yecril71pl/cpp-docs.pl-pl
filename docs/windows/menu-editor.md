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
ms.openlocfilehash: f2a5f1ac63007bf44dc331e2104c6e9e5cac23da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514825"
---
# <a name="menu-editor-c"></a>Edytor menu (C++)

Menu umożliwiają rozmieszczenie poleceń w logicznym i łatwym w użyciu sposób. Za pomocą **edytora menu**można tworzyć i edytować menu, pracując bezpośrednio z paskiem menu, który jest ściśle podobny do tego w ukończonej aplikacji.

> [!TIP]
> Korzystając z **edytora menu**, w wielu przypadkach można kliknąć prawym przyciskiem myszy, aby wyświetlić menu podręczne dla często używanych poleceń. Dostępne polecenia zależą od elementów wskazywanych przez wskaźnik.

## <a name="how-to"></a>Instrukcje

**Edytor menu** umożliwia:

### <a name="to-create-a-standard-menu"></a>Aby utworzyć menu standardowe

1. Przejdź do **widoku** > menu**Widok zasobów** i kliknij prawym przyciskiem myszy nagłówek **menu** . Wybierz pozycję **Dodaj zasób**, a następnie **menu**.

1. Zaznacz pole **nowy element** (prostokąt zawierający *tekst*) na pasku menu.

   ![Pole nowego elementu w edytorze menu](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Pole **nowego elementu**

1. Wpisz nazwę nowego menu, na przykład *plik*.

   Wpisany tekst jest wyświetlany w **Edytorze menu** i w polu **podpis** w [oknie właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości nowego menu w jednej z tych lokalizacji.

   Po otrzymaniu nowego menu nazwa na pasku menu nowe pole nowego elementu zostanie przesunięte w prawo (aby umożliwić dodanie innego menu), a kolejne nowe pole nowego elementu zostanie otwarte poniżej Twojego pierwszego menu, aby można było dodać do niego polecenia menu.

   ![Rozwinięte pole nowego elementu](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   **Nowe pole elementu** z fokusem przesunięte po wpisaniu nazwy menu

   > [!NOTE]
   > Aby utworzyć menu pojedynczego elementu na pasku menu, ustaw właściwość **popup** na **false**.

### <a name="to-create-a-submenu"></a>Aby utworzyć podmenu

1. Wybierz polecenie menu, dla którego chcesz utworzyć podmenu.

1. W polu **nowy element** , który pojawia się po prawej stronie, wpisz nazwę nowego polecenia menu. To nowe polecenie pojawi się najpierw w menu podmenu.

1. Dodaj dodatkowe polecenia menu do menu podmenu.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>Aby wstawić nowe menu między istniejącymi menu

Wybierz istniejącą nazwę menu i naciśnij klawisz **INSERT** lub kliknij prawym przyciskiem myszy pasek menu i wybierz polecenie **Wstaw nowy**.

   Pole **nowy element** zostanie wstawione przed wybranym elementem.

### <a name="to-add-commands-to-a-menu"></a>Aby dodać polecenia do menu

1. Utwórz menu. Następnie wybierz nazwę menu, na przykład **plik**.

   Każde menu spowoduje rozwinięcie i udostępnienie nowego pola elementu dla poleceń. Można na przykład dodać polecenia **New**, **Open**i **Close** do menu **plik** .

1. W polu Nowy element wpisz nazwę nowego polecenia menu.

   > [!NOTE]
   > Wpisany tekst jest wyświetlany w **Edytorze menu** i w polu **podpis** w [oknie właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości nowego menu w jednej z tych lokalizacji.

   > [!TIP]
   > Można zdefiniować klawisz skrótu (klawisz dostępu), który umożliwia użytkownikowi wybranie polecenia menu. Wpisz znak handlowego "`&`i" () przed literą, aby określić go jako element. Użytkownik może wybrać polecenie menu, wpisując tę literę.

1. W oknie **Właściwości** wybierz właściwości polecenia menu, które mają zastosowanie. Aby uzyskać szczegółowe informacje, zobacz [Właściwości polecenia menu](../windows/menu-command-properties.md).

1. W polu **monit** w oknie **Właściwości** wpisz ciąg monitu, który ma być wyświetlany na pasku stanu aplikacji.

   Ten krok powoduje utworzenie wpisu w tabeli ciągów z tym samym identyfikatorem zasobu co utworzone polecenie menu.

   > [!NOTE]
   > Polecenia monitujące mogą dotyczyć tylko elementów menu z właściwością popup **równą true**. Na przykład elementy menu najwyższego poziomu mogą mieć zapytanie, czy mają elementy menu podrzędnego. W celu **wyświetlenia monitu** należy wskazać, co się stanie, jeśli użytkownik wybierze element menu.

1. Naciśnij klawisz **Enter** , aby zakończyć polecenie menu.

   Pole nowy element jest zaznaczone, aby można było tworzyć dodatkowe polecenia menu.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>Aby wybrać wiele poleceń menu do uruchamiania operacji zbiorczych, takich jak usuwanie lub zmienianie właściwości

Przytrzymując wciśnięty klawisz **Ctrl** , wybierz odpowiednie polecenia menu lub podmenu.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Aby przenosić i kopiować menu i polecenia menu

- Użyj metody przeciągania i upuszczania:

   1. Przeciągnij lub skopiuj element, do którego chcesz przenieść:

      - Nowa lokalizacja w bieżącym menu.

      - Inne menu. Możesz przechodzić do innych menu, przeciągając nad nimi wskaźnik myszy.

   1. Upuść polecenie menu, gdy prowadnica wstawiania pokazuje wybraną pozycję.

- Użyj poleceń menu skrótów:

   1. Kliknij prawym przyciskiem myszy co najmniej jedno menu lub polecenia menu, a następnie wybierz polecenie Wytnij (aby przenieść) lub **Kopiuj**.

   1. Jeśli przenosisz elementy do innego zasobu menu lub pliku skryptu zasobu, [Otwórz go w innym oknie](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. Wybierz pozycję menu lub polecenia menu, do którego chcesz przenieść lub skopiować.

   1. Z menu skrótów wybierz polecenie **Wklej**. Przeniesiony lub skopiowany element zostanie umieszczony przed zaznaczonym elementem.

> [!NOTE]
> Możesz również przeciągać, kopiować i wklejać do innych menu w innych oknach menu.

### <a name="to-delete-a-menu-or-menu-command"></a>Aby usunąć menu lub polecenie menu

Kliknij prawym przyciskiem myszy nazwę menu lub polecenie, a następnie wybierz polecenie **Usuń**.

> [!NOTE]
> Analogicznie, możesz użyć menu skrótów, aby wykonać inne czynności, takie jak kopiowanie, wycinanie, wklejanie, wstawianie nowych, wstawianie separatora, edytowanie identyfikatorów, wyświetlanie jako wyskakujące okienka, sprawdzanie symboli itp.

## <a name="pop-up-menus"></a>Menu podręczne

[Menu podręczne](../mfc/menus-mfc.md) wyświetla często używane polecenia. Mogą być kontekstowe jako poufne dla lokalizacji wskaźnika. Korzystanie z menu podręcznych w aplikacji wymaga skompilowania menu, a następnie połączenia go z kodem aplikacji.

Po utworzeniu zasobu menu kod aplikacji musi załadować zasób menu i użyć [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) , aby spowodować wyświetlenie menu. Gdy użytkownik odrzuci menu wyskakujące, zaznaczając go poza nim lub zaznaczył polecenie, ta funkcja zwróci wartość. Jeśli użytkownik wybierze polecenie, ten komunikat polecenia zostanie wysłany do okna, którego dojście zostało przesłane.

> [!NOTE]
> W przypadku programów biblioteki Microsoft Foundation Class (MFC) i programów ATL Użyj **kreatorów kodu** , aby podłączyć polecenia menu do kodu. Aby uzyskać więcej informacji, zobacz [Dodawanie zdarzenia](../ide/adding-an-event-visual-cpp.md) i [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

- Aby utworzyć menu podręczne, Utwórz menu z pustym tytułem i nie podawanie *podpisu*. Następnie dodaj polecenie menu do nowego menu, przejdź do pierwszego polecenia menu poniżej pustego tytułu menu z podpisem tymczasowym *Wpisz tutaj* i wpisz *podpis* i inne informacje.

   Powtórz ten proces dla wszystkich innych poleceń menu w menu podręcznym i pamiętaj, aby zapisać zasób menu.

- Aby połączyć menu podręczne do aplikacji, na przykład Dodaj procedurę obsługi komunikatów dla WM_CONTEXTMENU, a następnie Dodaj następujący kod do programu obsługi komunikatów:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) , który został przesłany przez procedurę obsługi komunikatów, ma współrzędne ekranu.

Zwykle podczas pracy w **Edytorze menu**zasób menu jest wyświetlany jako pasek menu. Mogą jednak znajdować się zasoby menu, które są dodawane do paska menu aplikacji, gdy program jest uruchomiony.

- Aby wyświetlić zasób menu jako menu podręczne, kliknij prawym przyciskiem myszy menu i wybierz polecenie **Wyświetl jako okno podręczne**.

   Ta opcja ma tylko preferencję wyświetlania i nie modyfikuje menu.

> [!TIP]
> Aby zmienić z powrotem na widok paska menu, wybierz pozycję **Wyświetl jako podręczny** ponownie. Ta akcja powoduje usunięcie znacznika wyboru i zwrócenie widoku paska menu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Polecenia menu](../windows/menu-command-properties.md)<br/>
[Obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menu](../mfc/menus-mfc.md)<br/>
[Menu](/windows/win32/menurc/menus)