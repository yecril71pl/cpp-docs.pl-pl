---
title: "Makra mapy właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
dev_langs: C++
helpviewer_keywords: property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9e6ed73ffbf5823cde4b45e03d20742a63d9ae95
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="property-map-macros"></a>Makra mapy właściwości
Te makra określić map właściwości i wpisy.  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|Oznacza początek mapę właściwości ATL.|  
|[PROP_DATA_ENTRY](#prop_data_entry)|Wskazuje zakres lub wymiarów formantu ActiveX.|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|Wprowadza strony właściwości, właściwość DISPID oraz opis właściwości CLSID do mapy właściwości.|  
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Wprowadza opisu właściwości, właściwość DISPID, strona właściwości identyfikatora CLSID, i `IDispatch` identyfikator IID do mapy właściwości.|  
|[PROP_PAGE](#prop_page)|Wprowadza identyfikator CLSID strony właściwości do mapy właściwości.|  
|[END_PROP_MAP](#end_prop_map)|Oznacza koniec mapę właściwości ATL.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
   
##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP  
 Oznacza początek mapę właściwości obiektu.  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 [in] Określa klasę zawierającą mapę właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Mapy właściwości przechowuje opisów właściwości, identyfikatory DISPID właściwości, strona właściwości CLSID, i `IDispatch` IID. Klasy [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), i [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)użyć mapy właściwości, aby pobrać i ustawić te informacje.  
  
 Podczas tworzenia obiektu przy użyciu kreatora Projekt ATL, który Kreator ma utworzyć mapy właściwości empty, określając `BEGIN_PROP_MAP` następuje [END_PROP_MAP](#end_prop_map).  
  
 `BEGIN_PROP_MAP`nie są zapisywane limit zakresu (wymiarów) mapę właściwości, ponieważ obiekt przy użyciu mapy właściwości nie ma interfejsu użytkownika, więc zakresu nie może mieć. Jeśli obiekt jest kontrolki ActiveX z interfejsem użytkownika, ma zakres. W takim przypadku należy określić [PROP_DATA_ENTRY](#prop_data_entry) na mapie właściwości umożliwiają określanie wartości w zakresie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY  
 Wskazuje zakres lub wymiarów formantu ActiveX.  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>Parametry  
 `szDesc`  
 [in] Opis właściwości.  
  
 `member`  
 [in] Element członkowski danych zawierającego zakres; na przykład `m_sizeExtent`.  
  
 *VT*  
 [in] Określa typ WARIANTU właściwości.  
  
### <a name="remarks"></a>Uwagi  
 To makro powoduje, że element członkowski danych określonego utrwalenia.  
  
 Podczas tworzenia formantu ActiveX, kreator wstawia to makro po makra mapy właściwości [BEGIN_PROP_MAP](#begin_prop_map) i przed makra mapy właściwości [END_PROP_MAP](#end_prop_map).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zakres obiektu ( `m_sizeExtent`) jest są zachowywane.  
  
 [!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE  
 Umożliwia to makro wejścia strony właściwości, właściwość DISPID oraz opis właściwości identyfikatora CLSID obiektu właściwości mapy.  
  
```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```  
  
### <a name="parameters"></a>Parametry  
 `szDesc`  
 [in] Opis właściwości.  
  
 `dispid`  
 [in] Identyfikator DISPID właściwości.  
  
 `clsid`  
 [in] Identyfikator CLSID strony skojarzonej właściwości. Użyj wartości specjalne `CLSID_NULL` dla właściwości, która nie ma skojarzonej właściwości strony.  
  
 `vt`  
 [in] Typ właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `PROP_ENTRY` Makro jest niebezpieczne i przestarzałe. Zostało zastąpione przez `PROP_ENTRY_TYPE`.  
  
 [BEGIN_PROP_MAP](#begin_prop_map) makro oznacza początek mapę właściwości; [END_PROP_MAP](#end_prop_map) makro oznacza zakończenie.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_PROP_MAP](#begin_prop_map).  
  
##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX  
 Podobnie jak [PROP_ENTRY_TYPE](#prop_entry_type), ale można określić konkretnego identyfikatora IID, jeśli obiekt obsługuje wiele podwójne interfejsy.  
  
```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```    
  
### <a name="parameters"></a>Parametry  
 `szDesc`  
 [in] Opis właściwości.  
  
 `dispid`  
 [in] Identyfikator DISPID właściwości.  
  
 `clsid`  
 [in] Identyfikator CLSID strony skojarzonej właściwości. Użyj wartości specjalne `CLSID_NULL` dla właściwości, która nie ma skojarzonej właściwości strony.  
  
 `iidDispatch`  
 [in] Uzyskanie identyfikatora IID interfejsu podwójną Definiowanie właściwości.  
  
 `vt`  
 [in] Typ właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `PROP_ENTRY_EX` Makro jest niebezpieczne i przestarzałe. Zostało zastąpione przez `PROP_ENTRY_TYPE_EX`.  
  
 [BEGIN_PROP_MAP](#begin_prop_map) makro oznacza początek mapę właściwości; [END_PROP_MAP](#end_prop_map) makro oznacza zakończenie.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład grupy wpisy dla `IMyDual1` następuje wpis dotyczący `IMyDual2`. Grupowanie za pośrednictwem interfejsu podwójną umożliwi zwiększenie wydajności.  
  
 [!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="prop_page"></a>PROP_PAGE  
 Umożliwia to makro wprowadź identyfikator CLSID strony właściwości do mapy właściwości obiektu.  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [in] Identyfikator CLSID strony właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `PROP_PAGE`przypomina [PROP_ENTRY_TYPE](#prop_entry_type), ale nie wymaga opisu właściwości lub identyfikator DISPID.  
  
> [!NOTE]
>  Jeśli zostały już wprowadzone formantu o identyfikatorze CLSID `PROP_ENTRY_TYPE` lub [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), nie należy wprowadzać dodatkowych z `PROP_PAGE`.  
  
 [BEGIN_PROP_MAP](#begin_prop_map) makro oznacza początek mapę właściwości; [END_PROP_MAP](#end_prop_map) makro oznacza zakończenie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="end_prop_map"></a>END_PROP_MAP  
 Oznacza koniec mapę właściwości obiektu.  
  
```
END_PROP_MAP()
```  
  
### <a name="remarks"></a>Uwagi  
 Podczas tworzenia obiektu przy użyciu kreatora Projekt ATL, który Kreator ma utworzyć mapy właściwości empty, określając [BEGIN_PROP_MAP](#begin_prop_map) następuje `END_PROP_MAP`.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_PROP_MAP](#begin_prop_map).  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
