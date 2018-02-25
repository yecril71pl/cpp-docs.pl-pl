---
title: CManualAccessor::CreateAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
dev_langs:
- C++
helpviewer_keywords:
- CreateAccessor method
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 44b9edf987baf9ff2470ed536a1c657025766f23
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cmanualaccessorcreateaccessor"></a>CManualAccessor::CreateAccessor
Przydziela pamięć dla kolumny struktury powiązania i inicjuje elementów członkowskich danych kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nBindEntries`  
 [in] Liczba kolumn. Liczba ta powinna być zgodna liczba wywołań [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) funkcji.  
  
 `pBuffer`  
 [in] Wskaźnik do buforu, gdzie są przechowywane w kolumnach wyjściowych.  
  
 `nBufferSize`  
 [in] Rozmiar buforu w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, przed wywołaniem `CManualAccessor::AddBindEntry` funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cmanualaccessor — klasa](../../data/oledb/cmanualaccessor-class.md)   
 [Przykładowe DBViewer](../../visual-cpp-samples.md)