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
ms.openlocfilehash: c6d8a07ded3da02c21c4ee8c528474efc6e52b6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021567"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl — Klasa

Udostępnia implementację [IDBCreateCommand](/previous-versions/windows/desktop/ms711625\(v=vs.85\)) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Obiekt sesji jest pochodną `IDBCreateCommandImpl`.  
  
*CommandClass*<br/>
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

Zobacz [IDBCreateCommand::CreateCommand](/previous-versions/windows/desktop/ms709772\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które są opisane w `IDBCreateCommand::CreateCommand`:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>Zobacz też  

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)