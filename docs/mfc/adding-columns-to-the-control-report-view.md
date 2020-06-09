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
ms.openlocfilehash: 119f0f9cb92d724058ce97fbf477143739ec111e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617311"
---
# <a name="adding-columns-to-the-control-report-view"></a>Dodawanie kolumn do formantu (widok raportu)

> [!NOTE]
> Poniższa procedura dotyczy obiektu [CListView](reference/clistview-class.md) lub [CListCtrl](reference/clistctrl-class.md) .

Gdy kontrolka listy znajduje się w widoku raportu, są wyświetlane kolumny, co zapewnia metodę organizowania różnych podelementów każdego elementu formantu listy. Ta organizacja jest zaimplementowana z zastosowaniem jednej do jednego między kolumną w kontrolce list i skojarzoną podpozycją elementu formantu listy. Aby uzyskać więcej informacji na temat elementów SubItems, zobacz [Dodawanie elementów do kontrolki](adding-items-to-the-control.md). Przykład kontrolki listy w widoku Raport jest dostępny w widoku szczegółów w Eksploratorze Windows 95 i Windows 98. Pierwsza kolumna zawiera listę folderów, ikon plików i etykiet. Inne kolumny rozmiar pliku listy, typ pliku, Data ostatniej modyfikacji i tak dalej.

Mimo że kolumny można dodać do kontrolki listy w dowolnym momencie, kolumny są widoczne tylko wtedy, gdy kontrolka ma `LVS_REPORT` Włączony bit stylu.

Każda kolumna ma skojarzony element nagłówka (See [CHeaderCtrl](reference/cheaderctrl-class.md)) Object, który oznacza kolumnę i umożliwia użytkownikom zmianę rozmiaru kolumny.

Jeśli formant listy obsługuje widok raportu, należy dodać kolumnę dla każdego możliwego elementu podrzędnego w elemencie kontrolki listy. Dodaj kolumnę, przygotowując strukturę [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) , a następnie wywołując do [InsertColumn](reference/clistctrl-class.md#insertcolumn). Po dodaniu niezbędnych kolumn (czasami nazywanych elementami nagłówka) można zmienić ich kolejność przy użyciu funkcji składowych i stylów należących do osadzonego formantu nagłówka. Aby uzyskać więcej informacji, zobacz [porządkowanie elementów w formancie nagłówka](ordering-items-in-the-header-control.md).

> [!NOTE]
> Jeśli kontrolka listy jest tworzona z stylem **LVS_NOCOLUMNHEADER** , każda próba wstawienia kolumn zostanie zignorowana.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](using-clistctrl.md)<br/>
[Formanty](controls-mfc.md)
