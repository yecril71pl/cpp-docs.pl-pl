---
title: Klasa CBookmark | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
dev_langs: C++
helpviewer_keywords: CBookmark class
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 021158981f99661a1b9b694efb094dc329c684ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cbookmark-class"></a>Klasa CBookmark
Przechowuje wartość zakładki w swoim buforze.  
  
## <a name="syntax"></a>Składnia  
  
```  
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase  
template < >  
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
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)