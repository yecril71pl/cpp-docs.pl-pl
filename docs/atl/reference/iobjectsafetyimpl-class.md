---
title: IObjectSafetyImpl Class
ms.date: 11/04/2016
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
ms.openlocfilehash: e75c52b016fff5bf04fefc86d4289021efc4db8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277027"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl Class

Ta klasa udostępnia domyślną implementację elementu `IObjectSafety` interfejsu, aby umożliwić klientowi pobierać i ustawiać poziom bezpieczeństwa obiektu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `IObjectSafetyImpl`.

*dwSupportedSafety*<br/>
Określa opcje bezpieczeństwa obsługiwanych dla formantu. Może być jednym z następujących wartości:

- INTERFACESAFE_FOR_UNTRUSTED_CALLER interfejsie zidentyfikowany przez [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) parametru `riid` powinni należeć do obsługi skryptów.

- INTERFACESAFE_FOR_UNTRUSTED_DATA interfejsie zidentyfikowany przez `SetInterfaceSafetyOptions` parametru `riid` ustanowić bezpieczne dla niezaufanych danych podczas inicjowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Pobiera opcje bezpieczeństwa, obsługiwane przez obiekt, a także opcje bezpieczeństwa ustawione dla obiektu.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Sprawia, że obiekt bezpiecznego inicjowania lub skryptów.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Przechowuje obiekt bieżący poziom bezpieczeństwa.|

## <a name="remarks"></a>Uwagi

Klasa `IObjectSafetyImpl` udostępnia domyślną implementację elementu `IObjectSafety`. `IObjectSafety` Interfejs umożliwia klientowi pobrać i ustawić poziom bezpieczeństwa obiektu. Na przykład, można wywołać przeglądarki sieci web `IObjectSafety::SetInterfaceSafetyOptions` aby formant bezpiecznych inicjowania lub obsługi skryptów.

Należy pamiętać, że używanie [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) makro z kategorii składników CATID_SafeForScripting i CATID_SafeForInitializing zapewnia alternatywny sposób określania, czy składnik jest bezpieczne.

**Powiązane artykuły** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="getinterfacesafetyoptions"></a>  IObjectSafetyImpl::GetInterfaceSafetyOptions

Pobiera opcje bezpieczeństwa, obsługiwane przez obiekt, a także opcje bezpieczeństwa ustawione dla obiektu.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Uwagi

Implementacja zwraca odpowiednie wartości dla dowolnego interfejsu obsługiwana przez implementację obiektu `IUnknown::QueryInterface`.

> [!IMPORTANT]
>  Dowolny obiekt obsługujący `IObjectSafety` jest odpowiedzialny za własne zabezpieczeń i z dowolnego obiektu deleguje ona. Programista musi uwzględniać problemy związane z kontem wynikających z uruchamiania kodu w kontekście użytkownika, skryptów między witrynami i wykonują sprawdzanie odpowiedniej strefy.

Zobacz [IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx) w Windows SDK.

##  <a name="m_dwcurrentsafety"></a>  IObjectSafetyImpl::m_dwCurrentSafety

Przechowuje obiekt bieżący poziom bezpieczeństwa.

```
DWORD m_dwCurrentSafety;
```

##  <a name="setinterfacesafetyoptions"></a>  IObjectSafetyImpl::SetInterfaceSafetyOptions

Sprawia, że obiekt jest bezpieczny dla inicjowania lub skryptów przez ustawienie [m_dwCurrentSafety](#m_dwcurrentsafety) elementu członkowskiego odpowiednią wartość.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Uwagi

Implementacja zwraca E_NOINTERFACE dla dowolnego interfejsu nie jest obsługiwane przez implementację obiektu `IUnknown::QueryInterface`.

> [!IMPORTANT]
>  Dowolny obiekt obsługujący `IObjectSafety` jest odpowiedzialny za własne zabezpieczeń i z dowolnego obiektu deleguje ona. Programista musi uwzględniać problemy związane z kontem wynikających z uruchamiania kodu w kontekście użytkownika, skryptów między witrynami i wykonują sprawdzanie odpowiedniej strefy.

Zobacz [IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Interfejs IObjectSafety](https://msdn.microsoft.com/library/aa768224.aspx)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
