---
title: Edytowanie kilku menu lub poleceń Menu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: b6f17897-2a40-4afd-97d4-a38b7661680b
ms.openlocfilehash: 45e2c4e97dc850b4d6fb13a5526911e4bd5caec2
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703223"
---
# <a name="editing-multiple-menus-or-menu-commands"></a>Edytowanie kilku menu lub poleceń Menu

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-select-multiple-menu-commands"></a>Aby wybrać wiele poleceń menu

Możesz wybrać wiele nazw menu lub poleceń menu przeprowadzić operacje zbiorcze, takie jak usuwanie lub zmiana właściwości.

Przytrzymując naciśnięty **Ctrl** klucza, wybierz menu lub poleceń z podmenu ma.

## <a name="to-move-and-copy-menus-and-menu-commands"></a>Przenoszenie i kopiowanie menu i poleceń menu

Można przenosić i kopiować, menu i poleceń menu przy użyciu metody przeciągania i upuszczania lub za pomocą poleceń w menu skrótów (kliknij prawym przyciskiem myszy menu).

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Do przeniesienia lub skopiowania menu lub poleceń menu przy użyciu metody przeciągania i upuszczania

1. Przeciągnij lub skopiuj element, który chcesz przenieść do:

   - Nowa lokalizacja bieżącego menu.

   - Inne menu. (Można przejść do innych menu, przeciągając wskaźnik myszy nad nimi.)

1. Pomijać polecenia menu, gdy prowadnicę wstawiania pokazuje pozycji, które chcesz.

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Do przeniesienia lub skopiowania menu lub poleceń za pomocą polecenia menu skrótów

1. Kliknij prawym przyciskiem myszy jednego lub kilku menu lub poleceń menu.

1. Z menu skrótów wybierz polecenie **Wytnij** (Aby przenieść) lub **kopiowania**.

1. Jeśli przenosisz elementy do menu inny zasób lub pliku skryptu zasobu, [otwórz go w innym oknie](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

1. Wybierz pozycję menu lub polecenia menu, który chcesz przenieść lub skopiować do.

1. Z menu skrótów wybierz polecenie **Wklej**. Element przenoszone lub kopiowane jest umieszczany przed elementem, którą wybierzesz.

   > [!NOTE]
   > Można również przeciągnąć, skopiuj i Wklej do innych menu w innych oknach menu.

## <a name="to-delete-a-menu-or-menu-command"></a>Aby usunąć menu lub poleceń menu

1. Kliknij prawym przyciskiem myszy nazwę menu lub poleceń.

1. Wybierz **Usuń** z menu skrótów.

   > [!NOTE]
   > Podobnie można użyć menu skrótów do wykonywania innych akcji, takich jak kopiowanie, wycinanie, wklejanie, Wstaw nowy, Wstaw Separator edycji identyfikatorów Pokaż jako okno podręczne, sprawdź mnemonik itp.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)