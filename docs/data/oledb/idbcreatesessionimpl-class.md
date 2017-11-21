---
title: "Idbcreatesessionimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
dev_langs: C++
helpviewer_keywords: IDBCreateSessionImpl class
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 42f10a8df7fbf881b98287e5f9224517ed7160ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl — Klasa
Udostępnia implementację dla [IDBCreateSession](https://msdn.microsoft.com/en-us/library/ms724076.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 KLASY POCHODNE  
  
 `SessionClass`  
 Obiekt sesji.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[CreateSession](../../data/oledb/idbcreatesessionimpl-createsession.md)|Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzony sesji.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs obowiązkowy obiekty źródła danych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)