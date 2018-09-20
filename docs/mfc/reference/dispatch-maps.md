---
title: Mapy wysyłania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d22c94513e80c4f353de9e10588f219a2d3be92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388074"
---
# <a name="dispatch-maps"></a>Mapy wysyłania

Automatyzacji OLE zapewnia metody do wywołania metod i uzyskiwania dostępu do właściwości w aplikacjach. Mechanizm dostarczonych przez bibliotekę Microsoft Foundation Class dla wysyła te żądania jest "map wysyłania," które wyznacza wewnętrznych i zewnętrznych nazwy obiektu funkcji i właściwości, a także typy danych właściwości sobą i z argumenty funkcji.

|Makra mapy wysyłania|Opis|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Deklaruje, że mapa wysyłania będzie służyć do udostępnienia klasy, metody i właściwości (muszą być używane w deklaracji klasy).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Uruchamia definicji mapy wysyłania.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Kończy definicję Mapa wysyłania.|
|[DISP_FUNCTION](#disp_function)|Używane w mapie wysyłania do definiowania funkcji automatyzacji OLE.|
|[DISP_PROPERTY](#disp_property)|Definiuje właściwości automatyzacji OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Definiuje właściwości automatyzacji OLE i nazwy funkcje Get i Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Definiuje właściwości automatyzacji OLE z powiadomieniem.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Definiuje właściwości automatyzacji OLE, która przyjmuje parametry i nazwy funkcje Get i Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Sprawia, że istniejącej właściwości wartość domyślna obiektu.|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

Jeśli `CCmdTarget`-klasy pochodnej w programach obsługuje automatyzacji OLE, że klasa musi dostarczać mapy wysyłania w celu udostępnienia metod i właściwości.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Uwagi

Użyj DECLARE_DISPATCH_MAP — makro na końcu deklaracją klasy. Następnie w. Plik CPP, który definiuje funkcji elementów członkowskich dla tej klasy, użyj BEGIN_DISPATCH_MAP — makro. Następnie Dołącz — makro wpisy dla każdej metody narażonych swojej klasy i właściwości (DISP_FUNCTION DISP_PROPERTY i tak dalej). Na koniec użyj END_DISPATCH_MAP — makro.

> [!NOTE]
> Przy deklarowaniu wszystkie elementy członkowskie po DECLARE_DISPATCH_MAP należy określić nowy typ dostępu ( **publicznych**, **prywatnej**, lub **chronione**) dla nich.

Kreatorzy Kreatora aplikacji i kodu pomagają w klasy automatyzacji tworzenia i utrzymywania mapy wysyłania. Aby uzyskać więcej informacji na temat mapy wysyłania, zobacz [serwerów automatyzacji](../../mfc/automation-servers.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="begin_dispatch_map"></a>  BEGIN_DISPATCH_MAP

Deklaruje definicji mapy wysyłania.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy, która jest właścicielem tej mapy wysyłania.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcji elementów członkowskich dla swojej klasy rozpoczynać Mapa wysyłania BEGIN_DISPATCH_MAP — makro, Dodaj makro wpisy dla każdej właściwości i funkcji wysyłania i ukończyć mapy wysyłania za pomocą END_DISPATCH_ Makra mapy.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="end_dispatch_map"></a>  END_DISPATCH_MAP

Kończy definicję mapy wysyłania.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Uwagi

Musi być używany w połączeniu z BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_function"></a>  DISP_FUNCTION

Definiuje funkcję automatyzacji OLE w postaci mapy wysyłania.

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
Nazwa funkcji elementu członkowskiego.

*vtRetVal*<br/>
Wartość, określając typ zwracany przez funkcję.

*vtsParams*<br/>
Rozdzielonej spacjami listy co najmniej jedną stałą, określając listę parametrów funkcji.

### <a name="remarks"></a>Uwagi

*VtRetVal* argument jest typu VARTYPE. Następujące możliwe wartości dla tego argumentu są pobierane z `VARENUM` wyliczenia:

|Symbol|Zwracany typ|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATA|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|WARTOŚĆ LOGICZNA|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*VtsParams* argument jest rozdzielonej spacjami listy wartości z `VTS_*` stałe. Co najmniej jeden z tych wartości, rozdzielone spacjami (nie przecinki) określa listę parametrów funkcji. Na przykład

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

Określa listę zawierającą krótka liczba całkowita, następuje wskaźnik do krótka liczba całkowita.

`VTS_` Stałe i ich znaczenie są następujące:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` lub `CY*`|
|VTS_DATE|DATA|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|WARTOŚĆ LOGICZNA|
|VTS_VARIANT|`const VARIANT*` lub `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__Krótka\*__|
|VTS_PI4|__długi\*__|
|VTS_PR4|__float\*__|
|VTS_PR8|__Podwójne\*__|
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

## <a name="disp_property"></a>  DISP_PROPERTY

Definiuje właściwości automatyzacji OLE w postaci mapy wysyłania.

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
Nazwa zmiennej składowej, w którym przechowywany jest właściwość.

*vtPropType*<br/>
Wartość, określając typ właściwości.

### <a name="remarks"></a>Uwagi

*VtPropType* argument jest typu **VARTYPE**. Możliwe wartości dla tego argumentu są pobierane z wyliczenia VARENUM:

|Symbol|Typ właściwości|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATA|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|WARTOŚĆ LOGICZNA|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Zmiany właściwości, wartość zmiennej składowej, określony przez klienta zewnętrznego *memberName* zmiany; nie jest prezentowane żadne powiadomienie o zmianie.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

Definiuje właściwości automatyzacji OLE i nazwy funkcje służące do pobierania i ustawiania wartości właściwości w mapie wysyłania.

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
Nazwa funkcji składowej, używany do pobrania właściwości.

*zestaw elementów członkowskich*<br/>
Nazwa używana do ustawiania właściwości funkcji elementu członkowskiego.

*vtPropType*<br/>
Wartość, określając typ właściwości.

### <a name="remarks"></a>Uwagi

*MemberGet* i *zestaw elementów członkowskich* funkcje mają podpisy ustalany na podstawie *vtPropType* argumentu. *MemberGet* funkcja nie przyjmuje żadnych argumentów i zwraca wartość typu określonego przez *vtPropType*. *Zestaw elementów członkowskich* funkcja przyjmuje argument typu określonego przez *vtPropType* i zwraca wartość nothing.

*VtPropType* argument jest typu VARTYPE. Możliwe wartości dla tego argumentu są pobierane z wyliczenia VARENUM. Aby uzyskać listę tych wartości, zobacz uwagi dla *vtRetVal* parametru w [DISP_FUNCTION](#disp_function). Pamiętaj, że VT_EMPTY, uwagi DISP_FUNCTION na liście nie jest dozwolona jako typ danych właściwości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

Definiuje właściwości automatyzacji OLE z powiadomieniem Mapa wysyłania.

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
Nazwa zmiennej składowej, w którym przechowywany jest właściwość.

*pfnAfterSet*<br/>
Nazwa funkcji powiadomień dla *szExternalName*.

*vtPropType*<br/>
Wartość, określając typ właściwości.

### <a name="remarks"></a>Uwagi

W odróżnieniu od właściwości zdefiniowane za pomocą DISP_PROPERTY właściwości zdefiniowane za pomocą DISP_PROPERTY_NOTIFY będzie automatycznie wywoływać funkcji określonej przez *pfnAfterSet* po zmianie właściwości.

*VtPropType* argument jest typu VARTYPE. Możliwe wartości dla tego argumentu są pobierane z wyliczenia VARENUM:

|Symbol|Typ właściwości|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATA|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|WARTOŚĆ LOGICZNA|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_property_param"></a>  DISP_PROPERTY_PARAM

Definiuje właściwość uzyskuje się z oddzielnych `Get` i `Set` funkcji elementów członkowskich.

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
Nazwa funkcji składowej, używany do pobrania właściwości.

*pfnSet*<br/>
Nazwa używana do ustawiania właściwości funkcji elementu członkowskiego.

*vtPropType*<br/>
Wartość, określając typ właściwości.

*vtsParams*<br/>
Ciąg rozdzielonych spacjami `VTS_*` typów parametru variant, jeden dla każdego parametru.

### <a name="remarks"></a>Uwagi

W odróżnieniu od DISP_PROPERTY_EX — makro tego makra pozwala określić listę parametrów dla właściwości. Jest to przydatne do implementowania właściwości, które są indeksowane lub sparametryzowany.

### <a name="example"></a>Przykład

Rozważmy następującą deklarację get i funkcje, które umożliwiają użytkownikowi żądanie określonych wierszy i kolumn podczas uzyskiwania dostępu do właściwości elementu członkowskiego zestawu:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Odpowiadają one następujące DISP_PROPERTY_PARAM — makro kontrolki mapy wysyłania:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Inny przykład należy wziąć pod uwagę następujące get i elementu członkowskiego zestawu funkcji:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Odpowiadają one następujące DISP_PROPERTY_PARAM — makro kontrolki mapy wysyłania:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

Sprawia, że istniejącej właściwości wartość domyślna obiektu.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy.

*pszName*<br/>
Zewnętrzna nazwa właściwości, który reprezentuje "wartość" obiektu.

### <a name="remarks"></a>Uwagi

Przy użyciu wartości domyślnej ułatwia programowanie obiektu automatyzacji łatwiejsze w przypadku aplikacji Visual Basic.

"Wartość domyślna" obiektu jest właściwością, która jest pobrać lub ustawić, gdy odwołanie do obiektu nie określa właściwości lub funkcji składowej.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
