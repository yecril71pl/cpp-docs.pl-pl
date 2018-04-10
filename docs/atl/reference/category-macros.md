---
title: Kategoria makra | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
dev_langs:
- C++
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 752a0c0c9de5c726a106ca08a574844369c6bdc5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="category-macros"></a>Makra kategorii
Te makra Definiowanie kategorii mapy.  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Oznacza początek mapy kategorii.|  
|[END_CATEGORY_MAP](#end_category_map)|Oznacza koniec mapy kategorii.|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|Wskazuje kategorie, które są implementowane przez obiekt COM.|  
|[REQUIRED_CATEGORY](#required_category)|Wskazuje kategorie, które są wymagane kontenera przez obiekt COM.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  

##  <a name="begin_category_map"></a>BEGIN_CATEGORY_MAP  
 Oznacza początek mapy kategorii.  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 [in] Nazwa klasy zawierającej mapy kategorii.  
  
### <a name="remarks"></a>Uwagi  
 Mapa kategoria służy do określania kategorie składników, które wykona klasy COM i kategorie, które wymaga od jego kontenera.  
  
 Dodaj [IMPLEMENTED_CATEGORY](#implemented_category) wpisu mapy dla każdej kategorii zaimplementowany przez klasę COM. Dodaj [REQUIRED_CATEGORY](#required_category) wpisu mapy dla każdej kategorii, wymagającego klasy w swoich klientów do wdrożenia. Oznaczenia zakończenia mapy [END_CATEGORY_MAP](#end_category_map) makra.  
  
 Kategorii składników mapy na liście zostanie zarejestrowana automatycznie po zarejestrowaniu modułu, jeśli klasa ma skojarzoną [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .  
  
> [!NOTE]
>  ATL używa standardowy składnik menedżera kategorii można zarejestrować składnika kategorii. Jeśli Menedżer nie jest obecny w systemie, po zarejestrowaniu modułu, rejestracja zakończy się pomyślnie, ale kategorii składników nie zostanie zarejestrowany dla tej klasy.  
  
 Aby uzyskać więcej informacji o kategorii składników, zobacz [co to są kategorii składników i sposobu ich działania](http://msdn.microsoft.com/library/windows/desktop/ms694322) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="end_category_map"></a>END_CATEGORY_MAP  
 Oznacza koniec mapy kategorii.  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [BEGIN_CATEGORY_MAP](#begin_category_map).  
  
##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY  
 Dodaj `IMPLEMENTED_CATEGORY` makro do Twojej składnika [mapy kategorii](#begin_category_map) do określenia, czy powinien zostać zarejestrowany jako kategorii identyfikowane przez `catID` parametru.  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>Parametry  
 `catID`  
 [in] A **CATID** stałą lub zmienną zawierający Unikatowy identyfikator globalny (GUID) dla kategorii zaimplementowany. Adres `catID` zostanie wykonane i dodany do mapy. Poniższa tabela dla wyboru standardowych kategorii.  
  
### <a name="remarks"></a>Uwagi  
 Kategorii składników mapy na liście zostanie zarejestrowana automatycznie po zarejestrowaniu modułu, jeśli klasa ma skojarzoną [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra.  
  
 Klienci mogą używać informacji kategorii zarejestrowany dla klasy do określenia jej możliwości i wymagania bez konieczności tworzenia wystąpienia.  
  
 Aby uzyskać więcej informacji o kategorii składników, zobacz [co to są kategorii składników i sposobu ich działania](http://msdn.microsoft.com/library/windows/desktop/ms694322) w zestawie Windows SDK.  
  
### <a name="a-selection-of-stock-categories"></a>Wybór kategorii standardowych  
  
|Opis|Symbol|Identyfikator GUID rejestru|  
|-----------------|------------|-------------------|  
|Bezpieczne dla wykonywania skryptów|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Bezpieczne dla inicjowania|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Zawieranie lokacji proste ramki|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|Proste powiązanie danych|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Zaawansowane powiązania danych|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Formanty bez okien|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Obiekty obsługujących Internetowe|Zobacz [obiektów pamiętać Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) w zestawie Windows SDK w przykładowej listy.||  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="required_category"></a>REQUIRED_CATEGORY  
 Dodaj `REQUIRED_CATEGORY` makro do Twojej składnika [mapy kategorii](#begin_category_map) do określenia, czy powinien zostać zarejestrowany jako wymagające kategorii identyfikowane przez `catID` parametru.  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>Parametry  
 `catID`  
 [in] A **CATID** stałą lub zmienną zawierający Unikatowy identyfikator globalny (GUID) dla kategorii wymagane. Adres `catID` zostanie wykonane i dodany do mapy. Poniższa tabela dla wyboru standardowych kategorii.  
  
### <a name="remarks"></a>Uwagi  
 Kategorii składników mapy na liście zostanie zarejestrowana automatycznie po zarejestrowaniu modułu, jeśli klasa ma skojarzoną [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) lub [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra.  
  
 Klienci mogą używać informacji kategorii zarejestrowany dla klasy do określenia jej możliwości i wymagania bez konieczności tworzenia wystąpienia. Formant może na przykład wymagać, że kontener obsługuje powiązanie danych. Kontener można sprawdzić, czy ma funkcje niezbędne do hostowania kontrolki badając menedżera kategorii dla kategorii wymaganych przez ten formant. Jeśli kontener nie obsługuje wymaganych funkcji, można odmówić do obsługi obiektu COM.  
  
 Aby uzyskać więcej informacji o kategorii składników, łącznie z listą przykładowe zobacz [co to są kategorii składników i sposobu ich działania](http://msdn.microsoft.com/library/windows/desktop/ms694322) w zestawie Windows SDK.  
  
### <a name="a-selection-of-stock-categories"></a>Wybór kategorii standardowych  
  
|Opis|Symbol|Identyfikator GUID rejestru|  
|-----------------|------------|-------------------|  
|Bezpieczne dla wykonywania skryptów|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Bezpieczne dla inicjowania|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Zawieranie lokacji proste ramki|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|Proste powiązanie danych|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Zaawansowane powiązania danych|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Formanty bez okien|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Obiekty obsługujących Internetowe|Zobacz [obiektów pamiętać Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) w zestawie Windows SDK w przykładowej listy.||  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
