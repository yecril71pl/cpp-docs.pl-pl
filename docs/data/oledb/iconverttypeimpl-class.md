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
ms.openlocfilehash: 0b3c0f239b3c80d0b4d3c8425b03a3612a0e6db2
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556234"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl — Klasa

Udostępnia implementację [IConvertType](https://docs.microsoft.com/previous-versions/windows/desktop/ms715926(v=vs.85)) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IConvertTypeImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[CanConvert](#canconvert)|Udostępnia informacje o dostępności konwersje typów dotyczącą polecenia lub w zestawie wierszy.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest obowiązkowa w przypadku poleceń, zestawy wierszy i zestawy wierszy indeksu. `IConvertTypeImpl` implementuje interfejs przez delegowanie do konwersji obiektu pochodzącego z OLE DB.

## <a name="canconvert"></a> IConvertTypeImpl::CanConvert

Udostępnia informacje o dostępności konwersje typów dotyczącą polecenia lub w zestawie wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Parametry

Zobacz [IConvertType::CanConvert](https://docs.microsoft.com/previous-versions/windows/desktop/ms711224(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Używa konwersji danych OLE DB w `MSADC.DLL`.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)