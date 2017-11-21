---
title: IRowsetImpl::RestartPosition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
dev_langs: C++
helpviewer_keywords: RestartPosition method
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28aeb5548235fc49c8dd4c412e2a27eaa38a02d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplrestartposition"></a>IRowsetImpl::RestartPosition
Zmienia położenie dalej pozycji pobierania do pozycji początkowej; oznacza to utworzyć jej położenie podczas pierwszego zestawu wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD( RestartPosition )(  
   HCHAPTER /* hReserved */   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Pozycja zestawu wierszy jest niezdefiniowana do **GetNextRow** jest wywoływana. Można przenosić wstecz rowet przez wywołanie metody `RestartPosition` i pobierania lub przewijanie do tyłu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetimpl — klasa](../../data/oledb/irowsetimpl-class.md)