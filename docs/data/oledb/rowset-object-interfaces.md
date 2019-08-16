---
title: Interfejsy obiektu zestawu wierszy
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: d9c2c61714a98d9de09d8657352a14f296e35a58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501286"
---
# <a name="rowset-object-interfaces"></a>Interfejsy obiektu zestawu wierszy

W poniższej tabeli przedstawiono obowiązkowe i opcjonalne interfejsy zdefiniowane przez OLE DB dla obiektu zestawu wierszy.

|Interface|Wymagany?|Zaimplementowane przez OLE DB szablony?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|Obowiązkowy|Tak|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Obowiązkowy|Tak|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|Obowiązkowy|Tak|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|Obowiązkowy|Tak|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Obowiązkowy|Tak|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|Optional|Nie|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|Optional|Nie|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|Optional|Nie|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|Tak (za poorednictwem biblioteki ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|Optional|Nie|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|Optional|Nie|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|Optional|Tak|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|Optional|Nie|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|Optional|Nie|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|Optional|Nie|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|Opcjonalne (ale wymagane dla dostawców poziomu 0)|Tak|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|Optional|Nie|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|Optional|Tak|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|Optional|Nie|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|Optional|Nie|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|Optional|Tak|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|Optional|Nie|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|Tak|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|Optional|Nie|

Wygenerowany przez Kreatora obiekt zestawu wierszy implementuje `IAccessor`, `IRowset`i `IRowsetInfo` przez dziedziczenie. Powoduje `IAccessorImpl` powiązanie obu kolumn wyjściowych. `IRowset` Interfejs obsługuje pobieranie wierszy i danych. `IRowsetInfo` Interfejs obsługuje właściwości zestawu wierszy.

## <a name="see-also"></a>Zobacz także

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
