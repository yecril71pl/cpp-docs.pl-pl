---
title: Idbcreatecommandimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ffc92cecb3b28423aa2e869171f730c956996cd
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269754"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl — Klasa
Udostępnia implementację [IDBCreateCommand](https://msdn.microsoft.com/library/ms711625.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Obiekt sesji jest pochodną `IDBCreateCommandImpl`.  
  
 *CommandClass*  
 Klasa polecenia.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[CreateCommand —](#createcommand)|Tworzy nowe polecenie.|  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalny interfejs dla obiektu sesji można uzyskać nowe polecenie.  

## <a name="createcommand"></a> IDBCreateCommandImpl::CreateCommand
Tworzy nowe polecenie i zwraca żądanego interfejsu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IDBCreateCommand::CreateCommand](https://msdn.microsoft.com/library/ms709772.aspx) w *OLE DB Podręcznik programisty*.  
  
 Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które są opisane w `IDBCreateCommand::CreateCommand`:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
