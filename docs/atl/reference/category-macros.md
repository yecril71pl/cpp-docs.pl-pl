---
title: Makra kategorii
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 1d8bbae4608aa661bbc612604f7d85855f325f5f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321597"
---
# <a name="category-macros"></a>Makra kategorii

Te makra definiują mapy kategorii.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Oznacza początek mapy kategorii.|
|[END_CATEGORY_MAP](#end_category_map)|Oznacza koniec mapy kategorii.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Wskazuje kategorie, które są implementowane przez obiekt COM.|
|[REQUIRED_CATEGORY](#required_category)|Wskazuje kategorie, które są wymagane od kontenera przez obiekt COM.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="begin_category_map"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

Oznacza początek mapy kategorii.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
[w] Nazwa klasy zawierającej mapę kategorii.

### <a name="remarks"></a>Uwagi

Mapa kategorii służy do określania kategorii składników, które klasa COM zaimplementuje i jakie kategorie wymaga z jego kontenera.

Dodaj wpis [IMPLEMENTED_CATEGORY](#implemented_category) do mapy dla każdej kategorii zaimplementowanej przez klasę COM. Dodaj [wpis REQUIRED_CATEGORY](#required_category) do mapy dla każdej kategorii, która wymaga od swoich klientów zaimplementowania. Oznacz koniec mapy [END_CATEGORY_MAP](#end_category_map) makrą.

Kategorie komponentów wymienione na mapie zostaną automatycznie zarejestrowane po zarejestrowaniu modułu, jeśli klasa ma skojarzony [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).

> [!NOTE]
> ATL używa menedżera standardowych kategorii składników do rejestrowania kategorii składników. Jeśli menedżer nie jest obecny w systemie, gdy moduł jest zarejestrowany, rejestracja powiedzie się, ale kategorie składników nie zostaną zarejestrowane dla tej klasy.

Aby uzyskać więcej informacji na temat kategorii składników, zobacz [Jakie są kategorie składników i jak działają](/windows/win32/com/component-categories-and-how-they-work) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a>END_CATEGORY_MAP

Oznacza koniec mapy kategorii.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_CATEGORY_MAP](#begin_category_map).

## <a name="implemented_category"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Dodaj makro IMPLEMENTED_CATEGORY do [mapy kategorii](#begin_category_map) składnika, aby określić, że powinno ono zostać zarejestrowane jako implementujące kategorię identyfikowaną przez parametr *catID.*

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parametry

*katID (katID)*<br/>
[w] Stała LUB zmienna CATID przechowująca unikatowy identyfikator (GUID) dla zaimplementowanych kategorii. Adres *catID* zostanie pobrany i dodany do mapy. Zobacz poniższą tabelę, aby zapoznać się z wybranymi kategoriami akcji.

### <a name="remarks"></a>Uwagi

Kategorie komponentów wymienione na mapie zostaną automatycznie zarejestrowane po zarejestrowaniu modułu, jeśli klasa ma skojarzone [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra.

Klienci mogą używać informacji o kategorii zarejestrowanych dla klasy, aby określić jej możliwości i wymagania bez konieczności tworzenia wystąpienia.

Aby uzyskać więcej informacji na temat kategorii składników, zobacz [Jakie są kategorie składników i jak działają](/windows/win32/com/component-categories-and-how-they-work) w zestawie Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Wybór kategorii akcji

|Opis|Symbol|Identyfikator GUID rejestru|
|-----------------|------------|-------------------|
|Bezpieczne dla skryptów|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpieczne do inicjowania|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Proste hermetyzacja witryny ramki|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Proste powiązanie danych|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Zaawansowane powiązanie danych|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Kontrolki bez okien|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Obiekty z dostępem do Internetu|Zobacz [obiekty obsługujące internet](/windows/win32/com/internet-aware-objects) w zestawie Windows SDK, aby uzyskać przykładową listę.||

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a>REQUIRED_CATEGORY

Dodaj makro REQUIRED_CATEGORY do [mapy kategorii](#begin_category_map) komponentu, aby określić, że powinno ono być zarejestrowane jako wymagające kategorii określonej przez parametr *catID.*

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parametry

*katID (katID)*<br/>
[w] Stała LUB zmienna CATID przechowująca unikatowy identyfikator (GUID) dla wymaganej kategorii. Adres *catID* zostanie pobrany i dodany do mapy. Zobacz poniższą tabelę, aby zapoznać się z wybranymi kategoriami akcji.

### <a name="remarks"></a>Uwagi

Kategorie komponentów wymienione na mapie zostaną automatycznie zarejestrowane po zarejestrowaniu modułu, jeśli klasa ma skojarzone [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra.

Klienci mogą używać informacji o kategorii zarejestrowanych dla klasy, aby określić jej możliwości i wymagania bez konieczności tworzenia wystąpienia. Na przykład formant może wymagać, aby powiązanie danych obsługi kontenera. Kontener może dowiedzieć się, czy ma możliwości niezbędne do hostowania formantu, przeprowadzając kwerendę menedżera kategorii dla kategorii wymaganych przez ten formant. Jeśli kontener nie obsługuje wymaganej funkcji, może odmówić hosta obiektu COM.

Aby uzyskać więcej informacji na temat kategorii składników, w tym przykładowej listy, zobacz [Jakie są kategorie składników i jak działają](/windows/win32/com/component-categories-and-how-they-work) w zestawie Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Wybór kategorii akcji

|Opis|Symbol|Identyfikator GUID rejestru|
|-----------------|------------|-------------------|
|Bezpieczne dla skryptów|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpieczne do inicjowania|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Proste hermetyzacja witryny ramki|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Proste powiązanie danych|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Zaawansowane powiązanie danych|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Kontrolki bez okien|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Obiekty z dostępem do Internetu|Zobacz [obiekty obsługujące internet](/windows/win32/com/internet-aware-objects) w zestawie Windows SDK, aby uzyskać przykładową listę.||

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
