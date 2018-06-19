---
title: Klasa CEnumerator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b7e390212da53f85cb50dd5bb151ea6740784b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096109"
---
# <a name="cenumerator-class"></a>Klasa CEnumerator
Obiekt enumerator OLE DB, który udostępnia używa [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) interfejsu zwrócą zestawu wierszy opisu wszystkich źródeł danych i moduły wyliczające.  
  
## <a name="syntax"></a>Składnia

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Znajdź](../../data/oledb/cenumerator-find.md)|Wyszukiwanie za pomocą dostępnych dostawców (źródła danych), wyszukiwanie jeden o określonej nazwie.|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|Pobiera `IMoniker` interfejs dla bieżącego rekordu.|  
|[Otwórz](../../data/oledb/cenumerator-open.md)|Otwiera modułu wyliczającego.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz pobrać **ISourcesRowset** danych pośrednio z tej klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [DBViewer](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)