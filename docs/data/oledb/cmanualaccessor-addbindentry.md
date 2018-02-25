---
title: CManualAccessor::AddBindEntry | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
dev_langs:
- C++
helpviewer_keywords:
- AddBindEntry method
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e99e9822b60152fc8daa6f101bcca2ea7e60c25
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cmanualaccessoraddbindentry"></a>CManualAccessor::AddBindEntry
Dodaje wpis powiązanie kolumn danych wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```
void AddBindEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) w *OLE DB Podręcznik programisty*.  
  
 `nOrdinal`  
 [in] Numer kolumny.  
  
 `wType`  
 [in] Typ danych.  
  
 `nColumnSize`  
 [in] Kolumna rozmiar w bajtach.  
  
 `pData`  
 [in] Wskaźnik do kolumny danych przechowywanych w buforze.  
  
 `pLength`  
 [in] Wskaźnik do długość pola, jeśli jest to wymagane.  
  
 `pStatus`  
 [in] Wskaźnik do zmiennej może być powiązane z stan kolumny, jeśli jest to wymagane.  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć tej funkcji, należy najpierw wywołać [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md). Nie można dodać więcej wpisów niż liczba kolumn określona w `CreateAccessor`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cmanualaccessor — klasa](../../data/oledb/cmanualaccessor-class.md)   
 [Przykładowe DBViewer](../../visual-cpp-samples.md)