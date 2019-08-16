---
title: Klasa ISpecifyPropertyPagesImpl
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
ms.openlocfilehash: c201cf6d9d89ab1a6a8e888deee1be79e5770490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495408"
---
# <a name="ispecifypropertypagesimpl-class"></a>Klasa ISpecifyPropertyPagesImpl

Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację interfejsu [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) .

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `ISpecifyPropertyPagesImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Wypełnia zliczoną tablicę wartości UUID. Każdy identyfikator UUID odpowiada identyfikatorowi CLSID jednej ze stron właściwości, które mogą być wyświetlane w arkuszu właściwości obiektu.|

## <a name="remarks"></a>Uwagi

Interfejs [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) umożliwia klientowi uzyskanie listy identyfikatorów CLSID dla stron właściwości obsługiwanych przez obiekt. Klasa `ISpecifyPropertyPagesImpl` zapewnia domyślną implementację tego interfejsu i implementuje `IUnknown` przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

> [!NOTE]
>  Nie ujawniaj interfejsu `ISpecifyPropertyPages` , jeśli obiekt nie obsługuje stron właściwości.

**Powiązane artykuły** [Samouczek ATL](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="getpages"></a>ISpecifyPropertyPagesImpl:: GetPages

Wypełnia tablicę w strukturze [CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid) z identyfikatorami CLSID dla stron właściwości, które mogą być wyświetlane w arkuszu właściwości obiektu.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu, aby pobrać każdy identyfikator CLSID.

Zobacz [ISpecifyPropertyPages::](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) GetPages w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
