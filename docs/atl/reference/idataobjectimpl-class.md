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
ms.openlocfilehash: 379dd3304d96afcd2b0e98ec4a98f1bac64d4ad9
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470774"
---
# <a name="idataobjectimpl-class"></a>Klasa IDataObjectImpl

Ta klasa udostępnia metody obsługi Uniform Data Transfer i zarządzania połączeniami.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `IDataObjectImpl` .

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDataObjectImpl::D Advise](#dadvise)|Nawiązuje połączenie między obiektem danych i ujściam. Dzięki temu ujścia doradza do otrzymywania powiadomień o zmianach w obiekcie.|
|[IDataObjectImpl::D Unadvise](#dunadvise)|Kończy połączenie wcześniej ustanowione przez `DAdvise` .|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Tworzy moduł wyliczający do iteracji przy użyciu bieżących połączeń doradczych.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Tworzy moduł wyliczający do iteracji przez `FORMATETC` struktury obsługiwane przez obiekt danych. Implementacja ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Wysyła powiadomienie o zmianie z powrotem do każdego z doradców.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Pobiera logicznie równoważną `FORMATETC` strukturę do jednej, która jest bardziej skomplikowana. Implementacja ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl:: GetData](#getdata)|Przenosi dane z obiektu danych do klienta. Dane są opisane w `FORMATETC` strukturze i są przesyłane przez `STGMEDIUM` strukturę.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Podobnie jak w `GetData` przypadku programu, z tą różnicą, że klient musi przydzielić `STGMEDIUM` strukturę. Implementacja ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Określa, czy obiekt danych obsługuje określoną `FORMATETC` strukturę transferu danych. Implementacja ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl:: SetData](#setdata)|Przesyła dane z klienta do obiektu danych. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Interfejs [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) zapewnia metody do obsługi Uniform Data Transfer. `IDataObject`program używa standardowych struktur formatu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) i [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) do pobierania i przechowywania danych.

`IDataObject`zarządza również połączeniami, aby doradzać ujściam do obsługi powiadomień o zmianach danych. Aby klient mógł odbierać powiadomienia o zmianach danych z obiektu danych, klient musi zaimplementować interfejs [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) na obiekcie o nazwie "Advise". Gdy klient wywołuje `IDataObject::DAdvise` program, połączenie zostanie nawiązane między obiektem danych i ujściam doradzania.

Klasa `IDataObjectImpl` udostępnia domyślną implementację `IDataObject` i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

**Related Articles** [Samouczki dotyczące biblioteki](../../atl/active-template-library-atl-tutorial.md)ATL, [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectImpl::D Advise

Nawiązuje połączenie między obiektem danych i ujściam.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Uwagi

Dzięki temu ujścia doradza do otrzymywania powiadomień o zmianach w obiekcie.

Aby przerwać połączenie, wywołaj [DUnadvise](#dunadvise).

Zobacz [IDataObject::D Advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) w Windows SDK.

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectImpl::D Unadvise

Kończy połączenie wcześniej ustanowione za pomocą [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::D Unadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) in Windows SDK.

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise

Tworzy moduł wyliczający do iteracji przy użyciu bieżących połączeń doradczych.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject:: EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) w Windows SDK.

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc

Tworzy moduł wyliczający do iteracji przez `FORMATETC` struktury obsługiwane przez obiekt danych.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject:: EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectImpl::FireDataChange

Wysyła powiadomienie o zmianie z powrotem do każdego z doradców, który jest aktualnie zarządzany.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc

Pobiera logicznie równoważną `FORMATETC` strukturę do jednej, która jest bardziej skomplikowana.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject:: GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) w Windows SDK.

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectImpl:: GetData

Przenosi dane z obiektu danych do klienta.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Uwagi

Parametr *pformatetcIn* musi określać typ nośnika magazynu TYMED_MFPICT.

Zobacz [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w Windows SDK.

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectImpl::GetDataHere

Podobnie jak w `GetData` przypadku programu, z tą różnicą, że klient musi przydzielić `STGMEDIUM` strukturę.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject:: GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) w Windows SDK.

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectImpl::QueryGetData

Określa, czy obiekt danych obsługuje określoną `FORMATETC` strukturę transferu danych.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) w Windows SDK.

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectImpl:: SetData

Przesyła dane z klienta do obiektu danych.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject:: SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
