---
title: Rejestrowanie formantów OLE
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 2f2d7872e8b9369b5eef283e5b52a54c29afd563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372970"
---
# <a name="registering-ole-controls"></a>Rejestrowanie formantów OLE

Formanty OLE, podobnie jak inne obiekty serwera OLE, są dostępne dla innych aplikacji obsługujących ole. Osiąga się to poprzez zarejestrowanie biblioteki typów i klasy formantu.

Następujące funkcje umożliwiają dodawanie i usuwanie klasy formantu, stron właściwości i biblioteki typów w bazie danych rejestracji systemu Windows:

### <a name="registering-ole-controls"></a>Rejestrowanie formantów OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Dodaje klasę formantu do bazy danych rejestracji.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Dodaje stronę właściwości formantu do bazy danych rejestracji.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Dodaje bibliotekę typów formantu do bazy danych rejestracji.|
|[AfxOleUnregisterClass (Klasa AfxOleUnregister)](#afxoleunregisterclass)|Usuwa klasę formantu lub klasę strony właściwości z bazy danych rejestracji.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Usuwa bibliotekę typów formantu z bazy danych rejestracji.|

`AfxOleRegisterTypeLib`jest zazwyczaj wywoływana w implementacji dll sterowania `DllRegisterServer`. Podobnie, `AfxOleUnregisterTypeLib` jest wywoływana przez `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`i `AfxOleUnregisterClass` są zazwyczaj wywoływane przez funkcję `UpdateRegistry` elementu członkowskiego fabryki klasy formantu lub strony właściwości.

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

Rejestruje klasę formantu w bazie danych rejestracji systemu Windows.

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

*hInstance (Nieumieja)*<br/>
Dojście wystąpienia modułu skojarzonego z klasą kontrolną.

*Clsid*<br/>
Unikatowy identyfikator klasy formantu.

*pszProgID*<br/>
Unikatowy identyfikator programu formantu.

*nazwa idTypeName*<br/>
Identyfikator zasobu ciągu, który zawiera nazwę typu czytelnego dla użytkownika dla formantu.

*idBitmapa*<br/>
Identyfikator zasobu mapy bitowej używanej do reprezentowania formantu OLE na pasku narzędzi lub palecie.

*nRegSlags*<br/>
Zawiera co najmniej jedną z następujących flag:

- `afxRegInsertable`Umożliwia wyświetlenie formantu w oknie dialogowym Wstawianie obiektu dla obiektów OLE.

- `afxRegApartmentThreading`Ustawia model wątków w rejestrze na ThreadingModel=Apartment.

- `afxRegFreeThreading`Ustawia model wątków w rejestrze na ThreadingModel=Free.

   Można połączyć dwie `afxRegApartmentThreading` `afxRegFreeThreading` flagi i ustawić ThreadingModel=Both. Zobacz [InprocServer32](/windows/win32/com/inprocserver32) w windows SDK, aby uzyskać więcej informacji na temat rejestracji modelu wątkowości.

> [!NOTE]
> W wersjach MFC przed MFC 4.2 parametr **int** *nRegFlags* był parametrem BOOL, *bInsertable*, który zezwalał lub wyłączał wstawianie formantu z okna dialogowego Wstawianie obiektu.

*dwMiscStatus (Stan dwMisc)*<br/>
Zawiera co najmniej jedną z następujących flag stanu (opis flag można znaleźć w części Wyliczenie OLEMISC w zestaw windows SDK):

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

*tlid ( tlid )*<br/>
Unikatowy identyfikator klasy kontrolnej.

*wVerMajor*<br/>
Główny numer wersji klasy kontrolnej.

*wVerMinor*<br/>
Pomocniczy numer wersji klasy formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli klasa kontrolna została zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dzięki temu formant ma być używany przez kontenery, które są ole-control aware. `AfxOleRegisterControlClass`aktualizuje rejestr z nazwą i lokalizacją formantu w systemie, a także ustawia model wątków, który formant obsługuje w rejestrze. Aby uzyskać więcej informacji, zobacz [Uwaga techniczna 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Wątki modelu mieszkania w formantach OLE" i [Informacje o procesach i wątkach](/windows/win32/ProcThread/about-processes-and-threads) w programie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

Powyższy przykład pokazuje, jak `AfxOleRegisterControlClass` jest wywoływana z flagą do wstawiania i flagą dla modelu apartamentu ORed razem, aby utworzyć szósty parametr:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Formant pojawi się w oknie dialogowym Wstawianie obiektu dla włączonych kontenerów i będzie obsługujący model apartamentu. Formanty obsługujące model apartamentu muszą upewnić się, że dane klasy statycznej są chronione przez blokady, dzięki czemu podczas gdy formant w jednym mieszkaniu uzyskuje dostęp do danych statycznych, nie jest wyłączany przez harmonogram przed zakończeniem, a inne wystąpienie tej samej klasy rozpoczyna się przy użyciu tych samych danych statycznych. Wszelkie dostępy do danych statycznych będą otoczone kodem sekcji krytycznej.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass

Rejestruje klasę strony właściwości w bazie danych rejestracji systemu Windows.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Parametry

*hInstance (Nieumieja)*<br/>
Dojście wystąpienia modułu skojarzonego z klasą strony właściwości.

*Clsid*<br/>
Unikatowy identyfikator klasy strony właściwości.

*nazwa idTypeName*<br/>
Identyfikator zasobu ciągu, który zawiera nazwę czytelną dla użytkownika strony właściwości.

*nRegSlags*<br/>
Może zawierać flagę:

- `afxRegApartmentThreading`Ustawia model wątków w rejestrze na ThreadingModel = Apartment.

> [!NOTE]
> W wersjach MFC przed MFC 4.2 parametr **int** *nRegFlags* nie był dostępny. Należy również `afxRegInsertable` zauważyć, że flaga nie jest prawidłową opcją dla stron właściwości i spowoduje ASSERT w MFC, jeśli jest ustawiona

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli klasa kontrolna została zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dzięki temu strona właściwości do użycia przez kontenery, które są ole-control aware. `AfxOleRegisterPropertyPageClass`aktualizuje rejestr o nazwę strony właściwości i jego lokalizacji w systemie, a także ustawia model wątków, który formant obsługuje w rejestrze. Aby uzyskać więcej informacji, zobacz [Uwaga techniczna 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Wątki modelu mieszkania w formantach OLE" i [Informacje o procesach i wątkach](/windows/win32/ProcThread/about-processes-and-threads) w programie Windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

Rejestruje bibliotekę typów z bazą danych rejestracji systemu Windows i umożliwia biblioteki typów, które mają być używane przez inne kontenery, które są ole-control aware.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Parametry

*hInstance (Nieumieja)*<br/>
Dojście wystąpienia aplikacji skojarzonej z biblioteką typów.

*tlid ( tlid )*<br/>
Unikatowy identyfikator biblioteki typów.

*pszFileName*<br/>
Wskazuje opcjonalną nazwę pliku zlokalizowanej biblioteki typów (. TLB) dla formantu.

*pszHelpDir*<br/>
Nazwa katalogu, w którym można znaleźć plik pomocy dla biblioteki typów. Jeśli null, plik pomocy zakłada się, że w tym samym katalogu co sama biblioteka typów.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli biblioteka typów została zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja aktualizuje rejestr o nazwę biblioteki typów i jego lokalizację w systemie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>AfxOleUnregisterClass (Klasa AfxOleUnregister)

Usuwa wpis klasy formantu lub właściwości z bazy danych rejestracji systemu Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Unikatowy identyfikator klasy strony formantu lub właściwości.

*pszProgID*<br/>
Unikatowy identyfikator programu strony formantu lub właściwości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli klasa strony formantu lub właściwości została pomyślnie wyrejestrowana; w przeciwnym razie 0.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib

Wywołanie tej funkcji, aby usunąć wpis biblioteki typów z bazy danych rejestracji systemu Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parametry

*tlID (tlID)*<br/>
Unikatowy identyfikator biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli biblioteka typów została pomyślnie wyrejestrowana; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
