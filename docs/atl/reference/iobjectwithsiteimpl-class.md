---
title: Klasa IObjectWithSiteImpl
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
ms.openlocfilehash: 034e5dd42f6e10286520bb2a08effc40b0aca71a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329642"
---
# <a name="iobjectwithsiteimpl-class"></a>Klasa IObjectWithSiteImpl

Ta klasa zawiera metody umożliwiające obiekt do komunikowania się z jego witryny.

## <a name="syntax"></a>Składnia

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IObjectWithSiteImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Wysyła zapytania do witryny dla wskaźnika interfejsu.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Udostępnia obiektowi wskaźnik witryny. `IUnknown`|
|[IObjectWithSiteImpl::SetSite](#setsite)|Udostępnia obiektowi wskaźnik witryny. `IUnknown`|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Zarządza wskaźnikiem witryny. `IUnknown`|

## <a name="remarks"></a>Uwagi

[Interfejs IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) umożliwia obiektowi komunikowanie się z jego witryną. Klasa `IObjectWithSiteImpl` zapewnia domyślną implementację tego `IUnknown` interfejsu i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

`IObjectWithSiteImpl`określa dwie metody. Klient najpierw `SetSite`wywołuje , przekazując `IUnknown` wskaźnik witryny. Ten wskaźnik jest przechowywany w obiekcie, a później `GetSite`można go pobrać za pośrednictwem wywołania .

Zazwyczaj można wyprowadzić klasę `IObjectWithSiteImpl` z podczas tworzenia obiektu, który nie jest formantem. For controls, należy wyprowadzić klasę z [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), który zapewnia również wskaźnik witryny. Nie należy czerpać klasy `IObjectWithSiteImpl` `IOleObjectImpl`z obu i .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="iobjectwithsiteimplgetsite"></a><a name="getsite"></a>IObjectWithSiteImpl::GetSite

Wysyła zapytania do witryny pod kątem `riid`wskaźnika do interfejsu identyfikowanego przez program .

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Uwagi

Jeśli witryna obsługuje ten interfejs, `ppvSite`wskaźnik jest zwracany za pośrednictwem . W `ppvSite` przeciwnym razie jest ustawiona na WARTOŚĆ NULL.

Zobacz [IObjectWithSite::GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) w usłudze Windows SDK.

## <a name="iobjectwithsiteimplm_spunksite"></a><a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite

Zarządza wskaźnikiem witryny. `IUnknown`

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Uwagi

`m_spUnkSite`początkowo odbiera ten wskaźnik za pośrednictwem wywołania [SetSite](#setsite).

## <a name="iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite

Udostępnia obiektowi wskaźnik witryny. `IUnknown`

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Parametry

*pUnkSite (Niemka)*<br/>
[w] Wskaźnik do `IUnknown` wskaźnika interfejsu witryny zarządzającej tym obiektem. Jeśli NULL, obiekt `IUnknown::Release` powinien wywołać w każdej istniejącej witryny, w którym momencie obiekt nie zna już swojej witryny.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="iobjectwithsiteimplsetsite"></a><a name="setsite"></a>IObjectWithSiteImpl::SetSite

Udostępnia obiektowi wskaźnik witryny. `IUnknown`

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Uwagi

Zobacz [IObjectWithSite::SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
