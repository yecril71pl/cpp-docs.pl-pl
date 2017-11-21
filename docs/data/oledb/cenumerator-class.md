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
ms.openlocfilehash: 856356117161a0c9e3588732faf01c3a663b6a9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)