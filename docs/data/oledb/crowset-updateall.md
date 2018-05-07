---
title: CRowset::UpdateAll | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset::UpdateAll
- ATL.CRowset.UpdateAll
- CRowset<TAccessor>.UpdateAll
- ATL.CRowset<TAccessor>.UpdateAll
- UpdateAll
- CRowset.UpdateAll
- ATL::CRowset<TAccessor>::UpdateAll
- CRowset<TAccessor>::UpdateAll
- ATL::CRowset::UpdateAll
dev_langs:
- C++
helpviewer_keywords:
- UpdateAll method
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9e21cd34a4d758becb12b529fe858e96d18f187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetupdateall"></a>CRowset::UpdateAll
Wysyła wszystkie oczekujące zmiany do wszystkich wierszy od czasu ostatniego pobrania lub **aktualizacji** wywoływać w nim.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT UpdateAll(DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcRows`  
 [out] Wskaźnik do lokalizacji, gdzie `UpdateAll` zwraca liczbę wierszy nastąpiła próba aktualizacji, jeśli jest to wymagane.  
  
 `pphRow`  
 [out] Wskaźnik do pamięci, do której `UpdateAll` Zwraca dojście go podjęła próbę zaktualizowania wiersza. Dojście nie jest zwracana, gdy `pphRow` ma wartość null.  
  
 `ppStatus`  
 [out] Wskaźnik do lokalizacji, gdzie **aktualizacji** zwraca wartość stanu wiersza. Brak stanu jest zwracany, gdy `ppStatus` ma wartość null.  
  
## <a name="remarks"></a>Uwagi  
 Wysyła wszystkie oczekujące zmiany do wszystkich wierszy, ponieważ te wiersze zostały ostatniego pobrania lub zaktualizować za pomocą [aktualizacji](../../data/oledb/crowset-update.md) lub `UpdateAll`. `UpdateAll` zaktualizuje każdego wiersza, który został zmodyfikowany, niezależnie od tego, czy nadal masz dojście dla nich (zobacz `pphRow`) czy nie.  
  
 Na przykład jeśli użyto **Wstaw** Aby wstawić pięć wierszy w zestawie wierszy, można albo wywołanie **aktualizacji** pięć razy lub wywołanie `UpdateAll` raz, aby zaktualizować je wszystkie.  
  
 Ta metoda wymaga opcjonalny interfejs `IRowsetUpdate`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetUpdate** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)