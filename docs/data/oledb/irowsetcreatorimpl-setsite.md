---
title: IRowsetCreatorImpl::SetSite | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
dev_langs:
- C++
helpviewer_keywords:
- SetSite method
ms.assetid: e92e63d5-93e4-4ee0-9ef7-bb6583cc8091
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: af2883b261b754cee04e2c5090d1ef9b9887c04f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetcreatorimplsetsite"></a>IRowsetCreatorImpl::SetSite
Określa lokację, która zawiera obiekt zestawu wierszy. Aby uzyskać więcej informacji, zobacz [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(SetSite )(IUnknown* pCreator);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCreator`  
 [in] Wskaźnik do **IUnknown** wskaźnika interfejsu witryny Zarządzanie obiektu zestawu wierszy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ponadto `IRowsetCreatorImpl::SetSite` umożliwia OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS** właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetCreatorImpl, klasa](../../data/oledb/irowsetcreatorimpl-class.md)