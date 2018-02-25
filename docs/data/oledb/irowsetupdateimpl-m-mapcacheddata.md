---
title: IRowsetUpdateImpl::m_mapCachedData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- m_mapCachedData
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 55a48b9a6636a95ee4b91aa15c820560ffa0f9d5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetupdateimplmmapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData
Mapa zawierający oryginalnych danych dla operacji opóźnieniem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>Parametry  
 `hRow`  
 Dojście do wierszy danych.  
  
 `pData`  
 Wskaźnik do danych w pamięci podręcznej. Dane są typu *magazynu* (klasa rekordu użytkownika). Zobacz *magazynu* argument szablonu w [irowsetupdateimpl — klasa](../../data/oledb/irowsetupdateimpl-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetUpdateImpl, klasa](../../data/oledb/irowsetupdateimpl-class.md)