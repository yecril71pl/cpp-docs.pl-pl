---
title: "Idbcreatecommandimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3a4e5d676c004c7439b58631e87fbe0ac1e1af22
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl — Klasa
Udostępnia implementację elementu [IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Obiekt sesji jest pochodną `IDBCreateCommandImpl`.  
  
 `CommandClass`  
 Klasy poleceń.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[CreateCommand](../../data/oledb/idbcreatecommandimpl-createcommand.md)|Tworzy nowe polecenie.|  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalny interfejs dla obiektu sesji można uzyskać nowe polecenie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)