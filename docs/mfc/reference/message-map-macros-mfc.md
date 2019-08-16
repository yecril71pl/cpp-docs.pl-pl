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
ms.openlocfilehash: b88b745e3b70cf030f77f247ab03cd69d910109f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502085"
---
# <a name="message-map-macros-mfc"></a>Makra mapy komunikatów (MFC)

Aby obsługiwać mapy komunikatów, MFC udostępnia następujące makra:

### <a name="message-map-declaration-and-demarcation-macros"></a>Makra deklaracji i rozgraniczania mapy komunikatów

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Deklaruje, że mapa komunikatów zostanie użyta w klasie w celu mapowania komunikatów do funkcji (musi być używana w deklaracji klasy).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Rozpoczyna definicję mapy komunikatów (należy ją użyć w implementacji klasy).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Rozpoczyna definicję mapy komunikatów dla typu klasy zawierającej jeden argument szablonu. |
|[END_MESSAGE_MAP](#end_message_map)|Zamyka definicję mapy komunikatów (musi być używana w implementacji klasy).|

### <a name="message-mapping-macros"></a>Makra mapowania komunikatów

|||
|-|-|
|[ON_COMMAND](#on_command)|Wskazuje, która funkcja będzie obsługiwać określony komunikat polecenia.|
|[ON_COMMAND_EX](#on_command_ex)|Wskazuje, która funkcja będzie obsługiwać określony komunikat polecenia.|
|[ON_CONTROL](#on_control)|Wskazuje, która funkcja będzie obsługiwać określony komunikat kontroli — powiadomienie.|
|[ON_MESSAGE](#on_message)|Wskazuje, która funkcja będzie obsługiwać komunikat zdefiniowany przez użytkownika.|
|[ON_OLECMD](#on_olecmd)|Wskazuje, która funkcja będzie obsługiwać polecenie menu z DocObject lub jego kontenera.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Wskazuje, która funkcja będzie obsługiwać zarejestrowany komunikat zdefiniowany przez użytkownika.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Wskazuje, która funkcja będzie obsługiwać zarejestrowany komunikat zdefiniowany przez użytkownika, gdy użytkownik ma `CWinThread` klasę.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Wskazuje, która funkcja będzie obsługiwać komunikat zdefiniowany przez użytkownika, gdy posiadasz `CWinThread` klasę.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Wskazuje, która funkcja będzie obsługiwać określony komunikat polecenia aktualizacji interfejsu użytkownika.|

### <a name="message-map-range-macros"></a>Makra zakresu mapy komunikatów

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Wskazuje, która funkcja będzie obsługiwać zakres identyfikatorów poleceń określonych w pierwszych dwóch parametrach makra.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Wskazuje, która procedura obsługi aktualizacji będzie obsługiwać zakres identyfikatorów poleceń określonych w pierwszych dwóch parametrach makra.|
|[ON_CONTROL_RANGE](#on_control_range)|Wskazuje, która funkcja będzie obsługiwać powiadomienia z zakresu identyfikatorów kontroli określonych w drugim i trzecim parametrze makra. Pierwszy parametr to komunikat z powiadomieniem o kontrolce, taki jak BN_CLICKED.|

Aby uzyskać więcej informacji na temat map komunikatów, deklaracji i makr rozgraniczania mapy komunikatów oraz makr mapowania komunikatów, zobacz [mapy komunikatów](../../mfc/reference/message-maps-mfc.md) i [Obsługa komunikatów oraz mapowanie](../../mfc/message-handling-and-mapping.md). Aby uzyskać więcej informacji na temat zakresów map wiadomości, zobacz [programy obsługi dla zakresów map komunikatów](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

Rozpoczyna definicję mapy komunikatów.

### <a name="syntax"></a>Składnia

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy, dla której jest mapowany komunikat.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (. cpp), który definiuje funkcje elementów członkowskich klasy, uruchom mapę komunikatów za pomocą makra BEGIN_MESSAGE_MAP, a następnie Dodaj wpisy makr dla każdej funkcji obsługi komunikatów i Ukończ Mapowanie komunikatów za pomocą END_MESSAGE_MAP makro.

Aby uzyskać więcej informacji na temat map wiadomości, zobacz [mapy komunikatów](message-maps-mfc.md)

### <a name="example"></a>Przykład

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Rozpoczyna definicję mapy komunikatów dla typu klasy zawierającej jeden argument szablonu.

### <a name="syntax"></a>Składnia

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Określa nazwę klasy, dla której jest mapowany komunikat.

*type_name*<br/>
Nazwa parametru szablonu określonego dla klasy.

*baseClass*<br/>
Określa nazwę klasy bazowej *theClass*.

### <a name="remarks"></a>Uwagi

To makro jest podobne do makra [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) ; to makro jest jednak przeznaczone dla klas zawierających pojedynczy argument szablonu.

W sekcji implementacja metody klasy Uruchom mapę komunikatów za pomocą makra BEGIN_TEMPLATE_MESSAGE_MAP; następnie Dodaj wpisy makr dla każdej metody obsługi komunikatów, tak jak w przypadku standardowej mapy komunikatów. Podobnie jak w przypadku makra BEGIN_MESSAGE_MAP, Wypełnij mapę wiadomości szablonu za pomocą makra [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) .

Aby uzyskać więcej informacji na temat implementowania map komunikatów dla klas szablonów [, zobacz How to: Utwórz mapę komunikatów dla klasy](../how-to-create-a-message-map-for-a-template-class.md)szablonu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

Deklaruje, że klasa definiuje mapę komunikatów. Każda `CCmdTarget`Klasa pochodna w programie musi udostępniać mapę komunikatów do obsługi komunikatów.

### <a name="syntax"></a>Składnia

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Uwagi

Użyj makra DECLARE_MESSAGE_MAP na końcu deklaracji klasy. Następnie w pliku. cpp, który definiuje funkcje elementu członkowskiego dla klasy, użyj makra BEGIN_MESSAGE_MAP, wpisów makr dla każdej funkcji obsługi komunikatów i makra END_MESSAGE_MAP.

> [!NOTE]
>  W przypadku deklarowania dowolnego elementu członkowskiego po DECLARE_MESSAGE_MAP należy określić dla nich nowy typ dostępu (**publiczny**, **prywatny**lub **chroniony**).

Aby uzyskać więcej informacji na temat map komunikatów i makra DECLARE_MESSAGE_MAP, zobacz [temat Obsługa komunikatów i mapowanie](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Przykład

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="end_message_map"></a>END_MESSAGE_MAP

Zamyka definicję mapy komunikatów.

### <a name="syntax"></a>Składnia

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat map komunikatów i makra END_MESSAGE_MAP, zobacz [temat Obsługa komunikatów i mapowanie](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="on_command"></a>ON_COMMAND

To makro mapuje komunikat polecenia na funkcję członkowską.

### <a name="syntax"></a>Składnia

```
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*commandId*<br/>
Identyfikator polecenia.

*memberFxn*<br/>
Nazwa funkcji obsługi komunikatów, do której zostało zamapowane polecenie.

### <a name="remarks"></a>Uwagi

Wskazuje, która funkcja będzie obsługiwać komunikat polecenia z obiektu interfejsu użytkownika polecenia, takiego jak element menu lub przycisk paska narzędzi.

Gdy obiekt docelowy polecenia odbiera komunikat WM_COMMAND systemu Windows o określonym identyfikatorze, ON_COMMAND wywoła funkcję `memberFxn` członkowską, aby obsłużyć komunikat.

Użyj ON_COMMAND, aby zmapować pojedyncze polecenie do funkcji członkowskiej. Użyj [ON_COMMAND_RANGE](#on_command_range) do mapowania zakresu identyfikatorów poleceń na jedną funkcję członkowską. Tylko jeden wpis mapy komunikatów może pasować do danego identyfikatora polecenia. Oznacza to, że nie można zamapować polecenia na więcej niż jedną procedurę obsługi. Aby uzyskać więcej informacji i przykładów, zobacz [temat Obsługa komunikatów i mapowanie](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Przykład

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_. h

## <a name="on_command_ex"></a>ON_COMMAND_EX

Rozszerzona funkcja członkowska obsługi poleceń.

### <a name="syntax"></a>Składnia

```
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Parametry

*commandId*<br/>
Identyfikator polecenia.

*memberFxn*<br/>
Nazwa funkcji obsługi komunikatów, do której zostało zamapowane polecenie.

### <a name="remarks"></a>Uwagi

Rozszerzona forma obsługi komunikatów poleceń jest dostępna do użycia zaawansowanego. Makro ON_COMMAND_EX służy do obsługi komunikatów i zapewnia nadzbiór funkcji [ON_COMMAND](message-map-macros-mfc.md#on_command) . Rozszerzone funkcje składowe programu obsługi poleceń przyjmują jeden parametr, UINT zawierający identyfikator polecenia i zwracają wartość logiczną. Wartość zwracana powinna mieć wartość TRUE, aby wskazać, że polecenie zostało obsłużone; w przeciwnym razie Routing będzie kontynuował inne obiekty docelowe poleceń.

Aby uzyskać więcej informacji, zobacz Uwaga techniczna [TN006: Mapy komunikatów] tm006-Message-maps.md).

### <a name="requirements"></a>Wymagania

Plik nagłówkowy: afxmsg_. h

## <a name="on_control"></a>ON_CONTROL

Wskazuje, która funkcja będzie obsługiwać komunikat z powiadomieniem o kontrolce niestandardowej.

### <a name="syntax"></a>Składnia

```
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kod powiadomienia dla kontrolki.

*commandId*<br/>
Identyfikator polecenia.

*memberFxn*<br/>
Nazwa funkcji obsługi komunikatów, do której zostało zamapowane polecenie.

### <a name="remarks"></a>Uwagi

Komunikaty powiadomień sterujące są tymi, które są wysyłane z kontrolki do okna nadrzędnego.

Dla każdej wiadomości z powiadomieniem o kontroli, która musi zostać zmapowana do funkcji obsługi komunikatów, powinna istnieć dokładnie jedna instrukcja makra ON_CONTROL.

Aby uzyskać więcej informacji i przykładów, zobacz [temat Obsługa komunikatów i mapowanie](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_. h

## <a name="on_message"></a>ON_MESSAGE

Wskazuje, która funkcja będzie obsługiwać komunikat zdefiniowany przez użytkownika.

### <a name="syntax"></a>Składnia

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Identyfikator komunikatu.

*memberFxn*<br/>
Nazwa funkcji obsługi komunikatów, do której jest mapowany komunikat.

Typem funkcji musi być `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.

### <a name="remarks"></a>Uwagi

Komunikaty zdefiniowane przez użytkownika to komunikaty, które nie są standardowymi komunikatami WM_MESSAGE systemu Windows. W przypadku wybrania identyfikatora wiadomości należy użyć wartości z zakresu od WM_USER (0x0400) do 0x7FFF lub WM_APP (0x8000) na 0xBFFF. Aby uzyskać więcej informacji dotyczących identyfikatorów wiadomości, zobacz [WM_APP](/windows/win32/winmsg/wm-app).

Dla każdej wiadomości zdefiniowanej przez użytkownika, która musi zostać zmapowana do funkcji obsługi komunikatów, powinna istnieć dokładnie jedna instrukcja makra ON_MESSAGE.

> [!NOTE]
>  Oprócz komunikatów zdefiniowanych przez użytkownika, ON_MESSAGE obsługuje mniej typowe komunikaty systemu Windows. Aby uzyskać więcej informacji, zobacz [mapy komunikatów](../../mfc/tn006-message-maps.md).

Aby uzyskać więcej informacji i przykładów, zobacz [temat Obsługa komunikatów i mapowanie tematów](../../mfc/message-handling-and-mapping.md) oraz [programy obsługi zdefiniowane przez użytkownika](user-defined-handlers.md)

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

**Nagłówek:** afxmsg_. h

## <a name="on_olecmd"></a>ON_OLECMD

Kieruje polecenia za pomocą interfejsu `IOleCommandTarget`wysyłania poleceń.

### <a name="syntax"></a>Składnia

```
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Parametry

*pguid*<br/>
Identyfikator grupy poleceń, do której należy polecenie. Użyj wartości NULL dla grupy standardowej.

*olecmdid*<br/>
Identyfikator polecenia OLE.

*commandId*<br/>
Identyfikator menu, identyfikator paska narzędzi, identyfikator przycisku lub inny identyfikator zasobu lub obiektu, który wydał polecenie.

### <a name="remarks"></a>Uwagi

`IOleCommandTarget`umożliwia kontenerowi otrzymywanie poleceń, które pochodzą z interfejsu użytkownika DocObject, i umożliwia kontenerowi wysyłanie tych samych poleceń (takich jak New, Open, SaveAs i Print w menu plik, a następnie kopiowanie, wklejanie, cofanie i tak dalej w menu Edycja) do DocObject.

`IOleCommandTarget`jest prostsze niż Automatyzacja `IDispatch`OLE. `IOleCommandTarget`opiera się wyłącznie na standardowym zestawie poleceń, które rzadko mają argumenty, i nie ma żadnych informacji o typie (bezpieczeństwo typu jest również zmniejszane dla argumentów polecenia). Jeśli konieczne jest wysłanie poleceń z argumentami, użyj [COleServerDoc:: OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

`IOleCommandTarget` Standardowe polecenia menu zostały zaimplementowane przez MFC w następujących makrach:

**ON_OLECMD_CLEARSELECTION( )**

Wysyła polecenie Edytuj Wyczyść. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

Wysyła polecenie Edytuj kopię. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

Wysyła polecenie Edit Wytnij. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

Wysyła plik nowe polecenie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

Wysyła polecenie otwarcia pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

Wysyła polecenie Ustawienia strony pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

Wysyła polecenie Edytuj Wklej. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

Wysyła polecenie Edytuj Wklej specjalnie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

Wysyła polecenie plik Print. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

Wysyła polecenie podglądu wydruku pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

Wysyła polecenie Edytuj ponownie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

Wysyła polecenie zapisania pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

Wysyła plik Zapisz jako polecenie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

Wysyła plik Zapisz kopię jako polecenie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

Wysyła polecenie Edytuj Zaznacz wszystko. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

Wysyła polecenie Edit Undo. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob. h

## <a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Funkcja systemu `RegisterWindowMessage` Windows służy do definiowania nowego komunikatu okna, który ma być unikatowy w całym systemie.

### <a name="syntax"></a>Składnia

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nMessageVariable*<br/>
Zmienna identyfikatora komunikatu okna.

*memberFxn*<br/>
Nazwa funkcji obsługi komunikatów, do której jest mapowany komunikat.

### <a name="remarks"></a>Uwagi

To makro wskazuje, która funkcja będzie obsługiwać zarejestrowany komunikat.

Aby uzyskać więcej informacji i przykładów, zobacz [temat Obsługa komunikatów i mapowanie](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Przykład

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_. h

## <a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Wskazuje, która funkcja będzie obsługiwać komunikat zarejestrowany przez funkcję RegisterWindowMessage systemu Windows.

### <a name="syntax"></a>Składnia

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nMessageVariable*<br/>
Zmienna identyfikatora komunikatu okna.

*memberFxn*<br/>
Nazwa funkcji CWinThread-Message-Handler, do której jest mapowany komunikat.

### <a name="remarks"></a>Uwagi

RegisterWindowMessage służy do definiowania nowego komunikatu okna, który ma być unikatowy w całym systemie. ON_REGISTERED_THREAD_MESSAGE musi być używana zamiast ON_REGISTERED_MESSAGE, gdy istnieje Klasa CWinThread.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_. h

## <a name="on_thread_message"></a>ON_THREAD_MESSAGE

Wskazuje, która funkcja będzie obsługiwać komunikat zdefiniowany przez użytkownika.

### <a name="syntax"></a>Składnia

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Identyfikator komunikatu.

*memberFxn*<br/>
Nazwa `CWinThread`funkcji obsługi komunikatów, do której jest mapowany komunikat.

### <a name="remarks"></a>Uwagi

W przypadku `CWinThread` klasy należy użyć ON_THREAD_MESSAGE zamiast ON_MESSAGE. Komunikaty zdefiniowane przez użytkownika to komunikaty, które nie są standardowymi komunikatami WM_MESSAGE systemu Windows. Dla każdej wiadomości zdefiniowanej przez użytkownika, która musi zostać zmapowana do funkcji obsługi komunikatów, powinna istnieć dokładnie jedna instrukcja makra ON_THREAD_MESSAGE.

### <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

## <a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

To makro wskazuje, która funkcja będzie obsługiwać komunikat polecenia aktualizacji interfejsu użytkownika.

### <a name="syntax"></a>Składnia

```
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Parametry

*Identyfikatora*<br/>
Identyfikator komunikatu.

*memberFxn*<br/>
Nazwa funkcji obsługi komunikatów, do której jest mapowany komunikat.

### <a name="remarks"></a>Uwagi

Dla każdego polecenia aktualizacji interfejsu użytkownika, które musi zostać zamapowane na funkcję programu obsługi komunikatów, powinna istnieć dokładnie jedna instrukcja makra ON_UPDATE_COMMAND_UI.

Aby uzyskać więcej informacji i przykładów, zobacz [temat Obsługa komunikatów i mapowanie](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

## <a name="on_command_range"></a>ON_COMMAND_RANGE

To makro służy do mapowania ciągłego zakresu identyfikatorów poleceń do jednej funkcji obsługi komunikatów.

### <a name="syntax"></a>Składnia

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*id1*<br/>
Identyfikator polecenia na początku ciągłego zakresu identyfikatorów poleceń.

*id2*<br/>
Identyfikator polecenia na końcu ciągłego zakresu identyfikatorów poleceń.

*memberFxn*<br/>
Nazwa funkcji obsługi komunikatów, do której są mapowane polecenia.

### <a name="remarks"></a>Uwagi

Zakres identyfikatorów rozpoczyna się od *ID1* i kończą się *ID2*.

Użyj ON_COMMAND_RANGE do mapowania zakresu identyfikatorów poleceń na jedną funkcję członkowską. Użyj [ON_COMMAND](#on_command) , aby zmapować pojedyncze polecenie do funkcji członkowskiej. Tylko jeden wpis mapy komunikatów może pasować do danego identyfikatora polecenia. Oznacza to, że nie można zamapować polecenia na więcej niż jedną procedurę obsługi. Aby uzyskać więcej informacji na temat mapowania zakresów komunikatów, zobacz [programy obsługi dla zakresów map komunikatów](../../mfc/handlers-for-message-map-ranges.md).

Nie ma automatycznej obsługi dla zakresów map wiadomości, dlatego należy samodzielnie umieścić makro.

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

**Nagłówek:** afxmsg_. h

## <a name="on_update_command_ui_range"></a>  ON_UPDATE_COMMAND_UI_RANGE

Mapuje ciągły zakres identyfikatorów poleceń na pojedynczą funkcję obsługi komunikatów aktualizacji.

### <a name="syntax"></a>Składnia

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*id1*<br/>
Identyfikator polecenia na początku ciągłego zakresu identyfikatorów poleceń.

*id2*<br/>
Identyfikator polecenia na końcu ciągłego zakresu identyfikatorów poleceń.

*memberFxn*<br/>
Nazwa funkcji aktualizacji obsługi komunikatów, do której są mapowane polecenia.

### <a name="remarks"></a>Uwagi

Aktualizacja programów obsługi komunikatów aktualizuje stan elementów menu i przycisków paska narzędzi skojarzonych z poleceniem. Zakres identyfikatorów rozpoczyna się od *ID1* i kończą się *ID2*.

Nie ma automatycznej obsługi dla zakresów map wiadomości, dlatego należy samodzielnie umieścić makro.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_. h

## <a name="on_control_range"></a>ON_CONTROL_RANGE

To makro służy do mapowania ciągłego zakresu identyfikatorów sterujących na pojedynczą funkcję obsługi komunikatów dla określonego komunikatu powiadomienia systemu Windows, na przykład BN_CLICKED.

### <a name="syntax"></a>Składnia

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kod powiadomienia, na który odpowiada program obsługi.

*id1*<br/>
Identyfikator polecenia na początku ciągłego zakresu identyfikatorów sterowania.

*id2*<br/>
Identyfikator polecenia na końcu ciągłego zakresu identyfikatorów kontrolek.

*memberFxn*<br/>
Nazwa funkcji obsługi komunikatów, do której są mapowane formanty.

### <a name="remarks"></a>Uwagi

Zakres identyfikatorów rozpoczyna się od *ID1* i kończą się *ID2*. Procedura obsługi jest wywoływana dla określonego powiadomienia pochodzącego z dowolnej z zamapowanych kontrolek.

Nie ma automatycznej obsługi dla zakresów map wiadomości, dlatego należy samodzielnie umieścić makro.

Aby uzyskać więcej informacji na temat implementowania funkcji obsługi dla zakresu identyfikatorów sterowania, zapoznaj się z procedurami [obsługi dla zakresów map komunikatów](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_. h

## <a name="see-also"></a>Zobacz także

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: mapy komunikatów](../tn006-message-maps.md)<br/>
[Klasa COleCmdUI](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Programy obsługi zdefiniowane przez użytkownika](user-defined-handlers.md)<br/>
[Klasa CCmdUI](ccmdui-class.md)
