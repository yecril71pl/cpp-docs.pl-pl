---
title: IDBCreateSessionImpl::CreateSession | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- CreateSession method
ms.assetid: 035e5ddb-56e6-43b1-874d-89c0e40b103b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ebd9a985f73d990a669abc76bcbac045aa769690
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="idbcreatesessionimplcreatesession"></a>IDBCreateSessionImpl::CreateSession
Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzony sesji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(CreateSession)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IDBCreateSession::CreateSession](https://msdn.microsoft.com/en-us/library/ms714942.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IDBCreateSessionImpl, klasa](../../data/oledb/idbcreatesessionimpl-class.md)