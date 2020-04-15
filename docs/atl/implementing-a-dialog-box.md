---
title: Implementowanie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 435926b0a0affde03580ceb2b479cb08a17d0454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319475"
---
# <a name="implementing-a-dialog-box"></a>Implementowanie okna dialogowego

Istnieją dwa sposoby dodawania okna dialogowego do projektu ATL: użyj Kreatora okien dialogowych ATL lub dodaj je ręcznie.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Dodawanie okna dialogowego za pomocą Kreatora okien dialogowych ATL

W [oknie dialogowym Dodawanie klasy](../ide/add-class-dialog-box.md)wybierz obiekt okna dialogowego ATL, aby dodać okno dialogowe do projektu ATL. Wypełnij odpowiednio Kreatora okien dialogowych ATL i kliknij przycisk **Zakończ**. Kreator dodaje klasę pochodną [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) do projektu. Otwórz **widok zasobów** z menu **Widok,** znajdź okno dialogowe i kliknij go dwukrotnie, aby otworzyć go w edytorze zasobów.

> [!NOTE]
> Jeśli okno dialogowe pochodzi `CAxDialogImpl`z programu , może obsługiwać zarówno formanty ActiveX, jak i Windows. Jeśli nie chcesz obciążenie obsługi kontroli ActiveX w klasie okna dialogowego, należy użyć [CSimpleDialog](../atl/reference/csimpledialog-class.md) lub [CDialogImpl](../atl/reference/cdialogimpl-class.md) zamiast tego.

Programy obsługi wiadomości i zdarzeń można dodać do klasy okna dialogowego z widoku klasy. Aby uzyskać więcej informacji, zobacz [Dodawanie programu obsługi wiadomości ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Ręczne dodawanie okna dialogowego

Implementowanie okna dialogowego jest podobne do implementowania okna. Klasy można wyprowadzić z [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md)lub [CSimpleDialog](../atl/reference/csimpledialog-class.md) i zadeklarować [mapę wiadomości](../atl/message-maps-atl.md) do obsługi wiadomości. Jednak należy również określić identyfikator zasobu szablonu okna dialogowego w klasie pochodnej. Klasa musi mieć element `IDD` członkowski danych wywoływany do przechowywania tej wartości.

> [!NOTE]
> Podczas tworzenia okna dialogowego za pomocą Kreatora okien dialogowych ATL kreator automatycznie dodaje element `IDD` członkowski jako typ wyliczenia. **enum**

`CDialogImpl`umożliwia zaimplementowanie modalnego lub niemodalnego okna dialogowego zawierającego formanty systemu Windows. `CAxDialogImpl`umożliwia zaimplementowanie modalnego lub niemodalnego okna dialogowego, w którym znajdują się zarówno formanty ActiveX, jak i Windows.

Aby utworzyć modalne okno dialogowe, `CDialogImpl`utwórz wystąpienie `CAxDialogImpl`klasy pochodnej (lub pochodnej), a następnie wywołanie metody [DoModal.](../atl/reference/cdialogimpl-class.md#domodal) Aby zamknąć modalne okno dialogowe, wywołaj [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) metody z obsługi wiadomości. Aby utworzyć niemodowe okno dialogowe, należy `DoModal`wywołać metodę [Utwórz](../atl/reference/cdialogimpl-class.md#create) zamiast . Aby zniszczyć niemodowe okno dialogowe, zadzwoń [do destroywindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Zdarzenia sinking odbywa się automatycznie w [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Zaimplementuj programy obsługi komunikatów okna dialogowego, tak jak programy obsługi w klasie pochodnej. `CWindowImpl` Jeśli istnieje wartość zwracana specyficzna `LRESULT`dla wiadomości, zwróć ją jako . Zwracane `LRESULT` wartości są mapowane przez ATL w celu prawidłowej obsługi przez menedżera okien dialogowych systemu Windows. Aby uzyskać szczegółowe informacje, zobacz kod źródłowy [dla CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) w atlwin.h.

## <a name="example"></a>Przykład

Następująca klasa implementuje okno dialogowe:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Zobacz też

[Klasy okien](../atl/atl-window-classes.md)
