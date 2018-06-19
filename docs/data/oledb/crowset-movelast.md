---
title: CRowset::MoveLast | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRowset<TAccessor>::MoveLast
- CRowset<TAccessor>::MoveLast
- ATL.CRowset.MoveLast
- ATL::CRowset::MoveLast
- CRowset<TAccessor>.MoveLast
- MoveLast
- CRowset::MoveLast
- ATL.CRowset<TAccessor>.MoveLast
- CRowset.MoveLast
dev_langs:
- C++
helpviewer_keywords:
- MoveLast method
ms.assetid: 81063578-ae9d-467b-8c88-81d8fc66e020
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d02447462393924a446889093c17f1ae0bafde3e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096395"
---
# <a name="crowsetmovelast"></a>CRowset::MoveLast
Przesuwa kursor do ostatniego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MoveLast() throw();  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) Aby zmienić lokalizację pobierania dalej do ostatniej pozycji i pobiera ostatni wiersz.  
  
 Ta metoda wymaga, aby ustawić **DBPROP_CANSCROLLBACKWARDS** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy. (W celu poprawy wydajności można również ustawić **DBPROP_QUICKRESTART** do `VARIANT_TRUE`.)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)