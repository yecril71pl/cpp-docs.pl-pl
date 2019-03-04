---
title: Dodawanie kolumn do formantu (widok raportu)
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: d414c5f597628576916c5091fa63a4bf673c8c44
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292556"
---
# <a name="adding-columns-to-the-control-report-view"></a>Dodawanie kolumn do formantu (widok raportu)

> [!NOTE]
>  Poniższa procedura ma zastosowanie do każdego [CListView](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md) obiektu.

Gdy kontrolka listy znajduje się w widoku raportu, kolumny są wyświetlane, zapewniając metody organizowania różne elementy podrzędne elementu każdy element tej listy kontroli. Ta organizacja jest implementowane za pomocą relację między kolumną w formancie listy i podelement skojarzonego elementu kontrolki listy. Aby uzyskać więcej informacji na temat podrzędnych, zobacz [Dodawanie elementów do formantu](../mfc/adding-items-to-the-control.md). Przykład formantu listy, w widoku raportu znajduje się w widoku szczegółów w Windows 95 i Windows 98 Explorer. Pierwsza kolumna zawiera folder, plik ikony i etykiety. Rozmiar pliku, typu pliku, Data ostatniej modyfikacji i tak dalej, Wyświetl listę innych kolumn.

Mimo że kolumny można dodać formant listy w dowolnym momencie, kolumny są widoczne tylko wtedy, gdy kontrolka ma `LVS_REPORT` bit stylu włączona.

Każda kolumna ma element skojarzony nagłówek (zobacz [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) obiektu etykiet kolumny, która umożliwia użytkownikom zmiany rozmiaru kolumny.

Kontrolki listy obsługuje widoku raportu, należy dodać kolumnę dla każdej podpozycji możliwe w element formantu listy. Dodawanie kolumny za przygotowywanie [LV_COLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna) struktury, a następnie wywołuje element [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Po dodaniu niezbędne kolumny (czasami określane jako elementy nagłówka), można zmieniać kolejność ich przy użyciu funkcji elementów członkowskich i style należących do formantu osadzonego nagłówka. Aby uzyskać więcej informacji, zobacz [kolejność elementów w formancie nagłówka](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
>  Jeśli kontrolka listy jest tworzona przy użyciu **LVS_NOCOLUMNHEADER** stylu, wszelkie próby, aby wstawić kolumny zostaną zignorowane.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
