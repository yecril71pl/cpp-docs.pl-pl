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
ms.openlocfilehash: 6e9291f0f39057403bc27c7fe4ff5ca5a82dfe3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356587"
---
# <a name="message-map-macros-mfc"></a>Makra mapy komunikatów (MFC)

Aby obsługiwać mapy komunikatów, MFC dostarcza następujące makra:

### <a name="message-map-declaration-and-demarcation-macros"></a>Makra deklaracji i rozgraniczenia deklaracji mapy wiadomości

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Deklaruje, że mapa wiadomości będzie używana w klasie do mapowania wiadomości do funkcji (musi być używana w deklaracji klasy).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Rozpoczyna definicję mapy wiadomości (musi być używany w implementacji klasy).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Rozpoczyna definicję mapy wiadomości na typ klasy zawierający pojedynczy argument szablonu. |
|[END_MESSAGE_MAP](#end_message_map)|Kończy definicję mapy wiadomości (musi być używany w implementacji klasy).|

### <a name="message-mapping-macros"></a>Makra mapowania wiadomości

|||
|-|-|
|[On_command](#on_command)|Wskazuje, która funkcja będzie obsługiwać określony komunikat polecenia.|
|[ON_COMMAND_EX](#on_command_ex)|Wskazuje, która funkcja będzie obsługiwać określony komunikat polecenia.|
|[ON_CONTROL](#on_control)|Wskazuje, która funkcja będzie obsługiwać określony komunikat o powiadomieniu o formancie.|
|[ON_MESSAGE](#on_message)|Wskazuje, która funkcja będzie obsługiwać komunikat zdefiniowany przez użytkownika.|
|[ON_OLECMD](#on_olecmd)|Wskazuje, która funkcja będzie obsługiwać polecenie menu z DocObject lub jego kontenera.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Wskazuje, która funkcja będzie obsługiwać zarejestrowany komunikat zdefiniowany przez użytkownika.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Wskazuje, która funkcja będzie obsługiwać zarejestrowany komunikat `CWinThread` zdefiniowany przez użytkownika, gdy masz klasę.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Wskazuje, która funkcja będzie obsługiwać komunikat zdefiniowany przez użytkownika, gdy masz `CWinThread` klasę.|
|[On_update_command_ui](#on_update_command_ui)|Wskazuje, która funkcja będzie obsługiwać określony komunikat polecenia aktualizacji interfejsu użytkownika.|

### <a name="message-map-range-macros"></a>Makra zakresu mapy wiadomości

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Wskazuje, która funkcja będzie obsługiwać zakres identyfikatorów poleceń określonych w pierwszych dwóch parametrach do makra.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Wskazuje, który program obsługi aktualizacji będzie obsługiwał zakres identyfikatorów poleceń określony w pierwszych dwóch parametrach do makra.|
|[ON_CONTROL_RANGE](#on_control_range)|Wskazuje, która funkcja będzie obsługiwać powiadomienia z zakresu identyfikatorów sterowania określonych w drugim i trzecim parametrze do makra. Pierwszy parametr jest komunikatem o kontroli powiadomień, takim jak BN_CLICKED.|

Aby uzyskać więcej informacji na temat map wiadomości, makr deklaracji i rozgraniczenia mapy wiadomości oraz makr mapowania wiadomości, zobacz [Mapy wiadomości](../../mfc/reference/message-maps-mfc.md) oraz Tematy obsługi [i mapowania wiadomości](../../mfc/message-handling-and-mapping.md). Aby uzyskać więcej informacji na temat zakresów mapy wiadomości, zobacz [Programy obsługi zakresów mapy wiadomości](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a><a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

Rozpoczyna definicję mapy wiadomości.

### <a name="syntax"></a>Składnia

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Określa nazwę klasy, której jest to mapa wiadomości.

*Baseclass*<br/>
Określa nazwę klasy podstawowej *klasy klasy*.

### <a name="remarks"></a>Uwagi

W pliku implementacji (.cpp), który definiuje funkcje członkowskie dla klasy, uruchom mapę wiadomości BEGIN_MESSAGE_MAP makra, a następnie dodaj wpisy makr dla każdej funkcji obsługi wiadomości i uzupełnij mapę wiadomości END_MESSAGE_MAP makra.

Aby uzyskać więcej informacji na temat map wiadomości, zobacz [Mapy wiadomości](message-maps-mfc.md)

### <a name="example"></a>Przykład

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Rozpoczyna definicję mapy wiadomości na typ klasy zawierający pojedynczy argument szablonu.

### <a name="syntax"></a>Składnia

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Określa nazwę klasy, której jest to mapa wiadomości.

*Type_name*<br/>
Nazwa parametru szablonu określonego dla klasy.

*Baseclass*<br/>
Określa nazwę klasy podstawowej *klasy klasy*.

### <a name="remarks"></a>Uwagi

To makro jest podobne do [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) makra; jednak to makro jest przeznaczone dla klas zawierających pojedynczy argument szablonu.

W sekcji implementacji metody klasy uruchom mapę wiadomości BEGIN_TEMPLATE_MESSAGE_MAP makra; następnie dodaj wpisy makr dla każdej z metod obsługi wiadomości, tak jak w przypadku standardowej mapy wiadomości. Podobnie jak w makrze BEGIN_MESSAGE_MAP, uzupełnij mapę wiadomości szablonu [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) makra.

Aby uzyskać więcej informacji na temat implementowania map komunikatów dla klas szablonów, zobacz [Jak: Tworzenie mapy wiadomości dla klasy szablonu](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

Deklaruje, że klasa definiuje mapę wiadomości. Każda `CCmdTarget`klasa pochodna w programie musi zawierać mapę wiadomości do obsługi wiadomości.

### <a name="syntax"></a>Składnia

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Uwagi

Użyj makra DECLARE_MESSAGE_MAP na końcu deklaracji klasy. Następnie w pliku .cpp definiujący funkcje członkowskie dla klasy użyj BEGIN_MESSAGE_MAP makra, wpisów makr dla każdej funkcji obsługi wiadomości i makra END_MESSAGE_MAP.

> [!NOTE]
> Jeśli po DECLARE_MESSAGE_MAP zgłosisz dowolny element członkowski, musisz określić dla nich nowy typ dostępu (**publiczny,** **prywatny**lub **chroniony).**

Aby uzyskać więcej informacji na temat map wiadomości i makra DECLARE_MESSAGE_MAP, zobacz [Tematy obsługi i mapowania wiadomości](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Przykład

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a>END_MESSAGE_MAP

Kończy definicję mapy wiadomości.

### <a name="syntax"></a>Składnia

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat map wiadomości i makra END_MESSAGE_MAP, zobacz [Tematy obsługi i mapowania wiadomości](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a>On_command

To makro mapuje komunikat polecenia na funkcję elementu członkowskiego.

### <a name="syntax"></a>Składnia

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*Commandid*<br/>
Identyfikator polecenia.

*członekFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której jest mapowane polecenie.

### <a name="remarks"></a>Uwagi

Wskazuje, która funkcja będzie obsługiwać komunikat polecenia z obiektu interfejsu użytkownika polecenia, takiego jak element menu lub przycisk paska narzędzi.

Gdy obiekt docelowy polecenia odbiera komunikat WM_COMMAND systemu Windows o określonym identyfikatorze, ON_COMMAND `memberFxn` wywoła funkcję elementu członkowskiego w celu obsługi wiadomości.

Użyj ON_COMMAND, aby zamapować pojedyncze polecenie na funkcję elementu członkowskiego. Za pomocą [ON_COMMAND_RANGE](#on_command_range) można mapować zakres identyfikatorów poleceń na jedną funkcję członkowną. Tylko jeden wpis mapy wiadomości może być zgodny z podanym identyfikatorem polecenia. Oznacza to, że nie można mapować polecenia do więcej niż jednego programu obsługi. Aby uzyskać więcej informacji i przykładów, zobacz [Tematy obsługi wiadomości i mapowania](../../mfc/message-handling-and-mapping.md)wiadomości .

### <a name="example"></a>Przykład

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_command_ex"></a><a name="on_command_ex"></a>ON_COMMAND_EX

Rozszerzona funkcja elementu członkowskiego obsługi poleceń.

### <a name="syntax"></a>Składnia

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Parametry

*Commandid*<br/>
Identyfikator polecenia.

*członekFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której jest mapowane polecenie.

### <a name="remarks"></a>Uwagi

Rozszerzona forma obsługi komunikatów poleceń jest dostępna do zastosowań zaawansowanych. Makro ON_COMMAND_EX jest używane dla takich programów obsługi wiadomości i zapewnia nadzbioru [funkcji ON_COMMAND.](message-map-macros-mfc.md#on_command) Rozszerzone funkcje członkowskie obsługi poleceń przyjmują pojedynczy parametr, UINT zawierający identyfikator polecenia i zwracają BOOL. Zwracana wartość powinna być wartość TRUE, aby wskazać, że polecenie zostało obsłużone; w przeciwnym razie routing będzie nadal do innych obiektów docelowych polecenia.

Aby uzyskać więcej informacji, zobacz Uwaga techniczna [TN006: Mapy wiadomości]tm006-message-maps.md).

### <a name="requirements"></a>Wymagania

Plik nagłówka: afxmsg_.h

## <a name="on_control"></a><a name="on_control"></a>ON_CONTROL

Wskazuje, która funkcja będzie obsługiwać komunikat powiadomienia kontroli niestandardowej.

### <a name="syntax"></a>Składnia

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kod powiadomienia formantu.

*Commandid*<br/>
Identyfikator polecenia.

*członekFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której jest mapowane polecenie.

### <a name="remarks"></a>Uwagi

Komunikaty powiadomień kontroli są te wysyłane z formantu do okna nadrzędnego.

Powinno istnieć dokładnie jeden ON_CONTROL instrukcji makra na mapie wiadomości dla każdego komunikatu powiadomienia kontroli, które muszą być mapowane do funkcji obsługi wiadomości.

Aby uzyskać więcej informacji i przykładów, zobacz [Tematy obsługi wiadomości i mapowania](../../mfc/message-handling-and-mapping.md)wiadomości .

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_message"></a><a name="on_message"></a>ON_MESSAGE

Wskazuje, która funkcja będzie obsługiwać komunikat zdefiniowany przez użytkownika.

### <a name="syntax"></a>Składnia

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*Komunikat*<br/>
Identyfikator wiadomości.

*członekFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której jest mapowana wiadomość.

Typ funkcji musi być `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.

### <a name="remarks"></a>Uwagi

Wiadomości zdefiniowane przez użytkownika to wiadomości, które nie są standardowymi wiadomościami systemu Windows WM_MESSAGE. Wybierając identyfikator wiadomości, należy użyć wartości w zakresie od WM_USER (0x0400) do 0x7FFF lub WM_APP (0x8000) do 0xBFFF. Aby uzyskać więcej informacji dotyczących identyfikatorów wiadomości, zobacz [WM_APP](/windows/win32/winmsg/wm-app).

W mapie wiadomości powinna znajdować się dokładnie jedna instrukcja makra ON_MESSAGE dla każdej wiadomości zdefiniowanej przez użytkownika, która musi być mapowana na funkcję obsługi wiadomości.

> [!NOTE]
> Oprócz komunikatów zdefiniowanych przez użytkownika ON_MESSAGE obsługuje mniej typowe komunikaty systemu Windows. Aby uzyskać więcej informacji, zobacz [Mapy wiadomości](../../mfc/tn006-message-maps.md).

Aby uzyskać więcej informacji i przykładów, zobacz [Tematy obsługi i mapowania wiadomości](../../mfc/message-handling-and-mapping.md) oraz Programy obsługi [zdefiniowane przez użytkownika](user-defined-handlers.md)

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

## <a name="on_olecmd"></a><a name="on_olecmd"></a>ON_OLECMD

Trasy poleceń za pośrednictwem `IOleCommandTarget`interfejsu wysyłania poleceń .

### <a name="syntax"></a>Składnia

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Parametry

*pguid ( pguid )*<br/>
Identyfikator grupy poleceń, do której należy polecenie. Użyj wartości NULL dla grupy standardowej.

*olecmdid*<br/>
Identyfikator polecenia OLE.

*Commandid*<br/>
Identyfikator menu, identyfikator paska narzędzi, identyfikator przycisku lub inny identyfikator zasobu lub obiektu wydającego polecenie.

### <a name="remarks"></a>Uwagi

`IOleCommandTarget`umożliwia kontenerowi odbieranie poleceń pochodzących z interfejsu użytkownika DocObject i umożliwia kontenerowi wysyłanie tych samych poleceń (takich jak Nowe, Otwórz, Zapisz i Drukuj w menu Plik; i Kopiuj, Wklej, Cofnij i tak dalej w menu Edycja) do docObject.

`IOleCommandTarget`jest prostsza `IDispatch`niż OLE Automation. `IOleCommandTarget`opiera się wyłącznie na standardowym zestawie poleceń, które rzadko mają argumenty i nie ma informacji o typie (bezpieczeństwo typu jest zmniejszane również dla argumentów poleceń). Jeśli trzeba wysłać polecenia z argumentami, należy użyć [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

Standardowe `IOleCommandTarget` polecenia menu zostały zaimplementowane przez MFC w następujących makrach:

**ON_OLECMD_CLEARSELECTION( )**

Wysyła polecenie Edytuj wyczyść. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

Wysyła polecenie Edytuj kopię. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

Wysyła polecenie Edytuj wycięcie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

Wysyła polecenie Plik nowy. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

Wysyła polecenie Otwórz plik. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

Wysyła polecenie Ustawienia strony pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

Wysyła polecenie Edytuj wklej. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

Wysyła polecenie Edytuj wklej specjalnie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

Wysyła polecenie Drukowanie plików. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

Wysyła polecenie Podgląd wydruku pliku. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

Wysyła polecenie Edytuj ponawianie. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

Wysyła polecenie Zapisz plik. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

Wysyła polecenie Zapisz plik jako. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

Wysyła polecenie Zapisz plik jako. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

Wysyła polecenie Edytuj zaznacz wszystko. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

Wysyła polecenie Edytuj cofnij. Zaimplementowane jako:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob.h

## <a name="on_registered_message"></a><a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Funkcja `RegisterWindowMessage` systemu Windows służy do definiowania nowego komunikatu okna, który jest gwarantowany jako unikatowy w całym systemie.

### <a name="syntax"></a>Składnia

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nMessageWaryjne*<br/>
Zarejestrowana zmienna identyfikatora wiadomości okna.

*członekFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której jest mapowana wiadomość.

### <a name="remarks"></a>Uwagi

To makro wskazuje, która funkcja będzie obsługiwać zarejestrowaną wiadomość.

Aby uzyskać więcej informacji i przykładów, zobacz [Tematy obsługi wiadomości i mapowania](../../mfc/message-handling-and-mapping.md)wiadomości .

### <a name="example"></a>Przykład

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Wskazuje, która funkcja będzie obsługiwać komunikat zarejestrowany przez funkcję Windows RegisterWindowMessage.

### <a name="syntax"></a>Składnia

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nMessageWaryjne*<br/>
Zarejestrowana zmienna identyfikatora wiadomości okna.

*członekFxn*<br/>
Nazwa CWinThread-message-handler funkcji, do której wiadomość jest mapowana.

### <a name="remarks"></a>Uwagi

RegisterWindowMessage służy do definiowania nowego komunikatu okna, który jest gwarantowane, aby być unikatowe w całym systemie. ON_REGISTERED_THREAD_MESSAGE musi być używany zamiast ON_REGISTERED_MESSAGE, gdy masz CWinThread klasy.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_thread_message"></a><a name="on_thread_message"></a>ON_THREAD_MESSAGE

Wskazuje, która funkcja będzie obsługiwać komunikat zdefiniowany przez użytkownika.

### <a name="syntax"></a>Składnia

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*Komunikat*<br/>
Identyfikator wiadomości.

*członekFxn*<br/>
Nazwa funkcji `CWinThread`-message-handler, do której jest mapowana wiadomość.

### <a name="remarks"></a>Uwagi

ON_THREAD_MESSAGE musi być używany zamiast ON_MESSAGE, gdy masz `CWinThread` klasę. Wiadomości zdefiniowane przez użytkownika to wiadomości, które nie są standardowymi wiadomościami systemu Windows WM_MESSAGE. W mapie wiadomości powinna znajdować się dokładnie jedna instrukcja makra ON_THREAD_MESSAGE dla każdej wiadomości zdefiniowanej przez użytkownika, która musi być mapowana na funkcję obsługi wiadomości.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a>On_update_command_ui

To makro wskazuje, która funkcja będzie obsługiwać komunikat polecenia aktualizacji interfejsu użytkownika.

### <a name="syntax"></a>Składnia

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Parametry

*Messageid*<br/>
Identyfikator wiadomości.

*członekFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której jest mapowana wiadomość.

### <a name="remarks"></a>Uwagi

Powinno istnieć dokładnie jeden ON_UPDATE_COMMAND_UI instrukcji makra na mapie wiadomości dla każdego polecenia aktualizacji interfejsu użytkownika, które musi być mapowane do funkcji obsługi wiadomości.

Aby uzyskać więcej informacji i przykładów, zobacz [Tematy obsługi wiadomości i mapowania](../../mfc/message-handling-and-mapping.md)wiadomości .

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="on_command_range"></a><a name="on_command_range"></a>ON_COMMAND_RANGE

To makro służy do mapowania ciągłego zakresu identyfikatorów poleceń na funkcję obsługi pojedynczych wiadomości.

### <a name="syntax"></a>Składnia

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*id1*<br/>
Identyfikator polecenia na początku ciągłego zakresu identyfikatorów poleceń.

*Id2*<br/>
Identyfikator polecenia na końcu ciągłego zakresu identyfikatorów poleceń.

*członekFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której są mapowane polecenia.

### <a name="remarks"></a>Uwagi

Zakres identyfikatorów zaczyna się od *id1* i kończy się *id2*.

Użyj ON_COMMAND_RANGE, aby zamapować zakres identyfikatorów poleceń na jedną funkcję członkowną. Za pomocą [ON_COMMAND](#on_command) można zamapować pojedyncze polecenie na funkcję elementu członkowskiego. Tylko jeden wpis mapy wiadomości może być zgodny z podanym identyfikatorem polecenia. Oznacza to, że nie można mapować polecenia do więcej niż jednego programu obsługi. Aby uzyskać więcej informacji na temat mapowania zakresów komunikatów, zobacz [Programy obsługi zakresów map wiadomości](../../mfc/handlers-for-message-map-ranges.md).

Nie ma automatycznej obsługi zakresów map wiadomości, więc musisz umieścić makro samodzielnie.

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

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

Mapuje ciągły zakres identyfikatorów poleceń na funkcję obsługi pojedynczych komunikatów aktualizacji.

### <a name="syntax"></a>Składnia

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*id1*<br/>
Identyfikator polecenia na początku ciągłego zakresu identyfikatorów poleceń.

*Id2*<br/>
Identyfikator polecenia na końcu ciągłego zakresu identyfikatorów poleceń.

*członekFxn*<br/>
Nazwa funkcji programu obsługi komunikatów aktualizacji, do której są mapowane polecenia.

### <a name="remarks"></a>Uwagi

Programy obsługi komunikatów aktualizacji zaktualizować stan elementów menu i przycisków paska narzędzi skojarzonych z poleceniem. Zakres identyfikatorów zaczyna się od *id1* i kończy się *id2*.

Nie ma automatycznej obsługi zakresów map wiadomości, więc musisz umieścić makro samodzielnie.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="on_control_range"></a><a name="on_control_range"></a>ON_CONTROL_RANGE

To makro służy do mapowania ciągłego zakresu identyfikatorów formantów na funkcję obsługi pojedynczej wiadomości dla określonego komunikatu powiadomień systemu Windows, takiego jak BN_CLICKED.

### <a name="syntax"></a>Składnia

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kod powiadomień, na który odpowiada program obsługi.

*id1*<br/>
Identyfikator polecenia na początku ciągłego zakresu identyfikatorów sterowania.

*Id2*<br/>
Identyfikator polecenia na końcu ciągłego zakresu identyfikatorów sterowania.

*członekFxn*<br/>
Nazwa funkcji obsługi wiadomości, do której są mapowane formanty.

### <a name="remarks"></a>Uwagi

Zakres identyfikatorów zaczyna się od *id1* i kończy się *id2*. Program obsługi jest wywoływana dla określonego powiadomienia pochodzących z dowolnego z mapowanych formantów.

Nie ma automatycznej obsługi zakresów map wiadomości, więc musisz umieścić makro samodzielnie.

Aby uzyskać więcej informacji na temat implementowania funkcji obsługi dla zakresu identyfikatorów kontroli, zobacz [Programy obsługi dla zakresów map komunikatów](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxmsg_.h

## <a name="see-also"></a>Zobacz też

[On_command](message-map-macros-mfc.md#on_command)<br/>
[TN006: mapy komunikatów](../tn006-message-maps.md)<br/>
[Klasa COleCmdUI](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RejestracjaWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Programy obsługi zdefiniowane przez użytkownika](user-defined-handlers.md)<br/>
[Klasa CCmdUI](ccmdui-class.md)
