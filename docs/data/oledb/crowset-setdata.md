---
title: CRowset::SetData | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b8885c6e64fa7e7e22f6858d916a8e1afa8738d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098475"
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