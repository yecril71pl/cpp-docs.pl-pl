---
title: Tworzenie Menu (C++)
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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: 438480032f1fe9208e406b4ee499267e42148a48
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702807"
---
# <a name="creating-a-menu-c"></a>Tworzenie Menu (C++)

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

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)