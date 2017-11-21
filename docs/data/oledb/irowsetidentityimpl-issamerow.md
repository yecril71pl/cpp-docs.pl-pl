---
title: IRowsetIdentityImpl::IsSameRow | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs: C++
helpviewer_keywords: IsSameRow method
ms.assetid: e35ad54e-73f1-4dc0-8d8c-9e98202baf0a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: baab48b21ab624d285fecac0e888f8d32e86342b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetidentityimplissamerow"></a>IRowsetIdentityImpl::IsSameRow
Porównuje dwa dojść do wierszy czy odnoszą się do tego samego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD( IsSameRow )(  
   HROW hThisRow,  
   HROW hThatRow   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Aby porównać dojść do wierszy, ta metoda rzutuje **HROW** uchwytów na **RowClass** elementów członkowskich i wywołania `memcmp` na wskaźnikach.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetidentityimpl — klasa](../../data/oledb/irowsetidentityimpl-class.md)