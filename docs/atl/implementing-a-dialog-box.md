---
title: Implementowanie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 7866afd26c901181f2b4193a87daf5dca2b0c67f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226688"
---
# <a name="implementing-a-dialog-box"></a>Implementowanie okna dialogowego

Istnieją dwa sposoby dodawania okna dialogowego do projektu ATL: Użyj Kreatora okna dialogowego ATL lub Dodaj go ręcznie.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Dodawanie okna dialogowego przy użyciu kreatora okna dialogowego ATL

W [oknie dialogowym Dodawanie klasy](../ide/add-class-dialog-box.md)wybierz obiekt okna dialogowego ATL, aby dodać okno dialogowe do projektu ATL. Wypełnij odpowiednie pola w Kreatorze okna dialogowego ATL i kliknij przycisk **Zakończ**. Kreator dodaje klasę pochodzącą od [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) do projektu. Otwórz **Widok zasobów** z menu **Widok** , Znajdź okno dialogowe, a następnie kliknij je dwukrotnie, aby otworzyć je w edytorze zasobów.

> [!NOTE]
> Jeśli Twoje okno dialogowe pochodzi od `CAxDialogImpl` , może hostować zarówno kontrolki ActiveX, jak i Windows. Jeśli nie chcesz obciążać obsługi formantów ActiveX w klasie okna dialogowego, zamiast tego użyj [CSimpleDialog](../atl/reference/csimpledialog-class.md) lub [CDialogImpl](../atl/reference/cdialogimpl-class.md) .

Procedury obsługi komunikatów i zdarzeń można dodać do klasy okna dialogowego z Widok klasy. Aby uzyskać więcej informacji, zobacz [Dodawanie programu obsługi komunikatów ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Ręczne dodawanie okna dialogowego

Zaimplementowanie okna dialogowego jest podobne do implementującego okno. Klasa pochodzi od [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md)lub [CSimpleDialog](../atl/reference/csimpledialog-class.md) i deklaruje [mapę komunikatów](../atl/message-maps-atl.md) do obsługi komunikatów. Jednak należy również określić identyfikator zasobu szablonu okna dialogowego w klasie pochodnej. `IDD`Aby można było przytrzymać tę wartość, Klasa musi mieć element członkowski danych o nazwie.

> [!NOTE]
> Gdy tworzysz okno dialogowe przy użyciu kreatora okna dialogowego ATL, Kreator automatycznie doda `IDD` element członkowski jako **`enum`** Typ.

`CDialogImpl`umożliwia zaimplementowanie modalnego lub niemodalnego okna dialogowego, które obsługuje formanty systemu Windows. `CAxDialogImpl`umożliwia zaimplementowanie modalnego lub niemodalnego okna dialogowego, które obsługuje kontrolki ActiveX i okna.

Aby utworzyć modalne okno dialogowe, Utwórz wystąpienie `CDialogImpl` klasy pochodnej (lub `CAxDialogImpl` pochodnej), a następnie Wywołaj metodę [DoModal](../atl/reference/cdialogimpl-class.md#domodal) . Aby zamknąć modalne okno dialogowe, wywołaj metodę [zdarzenie EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) z procedury obsługi komunikatów. Aby utworzyć niemodalne okno dialogowe, wywołaj metodę [Create](../atl/reference/cdialogimpl-class.md#create) zamiast `DoModal` . Aby zniszczyć niemodalne okno dialogowe, wywołaj [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).

Zdarzenia dotyczące ujścia są automatycznie wykonywane w [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Zaimplementuj procedury obsługi komunikatów okna dialogowego, tak jak procedury obsługi w `CWindowImpl` klasie pochodnej. Jeśli istnieje wartość zwraca specyficzną dla wiadomości, zwróć ją jako `LRESULT` . Zwracane `LRESULT` wartości są mapowane przez ATL w celu zapewnienia prawidłowej obsługi przez Menedżera okien dialogowych systemu Windows. Aby uzyskać szczegółowe informacje, zobacz kod źródłowy dla [CDialogImplBaseT::D ialogproc](../atl/reference/cdialogimpl-class.md#dialogproc) w atlwin. h.

## <a name="example"></a>Przykład

Następująca Klasa implementuje okno dialogowe:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Zobacz także

[Klasy okien](../atl/atl-window-classes.md)
