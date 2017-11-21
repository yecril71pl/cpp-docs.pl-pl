---
title: Klasa CAtlModuleT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
dev_langs: C++
helpviewer_keywords: CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e336b7c9ed868e4aa1538c6673371b33123a4072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catlmodulet-class"></a>Klasa CAtlModuleT
Ta klasa implementuje moduł ATL.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy pochodne `CAtlModuleT`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlModuleT::InitLibId](#initlibid)|Inicjuje element danych zawierający identyfikator GUID bieżącego modułu.|  
|[CAtlModuleT::RegisterAppId](#registerappid)|Dodaje plik EXE w rejestrze.|  
|[CAtlModuleT::RegisterServer](#registerserver)|Dodaje usługę do rejestru.|  
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Usuwa plik EXE z rejestru.|  
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Usługa usuwa z rejestru.|  
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualizuje informacje o pliku EXE w rejestrze.|  
  
## <a name="remarks"></a>Uwagi  
 `CAtlModuleT`, pochodną [CAtlModule](../../atl/reference/catlmodule-class.md), implementuje modułu ATL usługi (EXE) lub pliku wykonywalnego (EXE). Wykonywalny modułu jest serwerem lokalnym, poza procesem, moduł usługi jest aplikacji systemu Windows, która działa w tle podczas uruchamiania systemu Windows.  
  
 `CAtlModuleT`zapewnia obsługę inicjowanie, rejestrowanie i wyrejestrowywanie modułu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT  
 Konstruktor.  
  
```
CAtlModuleT() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CAtlModuleT::InitLibId](#initlibid).  
  
##  <a name="initlibid"></a>CAtlModuleT::InitLibId  
 Inicjuje element danych zawierający identyfikator GUID bieżącego modułu.  
  
```
static void InitLibId() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywoływane przez konstruktora [CAtlModuleT::CAtlModuleT](#catlmodulet).  
  
##  <a name="registerappid"></a>CAtlModuleT::RegisterAppId  
 Dodaje plik EXE w rejestrze.  
  
```
HRESULT RegisterAppId() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="registerserver"></a>CAtlModuleT::RegisterServer  
 Dodaje usługę do rejestru.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany. Wartość domyślna to FALSE.  
  
 `pCLSID`  
 Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. Jeśli wartość NULL (wartość domyślna) wszystkie obiekty w mapie obiektu zostanie zarejestrowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId  
 Usuwa plik EXE z rejestru.  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="unregisterserver"></a>CAtlModuleT::UnregisterServer  
 Usługa usuwa z rejestru.  
  
```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bUnRegTypeLib`  
 Wartość TRUE, jeśli biblioteka typów jest również zostać wyrejestrowana.  
  
 `pCLSID`  
 Wskazuje identyfikator CLSID obiektu do wyrejestrowania. Jeśli wartość NULL (wartość domyślna) wszystkie obiekty w mapie obiektu zostanie wyrejestrowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId  
 Aktualizuje informacje o pliku EXE w rejestrze.  
  
```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bRegister`  
 Zastrzeżone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlModule](../../atl/reference/catlmodule-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)
