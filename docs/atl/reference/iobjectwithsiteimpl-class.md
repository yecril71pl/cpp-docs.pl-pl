---
title: IObjectWithSiteImpl Class
ms.date: 11/04/2016
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
ms.openlocfilehash: ad27c4288d7e16949fe38ea6b8a686e3d6916ee6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297024"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl Class

Ta klasa dostarcza metody, dzięki czemu obiekt, do komunikacji z jej lokacją.

## <a name="syntax"></a>Składnia

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IObjectWithSiteImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Wysyła zapytanie do witryny dla wskaźnika interfejsu.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Udostępnia obiekt w witrynie `IUnknown` wskaźnika.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Udostępnia obiekt w witrynie `IUnknown` wskaźnika.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Zarządza witryny `IUnknown` wskaźnika.|

## <a name="remarks"></a>Uwagi

[IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) interfejs umożliwia obiekt, do komunikacji z jej lokacją. Klasa `IObjectWithSiteImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

`IObjectWithSiteImpl` Określa dwie metody. Pierwszy wywołań klienta `SetSite`, przekazując witryny `IUnknown` wskaźnika. This, wskaźnik jest przechowywany w obiekcie, a później mogą być pobierane za pomocą wywołania `GetSite`.

Zazwyczaj pochodzą z klasy `IObjectWithSiteImpl` podczas tworzenia obiektu, który nie jest formantem. W przypadku kontrolek pochodzi z klasy [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), zapewniającą wskaźnik lokacji. Pochodzi z klasy z obu `IObjectWithSiteImpl` i `IOleObjectImpl`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite

Zapytania witryny dla wskaźnika do interfejsu identyfikowane przez `riid`.

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Uwagi

Jeśli lokacja obsługuje ten interfejs, wskaźnik jest zwracany za pośrednictwem `ppvSite`. W przeciwnym razie `ppvSite` ma wartość NULL.

Zobacz [IObjectWithSite::GetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-getsite) w Windows SDK.

##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite

Zarządza witryny `IUnknown` wskaźnika.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Uwagi

`m_spUnkSite` początkowo otrzyma ten wskaźnik poprzez wywołanie [setsite —](#setsite).

##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite

Udostępnia obiekt w witrynie `IUnknown` wskaźnika.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Parametry

*pUnkSite*<br/>
[in] Wskaźnik do `IUnknown` wskaźnika interfejsu lokacji zarządzania tego obiektu. Jeśli ma wartość NULL, obiekt powinien wywoływać `IUnknown::Release` witrynie istniejący w tym momencie obiektu nie jest już zna do niego lokacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite

Udostępnia obiekt w witrynie `IUnknown` wskaźnika.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Uwagi

Zobacz [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
