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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: e3b3cc58b82f68c55ac98601fd11775422c901e5
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905774"
---
# <a name="creating-menus-c"></a>Tworzenie menu (C++)

> [!NOTE]
> **Okno zasobów** nie jest dostępny w wersji Express.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-standard-menu"></a>Aby utworzyć menu standardowe

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

## <a name="to-create-a-submenu"></a>Aby utworzyć podmenu

1. Wybierz polecenie menu, dla której chcesz utworzyć podmenu.

1. W **nowy element** pole, które pojawia się po prawej stronie, wpisz nazwę nowego polecenia menu. To nowe polecenie pojawią się najpierw z menu podmenu.

1. Dodawanie dodatkowych poleceń do menu podmenu.

## <a name="to-insert-a-new-menu-between-existing-menus"></a>Aby wstawić nowego menu między istniejącymi menu

Wybierz istniejące nazwy menu i naciśnij klawisz **Wstaw** klucza. **Nowy element** pole jest wstawiany przed wybranego elementu.

   \- lub —

Kliknij prawym przyciskiem myszy na pasku menu, a następnie wybierz **Wstaw nowy** z menu skrótów.

## <a name="to-add-commands-to-a-menu"></a>Aby dodać polecenia do menu

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

## <a name="to-create-pop-up-menus"></a>Aby utworzyć menu wyskakujących

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

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytor menu](../windows/menu-editor.md)