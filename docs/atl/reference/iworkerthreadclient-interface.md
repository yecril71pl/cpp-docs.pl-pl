---
title: Interfejs IWorkerThreadClient | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
dev_langs:
- C++
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8336edb07d02bbbcd5775eaf3ef8fe0f735d3adb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359820"
---
# <a name="iworkerthreadclient-interface"></a>Interfejs IWorkerThreadClient
`IWorkerThreadClient` interfejs implementowany przez klientów [CWorkerThread](../../atl/reference/cworkerthread-class.md) klasy.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
__interface IWorkerThreadClient
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Funkcji CloseHandle:](#closehandle)|Zaimplementuj tę metodę, aby zamknąć dojścia skojarzone z tym obiektem.|  
|[Wykonanie](#execute)|Zaimplementuj tę metodę do wykonania kodu, gdy staje się sygnalizowane dojścia skojarzone z tym obiektem.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli masz kod, który ma zostać wykonane na wątek roboczy w odpowiedzi do uchwytu staje się sygnalizowane zawierać implementację tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle  
 Zaimplementuj tę metodę, aby zamknąć dojścia skojarzone z tym obiektem.  
  
```
HRESULT CloseHandle(HANDLE  hHandle);
```  
  
### <a name="parameters"></a>Parametry  
 *hHandle*  
 Dojście do zamknięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK na powodzenie lub błąd HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Dojście przekazane do tej metody został wcześniej skojarzony z tym obiektem przez wywołanie do [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Przykład  
 Poniższy kod przedstawia prostych implementacji `IWorkerThreadClient::CloseHandle`.  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]  
  
##  <a name="execute"></a>  IWorkerThreadClient::Execute  
 Zaimplementuj tę metodę do wykonania kodu, gdy staje się sygnalizowane dojścia skojarzone z tym obiektem.  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>Parametry  
 `dwParam`  
 Parametr użytkownika.  
  
 `hObject`  
 Dojście stają się sygnalizowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK na powodzenie lub błąd HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Dojście i przekazane do tej metody na wskaźnik DWORD były wcześniej skojarzone z tym obiektem przez wywołanie do [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Przykład  
 Poniższy kod przedstawia prostych implementacji `IWorkerThreadClient::Execute`.  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../atl/reference/atl-classes.md)   
 [Klasa CWorkerThread](../../atl/reference/cworkerthread-class.md)
