---
title: Interfejs IAxWinHostWindowLic
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: aca3970d13db53ffa04fe9582bbe9b8db78e820d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275993"
---
# <a name="iaxwinhostwindowlic-interface"></a>Interfejs IAxWinHostWindowLic

Ten interfejs zapewnia metody do manipulowania licencjonowany formant i jego obiekt hosta.

## <a name="syntax"></a>Składnia

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CreateControlLic](#createcontrollic)|Tworzy licencjonowany formant i dołącza je do obiektu hosta.|
|[CreateControlLicEx](#createcontrollicex)|Tworzy licencjonowany formant, a następnie dołącza je do obiektu hosta i opcjonalnie konfiguruje program obsługi zdarzeń.|

## <a name="remarks"></a>Uwagi

`IAxWinHostWindowLic` dziedziczy [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) i dodaje metody, które obsługują tworzenie licencjonowane formanty.

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu korzystającego z elementów członkowskich tego interfejsu.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna jako IDL lub C++, jak pokazano poniżej.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (dołączone do dodatków ATLBase.h)|

##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic

Tworzy licencjonowany formant, inicjuje go i umieszcza w oknie identyfikowane przez `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic*<br/>
[in] BSTR, który zawiera klucz licencji dla formantu.

### <a name="remarks"></a>Uwagi

Zobacz [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) opis pozostałych parametrów i zwracanej wartości.

Wywołanie tej metody jest równoważne z wywoływaniem [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `IAxWinHostWindowLic::CreateControlLic`.

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie, podobnie jak [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

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

*bstrLic*<br/>
[in] BSTR, który zawiera klucz licencji dla formantu.

### <a name="remarks"></a>Uwagi

Zobacz [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) opis pozostałych parametrów i zwracanej wartości.

### <a name="example"></a>Przykład

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) dla przykładu, który używa `IAxWinHostWindowLic::CreateControlLicEx`.
