---
title: Dodawanie okna dialogowego ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: 71290cf0763ac6594985acc4cb11562efe7028e6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499370"
---
# <a name="adding-an-atl-dialog-box"></a>Dodawanie okna dialogowego ATL

Aby dodać do projektu okno dialogowe ATL, projekt musi być projektem ATL lub projektem MFC zawierającym obsługę ATL. Możesz użyć [Kreatora projektu ATL](../../atl/reference/atl-project-wizard.md) do utworzenia aplikacji ATL lub [dodać obiekt ATL do aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) w celu zaimplementowania obsługi ATL dla aplikacji MFC.

Domyślnie Kreator okna dialogowego ATL implementuje okno dialogowe pochodzące z [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Ta klasa obejmuje obsługę hostingu formantów ActiveX i okien. Jeśli nie chcesz obciążać obsługi formantu ActiveX, po wygenerowaniu kodu przez kreatora Zastąp wszystkie wystąpienia `CAxDialogImpl` z [CSimpleDialog](../../atl/reference/csimpledialog-class.md) lub [CDialogImpl](../../atl/reference/cdialogimpl-class.md) jako klasą bazową.

> [!NOTE]
> `CSimpleDialog` tworzy tylko modalne okna dialogowe, które obsługują tylko formanty standardowe systemu Windows. `CDialogImpl` tworzy modalne lub Niemodalne okna dialogowe.

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Aby dodać zasób okna dialogowego ATL do projektu

1. Utwórz Projekt ATL przy użyciu [Kreatora projektu ATL](../../atl/reference/atl-project-wizard.md).

1. W [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code)kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Dodaj** z menu skrótów. Kliknij pozycję **Dodaj klasę**.

1. W okienku **Szablony** okna dialogowego [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) kliknij przycisk **okna dialogowego ATL**. Kliknij przycisk **Otwórz** , aby wyświetlić [Kreatora okna dialogowego ATL](../../atl/reference/atl-dialog-wizard.md).

Aby uzyskać więcej informacji, zobacz [implementowanie okna dialogowego](../../atl/implementing-a-dialog-box.md).

## <a name="see-also"></a>Zobacz też

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Klasy okien](../../atl/atl-window-classes.md)<br/>
[Mapy komunikatów](../../atl/message-maps-atl.md)
