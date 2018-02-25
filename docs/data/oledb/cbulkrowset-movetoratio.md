---
title: CBulkRowset::MoveToRatio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
dev_langs:
- C++
helpviewer_keywords:
- MoveToRatio method
ms.assetid: 86be60f5-9341-44c1-8e1e-9174c082d0d5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 675d2ec6c9a43e7f5b17acdb0c546e003fd5e986
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cbulkrowsetmovetoratio"></a>CBulkRowset::MoveToRatio
Pobiera wiersze, zaczynając od pozycji ułamkowych w zestawie wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,  
   DBCOUNTITEM nDenominator)throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nNumerator`  
 [in] Licznik używany do określenia pozycji ułamkową, z którego można pobrać danych.  
  
 `nDenominator`  
 [in] Mianownik używany do określenia pozycji ułamkową, z którego można pobrać danych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 `MoveToRatio` Pobiera wiersze około według następującego wzoru:  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 gdzie `RowsetSize` rozmiar wierszy, mierzony w wierszach. Dokładność formuły zależy od określonego dostawcy. Aby uzyskać więcej informacji, zobacz [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CBulkRowset, klasa](../../data/oledb/cbulkrowset-class.md)