---
title: "Mapy wysyłania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.maps
dev_langs: C++
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 76fc842626890f48b641a495567338404330d8d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dispatch-maps"></a>Mapy wysyłania
Automatyzacja OLE udostępnia metody do wywołania metody i mieć dostęp do właściwości w aplikacjach. Mechanizm dostarczonych przez Microsoft Foundation Class Library na potrzeby rozsyłania te żądania jest "mapy wysyłania," który wyznacza wewnętrznych i zewnętrznych nazwy obiektu funkcje i właściwości, a także same właściwości i elementu typy danych argumenty funkcji.  
  
### <a name="dispatch-maps"></a>Mapy wysyłania  
  
|||  
|-|-|  
|[DECLARE_DISPATCH_MAP —](#declare_dispatch_map)|Deklaruje, że mapy wysyłania będzie używany do udostępnienia metod klasy i właściwości (należy użyć w deklaracji klasy).|  
|[BEGIN_DISPATCH_MAP —](#begin_dispatch_map)|Uruchamia definicji mapy wysyłania.|  
|[END_DISPATCH_MAP —](#end_dispatch_map)|Kończy definicję planu wysyłania.|  
|[DISP_FUNCTION —](#disp_function)|Używane w mapie wysyłania do definiowania funkcji automatyzacji OLE.|  
|[DISP_PROPERTY —](#disp_property)|Definiuje właściwości automatyzacji OLE.|  
|[DISP_PROPERTY_EX —](#disp_property_ex)|Definiuje właściwości automatyzacji OLE oraz nazwy funkcje Get i Set.|  
|[DISP_PROPERTY_NOTIFY —](#disp_property_notify)|Definiuje właściwości automatyzacji OLE z powiadomień.|  
|[DISP_PROPERTY_PARAM —](#disp_property_param)|Definiuje właściwości automatyzacji OLE, który przyjmuje nazwy i parametry funkcji Get i Set.|  
|[DISP_DEFVALUE —](#disp_defvalue)|Powoduje, że właściwość istniejącej wartości domyślne obiektu.|  
  
##  <a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP —  
 Jeśli `CCmdTarget`-klasy pochodnej w programie obsługuje automatyzacji OLE, że klasa musi zapewniać mapy wysyłania do udostępnienia metod i właściwości.  
  
```   
DECLARE_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj `DECLARE_DISPATCH_MAP` makro końca z deklaracji klasy. Następnie w. Funkcje pliku CPP, który definiuje element członkowski klasy, należy użyć `BEGIN_DISPATCH_MAP` makra. Następnie dołączyć wpisy makro dla każdej klasy obiektu uwidocznione metody i właściwości ( `DISP_FUNCTION`, `DISP_PROPERTY`i tak dalej). Na koniec użyj `END_DISPATCH_MAP` makra.  
  
> [!NOTE]
>  W przypadku żadnych elementów członkowskich po `DECLARE_DISPATCH_MAP`, należy określić nowy typ dostępu ( **publicznego**, `private`, lub `protected`) dla nich.  
  
 Kreatorzy Kreatora aplikacji i kod pomagają w klasy automatyzacji tworzenia i utrzymywania mapy wysyłania. Aby uzyskać więcej informacji na mapy wysyłania, zobacz [serwery automatyzacji](../../mfc/automation-servers.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  

##  <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP —  
 Deklaruje definicji mapy wysyłania.  
  
```  
BEGIN_DISPATCH_MAP(theClass, baseClass)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Określa nazwę klasy, która jest właścicielem tej mapy wysyłania.  
  
 `baseClass`  
 Określa nazwę klasy podstawowej `theClass`.  
  
### <a name="remarks"></a>Uwagi  
 W pliku implementacji (.cpp), który definiuje funkcje Członkowskie dla klasy, należy uruchomić mapy wysyłania `BEGIN_DISPATCH_MAP` makra, Dodaj makro wpisy dla wszystkich funkcji wysyłania i właściwości, a następnie ukończ mapy wysyłania `END_DISPATCH_MAP` makra.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  

##  <a name="end_dispatch_map"></a>END_DISPATCH_MAP —  
 Kończy definicję mapy wysyłania.  
  
```   
END_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>Uwagi  
 Należy go używać w połączeniu z `BEGIN_DISPATCH_MAP`.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  

##  <a name="disp_function"></a>DISP_FUNCTION —  
 Definiuje funkcję automatyzacji OLE w mapie wysyłania.  
  
```   
DISP_FUNCTION(
  theClass, 
  pszName, 
  pfnMember, 
  vtRetVal, 
  vtsParams)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy.  
  
 `pszName`  
 Zewnętrzna nazwa funkcji.  
  
 `pfnMember`  
 Nazwa funkcji członkowskiej.  
  
 `vtRetVal`  
 Wartość określająca typ zwracany przez funkcję.  
  
 `vtsParams`  
 Rozdzielonej spacjami listy co najmniej jedną stałą określenie listy parametrów funkcji.  
  
### <a name="remarks"></a>Uwagi  
 `vtRetVal` Argument jest typu **VARTYPE**. Następujące możliwe wartości dla tego argumentu są pobierane z `VARENUM` wyliczenie:  
  
|Symbol|Zwracany typ|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**krótki**|  
|`VT_I4`|**długa**|  
|`VT_R4`|**float**|  
|`VT_R8`|**podwójne**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATA**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**WARTOŚĆ LOGICZNA**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 `vtsParams` Argument jest rozdzielonej spacjami listy wartości z **VTS_** stałe. Co najmniej jeden z tych wartości, rozdzielając je spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład 
  
 [!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]  
  
 Określa listę zawierającą krótka liczba całkowita, następuje wskaźnik do krótkich liczby całkowitej.  
  
 **VTS_** stałe i ich znaczenie są następujące:  
  
|Symbol|Typ parametru|  
|------------|--------------------|  
|**VTS_I2**|`Short`|  
|**VTS_I4**|`Long`|  
|**VTS_R4**|**Float**|  
|**VTS_R8**|`Double`|  
|**VTS_CY**|**Const CY** lub **CY\***|  
|**VTS_DATE**|**DATA**|  
|**VTS_BSTR**|`LPCSTR`|  
|**VTS_DISPATCH**|`LPDISPATCH`|  
|**VTS_SCODE**|`SCODE`|  
|**VTS_BOOL**|**WARTOŚĆ LOGICZNA**|  
|**VTS_VARIANT**|**Wariant Const\***  lub **VARIANT &**|  
|**VTS_UNKNOWN**|`LPUNKNOWN`|  
|**VTS_PI2**|**krótki\***|  
|**VTS_PI4**|**długa\***|  
|**VTS_PR4**|**float\***|  
|**VTS_PR8**|**podwójne\***|  
|**VTS_PCY**|**CY\***|  
|**VTS_PDATE**|**DATA\***|  
|**VTS_PBSTR**|**BSTR\***|  
|**VTS_PDISPATCH**|**LPDISPATCH\***|  
|**VTS_PSCODE**|**SCODE\***|  
|**VTS_PBOOL**|**WARTOŚĆ LOGICZNA\***|  
|**VTS_PVARIANT**|**VARIANT\***|  
|**VTS_PUNKNOWN**|**LPUNKNOWN\***|  
|**VTS_NONE**|Brak parametrów|  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h 

##  <a name="disp_property"></a>DISP_PROPERTY —  
 Definiuje właściwości automatyzacji OLE w mapie wysyłania.  
  
```   
DISP_PROPERTY(
  theClass, 
  pszName, 
  memberName, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy.  
  
 `pszName`  
 Zewnętrzna nazwa właściwości.  
  
 `memberName`  
 Nazwa zmiennej członkowskiej, w którym przechowywany jest właściwość.  
  
 `vtPropType`  
 Wartość określająca typ właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `vtPropType` Argument jest typu **VARTYPE**. Możliwe wartości dla tego argumentu są pobierane z `VARENUM` wyliczenie:  
  
|Symbol|**Typ właściwości**|  
|------------|-----------------------|  
|`VT_I2`|**krótki**|  
|`VT_I4`|**długa**|  
|`VT_R4`|**float**|  
|`VT_R8`|**podwójne**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATA**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**WARTOŚĆ LOGICZNA**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 Zmiany właściwości, wartość zmiennej członkowskiej, określony przez klientom zewnętrznym `memberName` zmienia; nie jest prezentowane nie powiadomienie o zmianie.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h 

##  <a name="disp_property_ex"></a>DISP_PROPERTY_EX —  
 Definiuje właściwości automatyzacji OLE i nazwy funkcje służące do pobierania i ustawiania wartości właściwości mapy wysyłania.  
  
```   
DISP_PROPERTY_EX(
  theClass, 
  pszName, 
  memberGet, 
  memberSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy.  
  
 `pszName`  
 Zewnętrzna nazwa właściwości.  
  
 `memberGet`  
 Nazwa funkcji członkowskiej, używany do pobierania właściwości.  
  
 `memberSet`  
 Nazwa funkcji członkowskiej używany do ustawiania właściwości.  
  
 `vtPropType`  
 Wartość określająca typ właściwości.  
  
### <a name="remarks"></a>Uwagi  
 `memberGet` i `memberSet` funkcje mają podpisy ustaleniami `vtPropType` argumentu. `memberGet` Funkcja nie przyjmuje żadnych argumentów i zwraca wartość typu określonego przez `vtPropType`. `memberSet` Funkcja przyjmuje argument typu określony przez `vtPropType` i nie zwraca żadnego.  
  
 `vtPropType` Argument jest typu **VARTYPE**. Możliwe wartości dla tego argumentu są pobierane z `VARENUM` wyliczenia. Aby uzyskać listę tych wartości, zobacz uwagi dla `vtRetVal` parametru w [disp_function —](#disp_function). Należy pamiętać, że `VT_EMPTY`, wymienionych w `DISP_FUNCTION` uwagi, jest niedozwolony jako typ danych właściwości.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h 

##  <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY —  
 Definiuje właściwości automatyzacji OLE powiadomienie na mapie wysyłania.  
  
```   
DISP_PROPERTY_NOTIFY(
  theClass, 
  szExternalName, 
  memberName, 
  pfnAfterSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy.  
  
 `szExternalName`  
 Zewnętrzna nazwa właściwości.  
  
 `memberName`  
 Nazwa zmiennej członkowskiej, w którym przechowywany jest właściwość.  
  
 `pfnAfterSet`  
 Nazwa funkcji powiadomień dla `szExternalName`.  
  
 `vtPropType`  
 Wartość określająca typ właściwości.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od właściwości zdefiniowane z `DISP_PROPERTY`, właściwość zdefiniowana z `DISP_PROPERTY_NOTIFY` automatycznie wywoła funkcji określonej przez `pfnAfterSet` zmiany właściwości.  
  
 `vtPropType` Argument jest typu **VARTYPE**. Możliwe wartości dla tego argumentu są pobierane z `VARENUM` wyliczenie:  
  
|Symbol|**Typ właściwości**|  
|------------|-----------------------|  
|`VT_I2`|**krótki**|  
|`VT_I4`|**długa**|  
|`VT_R4`|**float**|  
|`VT_R8`|**podwójne**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATA**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**WARTOŚĆ LOGICZNA**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h 

##  <a name="disp_property_param"></a>DISP_PROPERTY_PARAM —  
 Definiuje właściwość uzyskanie dostępu do oddzielnego **uzyskać** i `Set` funkcji elementów członkowskich.  
  
```   
DISP_PROPERTY_PARAM(
  theClass, 
  pszExternalName, 
  pfnGet, 
  pfnSet, 
  vtPropType,
  vtsParams)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy.  
  
 *pszExternalName*  
 Zewnętrzna nazwa właściwości.  
  
 `pfnGet`  
 Nazwa funkcji członkowskiej, używany do pobierania właściwości.  
  
 `pfnSet`  
 Nazwa funkcji członkowskiej używany do ustawiania właściwości.  
  
 `vtPropType`  
 Wartość określająca typ właściwości.  
  
 `vtsParams`  
 Ciąg rozdzielany **VTS_** typów parametru variant, po jednej dla każdego parametru.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od `DISP_PROPERTY_EX` makra, to makro umożliwia określenie listy parametrów dla właściwości. Jest to przydatne stosowania właściwości, które są indeksowane lub sparametryzowana.  
  
### <a name="example"></a>Przykład  
 Należy wziąć pod uwagę następujące oświadczenie get i zestawu funkcji, które umożliwiają użytkownikowi żądanie określonych wierszy i kolumn podczas uzyskiwania dostępu do właściwości:  
  
 [!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]  
  
 Odpowiadają one następujące `DISP_PROPERTY_PARAM` makra mapy wysyłania sterowania:  
  
 [!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]  
  
 Inny przykład wziąć pod uwagę następujące get i zestawu funkcji:  
  
 [!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]  
  
 Odpowiadają one następujące `DISP_PROPERTY_PARAM` makra mapy wysyłania sterowania:  
  
 [!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h 

##  <a name="disp_defvalue"></a>DISP_DEFVALUE —  
 Powoduje, że właściwość istniejącej wartości domyślne obiektu.  
  
```   
DISP_DEFVALUE(theClass, pszName)   
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy.  
  
 `pszName`  
 Zewnętrzna nazwa właściwości, która reprezentuje "value" obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Przy użyciu wartości domyślnej ułatwia programowanie obiektu automatyzacji prostsze dla aplikacji Visual Basic.  
  
 "Wartość domyślna" obiektu jest właściwością, która jest pobrać lub ustawić, gdy odwołanie do obiektu nie określa funkcja właściwości lub elementu członkowskiego.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h 

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
