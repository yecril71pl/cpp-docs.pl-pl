---
title: CRowset::SetData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.SetData
- SetData
- ATL::CRowset::SetData
- CRowset<TAccessor>.SetData
- CRowset::SetData
- ATL.CRowset.SetData
- CRowset.SetData
- CRowset<TAccessor>::SetData
- ATL::CRowset<TAccessor>::SetData
dev_langs:
- C++
helpviewer_keywords:
- SetData method
ms.assetid: 68125142-8510-4132-9393-e39efd39c784
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d9f42397ffaa186bfd96db454251c687b634d69
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetsetdata"></a>CRowset::SetData
Ustawia wartości danych w jednej lub kilku kolumn w wierszu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetData() const throw();   


HRESULT SetData(int nAccessor) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nAccessor`  
 [in] Liczba dostępu do użycia na potrzeby uzyskiwania dostępu do danych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać `SetData` formularz, który akceptuje żadnych argumentów, wszystkie metody dostępu są używane do aktualizowania. Zwykle wywołują **SetData** można ustawić wartości danych w kolumnach w wierszu, następnie wywołaj [aktualizacji](../../data/oledb/crowset-update.md) do przesyłania tych zmian.  
  
 Ta metoda wymaga opcjonalny interfejs `IRowsetChange`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetChange** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
 Operacja ustawienie może zakończyć się niepowodzeniem, jeśli co najmniej jedna kolumna nie jest zapisywalny. Zmodyfikuj mapy kursora, aby rozwiązać ten problem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)