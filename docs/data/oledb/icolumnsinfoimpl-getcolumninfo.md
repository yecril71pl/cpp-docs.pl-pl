---
title: IColumnsInfoImpl::GetColumnInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetColumnInfo
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
dev_langs: C++
helpviewer_keywords: GetColumnInfo method
ms.assetid: a6739a39-7402-496a-b544-a5b1ed05fadf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f2b21f37d8e71390a43a25b486466c99771ff649
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="icolumnsinfoimplgetcolumninfo"></a>IColumnsInfoImpl::GetColumnInfo
Zwraca metadane kolumny wymagane przez większość konsumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD (GetColumnInfo)(  
   DBORDINAL* pcColumns,  
   DBCOLUMNINFO** prgInfo,  
   OLECHAR** ppStringsBuffer   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Icolumnsinfoimpl — klasa](../../data/oledb/icolumnsinfoimpl-class.md)   
 [IColumnsInfoImpl::MapColumnIDs](../../data/oledb/icolumnsinfoimpl-mapcolumnids.md)