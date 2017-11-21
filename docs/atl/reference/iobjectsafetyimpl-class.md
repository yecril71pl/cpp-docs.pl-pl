---
title: Klasa IObjectSafetyImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
dev_langs: C++
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3b1c0369acceb792af26b7e9c8e8fd49f82a4468
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="iobjectsafetyimpl-class"></a>Klasa IObjectSafetyImpl
Ta klasa udostępnia domyślną implementację `IObjectSafety` interfejs umożliwia klienta pobrać i ustawić poziom bezpieczeństwa obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T,DWORD dwSupportedSafety>  
class IObjectSafetyImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IObjectSafetyImpl`.  
  
 *dwSupportedSafety*  
 Określa opcje bezpieczeństwa obsługiwanych dla formantu. Może to być jedna z następujących wartości:  
  
- **INTERFACESAFE_FOR_UNTRUSTED_CALLER** interfejsu identyfikowane przez [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) parametru `riid` powinni należeć do obsługi skryptów.  
  
- **INTERFACESAFE_FOR_UNTRUSTED_DATA** interfejsu identyfikowane przez `SetInterfaceSafetyOptions` parametru `riid` należy bezpieczne dla niezaufanych danych podczas inicjowania.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Pobiera opcje bezpieczeństwa obsługiwane przez obiekt, a także opcje bezpieczeństwa aktualnie ustawione dla obiekt.|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Sprawia, że obiekt bezpieczne inicjowanie lub skryptów.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Zapisuje bieżący poziom bezpieczeństwa obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa `IObjectSafetyImpl` udostępnia domyślną implementację elementu `IObjectSafety`. `IObjectSafety` Interfejsu temu klient może pobierać i ustawiać poziom bezpieczeństwa obiektu. Na przykład przeglądarki sieci web można wywołać **IObjectSafety::SetInterfaceSafetyOptions** aby formant bezpieczne inicjowanie lub bezpieczne dla wykonywania skryptów.  
  
 Należy pamiętać, że przy użyciu [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) makra o **CATID_SafeForScripting** i **CATID_SafeForInitializing** kategorii składników stanowi alternatywę sposób określania, czy składnik jest bezpieczne.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions  
 Pobiera opcje bezpieczeństwa obsługiwane przez obiekt, a także opcje bezpieczeństwa aktualnie ustawione dla obiekt.  
  
```
HRESULT GetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```  
  
### <a name="remarks"></a>Uwagi  
 Implementacja zwraca odpowiednie wartości dla dowolnego interfejsu obsługiwana przez implementację obiektu **IUnknown::QueryInterface**.  
  
> [!IMPORTANT]
>  Każdy obiekt, który obsługuje `IObjectSafety` jest odpowiedzialny za własną zabezpieczeń i z dowolnych obiektów deleguje ona. Programistę musi uwzględniać problemy z kontem wynikających z uruchamianie kodu w kontekście użytkownika, krzyżowych skryptów i sprawdzania odpowiednie strefy.  
  
 Zobacz [IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx) w systemie Windows SDK.  
  
##  <a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety  
 Zapisuje bieżący poziom bezpieczeństwa obiektu.  
  
```
DWORD m_dwCurrentSafety;
```  
  
##  <a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions  
 Sprawia, że obiekt jest bezpieczne inicjowanie lub skryptów przez ustawienie [m_dwCurrentSafety](#m_dwcurrentsafety) elementu członkowskiego na odpowiednią wartość.  
  
```
HRESULT SetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```  
  
### <a name="remarks"></a>Uwagi  
 Implementacja zwraca **E_NOINTERFACE** dla dowolnego interfejsu nie jest obsługiwana przez implementację obiektu **IUnknown::QueryInterface**.  
  
> [!IMPORTANT]
>  Każdy obiekt, który obsługuje `IObjectSafety` jest odpowiedzialny za własną zabezpieczeń i z dowolnych obiektów deleguje ona. Programistę musi uwzględniać problemy z kontem wynikających z uruchamianie kodu w kontekście użytkownika, krzyżowych skryptów i sprawdzania odpowiednie strefy.  
  
 Zobacz [IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IObjectSafety](https://msdn.microsoft.com/library/aa768224.aspx)   
 [Przegląd klas](../../atl/atl-class-overview.md)
