---
title: Makra mapy usługi
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: ab130b2401dc9885f82fd5668a2d722a96dd289b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274567"
---
# <a name="service-map-macros"></a>Makra mapy usługi

Te makra definiują map usług i wpisów.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Oznacza początek ATL mapy usługi.|
|[END_SERVICE_MAP](#end_service_map)|Oznacza koniec ATL mapy usługi.|
|[SERVICE_ENTRY](#service_entry)|Oznacza, że obiekt obsługuje identyfikatora dla określonej usługi.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Powoduje, że [IServiceProviderImpl::QueryService](#queryservice) do tworzenia łańcucha określony obiekt.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP

Oznacza początek mapy usługi.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[in] Określa klasę zawierającą mapy usługi.

### <a name="remarks"></a>Uwagi

Aby zaimplementować funkcję dostawcy usług na obiekcie COM, należy wykonać mapy usługi. Po pierwsze, musi pochodzić z klasy [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Istnieją dwa rodzaje wpisy:

- [SERVICE_ENTRY](#service_entry) wskazuje pomocy technicznej dla określonej usługi identyfikator (SID).

- [SERVICE_ENTRY_CHAIN](#service_entry_chain) nakazuje [IServiceProviderImpl::QueryService](#queryservice) do tworzenia łańcucha innego, określonego obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>  END_SERVICE_MAP

Oznacza koniec mapy usługi.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry"></a>  SERVICE_ENTRY

Oznacza, że obiekt obsługuje określonego przez identyfikator usługi *SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parametry

*IDENTYFIKATOR SID*<br/>
Identyfikator usługi.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN

Powoduje, że [IServiceProviderImpl::QueryService](#queryservice) do tworzenia łańcucha obiekt określony przez *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parametry

*punk*<br/>
Wskaźnik do **IUnknown** interfejsu, do którego łańcuch.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService

Tworzy lub uzyskuje dostęp do określonej usługi i zwraca wskaźnik interfejsu do określonego interfejsu usługi.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*guidService*<br/>
[in] Wskaźnik do identyfikator usług (SID).

*Parametr riid*<br/>
[in] Identyfikator interfejsu, do którego ma dostęp obiekt wywołujący.

*ppvObj*<br/>
[out] Pośredni wskaźnik do żądanego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwrócona wartość HRESULT jest jedną z następujących czynności:

|Wartość zwracana|Znaczenie|
|------------------|-------------|
|S_OK|Usługa została pomyślnie utworzone lub pobrać.|
|E_INVALIDARG|Co najmniej jeden z argumentów jest nieprawidłowa.|
|E_OUTOFMEMORY|Pamięć jest za mała, aby utworzyć usługę.|
|E_UNEXPECTED|Wystąpił nieznany błąd.|
|E_NOINTERFACE|Żądany interfejs nie jest częścią tej usługi lub usługa jest nieznany.|

### <a name="remarks"></a>Uwagi

`QueryService` Zwraca wartość pośredni wskaźnik do żądanego interfejsu w określonej usługi. Obiekt wywołujący jest odpowiedzialny za zwalniając tego wskaźnika, gdy nie jest już wymagany.

Gdy wywołujesz `QueryService`, należy przekazać identyfikatorem usługi (*guidService*) i identyfikator interfejsu (*riid*). *GuidService* Określa usługę, do którego mają dostęp, i *riid* identyfikuje interfejs, który jest częścią usługi. W zamian otrzymasz pośredni wskaźnik do interfejsu.

Obiekt, który implementuje interfejs może także implementować interfejsy, które należą do innych usług. Rozważ następujące opcje:

- Niektóre z tych interfejsów, może być opcjonalny. Nie wszystkie interfejsy, zdefiniowane w opisie usługi są zawsze obecne w każdej implementacji usługi lub dla każdego zwróconego obiektu.

- W przeciwieństwie do wywołania `QueryInterface`, przekazując identyfikator innej usługi nie musi oznaczać zwróceniem innego obiektu Component Object Model (COM).

- Zwrócony obiekt może mieć dodatkowe interfejsy, które nie są częścią definicji usługi.

Dwa różne usługi, takie jak SID_SMyService i SID_SYourService, zarówno określić korzystanie z tego samego interfejsu, mimo że implementacja interfejsu może być nic wspólnego między obiema usługami. To działa, ponieważ wywołanie `QueryService` (SID_SMyService, IID_IDispatch) może zwrócić obiekt inny niż `QueryService` (SID_SYourService, IID_IDispatch). Tożsamość obiektu nie zakłada, że podczas określania identyfikatora innej usługi.

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)
