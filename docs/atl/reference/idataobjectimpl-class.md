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
ms.openlocfilehash: 618f8248a03297120ae2504bcb30ba8f080b184d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329841"
---
# <a name="idataobjectimpl-class"></a>Klasa IDataObjectImpl

Ta klasa udostępnia metody obsługi jednolitego transferu danych i zarządzania połączeniami.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IDataObjectImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Ustanawia połączenie między obiektem danych a doradzić sink. Dzięki temu doradzić ujścia do odbierania powiadomień o zmianach w obiekcie.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Kończy połączenie wcześniej nawiązane `DAdvise`za pośrednictwem .|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Tworzy wyliczacz do iteracji za pośrednictwem bieżących połączeń doradczych.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Tworzy wyliczacz do iteracji `FORMATETC` za pośrednictwem struktur obsługiwanych przez obiekt danych. Implementacja ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Wysyła powiadomienie o zmianie z powrotem do każdego doradzić sink.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Pobiera logicznie równoważną `FORMATETC` strukturę do tej, która jest bardziej złożona. Implementacja ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::GetData](#getdata)|Przesyła dane z obiektu danych do klienta. Dane są opisane w `FORMATETC` strukturze i są `STGMEDIUM` przesyłane za pośrednictwem struktury.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Podobne `GetData`do , z wyjątkiem `STGMEDIUM` klienta musi przydzielić strukturę. Implementacja ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Określa, czy obiekt danych `FORMATETC` obsługuje określoną strukturę przesyłania danych. Implementacja ATL zwraca E_NOTIMPL.|
|[IDataObjectImpl::SetData](#setdata)|Przesyła dane z klienta do obiektu danych. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Interfejs [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) udostępnia metody obsługi jednolitego transferu danych. `IDataObject`używa standardowych struktur formatu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) i [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) do pobierania i przechowywania danych.

`IDataObject`zarządza również połączeniami, aby doradzać pochłaniaczom do obsługi powiadomień o zmianie danych. Aby klient odbierał powiadomienia o zmianie danych z obiektu danych, klient musi zaimplementować interfejs [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) na obiekcie o nazwie doradzić sink. Gdy klient następnie `IDataObject::DAdvise`wywołuje, połączenie jest ustanawiane między obiektem danych i doradzić sink.

Klasa `IDataObjectImpl` zapewnia domyślną `IDataObject` implementację `IUnknown` i implementuje, wysyłając informacje do urządzenia zrzutu w kompilacjach debugowania.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectImpl::DAdvise

Ustanawia połączenie między obiektem danych a doradzić sink.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Uwagi

Dzięki temu doradzić ujścia do odbierania powiadomień o zmianach w obiekcie.

Aby zakończyć połączenie, zadzwoń do [DUnadvise](#dunadvise).

Zobacz [IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) w windows SDK.

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectImpl::DUnadvise

Kończy połączenie wcześniej ustanowione za pośrednictwem [DAdvise](#dadvise).

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) w windows SDK.

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise

Tworzy wyliczacz do iteracji za pośrednictwem bieżących połączeń doradczych.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) w windows SDK.

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc

Tworzy wyliczacz do iteracji `FORMATETC` za pośrednictwem struktur obsługiwanych przez obiekt danych.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) w sdk systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectImpl::FireDataChange

Wysyła powiadomienie o zmianie z powrotem do każdego zlewu doradzić, który jest obecnie zarządzany.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc

Pobiera logicznie równoważną `FORMATETC` strukturę do tej, która jest bardziej złożona.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) w usłudze Windows SDK.

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectImpl::GetData

Przesyła dane z obiektu danych do klienta.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Uwagi

Parametr *pformatetcIn* musi określać typ nośnika magazynowego TYMED_MFPICT.

Zobacz [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w windows SDK.

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectImpl::GetDataHere

Podobne `GetData`do , z wyjątkiem `STGMEDIUM` klienta musi przydzielić strukturę.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) w windows SDK.

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectImpl::QueryGetData

Określa, czy obiekt danych `FORMATETC` obsługuje określoną strukturę przesyłania danych.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IDataObject::QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) w windows SDK.

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectImpl::SetData

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

Zobacz [IDataObject::SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
