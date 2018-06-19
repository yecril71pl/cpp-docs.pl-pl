---
title: Klasa ISpecifyPropertyPagesImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs:
- C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74f10684c32cc5b1b4b07ac30406520c9ba41ddd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362235"
---
# <a name="ispecifypropertypagesimpl-class"></a>Klasa ISpecifyPropertyPagesImpl
Ta klasa implementuje **IUnknown** i udostępnia domyślną implementację elementu [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) interfejsu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `ISpecifyPropertyPagesImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Wstawia wartości zliczane tablicy UUID. Każdy identyfikator UUID odnosi się do identyfikatora CLSID dla jednej strony właściwości, które mogą być wyświetlane w arkuszu właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) interfejs umożliwia klientowi uzyskiwania listy CLSID strony właściwości obsługiwanych przez obiekt. Klasa `ISpecifyPropertyPagesImpl` udostępnia domyślną implementację tego interfejsu i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
> [!NOTE]
>  Nie ujawniaj **ISpecifyPropertyPages** interfejsu, jeśli obiekt nie obsługuje strony właściwości.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages  
 Wypełnia tablicy [CAUUID](http://msdn.microsoft.com/library/windows/desktop/ms680048) struktury z CLSID dla strony właściwości, które mogą być wyświetlane w arkuszu właściwości.  
  
```
STDMETHOD(GetPages)(CAUUID* pPages);
```  
  
### <a name="remarks"></a>Uwagi  
 ATL używa mapę właściwości obiektu można pobrać każdy identyfikator CLSID.  
  
 Zobacz [ISpecifyPropertyPages::GetPages](http://msdn.microsoft.com/library/windows/desktop/ms687276) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)   
 [Klasa IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
