---
title: CRowset::MoveToRatio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MoveToRatio
- CRowset<TAccessor>::MoveToRatio
- CRowset::MoveToRatio
- CRowset<TAccessor>.MoveToRatio
- ATL.CRowset.MoveToRatio
- ATL::CRowset::MoveToRatio
- CRowset.MoveToRatio
- ATL.CRowset<TAccessor>.MoveToRatio
- ATL::CRowset<TAccessor>::MoveToRatio
dev_langs:
- C++
helpviewer_keywords:
- MoveToRatio method
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: df1e7f51fb1bf82ced62c18a863f25870a4e4493
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetmovetoratio"></a>CRowset::MoveToRatio
Pobiera wiersze, zaczynając od pozycji ułamkowych w zestawie wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,bool bForward = true) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nNumerator`  
 [in] Licznik używany do określenia ułamkowych pozycyjnych, z którego można pobrać danych.  
  
 `nDenominator`  
 [in] Denominator używany do określenia ułamkowych pozycyjnych, z którego można pobrać danych.  
  
 `bForward`  
 [in] Wskazuje, czy do przeniesienia do przodu i do tyłu. Wartość domyślna to do przodu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 `MoveToRatio` pobiera wierszy, zgodnie z grubsza następującej formuły:  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 gdzie `RowsetSize` rozmiar wierszy, mierzony w wierszach. Dokładność formuły zależy od określonego dostawcy. Aby uzyskać więcej informacji, zobacz [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx).  
  
 Ta metoda wymaga opcjonalny interfejs `IRowsetScroll`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetScroll** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRowset, klasa](../../data/oledb/crowset-class.md)