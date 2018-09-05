---
title: Klasa ISpecifyPropertyPagesImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs:
- C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d231f493fd2b2f2c492eec224a0ae041f175f53d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767353"
---
# <a name="ispecifypropertypagesimpl-class"></a>Klasa ISpecifyPropertyPagesImpl

Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) interfejsu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parametry

*T*  
Z klasą pochodną `ISpecifyPropertyPagesImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Wypełnia wartości liczone tablicy UUID. Każdy identyfikator UUID odnosi się do identyfikatora CLSID dla jednej strony właściwości, które mogą być wyświetlane w arkuszu właściwości.|

## <a name="remarks"></a>Uwagi

[ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) interfejs umożliwia klientowi uzyskać listę CLSID dla stron właściwości obsługiwanych przez obiekt. Klasa `ISpecifyPropertyPagesImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

> [!NOTE]
>  Nie ujawniaj `ISpecifyPropertyPages` interfejsu, jeśli obiekt nie obsługuje strony właściwości.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

Wypełnia tablicę [CAUUID](/windows/desktop/api/ocidl/ns-ocidl-tagcauuid) struktury z CLSID dla na stronach właściwości, które mogą być wyświetlane w arkuszu właściwości.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Uwagi

ATL używa map właściwości obiektu do pobrania każdy identyfikator CLSID.

Zobacz [ISpecifyPropertyPages::GetPages](/windows/desktop/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)   
[Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
