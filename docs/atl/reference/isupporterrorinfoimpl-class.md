---
title: Klasa ISupportErrorInfoImpl
ms.date: 06/13/2019
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: 650d90c9ec98754e11586f63e0871b70ebbe34f3
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141702"
---
# <a name="isupporterrorinfoimpl-class"></a>Klasa ISupportErrorInfoImpl

Ta klasa udostępnia domyślną implementację elementu [interfejsu Interfejs ISupportErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) i mogą być używane, gdy tylko jeden interfejs generuje błędy na obiekcie.

> [!IMPORTANT]
> Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Parametry

*piid*<br/>
Wskaźnik do identyfikatora IID interfejsu, który obsługuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Wskazuje, czy interfejsie zidentyfikowany przez `riid` obsługuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interfejsu.|

## <a name="remarks"></a>Uwagi

[Interfejsu Interfejs ISupportErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) gwarantuje, że informacje o błędzie mogą być zwrócone do klienta. Obiekty używające `IErrorInfo` musi implementować `ISupportErrorInfo`.

Klasa `ISupportErrorInfoImpl` udostępnia domyślną implementację elementu `ISupportErrorInfo` i mogą być używane, gdy tylko jeden interfejs generuje błędy na obiekcie. Na przykład:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Wskazuje, czy interfejsie zidentyfikowany przez `riid` obsługuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interfejsu.

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Uwagi

Zobacz [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
