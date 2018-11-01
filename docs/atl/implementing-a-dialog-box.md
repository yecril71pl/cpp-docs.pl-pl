---
title: Implementowanie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 680ca7a162d8fbedc793ff097663d942843887d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645422"
---
# <a name="implementing-a-dialog-box"></a>Implementowanie okna dialogowego

Istnieją dwa sposoby okno dialogowe Dodawanie do projektu ATL: Użyj Kreator okna dialogowego ATL lub dodać ją ręcznie.

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Dodawanie okno dialogowe z Kreator okna dialogowego ATL

W [okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md), wybierz obiekt okno dialogowe ATL do okno dialogowe Dodawanie do projektu ATL. Wypełnij Kreator okna dialogowego ATL, zgodnie z potrzebami, a następnie kliknij przycisk **Zakończ**. Kreator dodaje klasę pochodną [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) do projektu. Otwórz **widok zasobów** z **widoku** menu, zlokalizuj okna dialogowego, a następnie go dwukrotnie, aby otworzyć go w edytorze zasobów.

> [!NOTE]
>  Jeśli Twoje okno dialogowe jest tworzony na podstawie `CAxDialogImpl`, może on obsługiwać oba ActiveX i kontrolki Windows. Jeśli nie ma konieczności obsługi formantów ActiveX w klasie okno dialogowe, należy użyć [CSimpleDialog](../atl/reference/csimpledialog-class.md) lub [CDialogImpl](../atl/reference/cdialogimpl-class.md) zamiast tego.

Programy obsługi komunikatów i zdarzenia można dodać do klasy okien dialogowych z widoku klasy. Aby uzyskać więcej informacji, zobacz [Dodawanie programu obsługi komunikatów ATL](../atl/adding-an-atl-message-handler.md).

## <a name="adding-a-dialog-box-manually"></a>Ręczne dodawanie okno dialogowe

Implementowanie okna dialogowego przypomina Implementowanie okna. Wyprowadzić klasę z poziomu [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md), lub [CSimpleDialog](../atl/reference/csimpledialog-class.md) i Zadeklaruj [mapy komunikatów](../atl/message-maps-atl.md) do obsługi wiadomości. Jednakże należy także określić identyfikator zasobu szablonu okna dialogowego w klasie pochodnej. Klasa musi mieć element członkowski danych o nazwie `IDD` zawierającą tę wartość.

> [!NOTE]
>  Kiedy tworzysz okno dialogowe, za pomocą Kreator okna dialogowego ATL, Kreator automatycznie doda `IDD` jako element członkowski **wyliczenia** typu.

`CDialogImpl` pozwala na implementowanie modalne lub niemodalne okno dialogowe, który obsługuje formanty Windows. `CAxDialogImpl` pozwala na implementowanie modalne lub niemodalne okno dialogowe, który obsługuje formanty ActiveX i Windows.

Aby utworzyć modalne okno dialogowe, Utwórz wystąpienie obiektu usługi `CDialogImpl`— pochodnych (lub `CAxDialogImpl`— pochodzące) klasy, a następnie wywołać [DoModal](../atl/reference/cdialogimpl-class.md#domodal) metody. Aby zamknąć okno modalne okno dialogowe, należy wywołać [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) metody z obsługi wiadomości. Aby utworzyć niemodalnego okna dialogowego, wywołaj [Utwórz](../atl/reference/cdialogimpl-class.md#create) zamiast metody `DoModal`. Aby zniszczyć niemodalnego okna dialogowego, należy wywołać [destroywindow —](../atl/reference/cdialogimpl-class.md#destroywindow).

Wychwytywania zdarzeń jest wykonywane automatycznie [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implementuje okno dialogowe programy obsługi komunikatów, jak w przypadku obsługi w `CWindowImpl`-klasy pochodnej. Jeśli jest zwracana wartość specyficzne dla wiadomości, zwrócić go w formie `LRESULT`. Zwrócony `LRESULT` wartości są mapowane przez ATL do obsługi właściwego przez Menedżera okno dialogowe Windows. Aby uzyskać szczegółowe informacje, zobacz kod źródłowy [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) w atlwin.h.

## <a name="example"></a>Przykład

Następujące klasy implementuje okno dialogowe:

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>Zobacz też

[Klasy okien](../atl/atl-window-classes.md)

