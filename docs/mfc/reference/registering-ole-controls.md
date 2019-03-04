---
title: Rejestrowanie formantów OLE
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.ole
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9c480696bdec3591f0509cbad04051a2b3af4070
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262158"
---
# <a name="registering-ole-controls"></a>Rejestrowanie formantów OLE

Formanty OLE, podobnie jak inne obiekty serwera OLE, jest możliwy przez inne aplikacje OLE-aware. Jest to osiągane przez zarejestrowanie biblioteki typów i klasy kontrolki.

Następujące funkcje umożliwiają dodawanie i usuwanie formantu klasy strony właściwości i biblioteki typów w bazie danych rejestracji Windows:

### <a name="registering-ole-controls"></a>Rejestrowanie formantów OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Dodaje klasę formantu w bazie danych rejestracji.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Dodaje strony właściwości formantu w bazie danych rejestracji.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Dodaje bibliotekę typów formantu do bazy danych rejestracji.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Usuwa z bazy danych rejestracji klasy formantu lub klasy strony właściwości.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Usuwa biblioteki typu formantu z bazy danych rejestracji.|

`AfxOleRegisterTypeLib` zwykle jest wywoływana w celu wykonania Biblioteka DLL formantów `DllRegisterServer`. Podobnie `AfxOleUnregisterTypeLib` jest wywoływana przez `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, i `AfxOleUnregisterClass` są zwykle nazywane `UpdateRegistry` funkcji składowej klasy formantu strony fabryki lub właściwość.

##  <a name="afxoleregistercontrolclass"></a>  Afxoleregistercontrolclass —

Rejestruje klasy kontrolek Windows bazy danych rejestracji.

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
Dojście wystąpienia modułu, który został skojarzony z klasą formantu.

*Identyfikator klasy*<br/>
Identyfikator unikatowy klasy kontrolki.

*pszProgID*<br/>
Unikatowy identyfikator kontrolki.

*idTypeName*<br/>
Identyfikator zasobu ciągu, który zawiera nazwę typu czytelny dla użytkownika, dla formantu.

*idBitmap*<br/>
Identyfikator zasobu mapy bitowej wykorzystywany do reprezentowania kontrolki OLE na pasku narzędzi lub palety.

*nRegFlags*<br/>
Zawiera co najmniej jeden z następujących flag:

- `afxRegInsertable` Zapewnia kontrolę pojawią się w oknie dialogowym Wstaw obiekt dla obiektów OLE.

- `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze, aby ThreadingModel = typu Apartment.

- `afxRegFreeThreading` Ustawia model wątkowości w rejestrze, aby ThreadingModel = bezpłatna.

   Można połączyć dwie flagi `afxRegApartmentThreading` i `afxRegFreeThreading` można ustawić ThreadingModel = jednocześnie. Zobacz [InprocServer32](/windows/desktop/com/inprocserver32) w zestawie SDK Windows, aby uzyskać więcej informacji na temat rejestracji modelu wątkowości.

> [!NOTE]
>  W wersjach MFC przed MFC 4.2 **int** *nRegFlags* parametr jest parametrem BOOL *bInsertable*, który dozwolone lub niedozwolone formant, który ma zostać wstawiony z Insert Okno dialogowe obiektów.

*dwMiscStatus*<br/>
Zawiera co najmniej jeden z następujących flag stanu (Aby uzyskać opis flagi, zobacz wyliczenie OLEMISC w zestawie Windows SDK):

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
Unikatowy identyfikator klasy kontrolki.

*wVerMajor*<br/>
Główny numer wersji klasy kontrolki.

