---
title: Interfejs IAxWinAmbientDispatchEx
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: 638152d8c49bd20742a586bc665efcdb662b6f3a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413891"
---
# <a name="iaxwinambientdispatchex-interface"></a>Interfejs IAxWinAmbientDispatchEx

Ten interfejs implementuje dodatkowe właściwości otoczenia hostowanej kontrolki.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Ta metoda jest wywoływana, aby uzupełnić domyślny interfejs zmieniono właściwość przy użyciu interfejsu użytkownika.|

## <a name="remarks"></a>Uwagi

Dołącz ten interfejs aplikacji biblioteki ATL, które są statycznie łączone z ATL i hosta formantów ActiveX, szczególnie kontrolki ActiveX, który ma właściwości otoczenia. Bez tego interfejsu spowoduje wygenerowanie potwierdzenie: "Czy pamiętasz o do przekazania LIBID CComModule::Init"

Ten interfejs jest udostępniany przez ActiveX hostingu formantu ATL, obiekty. Pochodną [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` dodaje metodę, która umożliwia uzupełnienie zmieniono właściwość interfejsu przez ATL własny.

<xref:System.Windows.Forms.AxHost> próbuje załadować informacji o typie o `IAxWinAmbientDispatch` i `IAxWinAmbientDispatchEx` z biblioteki typów, która zawiera kod.

Jeśli łączysz się ATL90.dll, **AXHost** zostaną załadowane informacje o typie z biblioteki typów w bibliotece DLL.

Zobacz [hostingu ActiveX kontrolek przy użyciu ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) Aby uzyskać więcej informacji.

## <a name="requirements"></a>Wymagania

Definicja ten interfejs jest dostępny w wielu formach, jak pokazano w poniższej tabeli.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|atliface.IDL|
|Biblioteki typów|ATL.dll|
|C++|atliface.h (dołączone do dodatków ATLBase.h)|

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

Ta metoda jest wywoływana, aby uzupełnić domyślny interfejs zmieniono właściwość przy użyciu interfejsu użytkownika.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch*<br/>
Wskaźnik do nowego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Gdy `SetAmbientDispatch` jest wywoływana za pomocą wskaźnika do nowego interfejsu ten nowy interfejs będzie służyć do wywołania dowolnego właściwości lub metody wymagane przez obsługiwanego formantu, jeśli te właściwości nie są już udostępniane przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Zobacz także

[Interfejs IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)
