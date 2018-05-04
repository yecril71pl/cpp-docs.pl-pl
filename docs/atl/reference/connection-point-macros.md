---
title: Makra punktu połączenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e50a868dd87628873b2a43f0ace55690b0583fd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="connection-point-macros"></a>Makra punktu połączenia
Te makra zdefiniuj mapy punktu połączenia i wpisy.  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Oznacza początek wpisów map punktu połączenia.|  
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Wprowadza punkty połączenia do mapy.|  
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Podobny do CONNECTION_POINT_ENTRY trwa ale wskaźnik do identyfikatora iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Oznacza koniec wpisów map punktu połączenia.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h 
   
##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP  
 Oznacza początek wpisów map punktu połączenia.  
  
```
BEGIN_CONNECTION_POINT_MAP(x)
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa klasy zawierającej punkty połączenia.  
  
### <a name="remarks"></a>Uwagi  
 Uruchom mapy punktu połączenia z `BEGIN_CONNECTION_POINT_MAP` makra, dodanie wpisów dla każdego z punktów połączenia [CONNECTION_POINT_ENTRY](#connection_point_entry) makra i ukończyć mapy [END_CONNECTION_POINT_MAP](#end_connection_point_map) makra.  
  
 Aby uzyskać więcej informacji na temat punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]  
  
##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY i CONNECTION_POINT_ENTRY_P  
 Wejścia punktu połączenia dla określonego interfejsu mapy punktu połączenia, dzięki czemu będą one dostępne.  
  
```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID interfejsu dodawany do mapy punktu połączenia. 
 
 `piid`  
 [in] Wskaźnik do identyfikatora GUID interfejsu jest adde.   
  
### <a name="remarks"></a>Uwagi  
 Wpisy punktu połączenia w mapie są używane przez [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Klasa zawierająca mapy punktu połączenia musi dziedziczyć z `IConnectionPointContainerImpl`.  
  
 Uruchom mapy punktu połączenia z [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) makra, dodanie wpisów dla każdego z punktów połączenia `CONNECTION_POINT_ENTRY` makra i ukończyć mapy [END_CONNECTION_POINT_MAP ](#end_connection_point_map) makra.  
  
 Aby uzyskać więcej informacji na temat punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]  
  
##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP  
 Oznacza koniec wpisów map punktu połączenia.  
  
```
END_CONNECTION_POINT_MAP()
```  
  
### <a name="remarks"></a>Uwagi  
 Uruchom mapy punktu połączenia z [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) makra, dodanie wpisów dla każdego z punktów połączenia [CONNECTION_POINT_ENTRY](#connection_point_entry) makra i ukończyć mapy `END_CONNECTION_POINT_MAP` makra.  
  
 Aby uzyskać więcej informacji na temat punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)   
 [Funkcje globalne punktu połączenia](../../atl/reference/connection-point-global-functions.md)
