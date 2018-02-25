---
title: IRowsetUpdateImpl::SetData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
dev_langs:
- C++
helpviewer_keywords:
- SetData method
ms.assetid: 7288a8d1-a7cf-4957-b832-0f3b18fd0da4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 475951b0914e63dcbb0213ffb673677c49b74c17
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetupdateimplsetdata"></a>IRowsetUpdateImpl::SetData
Ustawia wartości danych w co najmniej jedną kolumnę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetChange::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) metoda zawiera jednak buforowanie oryginalnych danych jest bezpośrednim lub odroczonego przetwarzanie operacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetUpdateImpl, klasa](../../data/oledb/irowsetupdateimpl-class.md)