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
ms.openlocfilehash: 9d67f00b88be88e1cb2691414b0666bd298977dd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220183"
---
# <a name="iprovideclassinfo2impl-class"></a>Klasa IProvideClassInfo2Impl
Ta klasa udostępnia domyślną implementację elementu [IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) i [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) metody.  
  
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
 [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) interfejs rozszerza [IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) , dodając `GetGUID` metody. Ta metoda umożliwia klientowi można pobrać obiektu wychodzącego identyfikatora IID interfejsu dla jego domyślny zestaw zdarzeń. Klasa `IProvideClassInfo2Impl` udostępnia domyślną implementację elementu `IProvideClassInfo` i `IProvideClassInfo2` metody.  
  
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
 Zobacz [IProvideClassInfo::GetClassInfo](/windows/desktop/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) w Windows SDK.  
  
##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID  
 Pobiera identyfikator GUID obiektu dispinterface wychodzących.  
  
```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IProvideClassInfo2::GetGUID](/windows/desktop/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) w Windows SDK.  
  
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
 `_tih` Zarządza informacji o typie dla klasy coclass.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