*wVerMinor*<br/>
Pomocniczy numer wersji klasy kontrolki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli klasa sterowania został zarejestrowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dzięki temu formant, który ma być używany przez kontenerów, które są OLE-control. `AfxOleRegisterControlClass` aktualizuje rejestr przy użyciu nazwy i lokalizacji w systemie kontrolki, a także ustawia model wątków, które są obsługiwane przez kontrolkę w rejestrze. Aby uzyskać więcej informacji, zobacz [techniczne Pamiętaj, że 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Komórkowy Model wątkowości w OLE kontrolek" i [o procesy i wątki](/windows/desktop/ProcThread/about-processes-and-threads) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

W powyższym przykładzie pokazano, jak `AfxOleRegisterControlClass` jest wywoływana z flagą dla Wstawianie i flagi dla typu apartment modelu operacja logiczna ze sobą, aby utworzyć szóstego parametru:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Kontrolki pojawią się w oknie dialogowym Wstaw obiekt włączonych kontenerów, a zostanie on rozpoznające model. Kontrolki obsługującej modelu typu apartment upewnij tej klasy statycznej, które dane są chronione przez blokad, tak, aby podczas kontroli w jednym apartamentu uzyskuje dostęp do danych statycznych, nie jest ona wyłączona przez harmonogram, zanim zostanie zakończone, a inne wystąpienie tej samej klasy, który rozpoczyna się przy użyciu te same dane statyczne. Wszelkie dostęp do danych statycznych, zostanie on otoczony przez sekcję krytyczną kod.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="afxoleregisterpropertypageclass"></a>  Afxoleregisterpropertypageclass —

Rejestruje klasy strony właściwości z bazy danych rejestracji Windows.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście wystąpienia modułu, który został skojarzony z klasy strony właściwości.

*Identyfikator klasy*<br/>
Identyfikator unikatowy klasy strony właściwości.

*idTypeName*<br/>
Identyfikator zasobu ciągu, który zawiera nazwę czytelny dla użytkownika na stronie właściwości.

*nRegFlags*<br/>
Może zawierać flagi:

- `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze, aby ThreadingModel = typu Apartment.

> [!NOTE]
>  W wersjach MFC przed MFC 4.2 **int** *nRegFlags* parametr nie jest dostępna. Należy zauważyć, że `afxRegInsertable` flaga nie jest prawidłową opcją dla strony właściwości i będą powodować ASERCJA w MFC, jeśli jest ustawiona

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli klasa sterowania został zarejestrowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pozwala to na stronie właściwości, który będzie używany przez kontenerów, które są OLE — formant. `AfxOleRegisterPropertyPageClass` aktualizuje rejestr przy użyciu nazwy strony właściwości i jego lokalizacji w systemie, a także ustawia model wątków, które są obsługiwane przez kontrolkę w rejestrze. Aby uzyskać więcej informacji, zobacz [techniczne Pamiętaj, że 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Komórkowy Model wątkowości w OLE kontrolek" i [o procesy i wątki](/windows/desktop/ProcThread/about-processes-and-threads) w zestawie Windows SDK.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="afxoleregistertypelib"></a>  Afxoleregistertypelib —

Rejestruje bibliotekę typów z bazą danych programu Windows rejestracji i umożliwia biblioteki typów, który będzie używany przez inne kontenery, które są OLE-control.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście wystąpienia aplikacji skojarzony z biblioteki typów.

*tlid*<br/>
Unikatowy identyfikator biblioteki typów.

*pszFileName*<br/>
Wskazuje opcjonalna nazwa pliku biblioteki typów zlokalizowane (. Plik TLB) dla formantu.

*pszHelpDir*<br/>
Nazwa katalogu, gdzie można znaleźć w pliku pomocy biblioteki typów. Jeśli ma wartość NULL, w pliku pomocy zakłada się, że w tym samym katalogu co sama biblioteka typów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli biblioteka typów została zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja aktualizuje rejestr przy użyciu nazwy biblioteki typów i jego lokalizacji w systemie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass

Usuwa wpis klasy strony formantu lub właściwości z bazy danych rejestracji Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Parametry

*clsID*<br/>
Identyfikator unikatowy klasy strony formantu lub właściwości.

*pszProgID*<br/>
Unikatowy identyfikator strony formantu lub właściwości.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli klasa strony formantu lub właściwości został pomyślnie wyrejestrowany; w przeciwnym razie 0.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib

Wywołaj tę funkcję, aby usunąć wpis biblioteki typów z bazy danych rejestracji Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Parametry

*tlID*<br/>
Unikatowy identyfikator biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli biblioteka typów został pomyślnie wyrejestrowany; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdisp.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
