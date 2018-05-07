---
title: Dodawanie kolumn do formantu (widok raportu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 975d65119ba0ae24b236d96cbe67e73b70be6bac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="adding-columns-to-the-control-report-view"></a>Dodawanie kolumn do formantu (widok raportu)
> [!NOTE]
>  Poniższa procedura dotyczy, albo [clistview —](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md) obiektu.  
  
 W przypadku formantu listy w widoku raportu, kolumny są wyświetlane udostępnieniu metod organizowania różne elementy podrzędne poszczególnych elementów kontrolki listy. Ta organizacja jest implementowana przy użyciu odpowiednika między kolumnę w formancie listy i podelement skojarzonego elementu kontrolki listy. Aby uzyskać więcej informacji na elementy podrzędne, zobacz [Dodawanie elementów do formantu](../mfc/adding-items-to-the-control.md). Przykład formantu listy w widoku raportu są udostępniane przez widoku szczegółów w systemie Windows 95 i Windows 98 Explorer. Pierwsza kolumna zawiera folder, plik ikony i etykiety. Innych kolumn listy rozmiar pliku, typu pliku, Data ostatniej modyfikacji i tak dalej.  
  
 Mimo że formant listy można dodać kolumny w dowolnym momencie, kolumn są widoczne tylko wtedy, gdy formant ma `LVS_REPORT` bit stylu włączona.  
  
 Każda kolumna zawiera element skojarzony nagłówek (zobacz [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) obiektu etykiet kolumny, która umożliwia użytkownikom zmiany rozmiaru kolumny.  
  
 Formant listy obsługuje widoku raportu, należy dodać kolumnę dla każdego możliwe podelementu w elemencie listy kontroli. Dodaj kolumnę przez przygotowywanie [LV_COLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743) struktury, a następnie wywołuje element [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Po dodaniu kolumny konieczne (czasem określana jako elementy nagłówka), można zmienić kolejność ich przy użyciu funkcji Członkowskich i style należących do formantu osadzonego nagłówka. Aby uzyskać więcej informacji, zobacz [kolejności elementów w formancie nagłówka](../mfc/ordering-items-in-the-header-control.md).  
  
> [!NOTE]
>  Jeśli formant listy jest tworzony z **LVS_NOCOLUMNHEADER** stylu, wszelkie próby kolumn do wstawienia zostaną zignorowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

