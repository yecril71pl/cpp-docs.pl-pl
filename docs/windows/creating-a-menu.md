---
title: Tworzenie menu (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: da5fc355ae11ee5efb1c58be9e33bd4fb8bff02d
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320526"
---
# <a name="creating-menus-c"></a>Tworzenie menu (C++)

> [!NOTE]
> **Okno zasobów** nie jest dostępny w wersji Express.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="create-a-standard-menu"></a>Utwórz standardowe menu

1. Z **widoku** menu, wybierz opcję **widok zasobów** , a następnie kliknij prawym przyciskiem myszy **Menu** nagłówka, a następnie wybierz **Dodaj zasób**. Wybierz **Menu**.

1. Wybierz **nowy element** polu (prostokąt, zawierający "Typ w tym miejscu") na pasku menu.

   ![Pole nowego elementu w edytorze menu](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Pole nowego elementu

1. Wpisz nazwę nowego menu, na przykład "File".

   Można wpisać tekst, który jest dostępny w **Menu** edytora i **podpis** pole w [okno właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości nowego menu w jednej z tych lokalizacji.

   Po wyrażono nowe menu nazwę na pasku menu, okno nowy element przenosi się z prawej strony (co pozwala innym menu dodawania), a inny nowy element zostanie otwarte okno poniżej pierwszej menu, polecenia menu można dodać do niego.

   ![Rozwinięty okno nowy element](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Okno nowy element z fokusem przesunięte po wpisaniu nazwy Menu

   > [!NOTE]
   > Aby utworzyć pojedynczą pozycją menu na pasku menu, ustaw **okno podręczne** właściwości **False**.

## <a name="create-a-submenu"></a>Tworzenie podmenu

1. Wybierz polecenie menu, dla której chcesz utworzyć podmenu.

1. W **nowy element** pole, które pojawia się po prawej stronie, wpisz nazwę nowego polecenia menu. To nowe polecenie pojawią się najpierw z menu podmenu.

1. Dodawanie dodatkowych poleceń do menu podmenu.

## <a name="to-insert-a-new-menu-between-existing-menus"></a>Aby wstawić nowego menu między istniejącymi menu

Wybierz istniejące nazwy menu i naciśnij klawisz **Wstaw** klucza. **Nowy element** pole jest wstawiany przed wybranego elementu.

   \- lub —

Kliknij prawym przyciskiem myszy na pasku menu, a następnie wybierz **Wstaw nowy** z menu skrótów.

## <a name="add-commands-to-a-menu"></a>Dodawanie poleceń do menu

1. Tworzenie menu.

1. Na przykład wybierz nazwę menu **pliku**.

   Każde menu będzie Rozwiń i udostępnić pole nowego elementu w przypadku poleceń. Na przykład można dodać polecenia **New**, **Otwórz**, i **Zamknij** do **pliku** menu.

1. W polu Nowy element wpisz nazwę nowego polecenia menu.

   > [!NOTE]
   > Można wpisać tekst, który jest dostępny w **Menu** edytora i **podpis** pole w [okno właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości nowego menu w jednej z tych lokalizacji.

   > [!TIP]
   > Można zdefiniować mnemoników klucza (klawisz dostępu), który umożliwia użytkownikowi wybranie polecenia menu. Wpisz znak (`&`) przed literę, aby określić, że mnemonik. Użytkownik może wybrać polecenie menu, wpisując tę literę.

1. W **właściwości** okna, wybierz opcję menu polecenie Właściwości, które są stosowane. Aby uzyskać więcej informacji, zobacz [właściwości poleceń Menu](../windows/menu-command-properties.md).

1. W **wiersza** pole w **właściwości** okna, wpisz ciąg monitu mają być wyświetlane na pasku stanu aplikacji.

   W tym kroku tworzy wpis w tabeli ciągów za pomocą tego samego identyfikatora zasobu jako polecenia menu, który został utworzony.

   > [!NOTE]
   > Monity można stosować tylko do elementów menu za pomocą **okno podręczne** właściwość **True**. Na przykład elementy menu najwyższego poziomu może mieć monitów, jeśli mają one elementy menu podrzędne. Celem **monitu** jest wskazanie, co się stanie, jeśli użytkownik wybierze element menu.

1. Naciśnij klawisz **Enter** można ukończyć polecenia menu.

   Nowe pole elementu jest zaznaczone, aby można było utworzyć menu dodatkowych poleceń.

## <a name="create-pop-up-menus"></a>Tworzenie menu wyskakujących

[Menu wyskakujące](../mfc/menus-mfc.md) wyświetlania często używanych poleceń. Mogą to być kontekstowo lokalizacji wskaźnika. Używanie wyskakujących menu w aplikacji wymaga tworzenia samo menu, a następnie nawiąż połączenie z kodu aplikacji.

Po utworzeniu zasobu menu, kod aplikacji musi załadować zasobu menu i używać [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) aby spowodować, że są wyświetlane w menu. Po użytkownik został odrzucony wyskakujących menu, wybierając poza nim lub została wybrana polecenie, funkcja zwróci. Jeśli użytkownik wybierze polecenie, komunikat tego polecenia będą wysyłane do okna, w których uchwyt został przekazany.

### <a name="to-create-a-pop-up-menu"></a>Aby utworzyć menu podręcznego

1. [Tworzenie menu](../windows/creating-a-menu.md) z pustym tytułem (nie zapewniają **podpis**).

1. [Dodać polecenie menu do menu Nowy](../windows/adding-commands-to-a-menu.md). Przenieś do pierwszego polecenia menu poniżej tytułu menu puste (mówi tymczasowe podpis `Type Here`). Wpisz **podpis** i inne informacje.

   Powtórz ten proces dla innych poleceń menu w menu podręcznym.

1. Zapisz zasób menu.

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Aby nawiązać połączenie aplikacji menu podręcznego

1. Dodaj program obsługi komunikatów dla WM_CONTEXTMENU (na przykład). Aby uzyskać więcej informacji, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

1. Dodaj następujący kod do obsługi komunikatów:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) przekazywane przez komunikat program obsługi jest we współrzędnych ekranu.

   > [!NOTE]
   > Łączenie menu wyskakującego z Twoją aplikacją wymaga MFC.

### <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>Aby wyświetlić zasobów menu jako menu podręcznego

Zwykle podczas pracy **Menu** edytora, zasobu menu jest wyświetlana jako pasek menu. Jednak może być zasobów menu, które są dodawane do paska menu aplikacji, podczas gdy program jest uruchomiony.

Kliknij prawym przyciskiem myszy menu, a następnie wybierz **Pokaż jako menu podręczne** z menu skrótów.

   Ta opcja jest tylko preferencji wyświetlania i nie umożliwia modyfikowania menu.

   > [!NOTE]
   > Aby zmienić widok paska menu, kliknij przycisk **Pokaż jako menu podręczne** ponownie (który spowoduje usunięcie znacznika wyboru i zwraca widok pasek menu).

## <a name="edit-multiple-menus-or-menu-commands"></a>Edytuj kilku menu lub poleceń menu

### <a name="to-select-multiple-menu-commands"></a>Aby wybrać wiele poleceń menu

Możesz wybrać wiele nazw menu lub poleceń menu przeprowadzić operacje zbiorcze, takie jak usuwanie lub zmiana właściwości.

Przytrzymując naciśnięty **Ctrl** klucza, wybierz menu lub poleceń z podmenu ma.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Przenoszenie i kopiowanie menu i poleceń menu

Można przenosić i kopiować, menu i poleceń menu przy użyciu metody przeciągania i upuszczania lub za pomocą poleceń w menu skrótów (kliknij prawym przyciskiem myszy menu).

#### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Do przeniesienia lub skopiowania menu lub poleceń menu przy użyciu metody przeciągania i upuszczania

1. Przeciągnij lub skopiuj element, który chcesz przenieść do:

   - Nowa lokalizacja bieżącego menu.

   - Inne menu. (Można przejść do innych menu, przeciągając wskaźnik myszy nad nimi.)

1. Pomijać polecenia menu, gdy prowadnicę wstawiania pokazuje pozycji, które chcesz.

#### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Do przeniesienia lub skopiowania menu lub poleceń za pomocą polecenia menu skrótów

1. Kliknij prawym przyciskiem myszy jednego lub kilku menu lub poleceń menu.

1. Z menu skrótów wybierz polecenie **Wytnij** (Aby przenieść) lub **kopiowania**.

1. Jeśli przenosisz elementy do menu inny zasób lub pliku skryptu zasobu, [otwórz go w innym oknie](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

1. Wybierz pozycję menu lub polecenia menu, który chcesz przenieść lub skopiować do.

1. Z menu skrótów wybierz polecenie **Wklej**. Element przenoszone lub kopiowane jest umieszczany przed elementem, którą wybierzesz.

   > [!NOTE]
   > Można również przeciągnąć, skopiuj i Wklej do innych menu w innych oknach menu.

### <a name="to-delete-a-menu-or-menu-command"></a>Aby usunąć menu lub poleceń menu

1. Kliknij prawym przyciskiem myszy nazwę menu lub poleceń.

1. Wybierz **Usuń** z menu skrótów.

   > [!NOTE]
   > Podobnie można użyć menu skrótów do wykonywania innych akcji, takich jak kopiowanie, wycinanie, wklejanie, Wstaw nowy, Wstaw Separator edycji identyfikatorów Pokaż jako okno podręczne, sprawdź mnemonik itp.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytor menu](../windows/menu-editor.md)