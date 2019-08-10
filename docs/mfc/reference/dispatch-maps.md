---
title: Mapy wysyłania
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: f1afa95d7c20d54f2015255a7e4e0d7ad9ae9c2b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916514"
---
# <a name="dispatch-maps"></a>Mapy wysyłania

Automatyzacja OLE zapewnia sposoby wywoływania metod i dostępu do właściwości w aplikacjach. Mechanizmem dostarczanym przez biblioteka MFC do wysyłania tych żądań jest "Mapa wysyłania", która określa wewnętrzne i zewnętrzne nazwy funkcji obiektów i właściwości, a także typy danych samych właściwości i argumenty funkcji.

|Makro mapy wysyłania|Opis|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Deklaruje, że mapa wysyłania zostanie użyta do ujawnienia metod i właściwości klasy (musi być używana w deklaracji klasy).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Uruchamia definicję mapy wysyłania.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Zamyka definicję mapy wysyłania.|
|[DISP_FUNCTION](#disp_function)|Używane w mapie wysyłania do definiowania funkcji automatyzacji OLE.|
|[DISP_PROPERTY](#disp_property)|Definiuje Właściwość automatyzacji OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Definiuje Właściwość automatyzacji OLE i nazywa funkcje get i Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Definiuje Właściwość automatyzacji OLE z powiadomieniem.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Definiuje Właściwość automatyzacji OLE, która pobiera parametry i nazywa funkcje get i Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Tworzy istniejącą właściwość jako wartość domyślną obiektu.|

## <a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

`CCmdTarget`Jeśli klasa pochodna w programie obsługuje automatyzację OLE, ta klasa musi udostępnić mapę wysyłania, aby uwidocznić jej metody i właściwości.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj makra DECLARE_DISPATCH_MAP na końcu deklaracji klasy. Następnie w. Plik CPP, który definiuje funkcje elementu członkowskiego dla klasy, użyj makra BEGIN_DISPATCH_MAP. Następnie Uwzględnij wpisy makr dla każdej z klas i właściwości uwidocznionych (DISP_FUNCTION, DISP_PROPERTY itd.). Na koniec użyj makra END_DISPATCH_MAP.

> [!NOTE]
> W przypadku deklarowania członków po DECLARE_DISPATCH_MAP należy określić dla nich nowy typ dostępu ( **publiczny**, **prywatny**lub **chroniony**).

Kreator aplikacji i kreatory kodu pomagają w tworzeniu klas automatyzacji i zachowaniu map wysyłania. Aby uzyskać więcej informacji na temat map wysyłania, zobacz [serwery automatyzacji](../../mfc/automation-servers.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Deklaruje definicję mapy wysyłania.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy, która jest właścicielem tej mapy wysyłania.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (. cpp), który definiuje funkcje elementu członkowskiego dla klasy, uruchom mapę wysyłania za pomocą makra BEGIN_DISPATCH_MAP, Dodaj wpisy makr dla każdej funkcji i właściwości wysyłania, a następnie ukończ mapę wysyłania za pomocą END_DISPATCH_ MAPUJ makro.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="end_dispatch_map"></a>END_DISPATCH_MAP

Zamyka definicję mapy wysyłania.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Uwagi

Musi być używana w połączeniu z BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="disp_function"></a>DISP_FUNCTION

Definiuje funkcję automatyzacji OLE na mapie wysyłania.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy.

*pszName*<br/>
Zewnętrzna nazwa funkcji.

*pfnMember*<br/>
Nazwa funkcji składowej.

*vtRetVal*<br/>
Wartość określająca zwracany typ funkcji.

*vtsParams*<br/>
Rozdzielana spacjami lista jednej lub kilku stałych określających listę parametrów funkcji.

### <a name="remarks"></a>Uwagi

Argument *vtRetVal* jest typu VARTYPE. Następujące możliwe wartości tego argumentu są pobierane z `VARENUM` wyliczenia:

|Symbol|Typ zwracany|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|ANI|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|LOGICZNA|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Argument *vtsParams* jest rozdzielaną spacją listą wartości ze `VTS_*` stałych. Co najmniej jedna z tych wartości rozdzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

Określa listę zawierającą krótką liczbę całkowitą, a następnie wskaźnik do krótkiej liczby całkowitej.

`VTS_` Stałe i ich znaczenie są następujące:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` lub `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|LOGICZNA|
|VTS_VARIANT|`const VARIANT*` lub `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__wybierak\*__|
|VTS_PI4|__długo\*__|
|VTS_PR4|__float\*__|
|VTS_PR8|__Double\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|Brak parametrów|

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="disp_property"></a>DISP_PROPERTY

Definiuje Właściwość automatyzacji OLE na mapie wysyłania.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy.

*pszName*<br/>
Zewnętrzna nazwa właściwości.

*memberName*<br/>
Nazwa zmiennej członkowskiej, w której jest przechowywana właściwość.

*vtPropType*<br/>
Wartość określająca typ właściwości.

### <a name="remarks"></a>Uwagi

Argument *vtPropType* jest typu **VARTYPE**. Możliwe wartości tego argumentu są pobierane z wyliczenia VARENUM:

|Symbol|Typ właściwości|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|LOGICZNA|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Gdy Klient zewnętrzny zmieni właściwość, wartość zmiennej składowej określona przez *element MemberName* ulegnie zmianie; nie ma powiadomienia o zmianie.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="disp_property_ex"></a>DISP_PROPERTY_EX

Definiuje Właściwość automatyzacji OLE i nazwij funkcje używane do pobierania i ustawiania wartości właściwości w mapie wysyłania.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy.

*pszName*<br/>
Zewnętrzna nazwa właściwości.

*memberGet*<br/>
Nazwa funkcji składowej używanej do pobierania właściwości.

*memberSet*<br/>
Nazwa funkcji składowej używanej do ustawiania właściwości.

*vtPropType*<br/>
Wartość określająca typ właściwości.

### <a name="remarks"></a>Uwagi

Funkcje *memberGet* i *memberSet* mają sygnatury określone przez argument *vtPropType* . Funkcja *memberGet* nie przyjmuje argumentów i zwraca wartość typu określonego przez *vtPropType*. Funkcja *memberSet* przyjmuje argument typu określonego przez *vtPropType* i zwraca wartość Nothing.

Argument *vtPropType* jest typu VARTYPE. Możliwe wartości tego argumentu są pobierane z wyliczenia VARENUM. Aby uzyskać listę tych wartości, zobacz uwagi dotyczące parametru *vtRetVal* w [DISP_FUNCTION](#disp_function). Należy zauważyć, że VT_EMPTY, wymienione w DISP_FUNCTION uwagi, nie jest dozwolone jako typ danych właściwości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Definiuje Właściwość automatyzacji OLE z powiadomieniem w mapie wysyłania.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy.

*szExternalName*<br/>
Zewnętrzna nazwa właściwości.

*memberName*<br/>
Nazwa zmiennej członkowskiej, w której jest przechowywana właściwość.

*pfnAfterSet*<br/>
Nazwa funkcji powiadomień dla *szExternalName*.

*vtPropType*<br/>
Wartość określająca typ właściwości.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do właściwości zdefiniowanych za pomocą DISP_PROPERTY, właściwość zdefiniowana z DISP_PROPERTY_NOTIFY automatycznie wywoła funkcję określoną przez *pfnAfterSet* , gdy właściwość zostanie zmieniona.

Argument *vtPropType* jest typu VARTYPE. Możliwe wartości tego argumentu są pobierane z wyliczenia VARENUM:

|Symbol|Typ właściwości|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|LOGICZNA|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Definiuje właściwość, do której można `Get` uzyskać `Set` dostęp za pomocą oddzielnych funkcji i elementów członkowskich.

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszExternalName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy.

*pszExternalName*<br/>
Zewnętrzna nazwa właściwości.

*pfnGet*<br/>
Nazwa funkcji składowej używanej do pobierania właściwości.

*pfnSet*<br/>
Nazwa funkcji składowej używanej do ustawiania właściwości.

*vtPropType*<br/>
Wartość określająca typ właściwości.

*vtsParams*<br/>
Ciąg typów parametrów Variant rozdzielonych `VTS_*` spacjami, jeden dla każdego parametru.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do makra DISP_PROPERTY_EX, to makro pozwala określić listę parametrów dla właściwości. Jest to przydatne w przypadku implementowania właściwości, które są indeksowane lub sparametryzowane.

### <a name="example"></a>Przykład

Rozważmy następującą deklarację funkcji get i Set member, która umożliwia użytkownikowi zażądanie określonego wiersza i kolumny podczas uzyskiwania dostępu do właściwości:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Odpowiadają one następującemu makro DISP_PROPERTY_PARAM na mapie wysyłania kontrolek:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Innym przykładem jest rozważenie następujących funkcji elementów członkowskich get i set:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Odpowiadają one następującemu makro DISP_PROPERTY_PARAM na mapie wysyłania kontrolek:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="disp_defvalue"></a>DISP_DEFVALUE

Tworzy istniejącą właściwość jako wartość domyślną obiektu.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy.

*pszName*<br/>
Zewnętrzna nazwa właściwości, która reprezentuje "wartość" obiektu.

### <a name="remarks"></a>Uwagi

Użycie wartości domyślnej może sprawiać, że programowanie obiektu automatyzacji jest prostsze dla Visual Basic aplikacji.

"Wartość domyślna" obiektu jest właściwością pobieraną lub ustawianą, gdy odwołanie do obiektu nie określa właściwości lub funkcji członkowskiej.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="see-also"></a>Zobacz także

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
