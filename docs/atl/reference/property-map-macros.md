---
title: Makra mapy właściwości
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
ms.openlocfilehash: 1e2e7235dd924467d9d5e0613a704fedf8340ae4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857187"
---
# <a name="property-map-macros"></a>Makra mapy właściwości

Te makra definiują mapy właściwości i wpisy.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Oznacza początek mapy właściwości ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Wskazuje zakres lub wymiary kontrolki ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Wprowadza opis właściwości, DISPID właściwości i identyfikator CLSID strony właściwości do mapy właściwości.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Wprowadza opis właściwości, DISPID właściwości, identyfikator CLSID strony właściwości i `IDispatch` IID do mapy właściwości.|
|[PROP_PAGE](#prop_page)|Wprowadza identyfikator CLSID strony właściwości do mapy właściwości.|
|[END_PROP_MAP](#end_prop_map)|Oznacza koniec mapy właściwości ATL.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP

Oznacza początek mapy właściwości obiektu.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
podczas Określa klasę zawierającą mapę właściwości.

### <a name="remarks"></a>Uwagi

Mapa właściwości przechowuje opisy właściwości, identyfikatory SPID właściwości, identyfikatory CLSID strony właściwości i `IDispatch` IID. Klasy [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)i [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) używają mapy właściwości do pobierania i ustawiania tych informacji.

Podczas tworzenia obiektu za pomocą Kreatora projektu ATL Kreator utworzy pustą mapę właściwości, określając BEGIN_PROP_MAP, a następnie [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP nie zapisuje tego zakresu (czyli wymiarów) mapy właściwości, ponieważ obiekt używający mapy właściwości może nie mieć interfejsu użytkownika, dlatego nie będzie miał żadnego zakresu. Jeśli obiekt jest kontrolką ActiveX z interfejsem użytkownika, ma zakres. W takim przypadku należy określić [PROP_DATA_ENTRY](#prop_data_entry) w mapie właściwości, aby podać zakres.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY

Wskazuje zakres lub wymiary kontrolki ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
podczas Opis właściwości.

*członkiem*<br/>
podczas Element członkowski danych zawierający zakres; na przykład `m_sizeExtent`.

*VT*<br/>
podczas Określa typ WARIANTu właściwości.

### <a name="remarks"></a>Uwagi

To makro powoduje utrwalenie określonego elementu członkowskiego danych.

Po utworzeniu kontrolki ActiveX Kreator wstawi to makro po [BEGIN_PROP_MAP](#begin_prop_map) makro mapy właściwości i przed [END_PROP_MAP](#end_prop_map)makro mapy właściwości.

### <a name="example"></a>Przykład

W poniższym przykładzie zakres obiektu (`m_sizeExtent`) jest utrwalany.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE

To makro służy do wprowadzania opisu właściwości, DISPID właściwości i identyfikatora CLSID strony właściwości do mapy właściwości obiektu.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
podczas Opis właściwości.

*DISPID*<br/>
podczas Identyfikator DISPID właściwości.

*Identyfikator*<br/>
podczas Identyfikator CLSID skojarzonej strony właściwości. Użyj specjalnej wartości CLSID_NULL dla właściwości, która nie ma skojarzonej strony właściwości.

*VT*<br/>
podczas Typ właściwości.

### <a name="remarks"></a>Uwagi

Makro PROP_ENTRY było niebezpieczne i przestarzałe. Został on zastąpiony PROP_ENTRY_TYPE.

Makro [BEGIN_PROP_MAP](#begin_prop_map) oznacza początek mapy właściwości; makro [END_PROP_MAP](#end_prop_map) oznacza koniec.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Podobnie jak w przypadku [PROP_ENTRY_TYPE](#prop_entry_type), ale umożliwia określenie określonego identyfikatora IID, jeśli obiekt obsługuje wiele podwójnych interfejsów.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
podczas Opis właściwości.

*DISPID*<br/>
podczas Identyfikator DISPID właściwości.

*Identyfikator*<br/>
podczas Identyfikator CLSID skojarzonej strony właściwości. Użyj specjalnej wartości CLSID_NULL dla właściwości, która nie ma skojarzonej strony właściwości.

*iidDispatch*<br/>
podczas Identyfikator IID podwójnego interfejsu definiującego właściwość.

*VT*<br/>
podczas Typ właściwości.

### <a name="remarks"></a>Uwagi

Makro PROP_ENTRY_EX było niebezpieczne i przestarzałe. Został on zastąpiony PROP_ENTRY_TYPE_EX.

Makro [BEGIN_PROP_MAP](#begin_prop_map) oznacza początek mapy właściwości; makro [END_PROP_MAP](#end_prop_map) oznacza koniec.

### <a name="example"></a>Przykład

W poniższych przykładowych grupach wpisów dla `IMyDual1` następuje wpis `IMyDual2`. Grupowanie według podwójnego interfejsu poprawi wydajność.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>PROP_PAGE

To makro służy do wprowadzania identyfikatora CLSID strony właściwości do mapy właściwości obiektu.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
podczas Identyfikator CLSID strony właściwości.

### <a name="remarks"></a>Uwagi

PROP_PAGE jest podobna do [PROP_ENTRY_TYPE](#prop_entry_type), ale nie wymaga opisu właściwości ani identyfikatora DISPID.

> [!NOTE]
>  Jeśli wprowadzono już identyfikator CLSID z PROP_ENTRY_TYPE lub [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), nie musisz wprowadzać dodatkowych wpisów w PROP_PAGE.

Makro [BEGIN_PROP_MAP](#begin_prop_map) oznacza początek mapy właściwości; makro [END_PROP_MAP](#end_prop_map) oznacza koniec.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>END_PROP_MAP

Oznacza koniec mapy właściwości obiektu.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu za pomocą Kreatora projektu ATL Kreator utworzy pustą mapę właściwości, określając [BEGIN_PROP_MAP](#begin_prop_map) , a następnie END_PROP_MAP.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Zobacz także

[Utworze](../../atl/reference/atl-macros.md)
