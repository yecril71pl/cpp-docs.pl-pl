---
title: CRowset::MoveNext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.MoveNext
- ATL.CRowset.MoveNext
- ATL::CRowset<TAccessor>::MoveNext
- CRowset<TAccessor>.MoveNext
- CRowset.MoveNext
- CRowset<TAccessor>::MoveNext
- CRowset::MoveNext
- ATL::CRowset::MoveNext
dev_langs: C++
helpviewer_keywords: MoveNext method
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e2b0a3a3a10ae2cc18ab83800cc50f25903a3607
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetmovenext"></a>CRowset::MoveNext
Przesuwa kursor do następnego rekordu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT MoveNext( ) throw( );   
HRESULT MoveNext(   
   LONG lSkip,   
   bool bForward = true    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `lSkip`  
 [in] Liczba wierszy do pominięcia przed pobierania.  
  
 `bForward`  
 [in] Przekaż **true** przejścia do następnego rekordu **false** do tyłu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`. Osiągnięto koniec zestawu wierszy, zwraca **DB_S_ENDOFROWSET**.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera następnego wiersza sekwencyjnych z `CRowset` obiektu zapamiętywanie poprzedniej pozycji. Opcjonalnie możesz przejść od razu `lSkip` wierszy lub przenoszenie z poprzednimi wersjami.  
  
 Ta metoda wymaga, aby ustawić następujące właściwości przed wywołaniem **Otwórz** tabeli lub zawierający zestaw wierszy polecenia:  
  
-   **DBPROP_CANSCROLLBACKWARDS** musi być `VARIANT_TRUE` Jeśli `lSkip` < 0  
  
-   **DBPROP_CANFETCHBACKWARDS** musi być `VARIANT_TRUE` Jeśli `bForward` = false  
  
 W przeciwnym razie (Jeśli `lSkip` > = 0 i `bForward` = true), nie trzeba ustawiać żadnych dodatkowych właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)