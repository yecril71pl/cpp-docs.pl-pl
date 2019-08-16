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
ms.openlocfilehash: d5e7f087f6646940777ae8b2d2a4ea888fdd3593
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495364"
---
# <a name="isupporterrorinfoimpl-class"></a>Klasa ISupportErrorInfoImpl

Ta klasa udostępnia domyślną implementację [interfejsu ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) i może być używana w przypadku, gdy tylko jeden interfejs generuje błędy w obiekcie.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Parametry

*piid*<br/>
Wskaźnik do IID interfejsu, który obsługuje [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Wskazuje, czy interfejs identyfikowany `riid` przez program obsługuje interfejs [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) .|

## <a name="remarks"></a>Uwagi

[Interfejs ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) zapewnia, że informacje o błędzie mogą być zwracane do klienta. Obiekty korzystające `IErrorInfo` z programu `ISupportErrorInfo`muszą implementować.

Klasa `ISupportErrorInfoImpl` udostępnia`ISupportErrorInfo` implementację domyślną i może być używana, gdy tylko jeden interfejs generuje błędy w obiekcie. Na przykład:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="interfacesupportserrorinfo"></a>ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Wskazuje, czy interfejs identyfikowany `riid` przez program obsługuje interfejs [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) .

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Uwagi

Zobacz [ISupportErrorInfo:: InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
