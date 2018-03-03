---
title: Klasa IProvideClassInfo2Impl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6fe466608acaecfaf6219b6d15d27e0611ac2511
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iprovideclassinfo2impl-class"></a>Klasa IProvideClassInfo2Impl
Ta klasa udostępnia domyślną implementację [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) i [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) metody.  
  
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
 Wskaźnik do identyfikatora dla klasy coclass domyślnego wychodzące dispinterface.  
  
 `plibid`  
 Wskaźnik do identyfikatora LIBID biblioteki typów, który zawiera informacje o interfejsie. Domyślnie jest przekazywany z biblioteki typów na poziomie serwera.  
  
 `wMajor`  
 Wersja główna biblioteki typów. Wartość domyślna to 1.  
  
 `wMinor`  
 Wersja pomocnicza biblioteki typów. Wartość domyślna to 0.  
  
 `tihclass`  
 Klasa używana do zarządzania informacji o typie coclass. Wartość domyślna to `CComTypeInfoHolder`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Pobiera **ITypeInfo** wskaźnika do klasy coclass typu informacji.|  
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Pobiera identyfikator GUID obiektu dispinterface wychodzących.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::_tih](#_tih)|Zarządza informacji o typie dla klasy coclass.|  
  
## <a name="remarks"></a>Uwagi  
 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) rozszerza interfejs [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) przez dodanie `GetGUID` metody. Ta metoda umożliwia klientowi można pobrać obiektu wychodzącego identyfikatora IID interfejsu dla jego domyślny zestaw zdarzeń. Klasa `IProvideClassInfo2Impl` udostępnia domyślną implementację elementu **IProvideClassInfo** i `IProvideClassInfo2` metody.  
  
 `IProvideClassInfo2Impl`zawiera statyczny element członkowski typu `CComTypeInfoHolder` który zarządza informacji o typie dla klasy coclass.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getclassinfo"></a>IProvideClassInfo2Impl::GetClassInfo  
 Pobiera `ITypeInfo` wskaźnika do klasy coclass typu informacji.  
  
```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IProvideClassInfo::GetClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms690192) w systemie Windows SDK.  
  
##  <a name="getguid"></a>IProvideClassInfo2Impl::GetGUID  
 Pobiera identyfikator GUID obiektu dispinterface wychodzących.  
  
```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IProvideClassInfo2::GetGUID](http://msdn.microsoft.com/library/windows/desktop/ms679721) w systemie Windows SDK.  
  
##  <a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl  
 Konstruktor.  
  
```
IProvideClassInfo2Impl();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania `AddRef` na [_tih](#_tih) elementu członkowskiego. Wywołania destruktora **wersji**.  
  
##  <a name="_tih"></a>IProvideClassInfo2Impl::_tih  
 Ten element członkowski danych statycznych jest wystąpieniem klasy parametr szablonu, `tihclass`, która domyślnie wynosi `CComTypeInfoHolder`.  
  
```
static  tihclass
    _tih;
```     
  
### <a name="remarks"></a>Uwagi  
 `_tih`zarządza informacji o typie dla klasy coclass.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
