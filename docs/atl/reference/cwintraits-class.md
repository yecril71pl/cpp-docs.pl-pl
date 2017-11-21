---
title: Klasa CWinTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
dev_langs: C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fecb7c614320c202a1159a527b34159c01099af6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cwintraits-class"></a>Klasa CWinTraits
Ta klasa udostępnia metodę standaryzacji style używane podczas tworzenia obiektu okna.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `t_dwStyle`  
 Style okna Standardowy domyślny.  
  
 `t_dwExStyle`  
 Domyślnie rozszerzone Style okna.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statyczny) Pobiera rozszerzone style `CWinTraits` obiektu.|  
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statyczny) Pobiera standardowe style dla `CWinTraits` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 To [cech okna](../../atl/understanding-window-traits.md) klasa udostępnia prostą metodę standaryzacji stylów używany do tworzenia obiektu ATL okna. Użyj specjalizacji tej klasy jako parametr szablonu w celu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) lub innej firmy ATL — klasy okna do określenia wartości domyślne standardowe i rozszerzone style używane dla wystąpień tej klasy okna.  
  
 Użyj tego szablonu, gdy chcesz zapewnić domyślne style okna, które będą używane tylko wtedy, gdy nie inne style są określone w wywołaniu [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 ATL zawiera trzy wstępnie zdefiniowane specjalizacji szablonu dla często używanych kombinacji Style okna:  
  
 `CControlWinTraits`  
 Przeznaczona dla okna formantu standardowego. Są używane następujące standardowe style: **ws_child —**, **ws_visible —**, **ws_clipchildren —**, i **ws_clipsiblings —**. Nie ma żadnych rozszerzone style.  
  
 `CFrameWinTraits`  
 Przeznaczona dla standardowych ramki okna. Standardowe style używane obejmują: **ws_overlappedwindow —**, **ws_clipchildren —**, i **ws_clipsiblings —**. Rozszerzone style używane obejmują: **ws_ex_appwindow —** i **ws_ex_windowedge —**.  
  
 `CMDIChildWinTraits`  
 Przeznaczona dla standardowych okna podrzędnego MDI. Standardowe style używane obejmują: **ws_overlappedwindow —**, **ws_child —**, **ws_visible —**, **ws_clipchildren —**i **Ws_clipsiblings —**. Rozszerzone style używane obejmują: **ws_ex_mdichild —**.  
  
 Jeśli chcesz upewnić się, że niektóre style są ustawione dla wszystkich wystąpień klasy okna, umożliwiając inne style określone na podstawie poszczególnych wystąpień [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) zamiast tego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="getwndstyle"></a>CWinTraits::GetWndStyle  
 Wywołanie tej funkcji można pobrać standardowe style `CWinTraits` obiektu.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Standardowe style używany do tworzenia okna. Jeśli `dwStyle` ma wartość 0, wartości stylu szablonu ( `t_dwStyle`) są zwracane. Jeśli `dwStyle` jest różna od zera, `dwStyle` jest zwracany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Style okna standardowego obiektu.  
  
##  <a name="getwndexstyle"></a>CWinTraits::GetWndExStyle  
 Wywołanie tej funkcji można pobrać rozszerzone style `CWinTraits` obiektu.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Rozszerzone style używany do tworzenia okna. Jeśli `dwExStyle` ma wartość 0, wartości stylu szablonu ( `t_dwExStyle`) są zwracane. Jeśli `dwExStyle` jest różna od zera, `dwExStyle` jest zwracany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozszerzone Style okna obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Członkowie klasy](http://msdn.microsoft.com/en-us/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Opis cech okna](../../atl/understanding-window-traits.md)
