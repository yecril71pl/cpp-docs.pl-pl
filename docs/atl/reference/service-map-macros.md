---
title: Makra Service Map
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: 1fa163098d89dd949c17ee7cd5e4ddc46cd2a091
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835210"
---
# <a name="service-map-macros"></a>Makra Service Map

Te makra definiują mapy i wpisy usług.

|Nazwa|Opis|
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Oznacza początek mapy usługi ATL.|
|[END_SERVICE_MAP](#end_service_map)|Oznacza koniec mapy usługi ATL.|
|[SERVICE_ENTRY](#service_entry)|Wskazuje, że obiekt obsługuje określony identyfikator usługi.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Instruuje [IServiceProviderImpl:: QueryService](#queryservice) do łańcucha do określonego obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="begin_service_map"></a><a name="begin_service_map"></a> BEGIN_SERVICE_MAP

Oznacza początek mapy usługi.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
podczas Określa klasę zawierającą mapę usług.

### <a name="remarks"></a>Uwagi

Mapa usługi służy do implementowania funkcjonalności dostawcy usług na obiekcie COM. Najpierw należy utworzyć klasę z [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Istnieją dwa typy wpisów:

- [SERVICE_ENTRY](#service_entry)   Wskazuje obsługę określonego identyfikatora usługi (SID).

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Instruuje [IServiceProviderImpl:: QueryService](#queryservice) do łańcucha do innego, określonego obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a> END_SERVICE_MAP

Oznacza koniec mapy usługi.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry"></a><a name="service_entry"></a> SERVICE_ENTRY

Wskazuje, że obiekt obsługuje identyfikator usługi określony przez *Identyfikator SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parametry

*Identyfikator SID*<br/>
Identyfikator usługi.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a> SERVICE_ENTRY_CHAIN

Instruuje [IServiceProviderImpl:: QueryService](#queryservice) do łańcucha do obiektu określonego przez *punkt*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parametry

*punkt*<br/>
Wskaźnik do interfejsu **IUnknown** , który ma zostać powiązany z łańcuchem.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a> IServiceProviderImpl::QueryService

Tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnik interfejsu do określonego interfejsu dla usługi.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*guidService*<br/>
podczas Wskaźnik do identyfikatora usługi (SID).

*riid*<br/>
podczas Identyfikator interfejsu, do którego obiekt wywołujący ma uzyskać dostęp.

*ppvObj*<br/>
określoną Pośredni wskaźnik do żądanego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwrócona wartość HRESULT ma jedną z następujących wartości:

|Wartość zwracana|Znaczenie|
|------------------|-------------|
|S_OK|Usługa została pomyślnie utworzona lub pobrana.|
|E_INVALIDARG|Co najmniej jeden z argumentów jest nieprawidłowy.|
|E_OUTOFMEMORY|Brak wystarczającej ilości pamięci do utworzenia usługi.|
|E_UNEXPECTED|Wystąpił nieznany błąd.|
|E_NOINTERFACE|Żądany interfejs nie jest częścią tej usługi lub usługa jest nieznana.|

### <a name="remarks"></a>Uwagi

`QueryService` zwraca pośredni wskaźnik do żądanego interfejsu w określonej usłudze. Obiekt wywołujący jest odpowiedzialny za zwolnienie tego wskaźnika, gdy nie jest już wymagany.

Po wywołaniu należy `QueryService` przekazać zarówno identyfikator usługi (*guidService*), jak i identyfikator interfejsu (*riid*). *GuidService* określa usługę, do której chcesz uzyskać dostęp, a *riid* identyfikuje interfejs, który jest częścią usługi. W powrocie otrzymujesz pośredni wskaźnik do interfejsu.

Obiekt, który implementuje interfejs, może również zaimplementować interfejsy, które są częścią innych usług. Rozważ następujące źródła:

- Niektóre z tych interfejsów mogą być opcjonalne. Nie wszystkie interfejsy zdefiniowane w opisie usługi muszą być obecne w każdej implementacji usługi lub na każdym zwracanym obiekcie.

- W przeciwieństwie do wywołania `QueryInterface` , przekazywanie innego identyfikatora usługi nie musi oznaczać, że jest zwracany inny obiekt Component Object Model (com).

- Zwrócony obiekt może mieć dodatkowe interfejsy, które nie są częścią definicji usługi.

Dwie różne usługi, takie jak SID_SMyService i SID_SYourService, mogą określić użycie tego samego interfejsu, nawet jeśli implementacja interfejsu może nie zawierać żadnych wspólnych wartości między obiema usługami. To działa, ponieważ wywołanie metody `QueryService` (SID_SMyService, IID_IDispatch) może zwrócić inny obiekt niż `QueryService` (SID_SYourService, IID_IDispatch). Nie przyjmuje się tożsamości obiektu po określeniu innego identyfikatora usługi.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
