---
title: Icommandimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandImpl class
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d69ff56ec92fd3acb622aa4c0399893fb44c4d1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icommandimpl-class"></a>ICommandImpl — Klasa
Udostępnia implementację dla [ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `ICommandImpl`.  
  
 `CommandBase`  
 Interfejs polecenia. Wartość domyślna to `ICommand`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|Anuluje bieżący wykonywania polecenia.|  
|[Anulowanie](../../data/oledb/icommandimpl-cancel.md)|Anuluje bieżący wykonywania polecenia.|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|Tworzy obiekt zestawu wierszy.|  
|[Wykonanie](../../data/oledb/icommandimpl-execute.md)|Wykonuje polecenia.|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|Zwraca wskaźnik interfejsu do sesji, który utworzony polecenia.|  
|[Icommandimpl —](../../data/oledb/icommandimpl-icommandimpl.md)|Konstruktor.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|Wskazuje, czy polecenie ma być anulowane.|  
|[m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|Wskazuje, czy ma być anulowane podczas wykonywania polecenia.|  
|[m_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|Wskazuje, czy polecenie jest aktualnie wykonywany.|  
  
## <a name="remarks"></a>Uwagi  
 Obowiązkowego interfejsu dla obiektu polecenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)