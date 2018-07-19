---
title: Klasa CWinTraitsOR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a996b1f2a9b81e9d74548f3e69883cee447ac3a0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881620"
---
# <a name="cwintraitsor-class"></a>Klasa CWinTraitsOR
Ta klasa dostarcza metody do standaryzacji stylów używanych podczas tworzenia obiektu okna.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```  
  
#### <a name="parameters"></a>Parametry  
 *t_dwStyle*  
 Style okna ramowego domyślne.  
  
 *t_dwExStyle*  
 Domyślnie rozszerzone Style okna.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Pobiera rozszerzone style `CWinTraitsOR` obiektu.|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Pobiera standardowe style dla `CWinTraitsOR` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 To [cech okna](../../atl/understanding-window-traits.md) klasa udostępnia prostą metodę standaryzacji stylów używany do tworzenia obiektu ATL okna. Użyj specjalizacji tej klasy jako parametr szablonu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) lub innej klasy okien ATL, aby określić minimalny zestaw standardowych i rozszerzone style ma być używany dla wystąpień tej klasy okna.  
  
 Użyj specjalizacji tego szablonu, jeśli chcesz upewnić się, że określone style są ustawione dla wszystkich wystąpień klasy okna umożliwiając innymi stylami, należy ustawić na podstawie poszczególnych wystąpień w wywołaniu [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 Jeśli chcesz udostępnić domyślne style okna, które będą używane tylko wtedy, gdy nie inne style są określone w wywołaniu `CWindowImpl::Create`, użyj [CWinTraits](../../atl/reference/cwintraits-class.md) zamiast tego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="getwndstyle"></a>  CWinTraitsOR::GetWndStyle  
 Wywołaj tę funkcję, aby pobrać kombinacji (przy użyciu operatora logicznego OR) standardowa style `CWinTraits` obiektu i style domyślne określone przez *t_dwStyle*.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Style służy do tworzenia okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kombinacja style, które są przekazywane w *dwStyle* i domyślne te określone przez `t_dwStyle`, przy użyciu operatora logicznego OR.  
  
##  <a name="getwndexstyle"></a>  CWinTraitsOR::GetWndExStyle  
 Wywołaj tę funkcję, aby pobrać kombinacji (przy użyciu operatora logicznego OR) rozszerzone style `CWinTraits` obiektu i style domyślne określone przez `t_dwStyle`.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Rozszerzone style służy do tworzenia okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kombinacja rozszerzone style, które są przekazywane w *dwExStyle* i określonych przez domyślne `t_dwExStyle`, przy użyciu operatora logicznego OR  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Opis cech okna](../../atl/understanding-window-traits.md)

