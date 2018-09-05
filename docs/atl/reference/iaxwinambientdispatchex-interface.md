---
title: Interfejs IAxWinAmbientDispatchEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c1c6ed120705886c1b0bb4836e851139543f629
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753915"
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

Dołącz ten interfejs aplikacji biblioteki ATL, które są statycznie łączone z ATL i hosta formantów ActiveX, szczególnie kontrolki ActiveX, który ma właściwości otoczenia. Ta asercja nie wliczając tego interfejsu spowoduje wygenerowanie: "Czy pamiętasz o do przekazania LIBID CComModule::Init"

Ten interfejs jest udostępniany przez ActiveX hostingu formantu ATL, obiekty. Pochodną [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` dodaje metodę, która umożliwia uzupełnienie zmieniono właściwość interfejsu przez ATL własny.

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) spróbuje załadować informacji o typie o `IAxWinAmbientDispatch` i `IAxWinAmbientDispatchEx` z biblioteki typów, która zawiera kod.

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

*pDispatch*  
Wskaźnik do nowego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Gdy `SetAmbientDispatch` jest wywoływana za pomocą wskaźnika do nowego interfejsu ten nowy interfejs będzie służyć do wywołania dowolnego właściwości lub metody wymagane przez obsługiwanego formantu, jeśli te właściwości nie są już udostępniane przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>Zobacz też

[Interfejs IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)
