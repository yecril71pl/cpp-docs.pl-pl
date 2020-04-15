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
ms.openlocfilehash: 56fdb02939a99e396b9000705753e2475b80f6dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326090"
---
# <a name="property-map-macros"></a>Makra mapy właściwości

Te makra definiują mapy właściwości i wpisy.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Oznacza początek mapy właściwości ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Wskazuje zakres lub wymiary formantu ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Wprowadza opis właściwości, dispid właściwości i strony właściwości CLSID do mapy właściwości.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Wprowadza opis właściwości, właściwość DISPID, strona właściwości `IDispatch` CLSID i identyfikator IID do mapy właściwości.|
|[PROP_PAGE](#prop_page)|Wprowadza stronę właściwości CLSID do mapy właściwości.|
|[END_PROP_MAP](#end_prop_map)|Oznacza koniec mapy właściwości ATL.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP

Oznacza początek mapy właściwości obiektu.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
[w] Określa klasę zawierającą mapę właściwości.

### <a name="remarks"></a>Uwagi

Mapa właściwości przechowuje opisy właściwości, identyfikatory DISPI, identyfikatory `IDispatch` CLSID strony właściwości i identyfikatory IDENTYFIKATORÓW. Klasy [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)i [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) używają mapy właściwości do pobierania i ustawiania tych informacji.

Podczas tworzenia obiektu za pomocą Kreatora projektu ATL kreator utworzy pustą mapę właściwości, określając BEGIN_PROP_MAP a następnie [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP nie zapisuje zakresu (czyli wymiarów) mapy właściwości, ponieważ obiekt używający mapy właściwości może nie mieć interfejsu użytkownika, więc nie miałby żadnego zasięgu. Jeśli obiekt jest formantem ActiveX z interfejsem użytkownika, ma on zasięg. W takim przypadku należy określić [PROP_DATA_ENTRY](#prop_data_entry) na mapie właściwości, aby zapewnić zakres.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY

Wskazuje zakres lub wymiary formantu ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parametry

*szDesc (szDesc)*<br/>
[w] Opis właściwości.

*Członkowskich*<br/>
[w] Element członkowski danych zawierający zakres; na przykład `m_sizeExtent`.

*Vt*<br/>
[w] Określa typ VARIANT właściwości.

### <a name="remarks"></a>Uwagi

To makro powoduje, że określony element członkowski danych ma być utrwalony.

Podczas tworzenia formantu ActiveX kreator wstawia to makro po [BEGIN_PROP_MAP](#begin_prop_map) makra mapy właściwości i przed [END_PROP_MAP](#end_prop_map)makra mapy właściwości .

### <a name="example"></a>Przykład

W poniższym przykładzie zakres obiektu`m_sizeExtent`( ) jest zachowywany.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE

To makro służy do wprowadzania opisu właściwości, dispid właściwości i strony właściwości CLSID do mapy właściwości obiektu.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parametry

*szDesc (szDesc)*<br/>
[w] Opis właściwości.

*Dispid*<br/>
[w] Dispid właściwości.

*Clsid*<br/>
[w] Identyfikator CLSID strony właściwości skojarzonej. Użyj specjalnej wartości CLSID_NULL dla właściwości, która nie ma skojarzonej strony właściwości.

*Vt*<br/>
[w] Typ obiektu.

### <a name="remarks"></a>Uwagi

Makro PROP_ENTRY było niezabezpieczone i przestarzałe. Został on zastąpiony PROP_ENTRY_TYPE.

[Makro BEGIN_PROP_MAP](#begin_prop_map) oznacza początek mapy właściwości; [END_PROP_MAP](#end_prop_map) makr oznacza koniec.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Podobnie [jak PROP_ENTRY_TYPE](#prop_entry_type), ale pozwala określić określony identyfikator, jeśli obiekt obsługuje wiele dwóch interfejsów.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parametry

*szDesc (szDesc)*<br/>
[w] Opis właściwości.

*Dispid*<br/>
[w] Dispid właściwości.

*Clsid*<br/>
[w] Identyfikator CLSID strony właściwości skojarzonej. Użyj specjalnej wartości CLSID_NULL dla właściwości, która nie ma skojarzonej strony właściwości.

*iidDispatch (iidDispatch)*<br/>
[w] Identyfikator podwójnego interfejsu definiującego właściwość.

*Vt*<br/>
[w] Typ obiektu.

### <a name="remarks"></a>Uwagi

Makro PROP_ENTRY_EX było niezabezpieczone i przestarzałe. Został on zastąpiony PROP_ENTRY_TYPE_EX.

[Makro BEGIN_PROP_MAP](#begin_prop_map) oznacza początek mapy właściwości; [END_PROP_MAP](#end_prop_map) makr oznacza koniec.

### <a name="example"></a>Przykład

Poniższe przykładowe grupy `IMyDual1` wpisów, `IMyDual2`po których następuje wpis dla . Grupowanie za pomocą podwójnego interfejsu poprawi wydajność.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a>PROP_PAGE

To makro służy do wprowadzania strony właściwości CLSID do mapy właściwości obiektu.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
[w] Identyfikator CLSID strony właściwości.

### <a name="remarks"></a>Uwagi

PROP_PAGE jest podobny do [PROP_ENTRY_TYPE](#prop_entry_type), ale nie wymaga opisu właściwości lub DISPID.

> [!NOTE]
> Jeśli wprowadzono już CLSID z PROP_ENTRY_TYPE lub [PROP_ENTRY_TYPE_EX,](#prop_entry_type_ex)nie trzeba wprowadzać dodatkowego wpisu z PROP_PAGE.

[Makro BEGIN_PROP_MAP](#begin_prop_map) oznacza początek mapy właściwości; [END_PROP_MAP](#end_prop_map) makr oznacza koniec.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a>END_PROP_MAP

Oznacza koniec mapy właściwości obiektu.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu za pomocą Kreatora projektu ATL kreator utworzy pustą mapę właściwości, określając [BEGIN_PROP_MAP](#begin_prop_map) a następnie END_PROP_MAP.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
