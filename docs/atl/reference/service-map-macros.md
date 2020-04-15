---
title: Makra mapy usług
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: eb2fe41c79135a7ac2ced9bc3242b070170716b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325940"
---
# <a name="service-map-macros"></a>Makra mapy usług

Te makra definiują mapy usług i wpisy.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Oznacza początek mapy usługi ATL.|
|[END_SERVICE_MAP](#end_service_map)|Oznacza koniec mapy usługi ATL.|
|[SERVICE_ENTRY](#service_entry)|Wskazuje, że obiekt obsługuje określony identyfikator usługi.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Nakazuje [IServiceProviderImpl::QueryService](#queryservice) do łańcucha do określonego obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="begin_service_map"></a><a name="begin_service_map"></a>BEGIN_SERVICE_MAP

Oznacza początek mapy usługi.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
[w] Określa klasę zawierającą mapę usługi.

### <a name="remarks"></a>Uwagi

Użyj mapy usługi, aby zaimplementować funkcje dostawcy usług na obiekcie COM. Po pierwsze, należy wyprowadzić klasę z [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Istnieją dwa typy wpisów:

- [SERVICE_ENTRY](#service_entry)   Wskazuje obsługę określonego identyfikatora usługi (SID).

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Nakazuje [IServiceProviderImpl::QueryService](#queryservice) do łańcucha do innego, określonego obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a>END_SERVICE_MAP

Oznacza koniec mapy usługi.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry"></a><a name="service_entry"></a>SERVICE_ENTRY

Wskazuje, że obiekt obsługuje identyfikator usługi określony przez *identyfikator SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parametry

*Identyfikator SID*<br/>
Identyfikator usługi.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

Nakazuje [IServiceProviderImpl::QueryService](#queryservice) łańcuch do obiektu określonego przez *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
Wskaźnik do **interfejsu IUnknown,** do którego łańcuch.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).

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

[Makra](../../atl/reference/atl-macros.md)
