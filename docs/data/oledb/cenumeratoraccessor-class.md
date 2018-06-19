---
title: Cenumeratoraccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
dev_langs:
- C++
helpviewer_keywords:
- CEnumeratorAccessor class
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bb071f47eb7079c8de63da47ee0d837f44442c1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097244"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor — Klasa
Używane przez [CEnumerator](../../data/oledb/cenumerator-class.md) dostępu do danych z zestawu wierszy modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia

```cpp
class CEnumeratorAccessor  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|Zmienna wskazującą, czy moduł wyliczający jest wyliczający nadrzędnego, jeśli wiersz jest moduł wyliczający.|  
|[m_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|Zmienna wskazującą, czy wiersz zawiera opis źródła danych lub moduł wyliczający.|  
|[m_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|Opis źródła danych lub modułu wyliczającego.|  
|[m_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|Nazwa źródła danych lub modułu wyliczającego.|  
|[m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|Parametry do przekazania do [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) uzyskanie moniker dla źródła danych lub modułu wyliczającego.|  
  
## <a name="remarks"></a>Uwagi  
 Ten zestaw wierszy składa się z źródła danych i moduły wyliczające widoczne z bieżącej modułu wyliczającego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)