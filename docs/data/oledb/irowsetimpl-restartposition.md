---
title: IRowsetImpl::RestartPosition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c42e3685f1d857d60a4586544bf01a8a7d09f011
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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