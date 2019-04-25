---
title: Makra kategorii
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 9c74b1e8e9fc101ed9b3acd842d38dcdb9eb48f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247400"
---
# <a name="category-macros"></a>Makra kategorii

Te makra definiują mapy kategorii.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Oznacza początek mapy kategorii.|
|[END_CATEGORY_MAP](#end_category_map)|Oznacza koniec mapy kategorii.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Wskazuje, kategorie, które są implementowane przez obiekt COM.|
|[REQUIRED_CATEGORY](#required_category)|Wskazuje, kategorie, które są wymagane przez obiekt COM kontenera.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP

Oznacza początek mapy kategorii.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[in] Nazwa klasy zawierającej mapy kategorii.

### <a name="remarks"></a>Uwagi

Mapy kategorii służy do określania, które kategorie składnika wdroży klasa COM i kategorie, które wymaga od jego kontenera.

Dodaj [IMPLEMENTED_CATEGORY](#implemented_category) wpisu do mapy dla każdej kategorii, zaimplementowany przez klasę modelu COM. Dodaj [REQUIRED_CATEGORY](#required_category) wpisu do mapy dla każdej kategorii, wymagającego klasy w swoich klientów do wdrożenia. Oznacz koniec mapy za pomocą [END_CATEGORY_MAP](#end_category_map) makra.

Kategorii składników mapy na liście będą rejestrowane automatycznie po zarejestrowaniu modułu, jeśli klasa ma skojarzoną [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .

> [!NOTE]
>  ATL używa standardowy składnik Menedżer kategorii, aby zarejestrować kategorii składników. Jeśli Menedżer nie jest obecny w systemie, po zarejestrowaniu modułu, rejestracja zakończy się pomyślnie, ale kategorii składników nie zostanie zarejestrowany dla tej klasy.

Aby uzyskać więcej informacji na temat kategorii składników, zobacz [co to są kategorii składników i sposobie ich działania](/windows/desktop/com/component-categories-and-how-they-work) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>  END_CATEGORY_MAP

Oznacza koniec mapy kategorii.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_CATEGORY_MAP](#begin_category_map).

##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY

Dodaj makro IMPLEMENTED_CATEGORY do danego składnika [mapy kategorii](#begin_category_map) do określenia, czy powinien być zarejestrowany jako kategoria identyfikowane przez *catID* parametru.

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parametry

*catID*<br/>
[in] CATID stałą lub zmienną zawierający Unikatowy identyfikator globalny (GUID) dla kategorii zaimplementowano. Adres *catID* zostanie wykonane i dodany do mapy. Zobacz tabelę poniżej w przypadku wyboru akcji kategorii.

### <a name="remarks"></a>Uwagi

Kategorii składników mapy na liście będą rejestrowane automatycznie po zarejestrowaniu modułu, jeśli klasa ma skojarzoną [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra.

Klienci mogą używać informacji kategorii zarejestrowane dla tej klasy, aby określić wymagania i możliwości bez konieczności tworzenia jego wystąpienie.

Aby uzyskać więcej informacji na temat kategorii składników, zobacz [co to są kategorii składników i sposobie ich działania](/windows/desktop/com/component-categories-and-how-they-work) w zestawie Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Wybór kategorii podstawowe

|Opis|Symbol|Identyfikator GUID rejestru|
|-----------------|------------|-------------------|
|Bezpieczny dla skryptów|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpieczny w zakresie inicjowania|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Proste ramki lokacji zawierania|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Proste powiązanie danych|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Advanced Data Binding|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Od kontrolek bez okien|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Obiekty obsługujących Internet|Zobacz [obiektów pamiętać Internet](/windows/desktop/com/internet-aware-objects) w zestawie Windows SDK dla lista przykładów.||

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>  REQUIRED_CATEGORY

Dodaj makro REQUIRED_CATEGORY do danego składnika [mapy kategorii](#begin_category_map) do określenia, czy powinien być zarejestrowany jako wymagające kategorii identyfikowane przez *catID* parametru.

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parametry

*catID*<br/>
[in] CATID stałą lub zmienną zawierający Unikatowy identyfikator globalny (GUID) dla kategorii wymagane. Adres *catID* zostanie wykonane i dodany do mapy. Zobacz tabelę poniżej w przypadku wyboru akcji kategorii.

### <a name="remarks"></a>Uwagi

Kategorii składników mapy na liście będą rejestrowane automatycznie po zarejestrowaniu modułu, jeśli klasa ma skojarzoną [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra.

Klienci mogą używać informacji kategorii zarejestrowane dla tej klasy, aby określić wymagania i możliwości bez konieczności tworzenia jego wystąpienie. Na przykład formant może wymagać, że kontener obsługuje powiązanie danych. Kontener można dowiedzieć się, jeśli ma możliwości, które są niezbędne do hostowania kontrolki, badając Menedżer kategorii dla kategorii, wymagane przez tę kontrolkę. Jeśli kontener nie obsługuje wymaganych funkcji, można odmówić hosta obiektu COM.

Aby uzyskać więcej informacji na temat kategorii składników, takich jak lista przykładów, zobacz [co to są kategorii składników i sposobie ich działania](/windows/desktop/com/component-categories-and-how-they-work) w zestawie Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Wybór kategorii podstawowe

|Opis|Symbol|Identyfikator GUID rejestru|
|-----------------|------------|-------------------|
|Bezpieczny dla skryptów|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpieczny w zakresie inicjowania|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Proste ramki lokacji zawierania|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Proste powiązanie danych|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Advanced Data Binding|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Od kontrolek bez okien|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Obiekty obsługujących Internet|Zobacz [obiektów pamiętać Internet](/windows/desktop/com/internet-aware-objects) w zestawie Windows SDK dla lista przykładów.||

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)
