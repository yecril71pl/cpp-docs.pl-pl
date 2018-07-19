---
title: Klasa _U_MENUorID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f945766283fa6e58b1eb3430cc780b1ae136e9f
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884740"
---
# <a name="umenuorid-class"></a>Klasa _U_MENUorID
Ta klasa udostępnia otokę dla `CreateWindow` i `CreateWindowEx`.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
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
 Ta klasa adaptera argument umożliwia identyfikatorów (UINTs) lub menu dojścia (HMENUs), który zostanie przekazany do funkcji bez konieczności jawnego rzutowania przez obiekt wywołujący.  
  
 Ta klasa jest przeznaczona dla implementacji otoki do interfejsu API Windows, szczególnie [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) i [elementu CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkcje, które akceptują argument HMENU, które mogą być okna podrzędnego Identyfikator (UINT) zamiast uchwyt menu. Na przykład zostanie wyświetlony jako parametr do tej klasy w użyciu [CWindowImpl::Create](cwindowimpl-class.md#create).  

  
 Klasa definiuje dwa przeciążenia konstruktora: przyjmuje jeden UINT argument, a druga akceptuje HMENU argument. UINT argument tylko jest rzutowany na HMENU konstruktora i wyników, przechowywane w składowej danych jednego klasy, [m_hMenu](#_u_menuorid__m_hmenu). Argument Pro Konstruktor HMENU są przechowywane bezpośrednio, bez konwersji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu  
 Klasa przechowuje wartość przekazana do jednej z jego konstruktorów jako publicznej składowej danych HMENU.  
  
```
HMENU m_hMenu;
```  
  
##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID  
 UINT argument tylko jest rzutowany na HMENU konstruktora i wyników, przechowywane w składowej danych jednego klasy, [m_hMenu](#_u_menuorid__m_hmenu).  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Identyfikator okna podrzędnego.  
  
 *hMenu*  
 Uchwyt menu.  
  
### <a name="remarks"></a>Uwagi  
 Argument Pro Konstruktor HMENU są przechowywane bezpośrednio, bez konwersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
