---
title: Klasa CBookmark | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c14fde6fb07a35ef9e2955ce61f991bede6b11a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094754"
---
# <a name="cbookmark-class"></a>Klasa CBookmark
Przechowuje wartość zakładki w swoim buforze.  
  
## <a name="syntax"></a>Składnia

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### <a name="parameters"></a>Parametry  
 `nSize`  
 Rozmiar buforu zakładki w bajtach. Gdy `nSize` wynosi zero, buforu zakładki będzie można dynamicznie utworzyć w czasie wykonywania.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|Konstruktor|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|Pobiera wskaźnik do buforu.|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|Pobiera rozmiar buforu w bajtach.|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|Ustawia wartość zakładki.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../../data/oledb/cbookmark-operator-equal.md)|Przypisuje jedną `CBookmark` klasy do innego.|  
  
## <a name="remarks"></a>Uwagi  
 **CBookmark\<0 >** jest specjalizacją szablonu `CBookmark`; swojego bufora jest tworzone dynamicznie w czasie wykonywania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)