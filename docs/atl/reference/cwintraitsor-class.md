---
title: Klasa CWinTraitsOR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs: C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 14796948369b92c9137dc7e02a8399910d46997c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cwintraitsor-class"></a>Klasa CWinTraitsOR
Ta klasa udostępnia metodę standaryzacji style używane podczas tworzenia obiektu okna.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```  
  
#### <a name="parameters"></a>Parametry  
 `t_dwStyle`  
 Style okna domyślne.  
  
 `t_dwExStyle`  
 Domyślnie rozszerzone Style okna.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Pobiera rozszerzone style `CWinTraitsOR` obiektu.|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Pobiera standardowe style dla `CWinTraitsOR` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 To [cech okna](../../atl/understanding-window-traits.md) klasa udostępnia prostą metodę standaryzacji stylów używany do tworzenia obiektu ATL okna. Użyj specjalizacji tej klasy jako parametr szablonu w celu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) lub innej klasy okien ALT firmy do określenia minimalny zestaw standardowych i rozszerzone style do zastosowania w przypadku wystąpienia tej klasy okna.  
  
 Użyj specjalizacja szablonu, jeśli chcesz upewnić się, że niektóre style są ustawione dla wszystkich wystąpień klasy okna umożliwiając inne style można konfigurować na poszczególnych wystąpień w wywołaniu [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 Jeśli chcesz podać domyślne style okna, które będą używane tylko wtedy, gdy nie inne style są określone w wywołaniu `CWindowImpl::Create`, użyj [CWinTraits](../../atl/reference/cwintraits-class.md) zamiast tego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle  
 Wywołanie tej funkcji można pobrać kombinację (przy użyciu operatora logicznego OR) standardowe style `CWinTraits` obiektów i określonej przez domyślne style `t_dwStyle`.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Style używane do tworzenia okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kombinacja style, które są przekazywane w `dwStyle` i domyślne te określone przez `t_dwStyle`, przy użyciu operatora logicznego OR.  
  
##  <a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle  
 Wywołanie tej funkcji można pobrać kombinację (przy użyciu operatora logicznego OR) rozszerzone style `CWinTraits` obiektów i określonej przez domyślne style `t_dwStyle`.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Rozszerzone style używany do tworzenia okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kombinacja rozszerzone style, które są przekazywane w `dwExStyle` i domyślne określony przez `t_dwExStyle`, przy użyciu operator logiczny OR  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Opis cech okna](../../atl/understanding-window-traits.md)

