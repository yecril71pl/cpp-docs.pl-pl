---
title: IOpenRowsetImpl::OpenRowset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
dev_langs: C++
helpviewer_keywords: OpenRowset method
ms.assetid: 2ece8d6c-d165-4f1d-b155-8609bbb60eb6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0382c114975733b07616b697b709a297bef9ec48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iopenrowsetimplopenrowset"></a>IOpenRowsetImpl::OpenRowset
Otwiera i zwraca zestaw wierszy, która obejmuje wszystkie wiersze z jednej tabeli podstawowej lub indeks.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT OpenRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie znajduje się w ATLDB. H. Jest utworzony przez kreatora ATL obiektu podczas tworzenia dostawcy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IOpenRowsetImpl, klasa](../../data/oledb/iopenrowsetimpl-class.md)