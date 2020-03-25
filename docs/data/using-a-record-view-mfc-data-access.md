---
title: Korzystanie z widoku rekordu (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 611ddfd755eec84d4f2572a50c18802f988c5c3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209030"
---
# <a name="using-a-record-view--mfc-data-access"></a>Korzystanie z widoku rekordu (dostęp do danych MFC)

W tym temacie wyjaśniono, jak często można dostosować domyślny kod dla widoków rekordów, które kreator zapisuje dla Ciebie. Zazwyczaj chcesz ograniczyć wybór rekordu z [filtrem](../data/odbc/recordset-filtering-records-odbc.md) lub [parametrami](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), co może [posortować](../data/odbc/recordset-sorting-records-odbc.md) rekordy, Dostosuj instrukcję języka SQL.

Używanie `CRecordView` jest znacznie takie samo jak przy użyciu [CFormView](../mfc/reference/cformview-class.md). Podstawowym podejściem jest użycie widoku rekordu do wyświetlania i może aktualizować rekordy pojedynczego zestawu rekordów. Poza tym, możesz chcieć użyć innych zestawów rekordów, jak to opisano w [widokach rekordów: wypełnianie pola listy z drugiego zestawu rekordów](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

## <a name="see-also"></a>Zobacz też

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)
