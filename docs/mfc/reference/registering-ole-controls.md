---
title: Rejestrowanie formantów OLE
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 5468f3d4b730cc0b81a6ab814d495b061d292f20
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843576"
---
# <a name="registering-ole-controls"></a>Rejestrowanie formantów OLE

Formanty OLE, podobnie jak inne obiekty serwera OLE, są dostępne dla innych aplikacji obsługujących technologię OLE. Jest to osiągane przez zarejestrowanie biblioteki typów i klasy kontrolki.

Poniższe funkcje umożliwiają dodawanie i usuwanie klasy kontrolki, stron właściwości i biblioteki typów w bazie danych rejestracji systemu Windows:

### <a name="registering-ole-controls"></a>Rejestrowanie formantów OLE

|Nazwa|Opis|
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Dodaje klasę kontrolki do bazy danych rejestracji.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Dodaje stronę właściwości kontrolki do bazy danych rejestracji.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Dodaje bibliotekę typów kontrolki do bazy danych rejestracji.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Usuwa klasę formantów lub klasę strony właściwości z bazy danych rejestracji.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Usuwa bibliotekę typów formantu z bazy danych rejestracji.|

`AfxOleRegisterTypeLib` jest zazwyczaj wywoływana w implementacji biblioteki DLL kontrolek `DllRegisterServer` . Analogicznie, `AfxOleUnregisterTypeLib` jest wywoływana przez `DllUnregisterServer` . `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass` , i `AfxOleUnregisterClass` są zwykle wywoływane przez `UpdateRegistry` funkcję członkowską fabryki klasy lub strony właściwości formantu.

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a> AfxOleRegisterControlClass

Rejestruje klasę formantów w bazie danych rejestracji systemu Windows.

```
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,
    REFCLSID clsid,
    LPCTSTR pszProgID,
    UINT idTypeName,
    UINT idBitmap,
    int nRegFlags,
    DWORD dwMiscStatus,
    REFGUID tlid,
    WORD wVerMajor,
    WORD wVerMinor);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście wystąpienia modułu skojarzonego z klasą formantów.

*Identyfikator*<br/>
Unikatowy identyfikator klasy formantu.

*pszProgID*<br/>
Unikatowy identyfikator programu kontrolki.

*idTypeName*<br/>
Identyfikator zasobu ciągu, który zawiera nazwę typu możliwy do odczytania przez użytkownika dla kontrolki.

*idBitmap*<br/>
Identyfikator zasobu mapy bitowej używany do reprezentowania kontrolki OLE na pasku narzędzi lub palecie.

*nRegFlags*<br/>
Zawiera co najmniej jedną z następujących flag:

- `afxRegInsertable` Umożliwia wyświetlenie formantu w oknie dialogowym Wstaw obiekt dla obiektów OLE.

- `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze na ThreadingModel = Apartment.

- `afxRegFreeThreading` Ustawia model wątkowości w rejestrze w taki sposób, aby ThreadingModel = Free.

   Można połączyć dwie flagi `afxRegApartmentThreading` i `afxRegFreeThreading` ustawić ThreadingModel = oba. Aby uzyskać więcej informacji na temat rejestracji modelu wątków, zobacz [InprocServer32](/windows/win32/com/inprocserver32) w Windows SDK.

> [!NOTE]
> W wersjach MFC przed MFC 4,2 **`int`** parametr *nRegFlags* był parametrem bool, *bInsertable*, który dopuszcza lub nie zezwala na wstawianie kontrolki z okna dialogowego Wstawianie obiektu.

*dwMiscStatus*<br/>
Zawiera co najmniej jedną z następujących flag stanu (Aby uzyskać opis flag, zobacz Wyliczenie OLEMISC w Windows SDK):

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
Unikatowy identyfikator klasy formantu.

*wVerMajor*<br/>
Główny numer wersji klasy kontrolki.

