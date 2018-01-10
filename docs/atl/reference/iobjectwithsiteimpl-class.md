---
title: Klasa IObjectWithSiteImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
dev_langs: C++
helpviewer_keywords: IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49574d31ef0c606528f29c0045506e5febe69b28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iobjectwithsiteimpl-class"></a>Klasa IObjectWithSiteImpl
Ta klasa dostarcza metody, dzięki czemu obiekt do komunikacji z jej lokacją.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IObjectWithSiteImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|Wysyła zapytanie do lokacji dla wskaźnika interfejsu.|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Udostępnia obiekt z witryny **IUnknown** wskaźnika.|  
|[IObjectWithSiteImpl::SetSite](#setsite)|Udostępnia obiekt z witryny **IUnknown** wskaźnika.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Zarządza witryny **IUnknown** wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) interfejs umożliwiający obiekt do komunikacji z jej lokacją. Klasa `IObjectWithSiteImpl` udostępnia domyślną implementację tego interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 `IObjectWithSiteImpl`Określa dwie metody. Pierwsze wywołania klienta `SetSite`, przekazywanie witryny **IUnknown** wskaźnika. Ten wskaźnik jest przechowywany wewnątrz obiektu, a później mogą zostać pobrane za pośrednictwem wywołania `GetSite`.  
  
 Zwykle, pochodzi z klasy `IObjectWithSiteImpl` podczas tworzenia obiektu, który nie jest formantem. Dla formantów, pochodzi z klasy [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), zapewniające wskaźnik lokacji. Nie pochodzi z klasy z obu `IObjectWithSiteImpl` i `IOleObjectImpl`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getsite"></a>IObjectWithSiteImpl::GetSite  
 Wysyła zapytanie do lokacji dla wskaźnika interfejsu identyfikowane przez `riid`.  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli lokacja obsługuje ten interfejs, za pośrednictwem zwracany jest wskaźnik `ppvSite`. W przeciwnym razie `ppvSite` ustawiono **NULL**.  
  
 Zobacz [IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452) w systemie Windows SDK.  
  
##  <a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite  
 Zarządza witryny **IUnknown** wskaźnika.  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>Uwagi  
 `m_spUnkSite`początkowo odbiera ten wskaźnik poprzez wywołanie [SetSite](#setsite).  
  
##  <a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite  
 Udostępnia obiekt z witryny **IUnknown** wskaźnika.  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkSite*  
 [in] Wskaźnik do **IUnknown** wskaźnika interfejsu witryny Zarządzanie tego obiektu. Jeśli wartość NULL, obiekt powinien wywoływać `IUnknown::Release` na istniejącą witrynę w takim przypadku obiekt zna już do niego lokacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
##  <a name="setsite"></a>IObjectWithSiteImpl::SetSite  
 Udostępnia obiekt z witryny **IUnknown** wskaźnika.  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
