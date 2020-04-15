---
title: Klasa IPropertyPage2Impl
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: d112a2411a9debbf2eb77e6b851f4500e8d32ab8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329593"
---
# <a name="ipropertypage2impl-class"></a>Klasa IPropertyPage2Impl

Ta klasa `IUnknown` implementuje i dziedziczy domyślną implementację [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IPropertyPage2Impl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Określa, która kontrola właściwości otrzyma fokus po aktywowaniu strony właściwości. Implementacja ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

Interfejs [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) rozszerza [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) przez `EditProperty` dodanie metody. Ta metoda umożliwia klientowi wybranie określonej właściwości w obiekcie strony właściwości.

Klasa `IPropertyPage2Impl` po prostu zwraca `IPropertyPage2::EditProperty`E_NOTIMPL dla . Jednak dziedziczy domyślną implementację [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) `IUnknown` i implementuje, wysyłając informacje do urządzenia zrzutu w kompilacjach debugowania.

Podczas tworzenia strony właściwości, klasa jest zazwyczaj `IPropertyPageImpl`pochodną . Aby zapewnić dodatkową `IPropertyPage2`obsługę , zmodyfikuj `EditProperty` definicję klasy i zastąd w celu zastąpienia metody.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPropertyPage`

[Ipropertypageimpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ipropertypage2impleditproperty"></a><a name="editproperty"></a>IPropertyPage2Impl::EditProperty

Określa, która kontrola właściwości otrzyma fokus po aktywowaniu strony właściwości.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage2::EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl Klasa](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
