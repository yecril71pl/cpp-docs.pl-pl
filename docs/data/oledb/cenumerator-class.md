---
title: Klasa CEnumerator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CEnumerator
dev_langs: C++
helpviewer_keywords: CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a64ac02e7b16bfab70966ffaf2a1897ae955f8c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cenumerator-class"></a>Klasa CEnumerator
Obiekt enumerator OLE DB, który udostępnia używa [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) interfejsu zwrócą zestawu wierszy opisu wszystkich źródeł danych i moduły wyliczające.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 **Nagłówek:**atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [DBViewer](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)