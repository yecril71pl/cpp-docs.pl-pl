---
title: Interfejs IAxWinHostWindowlic
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: 561a65702f1d4f57b4db1afc75769ce4cc523c1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329921"
---
# <a name="iaxwinhostwindowlic-interface"></a>Interfejs IAxWinHostWindowlic

Ten interfejs zawiera metody manipulowania licencjonowanym formantem i jego obiektem hosta.

## <a name="syntax"></a>Składnia

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CreateControlLic (Twór niesie ze strony](#createcontrollic)|Tworzy licencjonowany formant i dołącza go do obiektu hosta.|
|[CreateControlLicEx](#createcontrollicex)|Tworzy licencjonowany formant, dołącza go do obiektu hosta i opcjonalnie konfiguruje program obsługi zdarzeń.|

## <a name="remarks"></a>Uwagi

`IAxWinHostWindowLic`dziedziczy z [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) i dodaje metody, które obsługują tworzenie licencjonowanych formantów.

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa członków tego interfejsu.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.

|Typ definicji|Plik|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (również w ATLBase.h)|

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Tworzy licencjonowany formant, inicjuje go i hostuje `hWnd`w oknie identyfikowanym przez program .

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic (bstrlic)*<br/>
[w] BSTR, który zawiera klucz licencyjny formantu.

### <a name="remarks"></a>Uwagi

Zobacz [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) opis pozostałych parametrów i zwracanej wartości.

Wywołanie tej metody jest równoznaczne z [wywołaniem IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `IAxWinHostWindowLic::CreateControlLic`.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go i obsługuje w określonym oknie, podobnie jak [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic (bstrlic)*<br/>
[w] BSTR, który zawiera klucz licencyjny formantu.

### <a name="remarks"></a>Uwagi

Zobacz [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) opis pozostałych parametrów i zwracanej wartości.

### <a name="example"></a>Przykład

Zobacz [Hosting ActiveX Formanty przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla próbki, która używa `IAxWinHostWindowLic::CreateControlLicEx`.
