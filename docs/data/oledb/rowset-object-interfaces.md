---
title: Interfejsy obiektu zestawu wierszy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e8a1a5f5256087a8869426489fe01250b16fc598
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340514"
---
# <a name="rowset-object-interfaces"></a>Interfejsy obiektu zestawu wierszy
W poniższej tabeli przedstawiono interfejsów obowiązkowych i opcjonalnych, zdefiniowane przez OLE DB dla obiektu zestawu wierszy.  
  
|Interface|Wymagany?|Implementowany przez Szablony OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](https://msdn.microsoft.com/library/ms719672.aspx)|Obowiązkowy|Tak|  
|[IColumnsInfo](https://msdn.microsoft.com/library/ms724541.aspx)|Obowiązkowy|Tak|  
|[IConvertType](https://msdn.microsoft.com/library/ms715926.aspx)|Obowiązkowy|Tak|  
|[IRowset](https://msdn.microsoft.com/library/ms720986.aspx)|Obowiązkowy|Tak|  
|[IRowsetInfo](https://msdn.microsoft.com/library/ms724541.aspx)|Obowiązkowy|Tak|  
|[IChapteredRowset](https://msdn.microsoft.com/library/ms718180.aspx)|Optional|Nie|  
|[IColumnsInfo2](https://msdn.microsoft.com/library/ms712953.aspx)|Optional|Nie|  
|[IColumnsRowset](https://msdn.microsoft.com/library/ms722657.aspx)|Optional|Nie|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|Tak (za pośrednictwem ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/library/ms709832.aspx)|Optional|Nie|  
|[IGetRow](https://msdn.microsoft.com/library/ms718047.aspx)|Optional|Nie|  
|[IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx)|Optional|Tak|  
|[IRowsetChapterMember](https://msdn.microsoft.com/library/ms725430.aspx)|Optional|Nie|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/library/ms709700.aspx)|Optional|Nie|  
|[IRowsetFind](https://msdn.microsoft.com/library/ms724221.aspx)|Optional|Nie|  
|[IRowsetIdentity](https://msdn.microsoft.com/library/ms715913.aspx)|Opcjonalnie (ale wymagane dla dostawców poziom 0)|Tak|  
|[IRowsetIndex](https://msdn.microsoft.com/library/ms719604.aspx)|Optional|Nie|  
|[Irowsetlocate —](https://msdn.microsoft.com/library/ms721190.aspx)|Optional|Tak|  
|[IRowsetRefresh](https://msdn.microsoft.com/library/ms714892.aspx)|Optional|Nie|  
|[IRowsetScroll](https://msdn.microsoft.com/library/ms712984.aspx)|Optional|Nie|  
|[IRowsetUpdate](https://msdn.microsoft.com/library/ms714401.aspx)|Optional|Tak|  
|[IRowsetView](https://msdn.microsoft.com/library/ms709755.aspx)|Optional|Nie|  
|[Interfejs ISupportErrorInfo](https://msdn.microsoft.com/library/ms715816.aspx)|Optional|Tak|  
|[IRowsetBookmark](https://msdn.microsoft.com/library/ms714246.aspx)|Optional|Nie|  
  
 Implementuje generowane przez kreatora obiektu zestawu wierszy `IAccessor`, `IRowset`, i `IRowsetInfo` poprzez dziedziczenie. `IAccessorImpl` Wiąże obie kolumny danych wyjściowych. `IRowset` Interfejs obsługuje wiersze odczyty i dane. `IRowsetInfo` Interfejs obsługuje właściwości zestawu wierszy.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)