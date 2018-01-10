---
title: IAccessorImpl::CreateAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
dev_langs: C++
helpviewer_keywords: CreateAccessor method
ms.assetid: f6b92075-c0b8-46ca-8361-026d562d24f5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 52c15b9f7c7f2b1a304cd5f05b4c05af6394977e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iaccessorimplcreateaccessor"></a>IAccessorImpl::CreateAccessor
Tworzy metody dostępu przy użyciu zestawu powiązań.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD(CreateAccessor)(  
   DBACCESSORFLAGS dwAccessorFlags,  
   DBCOUNTITEM cBindings,  
   const DBBINDING rgBindings[],  
   DBLENGTH cbRowSize,  
   HACCESSOR* phAccessor,  
   DBBINDSTATUS rgStatus[]   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IAccessor::CreateAccessor](https://msdn.microsoft.com/en-us/library/ms720969.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Iaccessorimpl — klasa](../../data/oledb/iaccessorimpl-class.md)   
 [IAccessorImpl::AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)   
 [IAccessorImpl::ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)