---
title: Klasa IProvideClassInfo2Impl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
dev_langs:
- C++
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7e0bd440e2e4bd8d32525fe4be6aaad2c401f6a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880625"
---
# <a name="iprovideclassinfo2impl-class"></a>Klasa IProvideClassInfo2Impl
Ta klasa udostępnia domyślną implementację elementu [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) i [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) metody.  
  
## <a name="syntax"></a>Składnia  
  
```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>  
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```  
  
#### <a name="parameters"></a>Parametry  
 *pcoclsid*  
 Wskaźnik do klasy coclass identyfikator.  
  
 *psrcid*  
 Wskaźnik na identyfikator dla domyślnej klasy coclass wychodzące dispinterface.  
  
 *plibid*  
 Wskaźnik do identyfikatora LIBID biblioteki typów, który zawiera informacje o interfejsie. Domyślnie jest przekazywany biblioteki typów na poziomie serwera.  
  
 *wMajor*  
 Wersja główna biblioteki typów. Wartość domyślna to 1.  
  
 *wMinor*  
 Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.  
  
 *tihclass*  
 Klasa używana do zarządzania informacjami o typie klasy coclass. Wartość domyślna to `CComTypeInfoHolder`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Pobiera `ITypeInfo` wskaźnik do informacji o typie klasy coclass.|  
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Pobiera identyfikator GUID obiektu dispinterface wychodzących.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::_tih](#_tih)|Zarządza informacji o typie dla klasy coclass.|  
  
## <a name="remarks"></a>Uwagi  
 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) interfejs rozszerza [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) , dodając `GetGUID` metody. Ta metoda umożliwia klientowi można pobrać obiektu wychodzącego identyfikatora IID interfejsu dla jego domyślny zestaw zdarzeń. Klasa `IProvideClassInfo2Impl` udostępnia domyślną implementację elementu `IProvideClassInfo` i `IProvideClassInfo2` metody.  
  
 `IProvideClassInfo2Impl` zawiera statyczny element członkowski typu `CComTypeInfoHolder` który zarządza informacji o typie dla klasy coclass.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getclassinfo"></a>  IProvideClassInfo2Impl::GetClassInfo  
 Pobiera `ITypeInfo` wskaźnik do informacji o typie klasy coclass.  
  
```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IProvideClassInfo::GetClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms690192) w Windows SDK.  
  
##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID  
 Pobiera identyfikator GUID obiektu dispinterface wychodzących.  
  
```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IProvideClassInfo2::GetGUID](http://msdn.microsoft.com/library/windows/desktop/ms679721) w Windows SDK.  
  
##  <a name="iprovideclassinfo2impl"></a>  IProvideClassInfo2Impl::IProvideClassInfo2Impl  
 Konstruktor.  
  
```
IProvideClassInfo2Impl();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania `AddRef` na [_tih](#_tih) elementu członkowskiego. Wywołania destruktora `Release`.  
  
##  <a name="_tih"></a>  IProvideClassInfo2Impl::_tih  
 Ten element członkowski danych statycznych jest wystąpieniem typu parametru szablonu klasy, *tihclass*, która domyślnie wynosi `CComTypeInfoHolder`.  
  
```
static  tihclass
    _tih;
```     
  
### <a name="remarks"></a>Uwagi  
 `_tih` zarządza informacji o typie dla klasy coclass.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
