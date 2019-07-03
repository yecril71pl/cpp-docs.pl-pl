---
title: Interfejs IDocHostUIHandlerDispatch
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: a60c178eff1e02c3032e792f9a0420dfeab82388
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552169"
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
>  Łącza w tabeli poniżej dotyczą tematy referencyjne INet zestawu SDK dla uczestników programu [IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) interfejsu. `IDocHostUIHandlerDispatch` ma taką samą funkcjonalność jak `IDocUIHostHandler`, z tą różnicą, że `IDocHostUIHandlerDispatch` jest dispinterface, natomiast `IDocUIHostHandler` jest niestandardowy interfejs.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Wywołuje się również, gdy MSHTML Wyświetla modalnego interfejsu użytkownika.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Wywoływane na hoście przez MSHTML, aby zezwolić na hosta zastąpić obiekt danych firmy MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Wywoływane przez MSHTML, gdy jest on używany jako miejsca docelowego umożliwia hosta, które umożliwiają określanie wartości zamiast [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Metoda wywoływana przez MSHTML można uzyskać interfejsu IDispatch hosta.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Pobiera funkcje interfejsu użytkownika hosta MSHTML.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Zwraca klucz rejestru, w którym są przechowywane preferencje użytkownika MSHTML.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Wywołuje się, gdy MSHTML usuwa jego menu i paski narzędzi.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Wywoływać z implementacji MSHTML [IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Wywoływana z MSHTML, aby wyświetlić menu kontekstowe.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Zezwalaj hostowi na Zastąp MSHTML menu i paski narzędzi.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Wywoływane przez MSHTML podczas [IOleInPlaceActiveObject::TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) lub [IOleControlSite::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) jest wywoływana.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Metoda wywoływana przez MSHTML, aby zezwolić na hoście szansy sprzedaży zmodyfikować adres URL do załadowania.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Powiadamia hosta, że stan polecenia został zmieniony.|

## <a name="remarks"></a>Uwagi

Hosta można zastąpić, menu, paski narzędzi i menu kontekstowe używane przez Microsoft HTML podczas analizowania i aparat renderowania (MSHTML) poprzez implementację tego interfejsu.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (dołączone do dodatków ATLBase.h)|

## <a name="see-also"></a>Zobacz także

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
