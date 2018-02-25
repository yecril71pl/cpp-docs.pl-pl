---
title: IGetDataSourceImpl::GetDataSource | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- GetDataSource method
ms.assetid: b70995d2-b951-452e-a2d4-fb3eb085886e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a30f2030dc6a1e45836d0a50aebf7a722f950bf3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="igetdatasourceimplgetdatasource"></a>IGetDataSourceImpl::GetDataSource
Zwraca obiekt źródła danych, która utworzona sesja wskaźnika interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IGetDataSource::GetDataSource](https://msdn.microsoft.com/en-us/library/ms725443.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Przydatne, jeśli chcesz uzyskać dostęp do właściwości w obiekcie źródła danych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IGetDataSourceImpl, klasa](../../data/oledb/igetdatasourceimpl-class.md)