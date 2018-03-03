---
title: Klasa _U_MENUorID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs:
- C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ddde6ff5d45c90e675bd2e44ac421e840d1357b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="umenuorid-class"></a>Klasa _U_MENUorID
Ta klasa udostępnia otoki **właściwości CreateWindow** i **CreateWindowEx**.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class _U_MENUorID
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|Konstruktor.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Dojście do menu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa karta argument umożliwia albo identyfikatorów ( **UINT**s) lub uchwyty menu ( `HMENU`s) mają być przekazane do funkcji bez konieczności jawnego rzutowania na części obiektu wywołującego.  
  
 Ta klasa jest przeznaczony do implementacji otoki do interfejsu API systemu Windows, szczególnie [właściwości CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) i [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkcje, które akceptują `HMENU` argumentu, który może być elementem podrzędnym Identyfikator okna ( **UINT**) zamiast dojście menu. Na przykład można zobaczyć ta klasa jest używana jako parametr [CWindowImpl::Create](cwindowimpl-class.md#create).  

  
 Klasa definiuje dwa przeciążenia konstruktora: jeden akceptuje **UINT** akceptuje argument, a druga `HMENU` argumentu. **UINT** argument jest po prostu rzutowane na `HMENU` w Konstruktorze i wynik przechowywany w element członkowski danych klasy, [m_hMenu](#_u_menuorid__m_hmenu). Argument `HMENU` konstruktora są przechowywane bezpośrednio, bez konwersji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu  
 Klasa zawiera wartość przekazywane do jednego z jego konstruktorów jako publiczną `HMENU` element członkowski danych.  
  
```
HMENU m_hMenu;
```  
  
##  <a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID  
 **UINT** argument jest po prostu rzutowane na `HMENU` w Konstruktorze i wynik przechowywany w element członkowski danych klasy, [m_hMenu](#_u_menuorid__m_hmenu).  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator okna podrzędnego.  
  
 `hMenu`  
 Dojście menu.  
  
### <a name="remarks"></a>Uwagi  
 Argument `HMENU` konstruktora są przechowywane bezpośrednio, bez konwersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
