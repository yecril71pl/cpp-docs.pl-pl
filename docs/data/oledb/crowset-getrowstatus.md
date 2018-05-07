---
title: CRowset::GetRowStatus | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset.GetRowStatus
- ATL.CRowset<TAccessor>.GetRowStatus
- ATL::CRowset<TAccessor>::GetRowStatus
- CRowset::GetRowStatus
- ATL::CRowset::GetRowStatus
- CRowset<TAccessor>::GetRowStatus
- ATL.CRowset.GetRowStatus
- CRowset<TAccessor>.GetRowStatus
- GetRowStatus
dev_langs:
- C++
helpviewer_keywords:
- GetRowStatus method
ms.assetid: 7a29a235-cb7e-40c1-92ce-5441751febee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3e3a0fb71a06a407a80a98717af53da926436f57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetgetrowstatus"></a>CRowset::GetRowStatus
Zwraca informacje o stanie wszystkich wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetRowStatus(DBPENDINGSTATUS* pStatus) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStatus`  
 [out] Wskaźnik do lokalizacji, gdzie `GetRowStatus` zwraca wartość stanu. Zobacz DBPENDINGSTATUS w odwołanie programisty OLE DB.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymaga opcjonalny interfejs `IRowsetUpdate`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetUpdate** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx)