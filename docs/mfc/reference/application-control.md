---
title: Sterowanie aplikacjami
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 1f438d3344e90a16def2bd4c0f9cedcd47a64203
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363553"
---
# <a name="application-control"></a>Sterowanie aplikacjami

Ole wymaga znacznej kontroli nad aplikacjami i ich obiektów. Biblioteki DLL systemu OLE muszą być w stanie automatycznie uruchamiać i zwalniać aplikacje, koordynować ich produkcję i modyfikację obiektów i tak dalej. Funkcje w tym temacie spełniają te wymagania. Oprócz wywoływania przez biblioteki DLL systemu OLE, te funkcje muszą być czasami wywoływane przez aplikacje, jak również.

### <a name="application-control"></a>Sterowanie aplikacjami

|||
|-|-|
|[AfxOleCanExitApp (AfxOleCanExitApp)](#afxolecanexitapp)|Wskazuje, czy aplikacja może zakończyć działanie.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Pobiera filtr bieżących wiadomości aplikacji.|
|[AfxOleGetUserCtrl (AfxOleGetUserCtrl)](#afxolegetuserctrl)|Pobiera bieżącą flagę kontroli użytkownika.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Ustawia lub czyści flagę kontroli użytkownika.|
|[AfxOleLockApp ( AfxOleLockApp )](#afxolelockapp)|Zwiększa globalną liczbę struktur liczby aktywnych obiektów w aplikacji.|
|[AfxOleLockControl](#afxolelockcontrol)| Blokuje fabrykę klasy określonego formantu. |
|[AfxOleUnlockApp (AfxOleUnlockApp)](#afxoleunlockapp)|Zmniejsza liczbę framework liczba aktywnych obiektów w aplikacji.|
|[AfxOleUnlockControl (Kontrola AfxOleUnlock)](#afxoleunlockcontrol)| Odblokowuje fabrykę klasy określonego formantu. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Rejestruje serwer w rejestrze systemu OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementuje interfejs użytkownika dla polecenia Object *nazwa typu.*|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp (AfxOleCanExitApp)

Wskazuje, czy aplikacja może zakończyć działanie.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli aplikacja może wyjść; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja nie powinna zakończyć się, jeśli istnieją zaległe odwołania do jego obiektów. Globalne `AfxOleLockApp` funkcje `AfxOleUnlockApp` i przyrost i dekrementacji, odpowiednio, licznik odwołań do obiektów aplikacji. Aplikacja nie powinna kończyć się, gdy ten licznik jest niezerowy. Jeśli licznik jest niezerowy, okno główne aplikacji jest ukryte (nie zniszczone), gdy użytkownik wybierze Opcję Zamknij z menu systemowego lub Zakończ z menu Plik. Struktura wywołuje tę `CFrameWnd::OnClose`funkcję w .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

Pobiera filtr bieżących wiadomości aplikacji.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego filtru wiadomości.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, `COleMessageFilter`aby uzyskać dostęp do bieżącego obiektu pochodnego, tak jak wywołać, `AfxGetApp` aby uzyskać dostęp do bieżącego obiektu aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxwin.h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl (AfxOleGetUserCtrl)

Pobiera bieżącą flagę kontroli użytkownika.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli użytkownik ma kontrolę nad aplikacją; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użytkownik ma kontrolę nad aplikacją, gdy użytkownik jawnie otworzył lub utworzył nowy dokument. Użytkownik ma również kontrolę, jeśli aplikacja nie została uruchomiona przez biblioteki DLL systemu OLE — innymi słowy, jeśli użytkownik uruchomił aplikację z powłoką systemową.

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Ustawia lub czyści flagę kontroli użytkownika, co jest `AfxOleGetUserCtrl`wyjaśnione w odwołaniu do .

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parametry

*bUserCtrl*<br/>
Określa, czy flaga kontroli użytkownika ma być ustawiona, czy wyczyszczona.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję, gdy użytkownik tworzy lub ładuje dokument, ale nie wtedy, gdy dokument jest ładowany lub tworzony za pomocą akcji pośredniej, takiej jak ładowanie osadzonego obiektu z aplikacji kontenera.

Wywołanie tej funkcji, jeśli inne akcje w aplikacji należy umieścić użytkownika w kontroli aplikacji.

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a>AfxOleLockApp ( AfxOleLockApp )

Zwiększa globalną liczbę struktury liczby aktywnych obiektów w aplikacji.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Uwagi

Struktura przechowuje liczbę obiektów aktywnych w aplikacji. I `AfxOleLockApp` `AfxOleUnlockApp` funkcje, odpowiednio, przyrost i zmniejszania tej liczby.

Gdy użytkownik próbuje zamknąć aplikację, która ma aktywne obiekty — aplikacja, dla której liczba aktywnych obiektów jest niezerowa — struktura ukrywa aplikację z widoku użytkownika, zamiast całkowicie ją zamknąć. Funkcja `AfxOleCanExitApp` wskazuje, czy aplikacja może zakończyć.

Wywołanie `AfxOleLockApp` z dowolnego obiektu, który udostępnia interfejsów OLE, jeśli byłoby niepożądane dla tego obiektu, które mają zostać zniszczone, podczas gdy nadal jest używany przez aplikację kliencką. Również `AfxOleUnlockApp` wywołać w destruktora `AfxOleLockApp` dowolnego obiektu, który wywołuje w konstruktorze. Domyślnie `COleDocument` (i klasy pochodne) automatycznie zablokować i odblokować aplikację.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOleUnlockApp (AfxOleUnlockApp)

Zmniejsza liczbę aktywnych obiektów w aplikacji.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Uwagi

Zobacz `AfxOleLockApp` więcej informacji.

Gdy liczba aktywnych obiektów osiągnie `AfxOleOnReleaseAllObjects` zero, jest wywoływana.

### <a name="example"></a>Przykład

Zobacz przykład [afxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Blokuje fabrykę klasy określonego formantu, dzięki czemu dynamicznie utworzone dane skojarzone z formantem pozostają w pamięci.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Unikatowy identyfikator klasy formantu.

*lpszProgID*<br/>
Unikatowy identyfikator programu formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli fabryka klasy formantu została pomyślnie zablokowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Może to znacznie przyspieszyć wyświetlanie elementów sterujących. Na przykład po utworzeniu formantu w oknie `AfxOleLockControl`dialogowym i zablokowaniu formantu za pomocą programu , nie trzeba go tworzyć i zabijać ponownie za każdym razem, gdy okno dialogowe jest wyświetlane lub niszczone. Jeśli użytkownik otwiera i zamyka okno dialogowe wielokrotnie, blokowanie formantów może znacznie zwiększyć wydajność. Gdy będziesz gotowy do zniszczenia `AfxOleUnlockControl`formantu, zadzwoń .

### <a name="example"></a>Przykład

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

Ta funkcja umożliwia zarejestrowanie serwera w rejestrze systemu OLE.

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Odwołanie do identyfikatora klasy OLE serwera.

*lpszClassName (nazwa klasy)*<br/>
Wskaźnik do ciągu zawierającego nazwę klasy obiektów serwera.

*lpszShortTypeName*<br/>
Wskaźnik do ciągu zawierającego krótką nazwę typu obiektu serwera, na przykład "Wykres".

*lpszLongTypeName*<br/>
Wskaźnik do ciągu zawierającego długą nazwę typu obiektu serwera, na przykład "Microsoft Excel 5.0 Chart".

*n Typ aplikacji*<br/>
Wartość, pobrana z OLE_APPTYPE wyliczenia, określając typ aplikacji OLE. Możliwe wartości są następujące:

- OAT_INPLACE_SERVER Server ma pełny interfejs użytkownika serwera.

- OAT_SERVER Serwer obsługuje tylko osadzanie.

- OAT_CONTAINER Container obsługuje łącza do osadzania.

- OAT_DISPATCH_OBJECT `IDispatch`obiekt.

*rglpszRegister*<br/>
Tablica wskaźników do ciągów reprezentujących klucze i wartości, które mają zostać dodane do rejestru systemu OLE, jeśli nie zostaną znalezione żadne istniejące wartości kluczy.

*rglpszOverwrite*<br/>
Tablica wskaźników do ciągów reprezentujących klucze i wartości, które mają zostać dodane do rejestru systemu OLE, jeśli rejestr zawiera istniejące wartości dla danych kluczy.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli klasa serwera jest pomyślnie zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Większość aplikacji `COleTemplateServer::Register` może używać do rejestrowania typów dokumentów aplikacji. Jeśli format rejestru systemowego aplikacji nie pasuje do typowego `AfxOleRegisterServerClass` wzorca, można użyć dla większej kontroli.

Rejestr składa się z zestawu kluczy i wartości. Argumenty *rglpszRegister* i *rglpszOverwrite* są tablicami wskaźników do ciągów, z których każdy składa się `'\0'`z klucza i wartości oddzielonej znakiem **NULL** ( ). Każdy z tych ciągów może mieć wymienne parametry, których miejsca są oznaczone sekwencjami znaków *od %1* do *%5*.

Symbole są wypełniane w następujący sposób:

|Symbol|Wartość|
|------------|-----------|
|%1|Identyfikator klasy sformatowany jako ciąg znaków|
|%2|Nazwa klasy|
|%3|Ścieżka do pliku wykonywalnego|
|%4|Krótka nazwa typu|
|%5|Długa nazwa typu|

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

Implementuje interfejs użytkownika dla polecenia Object *nazwa typu.*

```
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>Parametry

*pClient (właswoić)*<br/>
Wskaźnik do elementu OLE klienta.

*pMenu*<br/>
Wskaźnik do obiektu menu, który ma zostać zaktualizowany.

*Imenuitem*<br/>
Indeks elementu menu, który ma zostać zaktualizowany.

*nIDVerbMin*<br/>
Identyfikator polecenia, który odpowiada czasownikowi podstawowemu.

*nIDVerbMax*<br/>
Identyfikator polecenia, który odpowiada ostatniemu czasownikowi.

*nIDKonwert*<br/>
Identyfikator elementu menu Konwertuj.

### <a name="remarks"></a>Uwagi

Jeśli serwer rozpoznaje tylko zlecenie podstawowe, element menu staje się *"typename* zlecenie" i polecenie *nIDVerbMin* jest wysyłane, gdy użytkownik wybierze polecenie. Jeśli serwer rozpoznaje kilka zleceń, element menu staje się *"typename* Object", a podmenu zawierający listę wszystkich zleceń pojawia się, gdy użytkownik wybierze polecenie. Gdy użytkownik wybierze zlecenie z podmenu, *nIDVerbMin* jest wysyłany, jeśli wybrano pierwszy zlecenie, *nIDVerbMin* + 1 jest wysyłany, jeśli wybrano drugi czasownik i tak dalej. Domyślna `COleDocument` implementacja automatycznie obsługuje tę funkcję.

W skrypcie zasobów aplikacji klienta musi być niżej ściela się instrukcja (. RC) plik:

**#include \<afxolecl.rc>**

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxole.h

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a>AfxOleUnlockControl (Kontrola AfxOleUnlock)

Odblokowuje fabrykę klasy określonego formantu.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Unikatowy identyfikator klasy formantu.

*lpszProgID*<br/>
Unikatowy identyfikator programu formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli fabryka klasy formantu została pomyślnie odblokowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Formant jest zablokowany `AfxOleLockControl`za pomocą , dzięki czemu dynamicznie utworzone dane skojarzone z formantem pozostają w pamięci. Może to znacznie przyspieszyć wyświetlanie formantu, ponieważ formant nie musi być tworzony i niszczony za każdym razem, gdy jest wyświetlany. Gdy będziesz gotowy do zniszczenia `AfxOleUnlockControl`formantu, zadzwoń .

### <a name="example"></a>Przykład

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)<br/>
