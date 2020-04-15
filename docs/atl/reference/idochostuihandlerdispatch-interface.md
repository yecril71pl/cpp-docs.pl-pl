---
title: Interfejs IDocHostUIHandlerDispatch
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: b7072b80b738aa12635427a2604b38fb3585b452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329721"
---
# <a name="idochostuihandlerdispatch-interface"></a>Interfejs IDocHostUIHandlerDispatch

Interfejs do aparatu analizowania i renderowania html firmy Microsoft.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

> [!NOTE]
> Łącza w poniższej tabeli są do tematów odwołania SDK INet dla członków interfejsu [IDocUIHostHandler.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) `IDocHostUIHandlerDispatch`ma taką samą `IDocUIHostHandler`funkcjonalność jak , `IDocHostUIHandlerDispatch` z tą różnicą, `IDocUIHostHandler` że jest dispinterface, podczas gdy jest interfejs niestandardowy.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Wywoływana z implementacji MSHTML [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Wywoływana również wtedy, gdy MSHTML wyświetla modalny interfejs użytkownika.|
|[FilterDataObject (FilterDataObject)](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Wywołany przez MSHTML hosta, aby umożliwić hostowi zastąpienie obiektu danych MSHTML.|
|[GetDropTarget (GetDropTarget)](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Wywoływany przez MSHTML, gdy jest używany jako cel upuszczania, aby umożliwić gospodarzowi dostarczenie alternatywnego [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[GetExternal (własnośnik)GetEx](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Wywoływane przez MSHTML, aby uzyskać interfejs IDispatch hosta.|
|[GetHostInfo ( GetHostInfo )](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Pobiera możliwości interfejsu użytkownika hosta MSHTML.|
|[Ścieżka Dostępu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Zwraca klucz rejestru, pod którym mshtml przechowuje preferencje użytkownika.|
|[Hideui](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Wywoływane, gdy MSHTML usuwa jego menu i paski narzędzi.|
|[OnDocWindowAktywniej](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Wywoływana z implementacji MSHTML [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowAktywniej](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Wywoływana z implementacji MSHTML [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[Rozmiar RozmiaruBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Wywoływana z implementacji MSHTML [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[Showcontextmenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Wywoływane z MSHTML, aby wyświetlić menu kontekstowe.|
|[Showui](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Umożliwia hostowi zastąpienie menu MSHTML i pasków narzędzi.|
|[TłumaczAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Wywoływane przez MSHTML, gdy [IOleInPlaceActiveObject::TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) lub [IOleControlSite::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) jest wywoływana.|
|[TranslateUrl (Tłumaczenie)](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Wywoływane przez MSHTML, aby umożliwić hostowi możliwość zmodyfikowania adresu URL do załadowania.|
|[AktualizacjaUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Powiadamia hosta, że stan polecenia został zmieniony.|

## <a name="remarks"></a>Uwagi

Host może zastąpić menu, paski narzędzi i menu kontekstowe używane przez aparat analizowania i renderowania html firmy Microsoft (MSHTML) przez implementację tego interfejsu.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.

|Typ definicji|Plik|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (również w ATLBase.h)|

## <a name="see-also"></a>Zobacz też

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
