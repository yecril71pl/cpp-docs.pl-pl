---
title: Klasa CAtlWinModule | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcaf3d6573432b7f6f16826b2551a7e9330abed9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="catlwinmodule-class"></a>Klasa CAtlWinModule
Ta klasa obsługuje składniki okien ALT.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlWinModule : public _ATL_WIN_MODULE
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Konstruktor.|  
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Dodaje obiekt danych.|  
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Zwraca wskaźnik do obiektu danych modułu okna.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa obsługuje wszystkie klasy ATL, które wymagają funkcji okien.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)  
  
 `CAtlWinModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData  
 Ta metoda inicjuje i dodaje `_AtlCreateWndData` struktury.  
  
```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 Wskaźnik do `_AtlCreateWndData` struktury inicjowanie i dodany do bieżącego modułu.  
  
 `pObject`  
 Wskaźnik do obiektu **to** wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) które inicjuje [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury. Ta struktura będzie przechowywać **to** wskaźnika, używany do uzyskania wystąpienia klasy w procedury okna.  
  
##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule  
 Konstruktor.  
  
```
CAtlWinModule();
```  
  
### <a name="remarks"></a>Uwagi  
 W przypadku niepowodzenia inicjowania **EXCEPTION_NONCONTINUABLE** zgłoszony wyjątek.  
  
##  <a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule  
 Destruktor.  
  
```
~CAtlWinModule();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData  
 Ta metoda zwraca wskaźnik do `_AtlCreateWndData` struktury.  
  
```
void* ExtractCreateWndData();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do `_AtlCreateWndData` struktury uprzednio dodanych z [CAtlWinModule::AddCreateWndData](#addcreatewnddata), lub wartość NULL, jeśli obiekt nie jest dostępny.  
  
## <a name="see-also"></a>Zobacz też  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)
