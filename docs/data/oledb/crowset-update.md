---
title: CRowset::Update | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset.Update
- ATL.CRowset.Update
- ATL.CRowset<TAccessor>.Update
- ATL::CRowset<TAccessor>::Update
- CRowset<TAccessor>::Update
- CRowset::Update
- CRowset<TAccessor>.Update
- ATL::CRowset::Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: cd5fedc8-2b85-4cb8-8c40-c79576316903
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b40486db73d3d545a3226e71a19ba0b588f631ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098137"
---
# <a name="crowsetupdate"></a>CRowset::Update
Wysyła wszystkie oczekujące zmiany do bieżącego wiersza od czasu ostatniego pobrania lub **aktualizacji** wywoływać w nim.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Update(DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcRows`  
 [out] Wskaźnik do lokalizacji, gdzie **aktualizacji** zwraca liczbę wierszy nastąpiła próba aktualizacji, jeśli jest to wymagane.  
  
 `phRow`  
 [out] Wskaźnik do lokalizacji, gdzie **aktualizacji** Zwraca dojście go podjęła próbę zaktualizowania wiersza. Dojście nie jest zwracana, gdy `phRow` ma wartość null.  
  
 `pStatus`  
 [out] Wskaźnik do lokalizacji, gdzie **aktualizacji** zwraca wartość stanu wiersza. Brak stanu jest zwracany, gdy `pStatus` ma wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Wysyła wszystkie oczekujące zmiany do bieżącego wiersza od czasu ostatniego pobrania lub zaktualizować ten wiersz (przy użyciu **aktualizacji** lub [UpdateAll](../../data/oledb/crowset-updateall.md)). Zwykle wywołują [SetData](../../data/oledb/crowset-setdata.md) wartości danych w kolumnach w wierszu, a następnie wywołać **aktualizacji** do przesyłania tych zmian.  
  
 Ta metoda wymaga opcjonalny interfejs `IRowsetUpdate`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetUpdate** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)