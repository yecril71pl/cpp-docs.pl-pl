---
title: CRowset::UpdateAll | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: UpdateAll method
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5842fb52d2dae255186bb3e56da6e5a6744e1f0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetupdateall"></a>CRowset::UpdateAll
Wysyła wszystkie oczekujące zmiany do wszystkich wierszy od czasu ostatniego pobrania lub **aktualizacji** wywoływać w nim.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT UpdateAll(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcRows`  
 [out] Wskaźnik do lokalizacji, gdzie `UpdateAll` zwraca liczbę wierszy nastąpiła próba aktualizacji, jeśli jest to wymagane.  
  
 `pphRow`  
 [out] Wskaźnik do pamięci, do której `UpdateAll` Zwraca dojście go podjęła próbę zaktualizowania wiersza. Dojście nie jest zwracana, gdy `pphRow` ma wartość null.  
  
 `ppStatus`  
 [out] Wskaźnik do lokalizacji, gdzie **aktualizacji** zwraca wartość stanu wiersza. Brak stanu jest zwracany, gdy `ppStatus` ma wartość null.  
  
## <a name="remarks"></a>Uwagi  
 Wysyła wszystkie oczekujące zmiany do wszystkich wierszy, ponieważ te wiersze zostały ostatniego pobrania lub zaktualizować za pomocą [aktualizacji](../../data/oledb/crowset-update.md) lub `UpdateAll`. `UpdateAll`zaktualizuje każdego wiersza, który został zmodyfikowany, niezależnie od tego, czy nadal masz dojście dla nich (zobacz `pphRow`) czy nie.  
  
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