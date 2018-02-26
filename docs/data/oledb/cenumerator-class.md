---
title: Klasa CEnumerator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEnumerator
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d0ac9fe73b2d8b37e345ddcf602dd98316eedf46
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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
 **Header:**atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [DBViewer](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)