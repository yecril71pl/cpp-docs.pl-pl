---
title: Klasa IServiceProviderImpl
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: ef0ee4f77441cb8d19ea2d6dcada1fed9faf2782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329429"
---
# <a name="iserviceproviderimpl-class"></a>Klasa IServiceProviderImpl

Ta klasa zapewnia domyślną `IServiceProvider` implementację interfejsu.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `IServiceProviderImpl`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|Tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnik interfejsu do określonego interfejsu dla usługi.|

## <a name="remarks"></a>Uwagi

Interfejs `IServiceProvider` lokalizuje usługę określoną przez jego identyfikator GUID i zwraca wskaźnik interfejsu żądanego interfejsu w usłudze. Klasa `IServiceProviderImpl` zapewnia domyślną implementację tego interfejsu.

`IServiceProviderImpl`określa jedną metodę: [QueryService](#queryservice), która tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnik interfejsu do określonego interfejsu dla usługi.

`IServiceProviderImpl`korzysta z mapy usług, począwszy od [BEGIN_SERVICE_MAP,](service-map-macros.md#begin_service_map) a kończąc na [END_SERVICE_MAP](service-map-macros.md#end_service_map).

Mapa usługi zawiera dwa wpisy: [SERVICE_ENTRY](service-map-macros.md#service_entry), który wskazuje określony identyfikator usługi (SID) obsługiwany przez obiekt i `QueryService` [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), który wywołuje łańcuch do innego obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a>IServiceProviderImpl::QueryService

Tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnik interfejsu do określonego interfejsu dla usługi.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*usługa guid*<br/>
[w] Wskaźnik do identyfikatora usługi (SID).

*Riid*<br/>
[w] Identyfikator interfejsu, do którego jest obiektu wywołującego, aby uzyskać dostęp.

*ppvObj (polski)*<br/>
[na zewnątrz] Wskaźnik pośredni do żądanego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwrócona wartość HRESULT jest jedną z następujących wartości:

|Wartość zwracana|Znaczenie|
|------------------|-------------|
|S_OK|Usługa została pomyślnie utworzona lub pobrana.|
|E_invalidarg|Co najmniej jeden z argumentów jest nieprawidłowy.|
|E_outofmemory|Pamięć jest niewystarczająca do utworzenia usługi.|
|E_unexpected|Wystąpił nieznany błąd.|
|E_nointerface|Żądany interfejs nie jest częścią tej usługi lub usługa jest nieznana.|

### <a name="remarks"></a>Uwagi

`QueryService`zwraca wskaźnik pośredni do żądanego interfejsu w określonej usłudze. Wywołujący jest odpowiedzialny za zwolnienie tego wskaźnika, gdy nie jest już wymagane.

Podczas wywoływania `QueryService`należy przekazać zarówno identyfikator usługi (*guidService),* jak i identyfikator interfejsu (*riid*). *GuidService* określa usługę, do której chcesz uzyskać dostęp, a *riid* identyfikuje interfejs, który jest częścią usługi. W zamian otrzymasz wskaźnik pośredni do interfejsu.

Obiekt, który implementuje interfejs może również implementować interfejsy, które są częścią innych usług. Rozważ następujące źródła:

- Niektóre z tych interfejsów mogą być opcjonalne. Nie wszystkie interfejsy zdefiniowane w opisie usługi są koniecznie obecne przy każdej implementacji usługi lub na każdym zwróconym obiekcie.

- W przeciwieństwie `QueryInterface`do wywołań , przekazywanie innego identyfikatora usługi nie musi oznaczać, że zwracany jest inny obiekt modelu obiektu komponentu (COM).

- Zwrócony obiekt może mieć dodatkowe interfejsy, które nie są częścią definicji usługi.

Dwie różne usługi, takie jak SID_SMyService i SID_SYourService, można określić użycie tego samego interfejsu, mimo że implementacja interfejsu może mieć nic wspólnego między tymi dwiema usługami. To działa, ponieważ `QueryService` wywołanie (SID_SMyService, IID_IDispatch) może zwrócić inny `QueryService` obiekt niż (SID_SYourService, IID_IDispatch). Tożsamość obiektu nie jest przyjmowana po określeniu innego identyfikatora usługi.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
