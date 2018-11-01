---
title: Dodawanie okna dialogowego ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: ee6f6b1b83c625b30b601275084550309e0e7c68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495371"
---
# <a name="adding-an-atl-dialog-box"></a>Dodawanie okna dialogowego ATL

Aby dodać okno dialogowe ATL do projektu, projekt musi być projektu ATL lub projekt MFC, który obejmuje obsługę ATL. Możesz użyć [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

Domyślnie Kreator okna dialogowego ATL implementuje okno dialogowe pochodną [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Ta klasa zawiera obsługę hostowania kontrolki ActiveX i Windows. Jeśli nie mają obciążenie obsługi formantów ActiveX, gdy kreator został wygenerowany kod, należy zastąpić wszystkie wystąpienia elementu `CAxDialogImpl` z oboma [CSimpleDialog](../../atl/reference/csimpledialog-class.md) lub [CDialogImpl](../../atl/reference/cdialogimpl-class.md) jako klasę bazową .

> [!NOTE]
> `CSimpleDialog` tworzy tylko modalnych okien dialogowych, które obsługują tylko Windows wspólnych formantów. `CDialogImpl` Tworzy albo w modalnym lub niemodalnym dialogowych.

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Można dodać zasobu okna dialogowego ATL do projektu

1. Utwórz projekt ATL za pomocą [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md).

1. Z [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu i kliknij przycisk **Dodaj** z menu skrótów. Kliknij przycisk **Dodaj klasę**.

1. W **szablony** okienku [Dodaj klasę](../../ide/add-class-dialog-box.md) okno dialogowe, kliknij przycisk **okno dialogowe ATL**. Kliknij przycisk **Otwórz** do wyświetlenia [Kreator okna dialogowego ATL](../../atl/reference/atl-dialog-wizard.md).

Aby uzyskać więcej informacji, zobacz [Implementowanie okna dialogowego](../../atl/implementing-a-dialog-box.md).

## <a name="see-also"></a>Zobacz też

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Klasy okien](../../atl/atl-window-classes.md)<br/>
[Mapy komunikatów](../../atl/message-maps-atl.md)
