---
title: IOpenRowsetImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 66fce9d2ffe63798738be1658a5328e907395a54
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446327"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl — Klasa

Zapewnia implementację interfejsu `IOpenRowset`.

## <a name="syntax"></a>Składnia

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Parametry

*SessionClass*<br/>
Klasa, która pochodzi od `IOpenRowsetImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CreateRowset](#createrowset)|Tworzy obiekt zestawu wierszy. Nie wywołano bezpośrednio przez użytkownika.|
|[OpenRowset](#openrowset)|Otwiera i zwraca zestaw wierszy, który zawiera wszystkie wiersze z pojedynczej tabeli bazowej lub indeksu. (Nie w ATLDB. C|

## <a name="remarks"></a>Uwagi

Interfejs [IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85)) jest obowiązkowy dla obiektu Session. Otwiera i zwraca zestaw wierszy, który zawiera wszystkie wiersze z pojedynczej tabeli podstawowej lub indeksu.

## <a name="createrowset"></a>IOpenRowsetImpl:: isrowset

Tworzy obiekt zestawu wierszy. Nie wywołano bezpośrednio przez użytkownika. Zobacz [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) w *dokumentacji programisty OLE DB.*

### <a name="syntax"></a>Składnia

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Parametry

*RowsetClass*<br/>
Składowa klasy szablonu reprezentująca klasę zestawu wierszy użytkownika. Zwykle generowany przez kreatora.

*pRowsetObj*<br/>
określoną Wskaźnik do obiektu zestawu wierszy. Zazwyczaj ten parametr nie jest używany, ale może być używany, jeśli trzeba wykonać więcej pracy na zestawie wierszy przed przekazaniem go do obiektu COM. Okres istnienia *pRowsetObj* jest związany z *ppRowset*.

Aby poznać inne parametry, zobacz [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) w *dokumentacji programisty OLE DB.*

## <a name="openrowset"></a>IOpenRowsetImpl:: OpenRowset

Otwiera i zwraca zestaw wierszy, który zawiera wszystkie wiersze z pojedynczej tabeli bazowej lub indeksu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Parametry

Zobacz [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Ta metoda nie została znaleziona w ATLDB. C. Jest tworzony przez kreatora obiektów ATL podczas tworzenia dostawcy.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)