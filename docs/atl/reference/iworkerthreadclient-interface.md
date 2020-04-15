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
ms.openlocfilehash: 6a68f25f153a0ad2cf42ebfaa374ff63c5746fcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326297"
---
# <a name="iworkerthreadclient-interface"></a>Interfejs IWorkerThreadClient

`IWorkerThreadClient`jest interfejsem zaimplementowanym przez klientów klasy [CWorkerThread.](../../atl/reference/cworkerthread-class.md)

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Closehandle](#closehandle)|Zaimplementuj tę metodę, aby zamknąć dojście skojarzone z tym obiektem.|
|[Realizacja](#execute)|Zaimplementuj tę metodę, aby wykonać kod, gdy dojście skojarzone z tym obiektem staje się sygnalizowane.|

## <a name="remarks"></a>Uwagi

Zaimplementuj ten interfejs, gdy masz kod, który musi wykonać w wątku procesu roboczego w odpowiedzi na dojście staje się sygnalizowane.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::Zamknijhandle

Zaimplementuj tę metodę, aby zamknąć dojście skojarzone z tym obiektem.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Parametry

*hRejsz*<br/>
Uchwyt do zamknięcia.

### <a name="return-value"></a>Wartość zwracana

Powrót S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Dojście przekazane do tej metody zostało wcześniej skojarzone z tym obiektem przez wywołanie [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod przedstawia prostą implementację programu `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Wykonaj

Zaimplementuj tę metodę, aby wykonać kod, gdy dojście skojarzone z tym obiektem staje się sygnalizowane.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam (polski)*<br/>
Parametr użytkownika.

*hObiekt*<br/>
Uchwyt, który stał się sygnalizowany.

### <a name="return-value"></a>Wartość zwracana

Powrót S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Dojście i DWORD/pointer przekazane do tej metody były wcześniej skojarzone z tym obiektem przez wywołanie [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Przykład

Poniższy kod przedstawia prostą implementację programu `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)<br/>
[Klasa CWorkerThread](../../atl/reference/cworkerthread-class.md)
