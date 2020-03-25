---
title: IConvertTypeImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: e3b76be2a1f1edfcdc1139a3dd396835923c2b4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210694"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl — Klasa

Zapewnia implementację interfejsu [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa, która pochodzi od `IConvertTypeImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[Przekonwertuj](#canconvert)|Podaje informacje o dostępności konwersji typu dla polecenia lub zestawu wierszy.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest obowiązkowy dla poleceń, zestawów wierszy i zestawów wierszy indeksu. `IConvertTypeImpl` implementuje interfejs poprzez delegowanie do obiektu konwersji dostarczonego przez OLE DB.

## <a name="iconverttypeimplcanconvert"></a><a name="canconvert"></a>IConvertTypeImpl —:: setconvert

Podaje informacje o dostępności konwersji typu dla polecenia lub zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Parametry

Zobacz [IConvertType:: deconvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) in the *OLE DB programmer's Reference*.

### <a name="remarks"></a>Uwagi

Używa konwersji danych OLE DB w `MSADC.DLL`.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
