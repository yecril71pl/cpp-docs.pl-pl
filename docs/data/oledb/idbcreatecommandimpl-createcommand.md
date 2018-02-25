---
title: IDBCreateCommandImpl::CreateCommand | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- CreateCommand method
ms.assetid: 50ffbf8b-2c07-4bcb-96c5-ffce4519c7f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 83566713a42de25fb2c0e515daa94ee61eed53ed
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="idbcreatecommandimplcreatecommand"></a>IDBCreateCommandImpl::CreateCommand
Tworzy nowe polecenie i zwraca wartość żądanego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IDBCreateCommand::CreateCommand](https://msdn.microsoft.com/en-us/library/ms709772.aspx) w *OLE DB Podręcznik programisty*.  
  
 Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które zostały opisane w **IDBCreateCommand::CreateCommand**:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IDBCreateCommandImpl, klasa](../../data/oledb/idbcreatecommandimpl-class.md)