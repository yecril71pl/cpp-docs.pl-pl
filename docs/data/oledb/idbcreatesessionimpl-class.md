---
title: Idbcreatesessionimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d934e9ae5494b934acb0779665ba4471dfc4c2b7
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465346"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl — Klasa
Udostępnia implementację na potrzeby [IDBCreateSession](/previous-versions/windows/desktop/ms724076\(v=vs.85\)) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 KLASY POCHODZĄCE Z  
  
 *SessionClass*  
 Obiekt sesji.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h 
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[Createsession —](#createsession)|Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzoną sesji.|  
  
## <a name="remarks"></a>Uwagi  
 Obowiązkowego interfejsu na obiekty źródła danych.  

## <a name="createsession"></a> IDBCreateSessionImpl::CreateSession
Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzoną sesji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IDBCreateSession::CreateSession](/previous-versions/windows/desktop/ms714942\(v=vs.85\)) w *OLE DB Podręcznik programisty*.   
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)