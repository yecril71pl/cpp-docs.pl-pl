---
title: Interfejs IWorkerThreadClient
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 22ea136dd91a514ff10e13cd02b796565b7b0307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523642"
---
# <a name="iworkerthreadclient-interface"></a>Interfejs IWorkerThreadClient

`IWorkerThreadClient` interfejs implementowany przez klientów [CWorkerThread](../../atl/reference/cworkerthread-class.md) klasy.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Funkcja CloseHandle](#closehandle)|Zaimplementuj tę metodę, aby zamknąć dojście skojarzone z tym obiektem.|
|[Execute](#execute)|Zaimplementuj tę metodę w celu wykonania kodu, gdy staje się sygnalizowane uchwyt skojarzone z tym obiektem.|

## <a name="remarks"></a>Uwagi

Jeśli masz kod, który można wykonać w wątku roboczego w odpowiedzi na uchwyt, który jest sygnalizowany, należy zaimplementować ten interfejs.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Zaimplementuj tę metodę, aby zamknąć dojście skojarzone z tym obiektem.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Parametry

*hHandle*<br/>
Uchwyt zostanie zamknięty.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na powodzenie lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dojście przekazane do tej metody był wcześniej skojarzony z tym obiektem przez wywołanie [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod przedstawia proste wdrażanie `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Zaimplementuj tę metodę w celu wykonania kodu, gdy staje się sygnalizowane uchwyt skojarzone z tym obiektem.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam*<br/>
Parametr użytkownika.

*hObject*<br/>
Uchwyt, który ma być sygnalizowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na powodzenie lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dojście i przekazany do tej metody na wskaźnik typu DWORD były wcześniej skojarzone z tego obiektu przez wywołanie [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod przedstawia proste wdrażanie `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)<br/>
[Klasa CWorkerThread](../../atl/reference/cworkerthread-class.md)
