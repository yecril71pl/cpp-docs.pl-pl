---
title: IRowsetUpdateImpl::Update | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
dev_langs: C++
helpviewer_keywords: Update method
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2cf0b2989fabda9217abd64aef485f94b2c5ccc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetupdateimplupdate"></a>IRowsetUpdateImpl::Update
Przesyła zmiany wprowadzone od czasu ostatniego pobrania lub aktualizacji wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD ( Update )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hReserved`  
 [in] Odpowiada `hChapter` parametru w [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx).  
  
 Dla innych parametrów, zobacz [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Zmiany są przesyłane przez wywołanie metody [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Konsument musi wywołać [CRowset::Update](../../data/oledb/crowset-update.md) aby zmiany zaczęły obowiązywać. Ustaw *prgRowstatus* do odpowiedniej wartości zgodnie z opisem w [stany wiersza](https://msdn.microsoft.com/en-us/library/ms722752.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetUpdateImpl, klasa](../../data/oledb/irowsetupdateimpl-class.md)