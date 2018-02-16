---
title: IRowsetImpl::CreateRow | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
dev_langs:
- C++
helpviewer_keywords:
- CreateRow method
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4403388146b79eec4435374793b2517dd46ff188
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplcreaterow"></a>IRowsetImpl::CreateRow
Metoda wywoływana przez metodę Pomocnika [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) można przydzielić nowego **HROW**.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT CreateRow(DBROWOFFSET lRowsOffset,  
  DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows);  
```  
  
#### <a name="parameters"></a>Parametry  
 *lRowsOffset*  
 Pozycja kursora wiersza tworzona.  
  
 *cRowsObtained*  
 Odwołania przekazywane z powrotem do użytkownika wskazującą liczbę wierszy tworzone.  
  
 *rgRows*  
 Tablica **HROW**s zwróconych z uchwytami nowo utworzony wiersza.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli istnieje wiersz, ta metoda wywołuje [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) i zwraca. W przeciwnym razie przydziela nowe wystąpienie klasy RowClass zmiennej szablonu i dodanie go do [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetImpl, klasa](../../data/oledb/irowsetimpl-class.md)