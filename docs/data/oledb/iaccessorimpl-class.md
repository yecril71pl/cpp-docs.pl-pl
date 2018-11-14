---
title: IAccessorImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
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
ms.openlocfilehash: a01a090d4302983f7d53e051cf4d8a72bd739b4a
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556741"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl — Klasa

Udostępnia implementację [IAccessor](https://docs.microsoft.com/previous-versions/windows/desktop/ms719672(v=vs.85)) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasy obiektu zestawu wierszy lub polecenie.

*BindType*<br/>
Jednostki magazynu, aby uzyskać informacje o powiązaniu. Wartość domyślna to `ATLBINDINGS` struktury (patrz atldb.h).

*BindingVector*<br/>
Jednostki magazynu na potrzeby informacji o kolumnie. Wartość domyślna to [CAtlMap](../../atl/reference/catlmap-class.md) którym kluczowy element jest wartością HACCESSOR i element wartości jest wskaźnikiem do `BindType` struktury.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Iaccessorimpl —](#iaccessorimpl)|Konstruktor.|

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|Dodaje licznik odwołań do istniejącej metody dostępu.|
|[CreateAccessor](#createaccessor)|Tworzy metodę dostępu na podstawie zestawu powiązania.|
|[Getbindings —](#getbindings)|Zwraca powiązania w metodzie dostępu.|
|[ReleaseAccessor](#releaseaccessor)|Udostępnia metody dostępu.|

## <a name="remarks"></a>Uwagi

Jest to parametr obowiązkowy dla polecenia i zestawy wierszy. OLE DB wymaga dostawców w celu zaimplementowania HACCESSOR, czyli tag do tablicy [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) struktury. Dostarczone przez HACCESSORs `IAccessorImpl` są adresy `BindType` struktury. Domyślnie `BindType` jest zdefiniowany jako `ATLBINDINGS` w `IAccessorImpl`w definicji szablonu. `BindType` udostępnia mechanizm używany przez `IAccessorImpl` śledzić liczbę elementów w jego `DBBINDING` tablicy, a także flagi metody dostępu i liczba odwołań.

## <a name="iaccessorimpl"></a> IAccessorImpl::IAccessorImpl

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a> IAccessorImpl::AddRefAccessor

Dodaje licznik odwołań do istniejącej metody dostępu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parametry

Zobacz [IAccessor::AddRefAccessor](https://docs.microsoft.com/previous-versions/windows/desktop/ms714978(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="createaccessor"></a> IAccessorImpl::CreateAccessor

Tworzy metodę dostępu na podstawie zestawu powiązania.

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

Zobacz [IAccessor::CreateAccessor](https://docs.microsoft.com/previous-versions/windows/desktop/ms720969(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="getbindings"></a> IAccessorImpl::GetBindings

Zwraca powiązania kolumny podstawowe od konsumenta w metodzie dostępu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Parametry

Zobacz [IAccessor::GetBindings](https://docs.microsoft.com/previous-versions/windows/desktop/ms721253(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="releaseaccessor"></a> IAccessorImpl::ReleaseAccessor

Udostępnia metody dostępu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parametry

Zobacz [IAccessor::ReleaseAccessor](https://docs.microsoft.com/previous-versions/windows/desktop/ms719717(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)