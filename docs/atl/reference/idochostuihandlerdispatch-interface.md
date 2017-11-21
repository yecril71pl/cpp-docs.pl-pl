---
title: Interfejs IDocHostUIHandlerDispatch | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs: C++
helpviewer_keywords: IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: da373672c51dd47b67ee4457bd0d21f82a09c540
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="idochostuihandlerdispatch-interface"></a>Interfejs IDocHostUIHandlerDispatch
Interfejs do analizowania Microsoft HTML i aparatu renderowania.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
interface IDocHostUIHandlerDispatch : IDispatch
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
> [!NOTE]
>  Łącza w poniższej tabeli są tematy dokumentacji zestawu SDK INet dla członków [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx) interfejsu. `IDocHostUIHandlerDispatch`ma te same funkcje co **IDocUIHostHandler**, z tą różnicą, że trwa `IDocHostUIHandlerDispatch` jest dispinterface **IDocUIHostHandler** jest niestandardowy interfejs.  
  
|||  
|-|-|  
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115). Wywołuje się także, gdy MSHTML Wyświetla modalne interfejsu użytkownika.|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|Wywołuje się na hoście przez MSHTML umożliwia hosta zamienić MSHTML dla obiekt danych.|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|Wywoływane przez MSHTML, gdy jest on używany jako miejsca docelowego w jakim host do dostarczania zamiast [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679).|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|Metoda wywoływana przez MSHTML w celu uzyskania interfejsu IDispatch hosta.|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|Pobiera funkcje interfejsu użytkownika MSHTML hosta.|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|Zwraca klucz rejestru, w którym MSHTML są przechowywane preferencje użytkownika.|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|Wywoływane, gdy MSHTML Usuwa menu i pasków narzędzi.|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281).|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969).|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053).|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|Wywoływana z MSHTML, aby wyświetlić menu kontekstowe.|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|Umożliwia hosta zastąpić MSHTML menu i pasków narzędzi.|  
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|Wywoływane przez MSHTML podczas [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) lub [IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) jest wywoływana.|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|Metoda wywoływana przez MSHTML umożliwia hosta pozwala zmodyfikować adres URL do załadowania.|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|Powiadamia hosta, że stan polecenia został zmieniony.|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można zastąpić menu, paski narzędzi i menu kontekstowe używane przez Microsoft HTML podczas analizowania i aparatu renderowania (MSHTML) z zastosowaniem tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.  
  
|Typ definicji|Plik|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (również zawarte w ATLBase.h)|  
  
## <a name="see-also"></a>Zobacz też  
 [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)









