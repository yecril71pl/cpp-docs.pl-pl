---
title: IDBCreateCommandImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: 2ac243f5e2c91636183c31640b50fa7bef95254d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459023"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl — Klasa

Udostępnia implementację [IDBCreateCommand](/previous-versions/windows/desktop/ms711625) interfejsu.

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

Zobacz [IDBCreateCommand::CreateCommand](/previous-versions/windows/desktop/ms709772) w *OLE DB Podręcznik programisty*.

Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które są opisane w `IDBCreateCommand::CreateCommand`:

|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)