---
title: IOpenRowsetImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 3d4f778f560b55f22c1c54185bea79af07949ceb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422763"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl — Klasa

Udostępnia implementację dla `IOpenRowset` interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Parametry

*SessionClass*<br/>
Z klasą pochodną `IOpenRowsetImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Createrowset —](#createrowset)|Tworzy obiekt zestawu wierszy. Nie jest wywoływana bezpośrednio przez użytkownika.|
|[OpenRowset](#openrowset)|Zostanie otwarty i zwraca zestawu wierszy, który zawiera wszystkie wiersze z jednej tabeli bazowej lub indeksu. (Nie w ATLDB. GODZ.)|

## <a name="remarks"></a>Uwagi

[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85)) interfejsu jest obowiązkowa, aby obiekt sesji. Otwiera i zwraca zestawu wierszy, który zawiera wszystkie wiersze z jednej tabeli bazowej lub indeksu.

## <a name="createrowset"></a> IOpenRowsetImpl::CreateRowset

Tworzy obiekt zestawu wierszy. Nie jest wywoływana bezpośrednio przez użytkownika. Zobacz [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) w *OLE DB Podręcznik programisty.*

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
Składowa klasy szablonu reprezentująca klasy zestawów wierszy przez użytkownika. Zwykle generowane przez kreatora.

*pRowsetObj*<br/>
[out] Wskaźnik do obiektu zestawu wierszy. Zazwyczaj ten parametr nie jest używany, ale mogą używane, jeśli konieczne jest przeprowadzenie więcej pracy na zestawie wierszy przed przekazaniem go do obiektu COM. Okres istnienia *pRowsetObj* jest ograniczone przez *ppRowset*.

Dla innych parametrów, zobacz [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) w *OLE DB Podręcznik programisty.*

## <a name="openrowset"></a> IOpenRowsetImpl::OpenRowset

Zostanie otwarty i zwraca zestawu wierszy, który zawiera wszystkie wiersze z jednej tabeli bazowej lub indeksu.

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

Zobacz [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Ta metoda nie znajduje się w ATLDB. H. Jest on tworzony przez kreatora ATL obiektu po utworzeniu dostawcy usługi.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)