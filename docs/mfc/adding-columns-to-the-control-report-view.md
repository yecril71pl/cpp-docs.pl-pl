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
ms.openlocfilehash: 34d7b62985748b9b9d741c083ec9b34fce06b309
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370875"
---
# <a name="adding-columns-to-the-control-report-view"></a>Dodawanie kolumn do formantu (widok raportu)

> [!NOTE]
> Poniższa procedura ma zastosowanie do [obiektu CListView](../mfc/reference/clistview-class.md) lub [CListCtrl.](../mfc/reference/clistctrl-class.md)

Gdy formant listy jest w widoku raportu, kolumny są wyświetlane, zapewniając metodę organizowania różnych podelementów każdego elementu kontroli listy. Ta organizacja jest implementowana z korespondencją jeden do jednego między kolumną w formancie listy a skojarzonym podjednomatem elementu kontroli listy. Aby uzyskać więcej informacji na temat podelementów, zobacz [Dodawanie elementów do formantu](../mfc/adding-items-to-the-control.md). Przykład formantu listy w widoku raportu jest dostarczany przez widok Szczegóły w systemach Windows 95 i Windows 98 Explorer. Pierwsza kolumna zawiera listę folderów, ikon plików i etykiet. Inne kolumny lista rozmiar pliku, typ pliku, data ostatniej modyfikacji, i tak dalej.

Mimo że kolumny można dodać do formantu listy w dowolnym momencie, kolumny `LVS_REPORT` są widoczne tylko wtedy, gdy formant ma bit stylu włączony.

Każda kolumna ma skojarzony element nagłówka (zobacz [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)), który etykietuje kolumnę i umożliwia użytkownikom zmienić rozmiar kolumny.

Jeśli formant listy obsługuje widok raportu, należy dodać kolumnę dla każdego możliwego podjednatu w elemencie kontroli listy. Dodaj kolumnę, przygotowując strukturę [LVCOLUMN,](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) a następnie wywołując [polecenie InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Po dodaniu niezbędnych kolumn (czasami nazywanych elementami nagłówka) można zamieścić ich kolejność przy użyciu funkcji elementów członkowskich i stylów należących do osadzonego formantu nagłówka. Aby uzyskać więcej informacji, zobacz [Zamawianie elementów w formancie nagłówka](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
> Jeśli formant listy zostanie utworzony **przy** LVS_NOCOLUMNHEADER stylu, każda próba wstawienia kolumn zostanie zignorowana.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
