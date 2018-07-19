---
title: Klasa IObjectWithSiteImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
dev_langs:
- C++
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9403ed1a4ba82a1e60c42ed0e57e975e73d1dd
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883791"
---
# <a name="iobjectwithsiteimpl-class"></a>Klasa IObjectWithSiteImpl
Ta klasa dostarcza metody, dzięki czemu obiekt, do komunikacji z jej lokacją.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IObjectWithSiteImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|Wysyła zapytanie do witryny dla wskaźnika interfejsu.|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Udostępnia obiekt w witrynie `IUnknown` wskaźnika.|  
|[IObjectWithSiteImpl::SetSite](#setsite)|Udostępnia obiekt w witrynie `IUnknown` wskaźnika.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Zarządza witryny `IUnknown` wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) interfejs umożliwia obiekt, do komunikacji z jej lokacją. Klasa `IObjectWithSiteImpl` udostępnia domyślną implementację tego interfejsu i implementuje `IUnknown` , wysyłając informacje o do zrzutu kompilacji urządzenia podczas debugowania.  
  
 `IObjectWithSiteImpl` Określa dwie metody. Pierwszy wywołań klienta `SetSite`, przekazując witryny `IUnknown` wskaźnika. This, wskaźnik jest przechowywany w obiekcie, a później mogą być pobierane za pomocą wywołania `GetSite`.  
  
 Zazwyczaj pochodzą z klasy `IObjectWithSiteImpl` podczas tworzenia obiektu, który nie jest formantem. W przypadku kontrolek pochodzi z klasy [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), zapewniającą wskaźnik lokacji. Pochodzi z klasy z obu `IObjectWithSiteImpl` i `IOleObjectImpl`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite  
 Zapytania witryny dla wskaźnika do interfejsu identyfikowane przez `riid`.  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli lokacja obsługuje ten interfejs, wskaźnik jest zwracany za pośrednictwem `ppvSite`. W przeciwnym razie `ppvSite` ma wartość NULL.  
  
 Zobacz [IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452) w Windows SDK.  
  
##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite  
 Zarządza witryny `IUnknown` wskaźnika.  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>Uwagi  
 `m_spUnkSite` początkowo otrzyma ten wskaźnik poprzez wywołanie [setsite —](#setsite).  
  
##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite  
 Udostępnia obiekt w witrynie `IUnknown` wskaźnika.  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkSite*  
 [in] Wskaźnik do `IUnknown` wskaźnika interfejsu lokacji zarządzania tego obiektu. Jeśli ma wartość NULL, obiekt powinien wywoływać `IUnknown::Release` witrynie istniejący w tym momencie obiektu nie jest już zna do niego lokacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite  
 Udostępnia obiekt w witrynie `IUnknown` wskaźnika.  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) w Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
