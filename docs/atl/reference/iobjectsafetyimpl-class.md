---
title: Klasa IObjectSafetyImpl
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
ms.openlocfilehash: 6eee7585bc3c5587e106ab6b0cefb4b7129df59f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329660"
---
# <a name="iobjectsafetyimpl-class"></a>Klasa IObjectSafetyImpl

Ta klasa zapewnia domyślną `IObjectSafety` implementację interfejsu, aby umożliwić klientowi pobieranie i ustawianie poziomów bezpieczeństwa obiektu.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IObjectSafetyImpl`.

*dwSupportedBezpieczeństwo*<br/>
Określa obsługiwane opcje bezpieczeństwa dla sterowania. Może być jedną z następujących wartości:

- INTERFACESAFE_FOR_UNTRUSTED_CALLER Interfejs identyfikowany przez `riid` [parametr SetInterfaceSafetyOptions](#setinterfacesafetyoptions) powinien być bezpieczny dla skryptów.

- INTERFACESAFE_FOR_UNTRUSTED_DATA Interfejs identyfikowany przez `SetInterfaceSafetyOptions` parametr `riid` powinien być bezpieczny dla niezaufanych danych podczas inicjowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Pobiera opcje bezpieczeństwa obsługiwane przez obiekt, a także opcje bezpieczeństwa aktualnie ustawione dla obiektu.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Sprawia, że obiekt jest bezpieczny do inicjowania lub skryptów.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Przechowuje aktualny poziom bezpieczeństwa obiektu.|

## <a name="remarks"></a>Uwagi

Klasa `IObjectSafetyImpl` zapewnia domyślną `IObjectSafety`implementację . Interfejs `IObjectSafety` umożliwia klientowi pobieranie i ustawianie poziomów bezpieczeństwa obiektu. Na przykład przeglądarka sieci `IObjectSafety::SetInterfaceSafetyOptions` web może wywołać, aby formant bezpieczne do inicjowania lub bezpieczne dla skryptów.

Należy zauważyć, że użycie makra [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) z kategoriami składników CATID_SafeForScripting i CATID_SafeForInitializing zapewnia alternatywny sposób określania, że składnik jest bezpieczny.

**Podobne artykuły** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Tworzenie projektu [ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions

Pobiera opcje bezpieczeństwa obsługiwane przez obiekt, a także opcje bezpieczeństwa aktualnie ustawione dla obiektu.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Uwagi

Implementacja zwraca odpowiednie wartości dla dowolnego interfejsu obsługiwanego `IUnknown::QueryInterface`przez implementację obiektu .

> [!IMPORTANT]
> Każdy obiekt, `IObjectSafety` który obsługuje jest odpowiedzialny za własne zabezpieczenia i każdy obiekt, który deleguje. Programista musi wziąć pod uwagę problemy wynikające z uruchamiania kodu w kontekście użytkownika, skryptów między witrynami i wykonać odpowiednie sprawdzanie strefy.

Zobacz [IObjectSafety::GetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\)) w usłudze Windows SDK.

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety

Przechowuje aktualny poziom bezpieczeństwa obiektu.

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions

Sprawia, że obiekt jest bezpieczny do inicjowania lub skryptów, ustawiając [m_dwCurrentSafety](#m_dwcurrentsafety) element członkowski do odpowiedniej wartości.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Uwagi

Implementacja zwraca E_NOINTERFACE dla dowolnego interfejsu nie obsługiwane przez implementację obiektu `IUnknown::QueryInterface`.

> [!IMPORTANT]
> Każdy obiekt, `IObjectSafety` który obsługuje jest odpowiedzialny za własne zabezpieczenia i każdy obiekt, który deleguje. Programista musi wziąć pod uwagę problemy wynikające z uruchamiania kodu w kontekście użytkownika, skryptów między witrynami i wykonać odpowiednie sprawdzanie strefy.

Zobacz [IObjectSafety::SetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\)) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Interfejs bezpieczeństwa IObjectSafety](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
