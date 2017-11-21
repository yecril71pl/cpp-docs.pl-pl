---
title: CDataSource::GetProperties | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- GetProperties
dev_langs: C++
helpviewer_keywords: GetProperties method
ms.assetid: ffaecc17-9fe7-449e-94d6-43d31ad06cfc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d2dc4cdee71c15bdc3aadfabb6a253a2c0c8e548
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdatasourcegetproperties"></a>CDataSource::GetProperties
Zwraca właściwości informacji wymaganych dla obiekt źródła danych połączenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT GetProperties(   
   ULONG ulPropIDSets,   
   const DBPROPIDSET* pPropIDSet,   
   ULONG* pulPropertySets,   
   DBPROPSET** ppPropsets    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx) w *OLE DB Podręcznik programisty* w systemie Windows SDK.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać jedną właściwość, należy użyć [GetProperty](../../data/oledb/cdatasource-getproperty.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdatasource — klasa](../../data/oledb/cdatasource-class.md)