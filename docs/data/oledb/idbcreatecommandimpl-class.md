---
title: IDBCreateCommandImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: b7b658b2b365eb84a39ae94cef7c77e18d7bd4a0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845552"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl — Klasa

Zapewnia implementację interfejsu [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>Parametry

*T*<br/>
Obiekt sesji pochodzący od `IDBCreateCommandImpl` .

*CommandClass*<br/>
Klasa poleceń.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

| Nazwa | Opis |
|-|-|
|[CreateCommand](#createcommand)|Tworzy nowe polecenie.|

## <a name="remarks"></a>Uwagi

Opcjonalny interfejs w obiekcie sesji, aby uzyskać nowe polecenie.

## <a name="idbcreatecommandimplcreatecommand"></a><a name="createcommand"></a> IDBCreateCommandImpl —:: SetCommand

Tworzy nowe polecenie i zwraca żądany interfejs.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Parametry

Zobacz [IDBCreateCommand:: SetCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) w *dokumentacji programisty OLE DB*.

Niektóre parametry odpowiadają parametrom *referencyjnym programisty OLE DB* różnymi nazwami, które są opisane w `IDBCreateCommand::CreateCommand` :

|OLE DB parametry szablonu|*OLE DB parametry odwołania programisty*|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
