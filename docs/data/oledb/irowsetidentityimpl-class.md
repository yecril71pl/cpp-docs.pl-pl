---
title: IRowsetIdentityImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 48ed687ff67208109b5a2acf400d98491b4c769a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836146"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl — Klasa

Implementuje interfejs OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85)) , który umożliwia testowanie tożsamości wiersza.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodna `IRowsetIdentityImpl` .

*RowClass*<br/>
Jednostka magazynowa dla `HROW` .

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[IsSameRow](#issamerow)|Porównuje dwa uchwyty wierszy, aby zobaczyć, czy odwołują się do tego samego wiersza.|

## <a name="irowsetidentityimplissamerow"></a><a name="issamerow"></a> IRowsetIdentityImpl —:: IsSameRow

Porównuje dwa uchwyty wierszy, aby zobaczyć, czy odwołują się do tego samego wiersza.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetIdentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Aby porównać uchwyty wierszy, ta metoda rzutuje `HROW` dojść do `RowClass` elementów członkowskich i wywołań `memcmp` na wskaźnikach.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
