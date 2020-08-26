---
title: IDocHostUIHandlerDispatch, interfejs
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 4d80934a5768eda917c90345ddeeff017edf0eae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835444"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch, interfejs

Interfejs do aparatu analizy i renderowania HTML firmy Microsoft.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

> [!NOTE]
> Linki w poniższej tabeli dotyczą tematów referencyjnych dotyczących zestawu SDK INet dla elementów członkowskich interfejsu [IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) . `IDocHostUIHandlerDispatch` ma takie same funkcje jak `IDocUIHostHandler` , z różnicą, że `IDocHostUIHandlerDispatch` jest to dispinterface, który `IDocUIHostHandler` jest interfejsem niestandardowym.

|Nazwa|Opis|
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Wywoływana z implementacji MSHTML elementu [IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Wywoływana również, gdy MSHTML wyświetla modalny interfejs użytkownika.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Wywoływana na hoście przez MSHTML, aby umożliwić hostowi zastępowanie obiektu danych MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Wywoływane przez MSHTML, gdy jest używany jako element docelowy upuszczania, aby umożliwić hostowi dostarczenie alternatywnej [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[Getexternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Wywoływane przez MSHTML, aby uzyskać interfejs IDispatch hosta.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Pobiera możliwości interfejsu użytkownika hosta MSHTML.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Zwraca klucz rejestru, w którym w module MSHTML są przechowywane preferencje użytkownika.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Wywołuje się, gdy MSHTML usuwa menu i paski narzędzi.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Wywoływana z implementacji MSHTML elementu [IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Wywoływana z implementacji MSHTML elementu [IOleInPlaceActiveObject:: OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Wywoływana z implementacji MSHTML elementu [IOleInPlaceActiveObject:: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Wywoływana z MSHTML, aby wyświetlić menu kontekstowe.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Umożliwia hostowi zastępowanie menu i pasków narzędzi MSHTML.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Wywoływane przez MSHTML w przypadku wywołania [IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) lub [IOleControlSite:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) .|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Wywoływane przez MSHTML, aby umożliwić hostowi zmianę adresu URL do załadowania.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Powiadamia hosta o zmianie stanu polecenia.|

## <a name="remarks"></a>Uwagi

Host może zamienić menu, paski narzędzi i menu kontekstowe używane przez aparat analizy i renderowania HTML firmy Microsoft (MSHTML) przez implementację tego interfejsu.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|ATLIFace. idl|
|C++|ATLIFace. h (również zawarte w ATLBase. h)|

## <a name="see-also"></a>Zobacz też

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
