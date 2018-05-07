---
title: IRowsetImpl::RestartPosition | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
dev_langs:
- C++
helpviewer_keywords:
- RestartPosition method
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c203cc19e31f22df5903f099e953fcf5663718f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetimplrestartposition"></a>IRowsetImpl::RestartPosition
Zmienia położenie dalej pozycji pobierania do pozycji początkowej; oznacza to utworzyć jej położenie podczas pierwszego zestawu wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Pozycja zestawu wierszy jest niezdefiniowana do **GetNextRow** jest wywoływana. Można przenosić wstecz rowet przez wywołanie metody `RestartPosition` i pobierania lub przewijanie do tyłu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetImpl, klasa](../../data/oledb/irowsetimpl-class.md)