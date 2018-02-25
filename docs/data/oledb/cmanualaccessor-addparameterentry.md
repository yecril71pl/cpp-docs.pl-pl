---
title: CManualAccessor::AddParameterEntry | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
dev_langs:
- C++
helpviewer_keywords:
- AddParameterEntry method
ms.assetid: 9048b164-052b-41b1-a861-227fc529e0b5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab686bfed7abd3bece3effbcf9f5e2b98132bb8b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cmanualaccessoraddparameterentry"></a>CManualAccessor::AddParameterEntry
Dodaje wpis parametru do struktury zapis parametru.  
  
## <a name="syntax"></a>Składnia  
  
```
void AddParameterEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) w *OLE DB Podręcznik programisty*.  
  
 `nOrdinal`  
 [in] Liczba parametrów.  
  
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
  
 *eParamIO*  
 [in] Określa, czy parametr, z którym skojarzony jest powiązanie parametrów wejściowych, wejścia/wyjścia lub wyjściowych.  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć tej funkcji, należy najpierw wywołać [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cmanualaccessor — klasa](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)   
 [Przykładowe DBViewer](../../visual-cpp-samples.md)