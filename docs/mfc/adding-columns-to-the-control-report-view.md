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
ms.openlocfilehash: 9321a582f223269ee998dccd01721f47d90eb7fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509342"
---
# <a name="adding-columns-to-the-control-report-view"></a>Dodawanie kolumn do formantu (widok raportu)

> [!NOTE]
>  Poniższa procedura dotyczy obiektu [CListView](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md) .

Gdy kontrolka listy znajduje się w widoku raportu, są wyświetlane kolumny, co zapewnia metodę organizowania różnych podelementów każdego elementu formantu listy. Ta organizacja jest zaimplementowana z zastosowaniem jednej do jednego między kolumną w kontrolce list i skojarzoną podpozycją elementu formantu listy. Aby uzyskać więcej informacji na temat elementów SubItems, zobacz [Dodawanie elementów do kontrolki](../mfc/adding-items-to-the-control.md). Przykład kontrolki listy w widoku Raport jest dostępny w widoku szczegółów w Eksploratorze Windows 95 i Windows 98. Pierwsza kolumna zawiera listę folderów, ikon plików i etykiet. Inne kolumny rozmiar pliku listy, typ pliku, Data ostatniej modyfikacji i tak dalej.

Mimo że kolumny można dodać do kontrolki listy w dowolnym momencie, kolumny są widoczne tylko wtedy, gdy kontrolka ma `LVS_REPORT` włączony bit stylu.

Każda kolumna ma skojarzony element nagłówka (See [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) Object, który oznacza kolumnę i umożliwia użytkownikom zmianę rozmiaru kolumny.

Jeśli formant listy obsługuje widok raportu, należy dodać kolumnę dla każdego możliwego elementu podrzędnego w elemencie kontrolki listy. Dodaj kolumnę, przygotowując strukturę [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) , a następnie wywołując do [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Po dodaniu niezbędnych kolumn (czasami nazywanych elementami nagłówka) można zmienić ich kolejność przy użyciu funkcji składowych i stylów należących do osadzonego formantu nagłówka. Aby uzyskać więcej informacji, zobacz [porządkowanie elementów w formancie nagłówka](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
>  Jeśli formant listy jest tworzony przy użyciu stylu **LVS_NOCOLUMNHEADER** , każda próba wstawienia kolumn zostanie zignorowana.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
