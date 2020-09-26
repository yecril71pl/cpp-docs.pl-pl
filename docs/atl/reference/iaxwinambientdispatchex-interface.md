---
title: IAxWinAmbientDispatchEx, interfejs
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: 3359c17996eb78c3249abc83ff2d439381f209fe
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352989"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx, interfejs

Ten interfejs implementuje dodatkowe właściwości otoczenia dla hostowanej kontrolki.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|Ta metoda jest wywoływana w celu uzupełnienia domyślnego interfejsu właściwości otoczenia przy użyciu interfejsu zdefiniowanego przez użytkownika.|

## <a name="remarks"></a>Uwagi

Dołącz ten interfejs w aplikacjach ATL, które są statycznie połączone z ATL i hostami ActiveX, zwłaszcza formantów ActiveX mających właściwości otoczenia. Nie uwzględnia tego interfejsu spowoduje wygenerowanie tego potwierdzenia: "czy zapomnisz przekazać identyfikatora LIBID do CComModule:: init"

Ten interfejs jest udostępniany przez obiekty obsługujące kontrolki ActiveX ATL. Pochodny od [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` dodaje metodę, która pozwala na uzupełnienie interfejsu właściwości otoczenia zapewnianego przez ATL z jednym z własnych.

<xref:System.Windows.Forms.AxHost> podejmie próbę załadowania informacji o typie `IAxWinAmbientDispatch` i `IAxWinAmbientDispatchEx` z biblioteki typów, która zawiera kod.

Jeśli łączysz się z ATL90.dll, **AxHost** załaduje informacje o typie z biblioteki typów w bibliotece DLL.

Aby uzyskać więcej informacji, zobacz [hostowanie formantów ActiveX przy użyciu biblioteki ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) .

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna w wielu formularzach, jak pokazano w poniższej tabeli.

|Typ definicji|Plik|
|---------------------|----------|
|IDL|atliface. idl|
|Biblioteka typów|ATL.dll|
|C++|atliface. h (również zawarte w ATLBase. h)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> IAxWinAmbientDispatchEx::SetAmbientDispatch

Ta metoda jest wywoływana w celu uzupełnienia domyślnego interfejsu właściwości otoczenia przy użyciu interfejsu zdefiniowanego przez użytkownika.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch*<br/>
Wskaźnik do nowego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Gdy `SetAmbientDispatch` jest wywoływana za pomocą wskaźnika do nowego interfejsu, ten nowy interfejs zostanie użyty do wywołania wszelkich właściwości lub metod, które poprosi formant hostowany, jeśli te właściwości nie zostały jeszcze dostarczone przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Zobacz też

[IAxWinAmbientDispatch, interfejs](../../atl/reference/iaxwinambientdispatch-interface.md)
