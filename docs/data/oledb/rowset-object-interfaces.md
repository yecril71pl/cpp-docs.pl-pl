---
title: Interfejsy obiektu zestawu wierszy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc9ec134321b2acf9994ad7dfb43c5b14bf0e75f
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216451"
---
# <a name="rowset-object-interfaces"></a>Interfejsy obiektu zestawu wierszy

W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu zestawu wierszy.

|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672)|Obowiązkowy|Tak|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541)|Obowiązkowy|Tak|
|[IConvertType](/previous-versions/windows/desktop/ms715926)|Obowiązkowy|Tak|
|[IRowset](/previous-versions/windows/desktop/ms720986)|Obowiązkowy|Tak|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541)|Obowiązkowy|Tak|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180)|Optional|Nie|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953)|Optional|Nie|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657)|Optional|Nie|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|Tak (za pośrednictwem ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832)|Optional|Nie|
|[IGetRow](/previous-versions/windows/desktop/ms718047)|Optional|Nie|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790)|Optional|Tak|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430)|Optional|Nie|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700)|Optional|Nie|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221)|Optional|Nie|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913)|Opcjonalnie (ale wymagane dla dostawców poziom 0)|Tak|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604)|Optional|Nie|
|[Irowsetlocate —](/previous-versions/windows/desktop/ms721190)|Optional|Tak|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892)|Optional|Nie|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984)|Optional|Nie|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401)|Optional|Tak|
|[IRowsetView](/previous-versions/windows/desktop/ms709755)|Optional|Nie|
|[Interfejs ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|Optional|Tak|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246)|Optional|Nie|

Implementuje generowane przez kreatora obiektu zestawu wierszy `IAccessor`, `IRowset`, i `IRowsetInfo` poprzez dziedziczenie. `IAccessorImpl` Wiąże obie kolumny danych wyjściowych. `IRowset` Interfejs obsługuje wiersze odczyty i dane. `IRowsetInfo` Interfejs obsługuje właściwości zestawu wierszy.

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
