---
title: Interfejs IDocHostUIHandlerDispatch | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs:
- C++
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57dbb9e5ed73ce8ed85d7c90d05705cefdd4ed9b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194770"
---
# <a name="idochostuihandlerdispatch-interface"></a>Interfejs IDocHostUIHandlerDispatch
Interfejs do analizowania Microsoft HTML i aparat renderowania.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
interface IDocHostUIHandlerDispatch : IDispatch
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
> [!NOTE]
>  Łącza w tabeli poniżej dotyczą tematy referencyjne INet zestawu SDK dla uczestników programu [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx) interfejsu. `IDocHostUIHandlerDispatch` ma taką samą funkcjonalność jak `IDocUIHostHandler`, z tą różnicą, że `IDocHostUIHandlerDispatch` jest dispinterface, natomiast `IDocUIHostHandler` jest niestandardowy interfejs.  
  
|||  
|-|-|  
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Wywołuje się również, gdy MSHTML Wyświetla modalnego interfejsu użytkownika.|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|Wywoływane na hoście przez MSHTML, aby zezwolić na hosta zastąpić obiekt danych firmy MSHTML.|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|Wywoływane przez MSHTML, gdy jest on używany jako miejsca docelowego umożliwia hosta, które umożliwiają określanie wartości zamiast [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|Metoda wywoływana przez MSHTML można uzyskać interfejsu IDispatch hosta.|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|Pobiera funkcje interfejsu użytkownika hosta MSHTML.|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|Zwraca klucz rejestru, w którym są przechowywane preferencje użytkownika MSHTML.|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|Wywołuje się, gdy MSHTML usuwa jego menu i paski narzędzi.|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|Wywoływana z MSHTML, aby wyświetlić menu kontekstowe.|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|Zezwalaj hostowi na Zastąp MSHTML menu i paski narzędzi.|  
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|Wywoływane przez MSHTML podczas [IOleInPlaceActiveObject::TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) lub [IOleControlSite::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) jest wywoływana.|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|Metoda wywoływana przez MSHTML, aby zezwolić na hoście szansy sprzedaży zmodyfikować adres URL do załadowania.|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|Powiadamia hosta, że stan polecenia został zmieniony.|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można zastąpić, menu, paski narzędzi i menu kontekstowe używane przez Microsoft HTML podczas analizowania i aparat renderowania (MSHTML) poprzez implementację tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.  
  
|Typ definicji|Plik|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (dołączone do dodatków ATLBase.h)|  
  
## <a name="see-also"></a>Zobacz też  
 [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)









