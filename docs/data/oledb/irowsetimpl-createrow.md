---
title: IRowsetImpl::CreateRow | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
dev_langs: C++
helpviewer_keywords: CreateRow method
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f90a5de73b5eea37eea192a4886fe29d1d8b435b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetimplcreaterow"></a>IRowsetImpl::CreateRow
Metoda wywoływana przez metodę Pomocnika [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) można przydzielić nowego **HROW**.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT CreateRow(  
   DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows   
);  
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