---
title: IAccessorImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: 356278b316912bdb81f1c43bbf2034f00ec3d785
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845617"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl — Klasa

Zapewnia implementację interfejsu [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Zestaw wierszy lub Klasa obiektu polecenia.

*BindType*<br/>
Jednostka magazynowa służąca do powiązania informacji. Wartość domyślna to `ATLBINDINGS` Struktura (zobacz ATLDB. h).

*BindingVector*<br/>
Jednostka magazynowa dla informacji o kolumnie. Wartość domyślna to [CAtlMap](../../atl/reference/catlmap-class.md) , gdzie element key jest wartością HACCESSOR, a element Value jest wskaźnikiem do `BindType` struktury.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[IAccessorImpl](#iaccessorimpl)|Konstruktor.|

### <a name="interface-methods"></a>Metody interfejsu

| Nazwa | Opis |
|-|-|
|[AddRefAccessor](#addrefaccessor)|Dodaje liczbę odwołań do istniejącej metody dostępu.|
|[CreateAccessor](#createaccessor)|Tworzy metodę dostępu z zestawu powiązań.|
|[GetBindings](#getbindings)|Zwraca powiązania w metodzie dostępu.|
|[ReleaseAccessor](#releaseaccessor)|Zwalnia metodę dostępu.|

## <a name="remarks"></a>Uwagi

Jest to obowiązkowe dla zestawów wierszy i poleceń. OLE DB wymaga od dostawców zaimplementowania HACCESSOR, który jest tagiem tablicy struktur [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) . HACCESSORs podane przez `IAccessorImpl` są adresami `BindType` struktur. Domyślnie `BindType` jest definiowana jako `ATLBINDINGS` `IAccessorImpl` Definicja szablonu w. `BindType` zapewnia mechanizm używany przez program `IAccessorImpl` do śledzenia liczby elementów w `DBBINDING` tablicy, a także liczby odwołań i flag dostępu.

## <a name="iaccessorimpliaccessorimpl"></a><a name="iaccessorimpl"></a> IAccessorImpl:: IAccessorImpl

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
IAccessorImpl();
```

## <a name="iaccessorimpladdrefaccessor"></a><a name="addrefaccessor"></a> IAccessorImpl:: AddRefAccessor

Dodaje liczbę odwołań do istniejącej metody dostępu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parametry

Zobacz [IAccessor:: AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="iaccessorimplcreateaccessor"></a><a name="createaccessor"></a> IAccessorImpl:: isdostępu

Tworzy metodę dostępu z zestawu powiązań.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [IAccessor:: textaccess](/previous-versions/windows/desktop/ms720969(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="iaccessorimplgetbindings"></a><a name="getbindings"></a> IAccessorImpl:: GetBindings

Zwraca podstawowe powiązania kolumn od konsumenta w metodzie dostępu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Parametry

Zobacz [IAccessor:: GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="iaccessorimplreleaseaccessor"></a><a name="releaseaccessor"></a> IAccessorImpl:: ReleaseAccessor

Zwalnia metodę dostępu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parametry

Zobacz [IAccessor:: ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
