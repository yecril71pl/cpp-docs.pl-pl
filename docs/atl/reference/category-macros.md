---
title: Makra kategorii
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 411e06cc795827eef356018ba427510fd9eb7c06
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864449"
---
# <a name="category-macros"></a>Makra kategorii

Te makra definiują mapy kategorii.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Oznacza początek mapy kategorii.|
|[END_CATEGORY_MAP](#end_category_map)|Oznacza koniec mapy kategorii.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Wskazuje kategorie, które są implementowane przez obiekt COM.|
|[REQUIRED_CATEGORY](#required_category)|Wskazuje kategorie, które są wymagane przez obiekt COM.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

Oznacza początek mapy kategorii.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
podczas Nazwa klasy zawierającej mapę kategorii.

### <a name="remarks"></a>Uwagi

Mapa kategorii służy do określania kategorii składników, które będą implementowane przez klasę COM, oraz wymaganych kategorii z jej kontenera.

Dodaj wpis [IMPLEMENTED_CATEGORY](#implemented_category) do mapy dla każdej kategorii zaimplementowanej przez klasę com. Dodaj wpis [REQUIRED_CATEGORY](#required_category) do mapy dla każdej kategorii, którą Klasa wymaga od klientów do wdrożenia. Oznacz koniec mapy za pomocą makra [END_CATEGORY_MAP](#end_category_map) .

Kategorie składników wymienione na mapie zostaną zarejestrowane automatycznie podczas rejestrowania modułu, jeśli klasa ma skojarzoną [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).

> [!NOTE]
>  ATL używa standardowego Menedżera kategorii składników do rejestrowania kategorii składników. Jeśli Menedżer nie jest obecny w systemie, gdy moduł jest zarejestrowany, rejestracja zakończy się powodzeniem, ale kategorie składników nie zostaną zarejestrowane dla tej klasy.

Aby uzyskać więcej informacji o kategoriach składników, zobacz [co to są kategorie składników i jak działają](/windows/win32/com/component-categories-and-how-they-work) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>END_CATEGORY_MAP

Oznacza koniec mapy kategorii.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_CATEGORY_MAP](#begin_category_map).

##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Dodaj makro IMPLEMENTED_CATEGORY do [mapy kategorii](#begin_category_map) składnika, aby określić, że powinna być zarejestrowana w ramach implementacji kategorii identyfikowanej przez parametr *catID* .

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parametry

*catID*<br/>
podczas Stała CATID lub zmienna przechowująca unikatowy identyfikator globalny (GUID) dla zaimplementowanej kategorii. Adres *catID* zostanie pobrany i dodany do mapy. Zapoznaj się z tabelą poniżej, aby wybrać kategorie giełdowe.

### <a name="remarks"></a>Uwagi

Kategorie składników wymienione na mapie zostaną zarejestrowane automatycznie podczas rejestrowania modułu, jeśli klasa ma skojarzone [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro.

Klienci mogą używać informacji o kategorii zarejestrowanych dla klasy, aby określić jej możliwości i wymagania bez konieczności tworzenia wystąpienia.

Aby uzyskać więcej informacji o kategoriach składników, zobacz [co to są kategorie składników i jak działają](/windows/win32/com/component-categories-and-how-they-work) w Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Wybór kategorii giełdowych

|Opis|Symbol|Identyfikator GUID rejestru|
|-----------------|------------|-------------------|
|Bezpieczne dla skryptów|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpieczne do inicjowania|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Zawiera proste Lokacje ramki|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Proste powiązanie danych|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Zaawansowane powiązanie danych|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Kontrolki bez okien|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Obiekty obsługujące Internet|Listę przykładowych [obiektów obsługujących Internet](/windows/win32/com/internet-aware-objects) można znaleźć w Windows SDK.||

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>REQUIRED_CATEGORY

Dodaj makro REQUIRED_CATEGORY do [mapy kategorii](#begin_category_map) składnika, aby określić, że powinna zostać zarejestrowana jako wymagająca kategorii identyfikowanej przez parametr *catID* .

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parametry

*catID*<br/>
podczas Stała CATID lub zmienna przechowująca unikatowy identyfikator globalny (GUID) dla wymaganej kategorii. Adres *catID* zostanie pobrany i dodany do mapy. Zapoznaj się z tabelą poniżej, aby wybrać kategorie giełdowe.

### <a name="remarks"></a>Uwagi

Kategorie składników wymienione na mapie zostaną zarejestrowane automatycznie podczas rejestrowania modułu, jeśli klasa ma skojarzone [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro.

Klienci mogą używać informacji o kategorii zarejestrowanych dla klasy, aby określić jej możliwości i wymagania bez konieczności tworzenia wystąpienia. Na przykład kontrolka może wymagać powiązania danych z obsługą kontenera. Kontener może sprawdzić, czy ma możliwości niezbędne do hostowania kontroli, badając Menedżera kategorii dla kategorii wymaganych przez tę kontrolkę. Jeśli kontener nie obsługuje wymaganej funkcji, może odmówić hostowania obiektu COM.

Aby uzyskać więcej informacji o kategoriach składników, łącznie z listą przykładową, zobacz [co to są kategorie składników i jak działają](/windows/win32/com/component-categories-and-how-they-work) w Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Wybór kategorii giełdowych

|Opis|Symbol|Identyfikator GUID rejestru|
|-----------------|------------|-------------------|
|Bezpieczne dla skryptów|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Bezpieczne do inicjowania|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Zawiera proste Lokacje ramki|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|Proste powiązanie danych|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Zaawansowane powiązanie danych|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Kontrolki bez okien|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Obiekty obsługujące Internet|Listę przykładowych [obiektów obsługujących Internet](/windows/win32/com/internet-aware-objects) można znaleźć w Windows SDK.||

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Zobacz także

[Utworze](../../atl/reference/atl-macros.md)
