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
ms.openlocfilehash: 22815ddf3131b9d262d68a3202f4f500b7edf807
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358143"
---
# <a name="iaxwinambientdispatchex-interface"></a>Interfejs IAxWinAmbientDispatchEx
Ten interfejs implementuje dodatkowe właściwości otaczających hostowanej kontrolki.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[SetAmbientDispatch](#setambientdispatch)|Ta metoda jest wywoływana, aby uzupełnić domyślnego interfejsu — właściwość otoczenia z interfejsem użytkownika.|  
  
## <a name="remarks"></a>Uwagi  
 Dołącz ten interfejs ATL aplikacji, które są połączone statycznie z ATL i hosta formantów ActiveX, szczególnie kontrolki ActiveX ma właściwości otoczenia. W tym ten interfejs nie wygeneruje potwierdzenie: "Zapomnialeś do przekazania do CComModule::Init identyfikatora LIBID"  
  
 Ten interfejs jest udostępniany przez formant ActiveX w ATL hosting obiektów. Pochodną [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` dodaje metodę, która umożliwia uzupełnienie — właściwość otoczenia interfejsu przez ATL własny.  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) próbuje załadować informacji o typie o `IAxWinAmbientDispatch` i `IAxWinAmbientDispatchEx` z biblioteki typów, który zawiera kod.  
  
 Jeśli łączysz się ATL90.dll, **AXHost** załaduje informacji o typie z biblioteki typów w bibliotece DLL.  
  
 Zobacz [Hosting AXHost za pomocą biblioteki ATL programu ActiveX formanty](../../atl/hosting-activex-controls-using-atl-axhost.md) więcej szczegółów.  
  
## <a name="requirements"></a>Wymagania  
 Definicja tego interfejsu jest dostępne w wielu formularzach, jak pokazano w poniższej tabeli.  
  
|Typ definicji|Plik|  
|---------------------|----------|  
|IDL|atliface.IDL|  
|Biblioteki typów|ATL.dll|  
|C++|atliface.h (również zawarte w ATLBase.h)|  
  
##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch  
 Ta metoda jest wywoływana, aby uzupełnić domyślnego interfejsu — właściwość otoczenia z interfejsem użytkownika.  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 *pDispatch*  
 Wskaźnik do nowego interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `SetAmbientDispatch` jest wywoływana za pomocą wskaźnika do nowego interfejsu nowy interfejs będzie służyć do wywołania żadnych właściwości ani metod wyświetlony monit o podanie przez formant hostowanej, jeśli te właściwości nie są już dostarczane przez [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)
