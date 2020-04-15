---
title: ISpecifyPropertyPagesImpl Klasa
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
ms.openlocfilehash: 06b6b60227a659bd35e042952c7464971fc40bdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326410"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl Klasa

Ta klasa `IUnknown` implementuje i zapewnia domyślną implementację interfejsu [ISpecifyPropertyPages.](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `ISpecifyPropertyPagesImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Wypełnia zliczona tablica wartości UUID. Każdy identyfikator UUID odpowiada identyfikatorowi CLSID dla jednej ze stron właściwości, które mogą być wyświetlane w arkuszu właściwości obiektu.|

## <a name="remarks"></a>Uwagi

Interfejs [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) umożliwia klientowi uzyskanie listy identyfikatorów CLSID dla stron właściwości obsługiwanych przez obiekt. Klasa `ISpecifyPropertyPagesImpl` zapewnia domyślną implementację tego `IUnknown` interfejsu i implementuje przez wysyłanie informacji do urządzenia zrzutu w kompilacjach debugowania.

> [!NOTE]
> Nie należy `ISpecifyPropertyPages` udostępniać interfejsu, jeśli obiekt nie obsługuje stron właściwości.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ispecifypropertypagesimplgetpages"></a><a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages

Wypełnia tablicę w strukturze [CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid) identyfikatorami CLSID dla stron właściwości, które mogą być wyświetlane w arkuszu właściwości obiektu.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Uwagi

ATL używa mapy właściwości obiektu do pobierania każdego identyfikatora CLSID.

Zobacz [ISpecifyPropertyPages::GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) w usłudze Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
