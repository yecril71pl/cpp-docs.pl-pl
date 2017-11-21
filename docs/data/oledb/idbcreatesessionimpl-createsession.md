---
title: IDBCreateSessionImpl::CreateSession | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs: C++
helpviewer_keywords: CreateSession method
ms.assetid: 035e5ddb-56e6-43b1-874d-89c0e40b103b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cee8a99e39434ddab7061c2e67adafbeb864717
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="idbcreatesessionimplcreatesession"></a>IDBCreateSessionImpl::CreateSession
Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzony sesji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD(CreateSession)(   
   IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IDBCreateSession::CreateSession](https://msdn.microsoft.com/en-us/library/ms714942.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbcreatesessionimpl — klasa](../../data/oledb/idbcreatesessionimpl-class.md)