*wVerMinor*<br/>
Pomocniczy numer wersji klasy kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, Jeśli zarejestrowano klasę kontrolki; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pozwala to na użycie formantu przez kontenery, które są oparte na formancie OLE. `AfxOleRegisterControlClass` aktualizuje rejestr z nazwą i lokalizacją kontrolki w systemie, a także ustawia model wątkowości obsługiwany przez formant w rejestrze. Aby uzyskać więcej informacji, zobacz [Uwagi techniczne 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment-model threading in OLE Controls" i [Informacje o procesach i wątkach](/windows/win32/ProcThread/about-processes-and-threads) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

Powyższy przykład ilustruje, jak `AfxOleRegisterControlClass` jest wywoływana z flagą do wstawienia i flaga dla Apartament model logicznie razem, aby utworzyć szósty parametr:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Kontrolka zostanie wyświetlona w oknie dialogowym Wstaw obiekt dla włączonych kontenerów i będzie uwzględniać model typu Apartment. Zgodne z modelami kontrolki typu Apartment muszą zagwarantować, że dane klasy statycznej są chronione przez blokady, aby podczas gdy kontrolka w jednej z nich uzyskuje dostęp do danych statycznych, nie została wyłączona przez harmonogram, a inne wystąpienie tej samej klasy zaczyna używać tych samych danych statycznych. Wszelkie dostęp do danych statycznych będą ujęte w kodzie sekcji krytycznej.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a> AfxOleRegisterPropertyPageClass

Rejestruje klasę strony właściwości w bazie danych rejestracji systemu Windows.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście wystąpienia modułu skojarzonego z klasą strony właściwości.

*Identyfikator*<br/>
Unikatowy identyfikator klasy strony właściwości.

*idTypeName*<br/>
Identyfikator zasobu ciągu zawierającego czytelną dla użytkownika nazwę strony właściwości.

*nRegFlags*<br/>
Może zawierać flagę:

- `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze na ThreadingModel = Apartment.

> [!NOTE]
> W wersjach MFC wcześniejszych niż MFC 4,2 **`int`** parametr *nRegFlags* był niedostępny. Zwróć uwagę, że `afxRegInsertable` flaga nie jest prawidłową opcją dla stron właściwości i spowoduje, że zostanie potwierdzone w MFC, jeśli jest ustawiona

### <a name="return-value"></a>Wartość zwracana

Niezerowe, Jeśli zarejestrowano klasę kontrolki; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pozwala to na użycie strony właściwości przez kontenery, które są oparte na formancie OLE. `AfxOleRegisterPropertyPageClass` aktualizuje rejestr przy użyciu nazwy strony właściwości i jej lokalizacji w systemie, a także ustawia model wątkowości obsługiwany przez formant w rejestrze. Aby uzyskać więcej informacji, zobacz [Uwagi techniczne 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Apartment-model threading in OLE Controls" i [Informacje o procesach i wątkach](/windows/win32/ProcThread/about-processes-and-threads) w Windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a> AfxOleRegisterTypeLib

Rejestruje bibliotekę typów w bazie danych rejestracji systemu Windows i zezwala, aby biblioteka typów była używana przez inne kontenery, które są oparte na formancie OLE.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście do wystąpienia aplikacji skojarzonej z biblioteką typów.

*tlid*<br/>
Unikatowy identyfikator biblioteki typów.

*pszFileName*<br/>
Wskazuje opcjonalną nazwę pliku zlokalizowanej biblioteki typów (. TLB) dla kontrolki.

*pszHelpDir*<br/>
Nazwa katalogu, w którym można znaleźć plik pomocy dla biblioteki typów. Jeśli wartość jest równa NULL, zakłada się, że plik pomocy znajduje się w tym samym katalogu co sama biblioteka typów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli biblioteka typów została zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja aktualizuje rejestr przy użyciu nazwy biblioteki typów i jej lokalizacji w systemie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a> AfxOleUnregisterClass

Usuwa wpis klasy kontrolki lub właściwości z bazy danych rejestracji systemu Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Unikatowy identyfikator klasy kontrolki lub strony właściwości.

*pszProgID*<br/>
Unikatowy identyfikator programu na stronie kontrolki lub właściwości.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli Klasa strony kontrolki lub właściwości została pomyślnie wyrejestrowana; w przeciwnym razie 0.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a> AfxOleUnregisterTypeLib

Wywołaj tę funkcję, aby usunąć wpis biblioteki typów z bazy danych rejestracji systemu Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parametry

*tlID*<br/>
Unikatowy identyfikator biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli biblioteka typów została pomyślnie wyrejestrowana; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** AFXDISP. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
