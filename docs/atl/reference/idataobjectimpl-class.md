---
title: Klasa IDataObjectImpl
ms.date: 11/04/2016
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
ms.openlocfilehash: b73cfe83075b9595bc98ca05ab2ec2e1771a038d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275467"
---
# <a name="idataobjectimpl-class"></a>Klasa IDataObjectImpl

Ta klasa dostarcza metody do obsługi jednolitego transferu danych i zarządzania połączeniami.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IDataObjectImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Ustanawia połączenie między obiektu danych, jak i ujście porada. Dzięki temu ujścia Porada otrzymywać powiadomienia o zmianach w obiekcie.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Przerywa połączenie wcześniej ustanowione przez `DAdvise`.|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Tworzy moduł wyliczający do iterowania po bieżących połączeń doradztwa.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Tworzy moduł wyliczający do iterowania po `FORMATETC` konstrukcje obsługiwane przez obiekt danych. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Wysyła powiadomienie o zmianie do każdego obiektu sink porada.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Pobiera logicznie równoważne `FORMATETC` struktury na taki, który jest bardziej złożona. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Przesyła dane z obiektu danych do klienta. Dane są opisane w `FORMATETC` struktury i są przesyłane za pośrednictwem `STGMEDIUM` struktury.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Podobnie jak `GetData`, z wyjątkiem klienta należy przydzielić `STGMEDIUM` struktury. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Określa, czy obiekt danych obsługuje określonego `FORMATETC` struktury do przesyłania danych. Implementacja biblioteki ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Przesyła dane z klienta do obiektu danych. Implementacja biblioteki ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) interfejs zapewnia metody umożliwiające obsługę jednolitego transferu danych. `IDataObject` używa struktury formatu standardowego [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) i [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) do pobierania i przechowywania danych.

`IDataObject` zarządza także połączenia, aby importowali ujścia w celu obsługi powiadomień o zmianach danych. Aby klient na odbieranie powiadomień o zmianach danych z obiektu danych, klient musi implementować [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interfejs do obiektu o nazwie ujścia porada. Kiedy klient następnie wywołuje `IDataObject::DAdvise`, zostaje nawiązane połączenie między obiektu danych, jak i ujście porada.

Klasa `IDataObjectImpl` udostępnia domyślną implementację elementu `IDataObject` i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="dadvise"></a>  IDataObjectImpl::DAdvise

Ustanawia połączenie między obiektu danych, jak i ujście porada.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Uwagi

Dzięki temu ujścia Porada otrzymywać powiadomienia o zmianach w obiekcie.

Aby zakończyć połączenie, należy wywołać [DUnadvise](#dunadvise).

Zobacz [IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) w Windows SDK.

##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise

Przerywa połączenie wcześniej ustanowione przez [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) w Windows SDK.

##  <a name="enumdadvise"></a>  IDataObjectImpl::EnumDAdvise

Tworzy moduł wyliczający do iterowania po bieżących połączeń doradztwa.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::EnumDAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-enumdadvise) w Windows SDK.

##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc

Tworzy moduł wyliczający do iterowania po `FORMATETC` konstrukcje obsługiwane przez obiekt danych.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange

Wysyła powiadomienie o zmianie do każdego obiektu sink Porada, który jest obecnie zarządzany.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc

Pobiera logicznie równoważne `FORMATETC` struktury na taki, który jest bardziej złożona.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::GetCanonicalFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) w Windows SDK.

##  <a name="getdata"></a>  IDataObjectImpl::GetData

Przesyła dane z obiektu danych do klienta.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Uwagi

*PformatetcIn* parametr musi określać typ średnie magazynu TYMED_MFPICT.

Zobacz [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) w Windows SDK.

##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere

Podobnie jak `GetData`, z wyjątkiem klienta należy przydzielić `STGMEDIUM` struktury.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [Metoda IDataObject::GetDataHere](/windows/desktop/api/objidl/nf-objidl-idataobject-getdatahere) w Windows SDK.

##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData

Określa, czy obiekt danych obsługuje określonego `FORMATETC` struktury do przesyłania danych.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) w Windows SDK.

##  <a name="setdata"></a>  IDataObjectImpl::SetData

Przesyła dane z klienta do obiektu danych.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Wartość zwracana

Returns E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::SetData](/windows/desktop/api/objidl/nf-objidl-idataobject-setdata) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
