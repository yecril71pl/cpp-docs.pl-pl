---
title: IRowsetInfoImpl::GetSpecification | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
dev_langs:
- C++
helpviewer_keywords:
- GetSpecification method
ms.assetid: 8e14289d-9cca-4df7-a9e0-f4ef03c61e30
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0d740431452dd37de9cd361e524b45d99a6325f3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetinfoimplgetspecification"></a>IRowsetInfoImpl::GetSpecification
Zwraca wskaźnik interfejsu na obiekcie (polecenie lub sesji), który utworzył ten zestaw wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (GetSpecification )(REFIID riid,  
   IUnknown** ppSpecification);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetInfo::GetSpecification](https://msdn.microsoft.com/en-us/library/ms716746.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej metody za pomocą [igetdatasourceimpl —](../../data/oledb/igetdatasourceimpl-class.md) można pobrać właściwości z obiektu źródła danych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetinfoimpl — klasa](../../data/oledb/irowsetinfoimpl-class.md)   
 [IRowsetInfoImpl::GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)   
 [IRowsetInfoImpl::GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)