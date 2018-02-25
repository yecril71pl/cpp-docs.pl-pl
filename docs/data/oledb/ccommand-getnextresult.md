---
title: CCommand::GetNextResult | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
dev_langs:
- C++
helpviewer_keywords:
- GetNextResult method
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa77785373545b2c4efd2faef0a8c0a02ee26910
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandgetnextresult"></a>CCommand::GetNextResult
Pobiera następnego wyniku, jeśli jest dostępny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,  
   bool bBind = true) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pulRowsAffected*  
 [We/Wy] Wskaźnik do pamięci, w której jest zwracana liczba wierszy, których to dotyczy, za pomocą polecenia.  
  
 `bBind`  
 [in] Określa, czy można powiązać polecenie automatycznie po wykonywana. Wartość domyślna to **true**, co powoduje, że polecenie może być powiązane automatycznie. Ustawienie `bBind` do **false** uniemożliwia automatyczne powiązania polecenie tak, aby można powiązać ręcznie. (Ręczne powiązanie jest znaczący użytkownikom OLAP).  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zestaw wyników zostaną pobrane wcześniej, ta funkcja zwalnia poprzedniego zestawu wyników i usuwa powiązanie kolumn. Jeśli `bBind` jest **true**, tworzy ona powiązanie nowe kolumny.  
  
 Tej funkcji należy wywołać tylko wtedy, gdy określono wiele wyników przez ustawienie `CCommand` parametr szablonu *TMultiple*=`CMultipleResults`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CCommand, klasa](../../data/oledb/ccommand-class.md)