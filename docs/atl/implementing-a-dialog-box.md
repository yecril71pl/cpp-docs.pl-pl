---
title: Okno dialogowe wdrażanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 672696027a43cd5a50e2ad630824d305f7ca4b68
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355855"
---
# <a name="implementing-a-dialog-box"></a>Implementowanie okno dialogowe
Istnieją dwa sposoby okno dialogowe Dodawanie do projektu ATL: za pomocą Kreatora okna dialogowego ATL lub Dodaj ją ręcznie.  
  
## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Dodawanie okno dialogowe Kreator okna dialogowego ATL  
 W [okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md), wybierz obiektu okna dialogowego ATL do dodania do projektu ATL okno dialogowe. Wypełnij Kreator okna dialogowego ATL zależnie od potrzeb, a następnie kliknij przycisk **Zakończ**. Kreator dodaje klasę pochodzącą od [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) do projektu. Otwórz widok zasobów z **widoku** menu, zlokalizuj Twoje okno dialogowe, a następnie kliknij dwukrotnie, aby otworzyć go w edytorze zasobów.  
  
> [!NOTE]
>  Jeśli Twoje okno dialogowe jest pochodną `CAxDialogImpl`, może obsługiwać obu ActiveX i formanty systemu Windows. Jeśli nie chcesz koszty obsługi formantów ActiveX w klasie — okno dialogowe, użyj [CSimpleDialog](../atl/reference/csimpledialog-class.md) lub [cdialogimpl —](../atl/reference/cdialogimpl-class.md) zamiast tego.  
  
 Programy obsługi wiadomości i zdarzenia można dodać do klasy okien dialogowych z widoku klasy. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi ATL komunikat](../atl/adding-an-atl-message-handler.md).  
  
## <a name="adding-a-dialog-box-manually"></a>Ręczne dodawanie okno dialogowe  
 Implementowanie okno dialogowe jest podobny do implementacji okna. Wyprowadzenia klasy z albo [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [cdialogimpl —](../atl/reference/cdialogimpl-class.md), lub [CSimpleDialog](../atl/reference/csimpledialog-class.md) ani deklarować [mapy komunikatów](../atl/message-maps-atl.md) do obsługi wiadomości. Jednak musi również określić identyfikator zasobu okna dialogowego szablonu w klasie pochodnej. Klasy musi mieć element członkowski danych o nazwie `IDD` do przechowywania tej wartości.  
  
> [!NOTE]
>  Po utworzeniu za pomocą Kreatora okna dialogowego ATL okno dialogowe Kreator automatycznie doda `IDD` elementu członkowskiego jako `enum` typu.  
  
 `CDialogImpl` Umożliwia wdrożenie modalne i niemodalne okno dialogowe, które obsługuje formantów systemu Windows. `CAxDialogImpl` Umożliwia wdrożenie modalne i niemodalne okno dialogowe, które obsługuje zarówno ActiveX i systemu Windows.  
  
 Aby utworzyć modalne okno dialogowe, Utwórz wystąpienie z `CDialogImpl`— pochodnych (lub `CAxDialogImpl`— pochodnych) klasy, a następnie wywołać [DoModal](../atl/reference/cdialogimpl-class.md#domodal) — metoda. Aby zamknąć modalne okno dialogowe, wywołaj [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) metody obsługi wiadomości. Aby utworzyć niemodalne okno dialogowe, wywołaj [Utwórz](../atl/reference/cdialogimpl-class.md#create) zamiast metody `DoModal`. Aby zniszczyć niemodalne okno dialogowe, wywołaj [DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow).  
  
 Wychwytywanie zdarzeń jest wykonywane automatycznie [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Implementowanie obsługi komunikatów w oknie dialogowym, jak w przypadku obsługi w `CWindowImpl`-klasy. W przypadku wartości zwracanej specyficzne dla wiadomości, przywrócić go jako `LRESULT`. Zwrócona `LRESULT` wartości są mapowane przez ATL do obsługi odpowiednich przez Menedżera okno dialogowe systemu Windows. Aby uzyskać więcej informacji, zobacz kod źródłowy [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) w atlwin.h.  
  
## <a name="example"></a>Przykład  
 Następujące klasy implementuje okno dialogowe:  
  
 [!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien](../atl/atl-window-classes.md)

