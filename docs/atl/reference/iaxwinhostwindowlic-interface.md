---
title: Interfejs IAxWinHostWindowLic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b4d7891d1bb00f4ee689477d1056dbf2bf28cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362843"
---
# <a name="iaxwinhostwindowlic-interface"></a>Interfejs IAxWinHostWindowLic
Ten interfejs zawiera metody licencjonowanego formantu i jego obiektu hosta.  
  
## <a name="syntax"></a>Składnia  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|Tworzy kontrolkę licencjonowane i dołącza go do obiektu hosta.|  
|[CreateControlLicEx](#createcontrollicex)|Tworzy kontrolkę licencjonowanego, dołącza go do obiektu hosta i opcjonalnie Ustawia program obsługi zdarzeń.|  
  
## <a name="remarks"></a>Uwagi  
 `IAxWinHostWindowLic` dziedziczy [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) i dodaje metody, które obsługują tworzenie licencjonowane formanty.  
  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z członkami tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.  
  
|Typ definicji|Plik|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (również zawarte w ATLBase.h)|  
  
##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic  
 Tworzy kontrolkę licencjonowane inicjowane i znajduje się w oknie identyfikowane przez `hWnd`.  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrLic`  
 [in] BSTR, który zawiera klucz licencji dla formantu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) opis pozostałych parametrów i zwracanych wartości.  
  
 Wywołanie tej metody jest odpowiednikiem wywołania [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Przykład  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx  
 Tworzy licencjonowanego formantu ActiveX, inicjowane i znajduje się w określonym okna, podobnie jak [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).  
  
```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrLic`  
 [in] BSTR, który zawiera klucz licencji dla formantu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) opis pozostałych parametrów i zwracanych wartości.  
  
### <a name="example"></a>Przykład  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z `IAxWinHostWindowLic::CreateControlLicEx`.









