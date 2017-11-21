---
title: Makra wymiany danych rejestru | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
dev_langs: C++
helpviewer_keywords: RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f0864a46faf7fa083a2272cd56c72c8e4210ec5e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="registry-data-exchange-macros"></a>Makra wymiany danych rejestru
Te makra operacji wymiana danych z rejestru.  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|Oznacza początek mapy wymiany danych rejestru.|  
|[END_RDX_MAP](#end_rdx_map)|Oznacza koniec mapy wymiany danych rejestru.|  
|[RDX_BINARY](#rdx_binary)|Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu BYTE.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu obiektu CString.|  
|[RDX_DWORD](#rdx_dword)|Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu DWORD.|  
|[RDX_TEXT](#rdx_text)|Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu tchar —.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlplus.h  
   
##  <a name="begin_rdx_map"></a>BEGIN_RDX_MAP  
 Oznacza początek mapy wymiany danych rejestru.  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>Uwagi  
 Następujące makra są używane w mapie wymiany danych rejestru do odczytu i zapisu wpisy w rejestrze systemu:  
  
|Makra|Opis|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu BYTE.|  
|[RDX_DWORD](#rdx_dword)|Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu DWORD.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu obiektu CString.|  
|[RDX_TEXT](#rdx_text)|Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu tchar —.|  
  
 Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcja członkowska o takiej samej nazwie utworzone przez `BEGIN_RDX_MAP` i `END_RDX_MAP` makra, powinna być używana zawsze, gdy kod musi wymiany danych między rejestru systemowego i określone w planie RDX zmienne.  
  
##  <a name="end_rdx_map"></a>END_RDX_MAP  
 Oznacza koniec mapy wymiany danych rejestru.  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>RDX_BINARY  
 Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu BYTE.  
  
```
RDX_BINARY(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 `rootkey`  
 Głównego klucza rejestru.  
  
 `subkey`  
 Podklucz rejestru.  
  
 `valuename`  
 Klucz rejestru.  
  
 `member`  
 Zmiennej członkowskiej do skojarzenia z określony wpis rejestru.  
  
 `member_size`  
 Rozmiar w bajtach zmiennej członka.  
  
### <a name="remarks"></a>Uwagi  
 To makro jest używane w połączeniu z `BEGIN_RDX_MAP` i `END_RDX_MAP` makra do skojarzenia z wpisu rejestru danego zmiennej członkowskiej. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcja członkowska o takiej samej nazwie utworzone przez `BEGIN_RDX_MAP` i `END_RDX_MAP` makra, powinny być używane do wykonywania wymiany danych między rejestru systemowego i element członkowski zmienne w mapie RDX.  
  
##  <a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT  
 Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu obiektu CString.  
  
```
RDX_CSTRING_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 `rootkey`  
 Głównego klucza rejestru.  
  
 `subkey`  
 Podklucz rejestru.  
  
 `valuename`  
 Klucz rejestru.  
  
 `member`  
 Zmiennej członkowskiej do skojarzenia z określony wpis rejestru.  
  
 `member_size`  
 Rozmiar w bajtach zmiennej członka.  
  
### <a name="remarks"></a>Uwagi  
 To makro jest używane w połączeniu z `BEGIN_RDX_MAP` i `END_RDX_MAP` makra do skojarzenia z wpisu rejestru danego zmiennej członkowskiej. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcja członkowska o takiej samej nazwie utworzone przez `BEGIN_RDX_MAP` i `END_RDX_MAP` makra, powinny być używane do wykonywania wymiany danych między rejestru systemowego i element członkowski zmienne w mapie RDX.  
  
##  <a name="rdx_dword"></a>RDX_DWORD  
 Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu DWORD.  
  
```
RDX_DWORD(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 `rootkey`  
 Głównego klucza rejestru.  
  
 `subkey`  
 Podklucz rejestru.  
  
 `valuename`  
 Klucz rejestru.  
  
 `member`  
 Zmiennej członkowskiej do skojarzenia z określony wpis rejestru.  
  
 `member_size`  
 Rozmiar w bajtach zmiennej członka.  
  
### <a name="remarks"></a>Uwagi  
 To makro jest używane w połączeniu z `BEGIN_RDX_MAP` i `END_RDX_MAP` makra do skojarzenia z wpisu rejestru danego zmiennej członkowskiej. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcja członkowska o takiej samej nazwie utworzone przez `BEGIN_RDX_MAP` i `END_RDX_MAP` makra, powinny być używane do wykonywania wymiany danych między rejestru systemowego i element członkowski zmienne w mapie RDX.  
  
##  <a name="rdx_text"></a>RDX_TEXT  
 Kojarzy określony wpis rejestru z określonego elementu członkowskiego zmiennej typu tchar —.  
  
```
RDX_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parametry  
 `rootkey`  
 Głównego klucza rejestru.  
  
 `subkey`  
 Podklucz rejestru.  
  
 `valuename`  
 Klucz rejestru.  
  
 `member`  
 Zmiennej członkowskiej do skojarzenia z określony wpis rejestru.  
  
 `member_size`  
 Rozmiar w bajtach zmiennej członka.  
  
### <a name="remarks"></a>Uwagi  
 To makro jest używane w połączeniu z `BEGIN_RDX_MAP` i `END_RDX_MAP` makra do skojarzenia z wpisu rejestru danego zmiennej członkowskiej. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcja członkowska o takiej samej nazwie utworzone przez `BEGIN_RDX_MAP` i `END_RDX_MAP` makra, powinny być używane do wykonywania wymiany danych między rejestru systemowego i element członkowski zmienne w mapie RDX.  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)







