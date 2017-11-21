---
title: "Idbinitializeimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
dev_langs: C++
helpviewer_keywords: IDBInitializeImpl class
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a7a51023f167eee5fbd4082486409f4e11a15547
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl — Klasa
Udostępnia implementację dla [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IDBInitializeImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Idbinitializeimpl —](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)|Konstruktor.|  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[Inicjowanie](../../data/oledb/idbinitializeimpl-initialize.md)|Uruchamia dostawcy.|  
|[Odinicjalizuj](../../data/oledb/idbinitializeimpl-uninitialize.md)|Zatrzymuje dostawcy.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_dwStatus](../../data/oledb/idbinitializeimpl-m-dwstatus.md)|Flagi źródła danych.|  
|[m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)|Wskaźnik do implementacji właściwości bazy danych.|  
  
## <a name="remarks"></a>Uwagi  
 Obowiązkowego interfejsu na obiekty źródła danych i opcjonalnie interfejs moduły wyliczające.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)