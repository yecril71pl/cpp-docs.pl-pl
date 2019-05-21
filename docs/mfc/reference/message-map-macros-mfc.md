---
title: Makra mapy komunikatów (MFC)
ms.date: 03/27/2019
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
ms.openlocfilehash: f739dd8a74a106fb7a0e14baefcda59663ec66e0
ms.sourcegitcommit: a61d17cffdd50f1c3c6e082a01bbcbc85b6cc5a7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975124"
---
# <a name="message-map-macros-mfc"></a>Makra mapy komunikatów (MFC)

Aby zapewnić obsługę mapy komunikatów, MFC dostarcza następujące makra:

### <a name="message-map-declaration-and-demarcation-macros"></a>Mapy komunikatów deklaracja i odgraniczenie makra

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Deklaruje, używane w klasie do mapy wiadomości do funkcji (muszą być używane w deklaracji klasy) mapy komunikatów.|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Rozpoczyna się definicji mapy komunikatów (muszą być używane w implementacji klasy).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Rozpoczyna się definicji mapy komunikatów dla typu klasy zawierającego argumentu jednego szablonu. |
|[END_MESSAGE_MAP](#end_message_map)|Kończy definicję mapy komunikatów (muszą być używane w implementacji klasy).|

### <a name="message-mapping-macros"></a>Makra mapowania wiadomości

|||
|-|-|
|[ON_COMMAND](#on_command)|Wskazuje, funkcja, która będzie obsługiwać komunikat określonego polecenia.|
|[ON_COMMAND_EX](#on_command_ex)|Wskazuje, funkcja, która będzie obsługiwać komunikat określonego polecenia.|
|[ON_CONTROL](#on_control)|Wskazuje, funkcja, która będzie obsługiwać komunikat powiadamianie kontrolki.|
|[ON_MESSAGE](#on_message)|Wskazuje funkcję, która będzie obsługiwać wiadomości zdefiniowanych przez użytkownika.|
|[ON_OLECMD](#on_olecmd)|Wskazuje funkcję, która będzie obsługiwać polecenia menu z DocObject lub jego kontenera.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Wskazuje funkcję, która będzie obsługiwać zarejestrowany komunikat zdefiniowany przez użytkownika.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Wskazuje funkcję, która będzie obsługiwać zarejestrowany komunikat zdefiniowany przez użytkownika w przypadku `CWinThread` klasy.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Wskazuje, która funkcja będzie obsługiwać wiadomości zdefiniowanych przez użytkownika, w przypadku `CWinThread` klasy.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Wskazuje funkcję, która będzie obsługiwać komunikatem polecenia aktualizacji interfejsu użytkownika.|

### <a name="message-map-range-macros"></a>Makra mapy komunikatów zakresu

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Wskazuje funkcję, która będzie obsługiwać zakres identyfikatorów poleceń określony za pomocą dwóch pierwszych parametrów do makra.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Wskazuje, które procedury obsługi aktualizacji będzie obsługiwać zakres identyfikatorów poleceń określony za pomocą dwóch pierwszych parametrów do makra.|
|[ON_CONTROL_RANGE](#on_control_range)|Wskazuje, funkcja, która będzie obsługiwać powiadomienia z zakresu kontroli identyfikatory określone w parametrach drugi i trzeci do makra. Pierwszy parametr jest komunikat z powiadomieniem kontrolki, takie jak BN_CLICKED.|

Aby uzyskać więcej informacji na temat mapy komunikatów, deklaracja mapy komunikatów i odgraniczenie makr i makra mapowania wiadomości, zobacz [mapy wiadomości](../../mfc/reference/message-maps-mfc.md) i [obsługi wiadomości i tematy mapowania](../../mfc/message-handling-and-mapping.md). Aby uzyskać więcej informacji na temat zakresów map komunikatów, zobacz [programy obsługi dla zakresów Map komunikatów](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a> BEGIN_MESSAGE_MAP

Rozpoczyna się definicji mapy wiadomości.

### <a name="syntax"></a>Składnia

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy, w których wiadomość Mapuj jest.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcji elementów członkowskich dla swojej klasy rozpoczynać mapy komunikatów BEGIN_MESSAGE_MAP — makro, a następnie dodaj makro wpisy dla każdej funkcji obsługi wiadomości i ukończyć mapy komunikatów za pomocą END_MESSAGE_MAP makra.

Aby uzyskać więcej informacji na temat mapy komunikatów zobacz [mapy wiadomości](message-maps-mfc.md)

### <a name="example"></a>Przykład

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="begin_template_message_map"></a> begin_template_message_map

Rozpoczyna się definicji mapy komunikatów dla typu klasy zawierającego argumentu jednego szablonu.

### <a name="syntax"></a>Składnia

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy, w których wiadomość Mapuj jest.

*type_name*<br/>
Nazwa parametru szablonu, określony dla klasy.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

To makro jest podobny do [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) — makro; jednak to makro jest przeznaczona dla klasy zawierające argumentu jednego szablonu.

W sekcji implementacji metody klasy rozpoczynać mapy komunikatów makro BEGIN_TEMPLATE_MESSAGE_MAP; następnie dodać wpisy — makro dla poszczególnych metod obsługi wiadomości, podobnie jak w przypadku mapy komunikatów standardowych. Zgodnie z BEGIN_MESSAGE_MAP — makro, należy wykonać szablon mapy komunikatów za pomocą [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) makra.

Aby uzyskać więcej informacji dotyczących implementowania mapy komunikatów dla klasy szablonów, zobacz [jak: Tworzenie mapy komunikatów dla klasy szablonów](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="declare_message_map"></a>  DECLARE_MESSAGE_MAP

Deklaruje, że klasa definiuje mapy komunikatów. Każdy `CCmdTarget`-klasy pochodnej w swoim programie, należy podać mapy komunikatów do obsługi wiadomości.

### <a name="syntax"></a>Składnia

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Uwagi

Użyj DECLARE_MESSAGE_MAP — makro na końcu deklaracją klasy. Następnie plik .cpp, w którym zdefiniowano funkcji elementów członkowskich klasy, użyj BEGIN_MESSAGE_MAP — makro, makro wpisy dla każdej funkcji obsługi wiadomości i END_MESSAGE_MAP — makro.

> [!NOTE]
>  W przypadku dowolnego elementu członkowskiego jest zadeklarować po DECLARE_MESSAGE_MAP, należy określić nowy typ dostępu (**publicznych**, **prywatnej**, lub **chronione**) dla nich.

Aby uzyskać więcej informacji na temat mapy komunikatów i DECLARE_MESSAGE_MAP — makro, zobacz [wiadomościami i mapowanie tematów](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Przykład

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="end_message_map"></a>  END_MESSAGE_MAP

Kończy definicję mapy wiadomości.

### <a name="syntax"></a>Składnia

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat mapy komunikatów i END_MESSAGE_MAP — makro, zobacz [wiadomościami i mapowanie tematów](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="on_command"></a>  ON_COMMAND

To makro mapuje komunikatem polecenia do funkcji członkowskiej.

### <a name="syntax"></a>Składnia

```
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*commandId*<br/>
Identyfikator polecenia.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości, na który jest mapowany polecenia.

### <a name="remarks"></a>Uwagi

Oznacza to funkcja, która będzie obsługiwać komunikatem polecenia z polecenia obiektu interfejsu użytkownika, takie jak przycisk paska narzędzi lub elementu menu.

Gdy obiekt docelowy polecenia otrzymuje komunikat Windows WM_COMMAND o określonym identyfikatorze, ON_COMMAND będzie wywoływać funkcja elementu członkowskiego `memberFxn` , by obsłużyć komunikat.

ON_COMMAND umożliwia mapowanie jednego polecenia do funkcji członkowskiej. Użyj [ON_COMMAND_RANGE](#on_command_range) do mapowania zakresu identyfikatorów poleceń do funkcji jednego członka. Identyfikator polecenia może odnosić się tylko jeden wpis mapy komunikatów Oznacza to, że nie można zamapować polecenia do więcej niż jednego programu obsługi. Aby uzyskać więcej informacji i przykładów, zobacz [wiadomościami i mapowanie tematów](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Przykład

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_command_ex"></a>  ON_COMMAND_EX

Rozszerzona funkcja elementu członkowskiego program obsługi poleceń.

### <a name="syntax"></a>Składnia

```
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Parametry

*commandId*<br/>
Identyfikator polecenia.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości, na który jest mapowany polecenia.

### <a name="remarks"></a>Uwagi

Rozszerzone rodzaj procedury obsługi komunikatów polecenia jest dostępna dla wykorzystuje zaawansowane. ON_COMMAND_EX — makro jest używana do obsługi takich komunikatów i zapewnia nadzbiorem [ON_COMMAND](message-map-macros-mfc.md#on_command) funkcji. Rozszerzona procedura obsługi polecenia elementów członkowskich przyjmować jeden parametr, UINT, zawierający identyfikator polecenia i zwracać wartość LOGICZNĄ. Wartość zwracana powinna być PRAWDA w celu wskazania, że polecenie został obsłużony; w przeciwnym razie routingu będzie innych obiektów docelowych polecenia.

Aby uzyskać więcej informacji, zobacz Uwaga techniczna [TN006: Mapy komunikatów] tm006-komunikat maps.md).

### <a name="requirements"></a>Wymagania

Header file: afxmsg_.h

## <a name="on_control"></a>  ON_CONTROL

Wskazuje funkcję, która będzie obsługiwać komunikat z powiadomieniem formant niestandardowy.

### <a name="syntax"></a>Składnia

```
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kod powiadomienia formantu.

*commandId*<br/>
Identyfikator polecenia.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości, na który jest mapowany polecenia.

### <a name="remarks"></a>Uwagi

Komunikaty powiadomień dotyczących kontrolki są wysyłane z formantu do okna nadrzędnego.

Powinien istnieć dokładnie jeden ON_CONTROL — makro instrukcję na mapie komunikatów dla każdego komunikatu powiadomienia kontroli, który musi być zamapowany na funkcję obsługi wiadomości.

Aby uzyskać więcej informacji i przykładów, zobacz [wiadomościami i mapowanie tematów](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_message"></a>  ON_MESSAGE

Wskazuje funkcję, która będzie obsługiwać wiadomości zdefiniowanych przez użytkownika.

### <a name="syntax"></a>Składnia

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Identyfikator komunikatu.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości zmapowany wiadomości.

Typ funkcji musi być `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.

### <a name="remarks"></a>Uwagi

Zdefiniowane przez użytkownika wiadomości są wszystkie komunikaty, które nie są standardowe komunikaty Windows WM_MESSAGE. Podczas wybierania identyfikator komunikatu, musisz podać wartości w ramach zakresu WM_USER (0x0400) 0x7FFF lub WM_APP (0x8000) do 0xBFFF. Aby uzyskać więcej informacji na temat identyfikatory komunikatów zobacz [WM_APP](/windows/desktop/winmsg/wm-app).

Powinien istnieć dokładnie jeden ON_MESSAGE — makro instrukcję na mapie komunikatów dla każdej wiadomości zdefiniowanych przez użytkownika, który musi być zamapowany na funkcję obsługi wiadomości.

> [!NOTE]
>  Oprócz wiadomości zdefiniowanych przez użytkownika ON_MESSAGE obsługuje mniej typowych komunikatów Windows. Aby uzyskać więcej informacji, zobacz [mapy komunikatów](../../mfc/tn006-message-maps.md).

Aby uzyskać więcej informacji i przykładów, zobacz [wiadomościami i mapowanie tematów](../../mfc/message-handling-and-mapping.md) i [programy obsługi zdefiniowane przez użytkownika](user-defined-handlers.md)

### <a name="example"></a>Przykład

```cpp
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here.

   return 0;
}
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_olecmd"></a>  ON_OLECMD

Kieruje poleceń przez interfejs ekspedycji polecenia `IOleCommandTarget`.

### <a name="syntax"></a>Składnia

```
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Parametry

*pguid*<br/>
Identyfikator grupy poleceń, do której należy to polecenie. Na użytek standardowa grupy o wartości NULL.

*olecmdid*<br/>
Identyfikator polecenia OLE.

*commandId*<br/>
Identyfikator menu, pasek narzędzi identyfikator, identyfikator przycisku lub innych identyfikator zasobu lub obiekt wydanie polecenia.

### <a name="remarks"></a>Uwagi

`IOleCommandTarget` Umożliwia kontenera w celu odbierania poleceń, które pochodzą z interfejsu użytkownika DocObject i umożliwia kontenera do wysyłania poleceń tym samym (takie jak nowy, Otwórz, Zapisz jako i drukowanie w menu Plik; i kopiowania, wklejania, cofnąć i innych elementów w menu Edycja) na obiekt DocObject.

`IOleCommandTarget` jest prostsze niż automatyzacji OLE firmy `IDispatch`. `IOleCommandTarget` opiera się wyłącznie na standardowy zestaw poleceń, który rzadko muszą przeciążać argumentów i nie informacji o typie jest zaangażowana (bezpieczeństwo typów będzie mniejsza także argumentów polecenia). Jeśli musisz wysyłać polecenia z argumentami, użyj [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

`IOleCommandTarget` Polecenia standardowe menu zostały zaimplementowane przez MFC w następujące makra:

**ON_OLECMD_CLEARSELECTION( )**

Wywołuje polecenie Edytuj czyszczenia. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

Wywołuje polecenie Edytuj kopię. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

Wywołuje polecenia Wytnij edycji. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

Wywołuje polecenie Nowy plik. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

Wywołuje polecenia Otwórz plik. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

Wywołuje polecenie Ustawienia strony pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

Wywołuje polecenie Paste edycji. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

Wywołuje polecenie Edytuj Wklej specjalne. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

Wywołuje polecenia drukowania pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

Wywołuje polecenie Podgląd wydruku z pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

Wywołuje polecenie Edytuj wykonaj ponownie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

Wywołuje polecenie Zapisz plik. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

Wywołuje polecenie Zapisz jako plik. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

Wywołuje plik polecenia Zapisz jako. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

Wywołuje polecenie Edytuj Zaznacz wszystko. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

Wywoła polecenie Cofnij edycji. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob.h

## <a name="on_registered_message"></a>  ON_REGISTERED_MESSAGE

Windows `RegisterWindowMessage` funkcja służy do definiowania nowego komunikatu w oknie, która może być unikatowy w całym systemie.

### <a name="syntax"></a>Składnia

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nMessageVariable*<br/>
Zmienna Identyfikatora zarejestrowanych komunikatów okien.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości zmapowany wiadomości.

### <a name="remarks"></a>Uwagi

To makro wskazuje, funkcja, która będzie obsługiwać zarejestrowanych komunikatów.

Aby uzyskać więcej informacji i przykładów, zobacz [wiadomościami i mapowanie tematów](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Przykład

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_registered_thread_message"></a>  ON_REGISTERED_THREAD_MESSAGE

Wskazuje funkcję, która będzie obsługiwać komunikat zarejestrowany przez funkcję Windows RegisterWindowMessage.

### <a name="syntax"></a>Składnia

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nMessageVariable*<br/>
Zmienna Identyfikatora zarejestrowanych komunikatów okien.

*memberFxn*<br/>
Nazwa funkcji programu obsługi komunikatów CWinThread zmapowany wiadomości.

### <a name="remarks"></a>Uwagi

RegisterWindowMessage jest używane do definiowania nowego komunikatu w oknie, która może być unikatowy w całym systemie. Podczas istnieje klasa CWinThread należy użyć zamiast ON_REGISTERED_MESSAGE ON_REGISTERED_THREAD_MESSAGE.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_thread_message"></a>  ON_THREAD_MESSAGE

Wskazuje funkcję, która będzie obsługiwać wiadomości zdefiniowanych przez użytkownika.

### <a name="syntax"></a>Składnia

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Identyfikator komunikatu.

*memberFxn*<br/>
Nazwa `CWinThread`-komunikat-funkcji obsługi, do którego komunikat jest zamapowany.

### <a name="remarks"></a>Uwagi

ON_THREAD_MESSAGE można używać zamiast ON_MESSAGE, gdy masz `CWinThread` klasy. Zdefiniowane przez użytkownika wiadomości są wszystkie komunikaty, które nie są standardowe komunikaty Windows WM_MESSAGE. Powinien istnieć dokładnie jeden ON_THREAD_MESSAGE — makro instrukcję na mapie komunikatów dla każdej wiadomości zdefiniowanych przez użytkownika, który musi być zamapowany na funkcję obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="on_update_command_ui"></a>  ON_UPDATE_COMMAND_UI

To makro wskazuje funkcję, która będzie obsługiwać komunikatem polecenia aktualizacji interfejsu użytkownika.

### <a name="syntax"></a>Składnia

```
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Parametry

*messageId*<br/>
Identyfikator komunikatu.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości zmapowany wiadomości.

### <a name="remarks"></a>Uwagi

Powinien istnieć dokładnie jeden ON_UPDATE_COMMAND_UI — makro instrukcję na mapie komunikatów dla każdego polecenia aktualizacji interfejsu użytkownika, który musi być zamapowany na funkcję obsługi wiadomości.

Aby uzyskać więcej informacji i przykładów, zobacz [wiadomościami i mapowanie tematów](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="on_command_range"></a>  ON_COMMAND_RANGE

Użyj tego makra, aby zamapować ciągły zakres identyfikatorów poleceń do funkcji obsługi pojedynczą wiadomość.

### <a name="syntax"></a>Składnia

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*id1*<br/>
Identyfikator polecenia na początku ciągły zakres identyfikatorów poleceń.

*id2*<br/>
Identyfikator polecenia na końcu ciągły zakres identyfikatorów poleceń.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której polecenia są zamapowane.

### <a name="remarks"></a>Uwagi

Zakres identyfikatorów zaczyna się od *id1* i kończy *id2*.

ON_COMMAND_RANGE umożliwia mapowanie zakresu identyfikatorów poleceń do funkcji jednego członka. Użyj [ON_COMMAND](#on_command) do mapowania jedno polecenie do funkcji członkowskiej. Identyfikator polecenia może odnosić się tylko jeden wpis mapy komunikatów Oznacza to, że nie można zamapować polecenia do więcej niż jednego programu obsługi. Aby uzyskać więcej informacji na temat mapowania zakresy wiadomości, zobacz [programy obsługi dla zakresów Map komunikatów](../../mfc/handlers-for-message-map-ranges.md).

Brak automatyczne obsługi dla zakresów map komunikatów, dzięki czemu możesz makro należy umieścić.

### <a name="example"></a>Przykład

```cpp
// The code fragment below shows how to use ON_COMMAND_RANGE macro
// to map a contiguous range of command IDs to a single message
// handler function (i.e. OnRangeCmds() in the sample below). In
// addition, it also shows how to use CheckMenuRadioItem() to check a
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3,
      nID, MF_BYCOMMAND);
}
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_update_command_ui_range"></a>  ON_UPDATE_COMMAND_UI_RANGE

Mapuje ciągły zakres identyfikatorów poleceń do funkcji obsługi komunikatów jedną aktualizację.

### <a name="syntax"></a>Składnia

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*id1*<br/>
Identyfikator polecenia na początku ciągły zakres identyfikatorów poleceń.

*id2*<br/>
Identyfikator polecenia na końcu ciągły zakres identyfikatorów poleceń.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości aktualizacji, do której polecenia są zamapowane.

### <a name="remarks"></a>Uwagi

Programy obsługi komunikatów aktualizacji aktualizacji stanu elementów menu i przycisków paska narzędzi powiązanych z poleceniem. Zakres identyfikatorów zaczyna się od *id1* i kończy *id2*.

Brak automatyczne obsługi dla zakresów map komunikatów, dzięki czemu możesz makro należy umieścić.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_control_range"></a>  ON_CONTROL_RANGE

Użyj tego makra, aby zamapować ciągły zakres identyfikatorów kontroli do funkcji obsługi pojedynczy komunikat dla określonego komunikatu powiadomienia Windows, takich jak BN_CLICKED.

### <a name="syntax"></a>Składnia

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kod powiadomienia, do którego odpowiada programu obsługi.

*id1*<br/>
Identyfikator polecenia na początku ciągły zakres kontroli identyfikatorów.

*id2*<br/>
Identyfikator polecenia na końcu ciągły zakres kontroli identyfikatorów.

*memberFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której formanty są mapowane.

### <a name="remarks"></a>Uwagi

Zakres identyfikatorów zaczyna się od *id1* i kończy *id2*. Program obsługi jest wywoływana dla określonego powiadomienia pochodzące z dowolnej kontrolki zamapowany.

Brak automatyczne obsługi dla zakresów map komunikatów, dzięki czemu możesz makro należy umieścić.

Aby uzyskać więcej informacji dotyczących implementowania funkcji obsługi szeregu kontroli identyfikatorów, zobacz [programy obsługi dla zakresów Map komunikatów](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="see-also"></a>Zobacz także

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: mapy komunikatów](../tn006-message-maps.md)<br/>
[Klasa COleCmdUI](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea)<br/>
[Programy obsługi zdefiniowane przez użytkownika](user-defined-handlers.md)<br/>
[Klasa CCmdUI](ccmdui-class.md)
