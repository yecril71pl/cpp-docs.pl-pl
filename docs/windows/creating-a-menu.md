---
title: Tworzenie Menu (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: b779e6b089410b818247471086fe987c37b1f36c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518563"
---
# <a name="creating-a-menu-c"></a>Tworzenie Menu (C++)

> [!NOTE]
> **Okno zasobów** nie jest dostępny w wersji Express.

### <a name="to-create-a-standard-menu"></a>Aby utworzyć menu standardowe

1. Z **widoku** menu, kliknij pozycję **widok zasobów** , a następnie kliknij prawym przyciskiem myszy **Menu** nagłówka, a następnie wybierz **Dodaj zasób**. Wybierz **Menu**.

2. Wybierz **nowy element** polu (prostokąt, zawierający "Typ w tym miejscu") na pasku menu.

   ![Pole nowego elementu w edytorze menu](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Pole nowego elementu

3. Wpisz nazwę nowego menu, na przykład "File".

   Można wpisać tekst, który jest dostępny w **Menu** edytora i **podpis** pole w [okno właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości nowego menu w jednej z tych lokalizacji.

   Po wyrażono nowe menu nazwę na pasku menu, okno nowy element przenosi się z prawej strony (co pozwala innym menu dodawania), a inny nowy element zostanie otwarte okno poniżej pierwszej menu, polecenia menu można dodać do niego.

   ![Rozwinięty okno nowy element](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Okno nowy element z fokusem przesunięte po wpisaniu nazwy Menu

   > [!NOTE]
   > Aby utworzyć pojedynczą pozycją menu na pasku menu, ustaw **okno podręczne** właściwości **False**.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)