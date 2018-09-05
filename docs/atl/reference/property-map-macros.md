---
title: Makra mapy właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
dev_langs:
- C++
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf82c48cb5b1f9bd93a9c30afe8c698699c8199b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758095"
---
# <a name="property-map-macros"></a>Makra mapy właściwości

Te makra definiują właściwości mapy i wpisy.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Oznacza początek map właściwości ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Wskazuje zakres lub wymiarów kontrolki ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Wprowadza strony właściwości, właściwość DISPID oraz opis właściwości identyfikatora CLSID w map właściwości.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Wprowadza opisu właściwości, właściwość DISPID, CLSID — strona właściwości i `IDispatch` IID do mapy właściwości.|
|[PROP_PAGE](#prop_page)|Wprowadza CLSID strony właściwości w mapie właściwości.|
|[END_PROP_MAP](#end_prop_map)|Oznacza koniec map właściwości ATL.|  

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="begin_prop_map"></a>  BEGIN_PROP_MAP

Oznacza początek map właściwości obiektu.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*  
[in] Określa klasę zawierającą map właściwości.

### <a name="remarks"></a>Uwagi

Mapy właściwości przechowuje opisy właściwości, właściwość DISPID, CLSID, — strona właściwości i `IDispatch` IID. Klasy [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), i [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)używaj tej mapy właściwości, aby pobrać i ustawić te informacje.

Po utworzeniu obiektu za pomocą Kreatora projektu ATL, Kreator utworzy z pustą właściwością mapy, określając BEGIN_PROP_MAP następuje [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP nie zapisuje się zakres mapy właściwości (wymiarów), ponieważ obiekt przy użyciu map właściwości nie może mieć interfejs użytkownika, więc zakresu nie może mieć. Jeśli obiekt jest kontrolki ActiveX z interfejsem użytkownika, ma zakres. W takim przypadku należy określić [PROP_DATA_ENTRY](#prop_data_entry) na mapie właściwość umożliwiają określanie wartości w zakresie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>  PROP_DATA_ENTRY

Wskazuje zakres lub wymiarów kontrolki ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*  
[in] Opis właściwości.

*Element członkowski*  
[in] Element członkowski danych zawierająca w zakresie; na przykład `m_sizeExtent`.

*vt*  
[in] Określa typ WARIANTU właściwości.

### <a name="remarks"></a>Uwagi

To makro powoduje, że członek określone dane w celu jego utrwalenia.

Podczas tworzenia formantu ActiveX, kreator wstawia to makro po makra mapy właściwości [BEGIN_PROP_MAP](#begin_prop_map) i przed makra mapy właściwości [END_PROP_MAP](#end_prop_map).

### <a name="example"></a>Przykład

W poniższym przykładzie zakres obiektu (`m_sizeExtent`) jest jest trwały.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>  PROP_ENTRY_TYPE

Użyj tego makra do strony właściwości, właściwość DISPID oraz opis właściwości identyfikatora CLSID map właściwości obiektu.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*  
[in] Opis właściwości.

*identyfikator DISPID*  
[in] Identyfikator DISPID właściwości.

*Identyfikator klasy*  
[in] Identyfikator CLSID strony właściwości skojarzonej. Specjalna wartość CLSID_NULL na użytek właściwość, która nie ma skojarzonej właściwości strony.

*vt*  
[in] Typ właściwości.

### <a name="remarks"></a>Uwagi

Makra PROP_ENTRY jest niebezpieczne i przestarzałe. Zamieniono PROP_ENTRY_TYPE.

[BEGIN_PROP_MAP](#begin_prop_map) — makro oznacza początek map właściwości; [END_PROP_MAP](#end_prop_map) — makro oznacza koniec.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>  PROP_ENTRY_TYPE_EX

Podobnie jak [PROP_ENTRY_TYPE](#prop_entry_type), ale pozwala określić konkretnego identyfikatora IID, jeśli obiekt obsługuje wiele podwójnych interfejsów.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*  
[in] Opis właściwości.

*identyfikator DISPID*  
[in] Identyfikator DISPID właściwości.

*Identyfikator klasy*  
[in] Identyfikator CLSID strony właściwości skojarzonej. Specjalna wartość CLSID_NULL na użytek właściwość, która nie ma skojarzonej właściwości strony.

*iidDispatch*  
[in] Identyfikator IID podwójnego interfejsu Definiowanie właściwości.

*vt*  
[in] Typ właściwości.

### <a name="remarks"></a>Uwagi

Makra PROP_ENTRY_EX jest niebezpieczne i przestarzałe. Zamieniono PROP_ENTRY_TYPE_EX.

[BEGIN_PROP_MAP](#begin_prop_map) — makro oznacza początek map właściwości; [END_PROP_MAP](#end_prop_map) — makro oznacza koniec.

### <a name="example"></a>Przykład

Poniższy przykład grup wpisy dla `IMyDual1` następuje wpis dla `IMyDual2`. Grupowanie według podwójnego interfejsu poprawi wydajność.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>  PROP_PAGE

Użyj tego makra, aby wprowadzić identyfikator CLSID strony właściwości do map właściwości obiektu.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*  
[in] Identyfikator CLSID strony właściwości.

### <a name="remarks"></a>Uwagi

PROP_PAGE jest podobny do [PROP_ENTRY_TYPE](#prop_entry_type), ale nie jest wymagane, opisu właściwości lub identyfikator DISPID.

> [!NOTE]
>  Jeśli już wprowadzone CLSID z PROP_ENTRY_TYPE lub [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), nie musisz wprowadzić dodatkowe wpis z PROP_PAGE.

[BEGIN_PROP_MAP](#begin_prop_map) — makro oznacza początek map właściwości; [END_PROP_MAP](#end_prop_map) — makro oznacza koniec.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>  END_PROP_MAP

Oznacza koniec map właściwości obiektu.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu za pomocą Kreatora projektu ATL, Kreator utworzy pustą właściwością mapy, określając [BEGIN_PROP_MAP](#begin_prop_map) następuje END_PROP_MAP.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
