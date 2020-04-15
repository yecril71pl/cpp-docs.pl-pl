---
title: Mapy wysyłania
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 59dd8c7a7b0b930ffdb68fd96410fd73aeb02e81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365755"
---
# <a name="dispatch-maps"></a>Mapy wysyłania

Automatyzacja OLE udostępnia sposoby wywoływania metod i dostępu do właściwości w aplikacjach. Mechanizm dostarczony przez Bibliotekę klas Microsoft Foundation do wysyłania tych żądań jest "mapa wysyłki", który wyznacza wewnętrzne i zewnętrzne nazwy funkcji i właściwości obiektu, a także typy danych samych właściwości i argumentów funkcji.

|Makra mapy wysyłki|Opis|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Deklaruje, że mapa wysyłki będzie używany do udostępnienia metody i właściwości klasy (musi być używany w deklaracji klasy).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Rozpoczyna definicję mapy wysyłki.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Kończy definicję mapy wysyłki.|
|[DISP_FUNCTION](#disp_function)|Używane na mapie wysyłki do definiowania funkcji automatyzacji OLE.|
|[DISP_PROPERTY](#disp_property)|Definiuje właściwość automatyzacji OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Definiuje właściwość automatyzacji OLE i nazwy Get i Set funkcje.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Definiuje właściwość automatyzacji OLE z powiadomieniem.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Definiuje właściwość automatyzacji OLE, która przyjmuje parametry i nazwy funkcji Pobierz i Ustaw.|
|[DISP_DEFVALUE](#disp_defvalue)|Sprawia, że istniejąca właściwość jest wartością domyślną obiektu.|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

Jeśli `CCmdTarget`klasa pochodna w programie obsługuje automatyzacji OLE, ta klasa musi dostarczyć mapę wysyłki, aby udostępnić jego metody i właściwości.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj makra DECLARE_DISPATCH_MAP na końcu deklaracji klasy. Następnie, w . Plik CPP, który definiuje funkcje członkowskie dla klasy, należy użyć makra BEGIN_DISPATCH_MAP. Następnie należy uwzględnić wpisy makr dla każdej z dostępnych metod i właściwości klasy (DISP_FUNCTION, DISP_PROPERTY itd.). Na koniec użyj makra END_DISPATCH_MAP.

> [!NOTE]
> Jeśli po DECLARE_DISPATCH_MAP zgłosisz dowolny element członkowek, musisz określić dla nich nowy typ dostępu ( **publiczny,** **prywatny**lub **chroniony).**

Kreator aplikacji i kreatorzy kodu pomagają w tworzeniu klas automatyzacji i w utrzymywaniu map wysyłki. Aby uzyskać więcej informacji na temat map wysyłki, zobacz [Serwery automatyzacji](../../mfc/automation-servers.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Deklaruje definicję mapy wysyłki.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Określa nazwę klasy, która jest właścicielem tej mapy wysyłki.

*Baseclass*<br/>
Określa nazwę klasy podstawowej *klasy klasy*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcje członkowskie dla klasy, uruchom mapę wysyłki z BEGIN_DISPATCH_MAP makra, dodaj wpisy makr dla każdej funkcji i właściwości wysyłki i uzupełnij mapę wysyłki END_DISPATCH_MAP makra.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP

Kończy definicję mapy wysyłki.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Uwagi

Musi być stosowany w połączeniu z BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a>DISP_FUNCTION

Definiuje funkcję automatyzacji OLE na mapie wysyłki.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Nazwa klasy.

*pszName (Nazwa psz)*<br/>
Zewnętrzna nazwa funkcji.

*numer pfn*<br/>
Nazwa funkcji elementu członkowskiego.

*vtRetVal ( vtRetVal )*<br/>
Wartość określająca typ zwracany funkcji.

*vtsParams ( vtsParams )*<br/>
Oddzielona spacja lista jednej lub więcej stałych określających listę parametrów funkcji.

### <a name="remarks"></a>Uwagi

Argument *vtRetVal* jest typu VARTYPE. Następujące możliwe wartości dla tego argumentu są pobierane z wyliczenia: `VARENUM`

|Symbol|Zwracany typ|
|------------|-----------------|
|Vt_empty|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|Vt_bstr|Bstr|
|VT_DISPATCH|LPDISPATCH ( LPDISPATCH )|
|VT_ERROR|SCODE|
|VT_BOOL|Bool|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*VtsParams* argument jest oddzielona spacja lista `VTS_*` wartości ze stałych. Jedna lub więcej z tych wartości oddzielonych spacjami (nie przecinkami) określa listę parametrów funkcji. Na przykład:

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

określa listę zawierającą krótką liczbę całkowitą, po której następuje wskaźnik do krótkiej liczby całkowitej.

Stałe `VTS_` i ich znaczenie są następujące:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` lub `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH ( LPDISPATCH )|
|VTS_SCODE|SCODE|
|VTS_BOOL|Bool|
|VTS_VARIANT|`const VARIANT*` lub `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__Krótki\*__|
|VTS_PI4|__Długi\*__|
|VTS_PR4|__float\*__|
|VTS_PR8|__double\*__|
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

**Nagłówek:** afxdisp.h

## <a name="disp_property"></a><a name="disp_property"></a>DISP_PROPERTY

Definiuje właściwość automatyzacji OLE na mapie wysyłki.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Nazwa klasy.

*pszName (Nazwa psz)*<br/>
Nazwa zewnętrzna właściwości.

*Membername*<br/>
Nazwa zmiennej członkowskiej, w której przechowywana jest właściwość.

*vtPropType (Typ vtPropType)*<br/>
Wartość określająca typ właściwości.

### <a name="remarks"></a>Uwagi

Argument *vtPropType* jest typu **VARTYPE**. Możliwe wartości dla tego argumentu są pobierane z wyliczenia VARENUM:

|Symbol|Typ właściwości|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|Vt_bstr|`CString`|
|VT_DISPATCH|LPDISPATCH ( LPDISPATCH )|
|VT_ERROR|SCODE|
|VT_BOOL|Bool|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Gdy klient zewnętrzny zmienia właściwość, zmienia się wartość zmiennej członkowskiej określonej przez *memberName;* nie ma powiadomienia o zmianie.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX

Definiuje właściwość automatyzacji OLE i nazwę funkcji używanych do uzyskania i ustawić wartość właściwości w mapie wysyłki.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Nazwa klasy.

*pszName (Nazwa psz)*<br/>
Nazwa zewnętrzna właściwości.

*członekGet*<br/>
Nazwa funkcji elementu członkowskiego używanej do uzyskania właściwości.

*memberSet*<br/>
Nazwa funkcji elementu członkowskiego używanej do ustawiania właściwości.

*vtPropType (Typ vtPropType)*<br/>
Wartość określająca typ właściwości.

### <a name="remarks"></a>Uwagi

Funkcje *memberGet* i *memberSet* mają podpisy określone przez argument *vtPropType.* Funkcja *memberGet* nie przyjmuje żadnych argumentów i zwraca wartość typu określonego przez *vtPropType*. Funkcja *memberSet* przyjmuje argument typu określonego przez *vtPropType* i nic nie zwraca.

Argument *vtPropType* jest typu VARTYPE. Możliwe wartości dla tego argumentu są pobierane z wyliczenia VARENUM. Aby uzyskać listę tych wartości, zobacz Uwagi dla parametru *vtRetVal* w [DISP_FUNCTION](#disp_function). Należy zauważyć, że VT_EMPTY, wymienione w DISP_FUNCTION uwagi, nie jest dozwolone jako typ danych właściwości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Definiuje właściwość automatyzacji OLE z powiadomieniem na mapie wysyłki.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Nazwa klasy.

*szExternalName*<br/>
Nazwa zewnętrzna właściwości.

*Membername*<br/>
Nazwa zmiennej członkowskiej, w której przechowywana jest właściwość.

*pfnAfterSet (Zestaw)*<br/>
Nazwa funkcji powiadomień dla *szExternalName*.

*vtPropType (Typ vtPropType)*<br/>
Wartość określająca typ właściwości.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do właściwości zdefiniowanych za pomocą DISP_PROPERTY, właściwość zdefiniowana za pomocą DISP_PROPERTY_NOTIFY automatycznie wywoła funkcję określoną przez *pfnAfterSet* po zmianie właściwości.

Argument *vtPropType* jest typu VARTYPE. Możliwe wartości dla tego argumentu są pobierane z wyliczenia VARENUM:

|Symbol|Typ właściwości|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|Vt_bstr|`CString`|
|VT_DISPATCH|LPDISPATCH ( LPDISPATCH )|
|VT_ERROR|SCODE|
|VT_BOOL|Bool|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_property_param"></a><a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Definiuje właściwość dostęp do `Get` `Set` funkcji oddzielnych i elementów członkowskich.

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

*klasa*<br/>
Nazwa klasy.

*pszExternalName*<br/>
Nazwa zewnętrzna właściwości.

*pfnGet (angielski)*<br/>
Nazwa funkcji elementu członkowskiego używanej do uzyskania właściwości.

*zestaw pfnSet*<br/>
Nazwa funkcji elementu członkowskiego używanej do ustawiania właściwości.

*vtPropType (Typ vtPropType)*<br/>
Wartość określająca typ właściwości.

*vtsParams ( vtsParams )*<br/>
Ciąg typów parametrów `VTS_*` wariantu oddzielonych odstępami, po jednym dla każdego parametru.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do makra DISP_PROPERTY_EX, to makro umożliwia określenie listy parametrów właściwości. Jest to przydatne do implementowania właściwości, które są indeksowane lub sparametryzowane.

### <a name="example"></a>Przykład

Należy wziąć pod uwagę następującą deklarację get i set funkcji członkowskich, które umożliwiają użytkownikowi żądanie określonego wiersza i kolumny podczas uzyskiwania dostępu do właściwości:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Odpowiadają one następującym makro DISP_PROPERTY_PARAM na mapie wysyłki sterowania:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Jako inny przykład należy wziąć pod uwagę następujące funkcje elementów członkowskich get i set:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Odpowiadają one następującym makro DISP_PROPERTY_PARAM na mapie wysyłki sterowania:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE

Sprawia, że istniejąca właściwość jest wartością domyślną obiektu.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Nazwa klasy.

*pszName (Nazwa psz)*<br/>
Nazwa zewnętrzna właściwości, która reprezentuje "wartość" obiektu.

### <a name="remarks"></a>Uwagi

Użycie wartości domyślnej może ułatwić programowanie obiektu automatyzacji w aplikacjach języka Visual Basic.

"Wartość domyślna" obiektu jest właściwość, która jest pobierana lub ustawiana, gdy odwołanie do obiektu nie określa właściwości lub funkcji elementu członkowskiego.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
