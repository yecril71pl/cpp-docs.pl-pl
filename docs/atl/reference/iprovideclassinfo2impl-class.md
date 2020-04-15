---
title: Klasa IProvideClassInfo2Impl
ms.date: 11/04/2016
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
ms.openlocfilehash: 0d1ee9acc1cfabc71ecf33fcb5919d826899c671
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329567"
---
# <a name="iprovideclassinfo2impl-class"></a>Klasa IProvideClassInfo2Impl

Ta klasa zapewnia domyślną implementację metod [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) i [IProvideClassInfo2.](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)

## <a name="syntax"></a>Składnia

```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```

#### <a name="parameters"></a>Parametry

*pcoclsid ( pcoclsid )*<br/>
Wskaźnik do identyfikatora coclass.

*psrcid ( psrcid )*<br/>
Wskaźnik do identyfikatora domyślnego wychodzącego dispinterface coclass.

*plibid ( plibid )*<br/>
Wskaźnik do libid biblioteki typów, który zawiera informacje o interfejsie. Domyślnie biblioteka typów na poziomie serwera jest przekazywana.

*wMajor*<br/>
Główna wersja biblioteki typów. Wartość domyślna to 1.

*wMinor*<br/>
Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.

*tihclass (klasa tihclass)*<br/>
Klasa używana do zarządzania informacjami o typie coclass. Wartością domyślną jest `CComTypeInfoHolder`.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Nazwa|Opis|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Pobiera `ITypeInfo` wskaźnik do informacji o typie coclass.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Pobiera identyfikator GUID dla wychodzącego dispinterface obiektu.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Zarządza informacjami o typie dla coclass.|

## <a name="remarks"></a>Uwagi

[Interfejs IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) rozszerza [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) przez `GetGUID` dodanie metody. Ta metoda umożliwia klientowi pobranie identyfikatora interfejsu wychodzącego obiektu dla jego domyślnego zestawu zdarzeń. Klasa `IProvideClassInfo2Impl` zapewnia domyślną `IProvideClassInfo` implementację i `IProvideClassInfo2` metody.

`IProvideClassInfo2Impl`zawiera statyczny element `CComTypeInfoHolder` członkowski typu, który zarządza informacjami o typie dla coclass.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>IProvideClassInfo2Impl::GetClassInfo

Pobiera `ITypeInfo` wskaźnik do informacji o typie coclass.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Uwagi

Zobacz [IProvideClassInfo::GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) w usłudze Windows SDK.

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a>IProvideClassInfo2Impl::GetGUID

Pobiera identyfikator GUID dla wychodzącego dispinterface obiektu.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Uwagi

Zobacz [IProvideClassInfo2::GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) w windows SDK.

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl

Konstruktor.

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Uwagi

Wzywa `AddRef` [członka _tih.](#_tih) Destruktor wywołuje `Release`.

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a>IProvideClassInfo2Impl::_tih

Ten statyczny element członkowski danych jest wystąpieniem parametru szablonu `CComTypeInfoHolder`klasy, *tihclass*, który domyślnie jest .

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Uwagi

`_tih`zarządza informacjami o typie dla coclass.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
