---
title: Klasa IPropertyPage2Impl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9329888f9a97c9bf5fad0d3834bde33845943edd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093311"
---
# <a name="ipropertypage2impl-class"></a>Klasa IPropertyPage2Impl

Ta klasa implementuje `IUnknown` i dziedziczy domyślna Implementacja klasy [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IPropertyPage2Impl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Określa, które określają właściwość otrzyma fokus, po aktywowaniu na stronie właściwości. Implementacja biblioteki ATL zwraca E_NOTIMPL.|

## <a name="remarks"></a>Uwagi

[IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) interfejs rozszerza [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) , dodając `EditProperty` metody. Ta metoda umożliwia klientowi do wybrania konkretnej właściwości w obiekcie strony właściwości.

Klasa `IPropertyPage2Impl` po prostu zwraca E_NOTIMPL dla `IPropertyPage2::EditProperty`. Jednak dziedziczy domyślna Implementacja klasy [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.

Po utworzeniu strony właściwości klasy jest zazwyczaj tworzony na podstawie `IPropertyPageImpl`. Aby zapewnić obsługę dodatkowych `IPropertyPage2`, zmodyfikuj swojej definicji klasy i zastąpić `EditProperty` metody.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

Określa, które określają właściwość otrzyma fokus, po aktywowaniu na stronie właściwości.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca E_NOTIMPL.

### <a name="remarks"></a>Uwagi

Zobacz [IPropertyPage2::EditProperty](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage2-editproperty) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Klasa ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
