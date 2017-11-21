---
title: Klasa CAtlComModule | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs: C++
helpviewer_keywords: CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8a0d0e240e1c830763b5b7781fb3a1e536d4672
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catlcommodule-class"></a>Klasa CAtlComModule
Ta klasa implementuje moduł serwera COM.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlComModule : public _ATL_COM_MODULE
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](#catlcommodule)|Konstruktor.|  
|[CAtlComModule:: ~ CAtlComModule](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](#registerserver)|Wywołaj tę metodę, aby zaktualizować rejestru systemowego dla każdego obiektu w mapie obiektu.|  
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Wywołanie tej metody można zarejestrować biblioteki typów.|  
|[CAtlComModule::UnregisterServer](#unregisterserver)|Wywołaj tę metodę, aby wyrejestrować każdego obiektu w mapie obiektu.|  
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Wywołanie tej metody można wyrejestrować biblioteki typów.|  
  
## <a name="remarks"></a>Uwagi  
 `CAtlComModule`implementuje moduł serwera COM, umożliwiając klientowi dostęp do składników modułu.  
  
 Ta klasa zastępuje przestarzałe [ccommodule —](../../atl/reference/ccommodule-class.md) klasy używany w starszych wersjach ATL. Zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)  
  
 `CAtlComModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="catlcommodule"></a>CAtlComModule::CAtlComModule  
 Konstruktor.  
  
```
CAtlComModule() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje modułu.  
  
##  <a name="dtor"></a>CAtlComModule:: ~ CAtlComModule  
 Destruktor.  
  
```
~CAtlComModule();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie fabryki klas.  
  
##  <a name="registerserver"></a>CAtlComModule::RegisterServer  
 Wywołaj tę metodę, aby zaktualizować rejestru systemowego dla każdego obiektu w mapie obiektu.  
  
```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany. Wartość domyślna to FALSE.  
  
 `pCLSID`  
 Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. Jeśli wartość NULL (wartość domyślna) wszystkie obiekty w mapie obiektu zostanie zarejestrowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji globalnej [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).  
  
##  <a name="registertypelib"></a>CAtlComModule::RegisterTypeLib  
 Wywołanie tej metody można zarejestrować biblioteki typów.  
  
```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszIndex`  
 Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeksu zasobu biblioteki typów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Dodaje informacje o biblioteki typów w rejestrze systemu. Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj pierwszą wersję tej metody, aby określić, biblioteki typów, które powinny być używane.  
  
##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer  
 Wywołaj tę metodę, aby wyrejestrować każdego obiektu w mapie obiektu.  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 Wartość TRUE, jeśli można wyrejestrować biblioteki typów. Wartość domyślna to FALSE.  
  
 `pCLSID`  
 Wskazuje identyfikator CLSID obiektu do wyrejestrowania. Jeśli wartość NULL (wartość domyślna) wszystkie obiekty w mapie obiektu zostanie wyrejestrowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji globalnej [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).  
  
##  <a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib  
 Wywołanie tej metody można wyrejestrować biblioteki typów.  
  
```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszIndex`  
 Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeksu zasobu biblioteki typów.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa informacje o bibliotece typów z rejestru systemowego. Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj pierwszą wersję tej metody, aby określić, biblioteki typów, które powinny być używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
## <a name="see-also"></a>Zobacz też  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [Przegląd klas](../../atl/atl-class-overview.md)
