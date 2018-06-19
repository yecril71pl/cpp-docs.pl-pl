---
title: Klasa elementem IDispatchImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fddf556eba07264f6ea0b01edea3e3d1e8a3a7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364369"
---
# <a name="idispatchimpl-class"></a>Klasa elementem IDispatchImpl
Udostępnia domyślną implementację dla `IDispatch` część w podwójne interfejsu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0, 
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `T`  
 Interfejs podwójny.  
  
 [in] `piid`  
 Wskaźnik na celu uzyskanie identyfikatora IID `T`.  
  
 [in] `plibid`  
 Wskaźnik do identyfikatora LIBID biblioteki typów, który zawiera informacje o interfejsie. Domyślnie jest przekazywany z biblioteki typów na poziomie serwera.  
  
 [in] `wMajor`  
 Wersja główna biblioteki typów. Domyślna wartość to 1.  
  
 [in] `wMinor`  
 Wersja pomocnicza biblioteki typów. Domyślna wartość to 0.  
  
 [in] `tihclass`  
 Klasa używana do zarządzania informacji o typie `T`. Domyślna wartość to `CComTypeInfoHolder`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Konstruktor. Wywołania `AddRef` w zmiennej członka chronionego, która zarządza informacji o typie dla dwóch interfejsu. Wywołania destruktora `Release`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Zestaw nazw jest mapowany na odpowiedni zestaw identyfikatorów wysyłania.|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Pobiera informacje o typie dla dwóch interfejsu.|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Określa, czy jest informacji o typie podwójną interfejsu.|  
|[IDispatchImpl::Invoke](#invoke)|Zapewnia dostęp do metody i właściwości udostępniane przez interfejs podwójny.|  
  
## <a name="remarks"></a>Uwagi  
 `IDispatchImpl` udostępnia domyślną implementację dla `IDispatch` należą do żadnych podwójną interfejs dla obiektu. Interfejs podwójny pochodzi z `IDispatch` i używa tylko typów automatyzacji. Jak dispinterface podwójna interfejs obsługuje powiązanie wczesne i późne wiązanie; Podwójna interfejs obsługuje również wiązanie z vtable.  
  
 W poniższym przykładzie przedstawiono Typowa implementacja `IDispatchImpl`.  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 Domyślnie `IDispatchImpl` klasy odwołuje się do informacji o typie `T` w rejestrze. Aby zaimplementować interfejs wyrejestrować, można użyć `IDispatchImpl` klasy bez uzyskiwania dostępu do rejestru za pomocą numeru wersji wstępnie zdefiniowane. W przypadku utworzenia `IDispatchImpl` obiektu, który ma jako wartość 0xFFFF `wMajor` i 0xFFFF jako wartość `wMinor`, `IDispatchImpl` klasy pobiera biblioteki typów z pliku dll zamiast rejestru.  
  
 `IDispatchImpl` zawiera statyczny element członkowski typu `CComTypeInfoHolder` który zarządza informacji o typie dla dwóch interfejsu. Jeśli masz wiele obiektów implementujących podwójną sam interfejs, tylko jedno wystąpienie `CComTypeInfoHolder` jest używany.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames  
 Zestaw nazw jest mapowany na odpowiedni zestaw identyfikatorów wysyłania.  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [funkcji IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) w systemie Windows SDK.  
  
##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo  
 Pobiera informacje o typie dla dwóch interfejsu.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) w systemie Windows SDK.  
  
##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount  
 Określa, czy jest informacji o typie podwójną interfejsu.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz `IDispatch::GetTypeInfoCount` w systemie Windows SDK.  
  
##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl  
 Konstruktor. Wywołania `AddRef` w zmiennej członka chronionego, która zarządza informacji o typie dla dwóch interfejsu. Wywołania destruktora **wersji**.  
  
```
IDispatchImpl();
```  
  
##  <a name="invoke"></a>  IDispatchImpl::Invoke  
 Zapewnia dostęp do metody i właściwości udostępniane przez interfejs podwójny.  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
