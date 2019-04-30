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
ms.openlocfilehash: 7450d91cd5e5383b55e2ebb391fe5f1190cbed2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408917"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl — Klasa

Udostępnia implementację [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) interfejsu.

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
|[CreateCommand](#createcommand)|Tworzy nowe polecenie.|

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

Zobacz [IDBCreateCommand::CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) w *OLE DB Podręcznik programisty*.

Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które są opisane w `IDBCreateCommand::CreateCommand`:

|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)