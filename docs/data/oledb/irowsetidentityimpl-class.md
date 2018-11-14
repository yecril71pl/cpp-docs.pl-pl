---
title: IRowsetIdentityImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: b70ebdaa44331d9fa545763f0dd19e6320dd652b
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556221"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl — Klasa

Implementuje OLE DB [IRowsetIdentity](https://docs.microsoft.com/previous-versions/windows/desktop/ms715913(v=vs.85)) interfejs, który umożliwia testowanie pod kątem tożsamość wiersza.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodząca z `IRowsetIdentityImpl`.

*RowClass*<br/>
Jednostki magazynu na potrzeby `HROW`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Issamerow —](#issamerow)|Porównuje dwa uchwytów wierszy, aby sprawdzić, czy odnoszą się do tego samego wiersza.|

## <a name="issamerow"></a> IRowsetIdentityImpl::IsSameRow

Porównuje dwa uchwytów wierszy, aby sprawdzić, czy odnoszą się do tego samego wiersza.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetIdentity::IsSameRow](https://docs.microsoft.com/previous-versions/windows/desktop/ms719629(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Aby porównać dojść do wierszy, ta metoda rzutuje `HROW` uchwytów na `RowClass` elementów członkowskich i wywołania `memcmp` na wskaźniki.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)