---
title: Przystawka obiekt makra | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
dev_langs: C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b70a8e3d644389bcfb21b276c5a3bcfad84891a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="snap-in-object-macros"></a>Przystawka obiekt makra
Makra te zapewniają obsługę rozszerzeń przystawek.  
  
|||  
|-|-|  
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Oznacza początek mapowania klasy przystawkę rozszerzenia danych dla obiekt przystawki.|  
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Oznacza początek mapy paska narzędzi dla obiekt przystawki.|  
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Oznacza koniec mapowania klasy przystawkę rozszerzenia danych dla obiekt przystawki.|  
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Oznacza koniec mapy paska narzędzi dla obiekt przystawki.|  
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Tworzy element członkowski danych klasy danych rozszerzenia przystawki.|  
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Wprowadza klasy danych przystawkę rozszerzenia do rozszerzenia przystawki mapowania klasy danych obiektu przystawki.|  
|[SNAPINMENUID](#snapinmenuid)|Deklaruje identyfikator menu kontekstowe używane przez obiekt przystawki.|  
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Wejścia paska narzędzi w planie narzędzi obiektu przystawki.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsnap.h 
   
##  <a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP  
 Oznacza początek rozszerzenia przystawki mapowania klasy danych.  
  
```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```  
  
### <a name="parameters"></a>Parametry  
 *ClassName*  
 [in] Nazwa klasy danych rozszerzenia przystawki.  
  
### <a name="remarks"></a>Uwagi  
 Uruchom przystawkę rozszerzenia mapę z `BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP` makra, dodanie wpisów dla każdego z typów danych rozszerzenia przystawki [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makra i ukończyć mapy [END_ EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP  
 Deklaruje początku mapy identyfikator narzędzi dla obiekt przystawki.  
  
```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```  
  
### <a name="parameters"></a>Parametry  
 `_class`  
 [in] Określa klasę obiektu przystawki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]  
  
##  <a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP  
 Oznacza koniec rozszerzenia przystawki mapowania klasy danych.  
  
```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```  
  
### <a name="remarks"></a>Uwagi  
 Uruchom przystawkę rozszerzenia mapę z [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makra, dodanie wpisów dla poszczególnych typów danych w przystawce rozszerzenia z [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makra i ukończyć mapy `END_EXTENSION_SNAPIN_NODEINFO_MAP` makra.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).  
  
##  <a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP  
 Deklaruje koniec mapy identyfikator narzędzi dla obiekt przystawki.  
  
```
END_SNAPINTOOLBARID_MAP( _class )
```  
  
### <a name="parameters"></a>Parametry  
 `_class`  
 [in] Określa klasę obiektu przystawki.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).  
  
##  <a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS  
 Dodaje element członkowski danych klasy przystawkę rozszerzenia danych dla **ISnapInItemImpl**-klasy.  
  
```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```  
  
### <a name="parameters"></a>Parametry  
 `dataClass`  
 [in] Klasa danych rozszerzenia przystawki.  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa stosuje się do klasy mapowanie danych rozszerzenia przystawki. Uruchom mapy klasa rozszerzenia przystawki danych z [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makra, dodanie wpisów dla każdego z typów danych rozszerzenia przystawki [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)makra i ukończyć mapy [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY  
 Dodaje klasę danych przystawkę rozszerzenia do rozszerzenia przystawki mapowania klasy danych.  
  
```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```  
  
### <a name="parameters"></a>Parametry  
 `dataClass`  
 [in] Klasa danych rozszerzenia przystawki.  
  
### <a name="remarks"></a>Uwagi  
 Uruchom mapy klasa rozszerzenia przystawki danych z [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makra, dodanie wpisów dla każdego z typów danych rozszerzenia przystawki `EXTENSION_SNAPIN_NODEINFO_ENTRY` makra i ukończyć mapy [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).  
  
##  <a name="snapinmenuid"></a>SNAPINMENUID  
 Umożliwia to makro zadeklarować zasobów menu kontekstowe obiektu przystawki.  
  
```
SNAPINMENUID( id )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikuje menu kontekstowe obiektu przystawki.  
  
##  <a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY  
 Umożliwia to makro wprowadź identyfikator narzędzi do przystawki obiektu narzędzi identyfikator mapy.  
  
```
SNAPINTOOLBARID_ENTRY( id )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikuje formant paska narzędzi.  
  
### <a name="remarks"></a>Uwagi  
 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) makro oznacza początek mapy identyfikator narzędzi; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) makro oznacza zakończenie.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
