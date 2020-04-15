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
ms.openlocfilehash: f4816846801e388619db62998ec979a1100916ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329980"
---
# <a name="iaxwinambientdispatchex-interface"></a>Interfejs IAxWinAmbientDispatchEx

Ten interfejs implementuje dodatkowe właściwości otoczenia dla hostowanego formantu.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[SetAmbientDispatch (SetAmbientDispatch)](#setambientdispatch)|Ta metoda jest wywoływana w celu uzupełnienia domyślnego interfejsu właściwości otoczenia za pomocą interfejsu zdefiniowanego przez użytkownika.|

## <a name="remarks"></a>Uwagi

Dołącz ten interfejs w aplikacjach ATL, które są statycznie połączone z ATL i hosta ActiveX Formanty, zwłaszcza ActiveX Formanty, które mają właściwości otoczenia. Nie wliczając tego interfejsu wygeneruje to twierdzenie: "Czy zapomniałeś przekazać LIBID do CComModule::Init"

Ten interfejs jest narażony przez obiekty hostingowe activex formantu ATL. Pochodzi z [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), dodaje metodę, `IAxWinAmbientDispatchEx` która pozwala na uzupełnienie interfejsu właściwości otoczenia dostarczonych przez ATL z jednym z własnych.

<xref:System.Windows.Forms.AxHost>spróbuje załadować informacje `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` o typie o i z biblioteki typów, która zawiera kod.

Jeśli łączysz się z biblioteką ATL90.dll, **AXHost** załaduje informacje o typie z biblioteki typów w bibliotece DLL.

Aby uzyskać więcej informacji, zobacz [Hostowanie formantów ActiveX za pomocą AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) a.

## <a name="requirements"></a>Wymagania

Definicja tego interfejsu jest dostępna w wielu formach, jak pokazano w poniższej tabeli.

|Typ definicji|Plik|
|---------------------|----------|
|Idl|atliface.idl|
|Biblioteka typów|Plik ATL.dll|
|C++|atliface.h (również w ATLBase.h)|

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Ta metoda jest wywoływana w celu uzupełnienia domyślnego interfejsu właściwości otoczenia za pomocą interfejsu zdefiniowanego przez użytkownika.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch (Niedysp.*<br/>
Wskaźnik do nowego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Gdy `SetAmbientDispatch` jest wywoływana ze wskaźnikiem do nowego interfejsu, ten nowy interfejs będzie używany do wywoływania wszelkich właściwości lub metod żądanych przez hostowany formant, jeśli te właściwości nie są już dostarczone przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Zobacz też

[Interfejs IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)
