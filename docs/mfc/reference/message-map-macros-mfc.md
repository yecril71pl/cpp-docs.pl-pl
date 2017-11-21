---
title: Komunikat makra Map (MFC) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70f88d493ad557515cfac1f8cffeaa305c849f63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="message-map-macros-mfc"></a>Makra mapy komunikatów (MFC)
Aby obsługiwać mapy komunikatów, MFC dostarcza następujące makra:  
  
### <a name="message-map-declaration-and-demarcation-macros"></a>Mapy wiadomości deklaracja i odgraniczenie makra  
  
|||  
|-|-|  
|[DECLARE_MESSAGE_MAP —](#declare_message_map)|Deklaruje używane w klasie mapowania komunikatów na funkcje (należy użyć w deklaracji klasy) mapy komunikatów.|  
|[BEGIN_MESSAGE_MAP —](#begin_message_map)|Rozpoczyna się definicji mapy komunikatów (musi być zastosowany w implementacji klasy).|  
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_interface_map)|Rozpoczyna się definicji mapy komunikatów dla typu klasy zawierającego argument jednego szablonu. |
|[END_MESSAGE_MAP —](#end_message_map)|Kończy definicję mapy komunikatów (musi być zastosowany w implementacji klasy).|  
  
### <a name="message-mapping-macros"></a>Makra mapowania wiadomości  
  
|||  
|-|-|  
|[ON_COMMAND —](#on_command)|Wskazuje, funkcji obsługi wiadomości określonego polecenia.|  
|[ON_COMMAND_EX —](#on_command_ex)|Wskazuje, funkcji obsługi wiadomości określonego polecenia.|  
|[ON_CONTROL —](#on_control)|Wskazuje, funkcji obsługi komunikatów powiadomienie kontroli.|  
|[ON_MESSAGE —](#on_message)|Wskazuje, funkcji obsługi wiadomości zdefiniowane przez użytkownika.|  
|[ON_OLECMD —](#on_olecmd)|Wskazuje, która funkcja obsługi polecenia menu z DocObject lub jego kontenera.|  
|[ON_REGISTERED_MESSAGE —](#on_registered_message)|Wskazuje, funkcji, które będą obsługiwać zarejestrowanych wiadomości zdefiniowane przez użytkownika.|  
|[ON_REGISTERED_THREAD_MESSAGE —](#on_registered_thread_message)|Wskazuje funkcji obsłuży zarejestrowanych wiadomości zdefiniowane przez użytkownika, jeśli masz `CWinThread` klasy.|  
|[ON_THREAD_MESSAGE —](#on_thread_message)|Wskazuje, funkcji obsługi wiadomości zdefiniowane przez użytkownika, jeśli masz `CWinThread` klasy.|  
|[ON_UPDATE_COMMAND_UI —](#on_update_command_ui)|Wskazuje, funkcji obsługi wiadomości polecenia aktualizacji interfejsu użytkownika.|  
  
### <a name="message-map-range-macros"></a>Makra mapy komunikatów zakresu  
  
|||  
|-|-|  
|[ON_COMMAND_RANGE —](#on_command_range)|Wskazuje, funkcji, które będą obsługiwać zakres identyfikatorów poleceń określone w pierwszych dwóch parametrów makra.|  
|[ON_UPDATE_COMMAND_UI_RANGE —](#on_update_command_ui_range)|Wskazuje, które procedury obsługi aktualizacji będzie obsługiwać zakres identyfikatorów poleceń określony w dwóch pierwszych pa] arametry w makrze.|  
|[ON_CONTROL_RANGE —](#on_control_range)|Wskazuje, funkcji obsługi powiadomień z zakresu kontroli określonych w parametrach drugi i trzeci w makrze identyfikatorów. Pierwszym parametrem jest komunikatów powiadomień dotyczących formantu, **BN_CLICKED**.|  
  
 Aby uzyskać więcej informacji dotyczących mapy komunikatów, deklaracji mapy komunikatów i odgraniczenie makra i makra mapowania wiadomości, zobacz [mapy wiadomości](../../mfc/reference/message-maps-mfc.md) i [obsługi wiadomości i tematy mapowania](../../mfc/message-handling-and-mapping.md). Aby uzyskać więcej informacji na temat zakresów map komunikatów, zobacz [programy obsługi dla zakresów Map komunikatów](../../mfc/handlers-for-message-map-ranges.md).  


## <a name="begin_message_map"></a>BEGIN_MESSAGE_MAP —
Rozpoczyna się definicji mapy wiadomości.  
  
### <a name="syntax"></a>Składnia  
  
```  
BEGIN_MESSAGE_MAP( theClass, baseClass )  
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Określa nazwę klasy, których wiadomości mapowania.  
  
 `baseClass`  
 Określa nazwę klasy podstawowej `theClass`.  
  
### <a name="remarks"></a>Uwagi  
 W pliku implementacji (.cpp), który definiuje funkcje Członkowskie dla klasy, należy uruchomić Mapa wiadomości z `BEGIN_MESSAGE_MAP` makra, Dodaj makro wpisy dla każdej funkcji obsługi wiadomości i ukończyć Mapa wiadomości z `END_MESSAGE_MAP` makra.  
  
 Aby uzyskać więcej informacji na temat mapy komunikatów, zobacz [mapy wiadomości](message-maps-mfc.md)  
  
### <a name="example"></a>Przykład  
```cpp  
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h 

##  <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP
Rozpoczyna się definicji mapy komunikatów dla typu klasy zawierającego argument jednego szablonu.  
   
### <a name="syntax"></a>Składnia  
  ```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )  
```
### <a name="parameters"></a>Parametry  
 `theClass`  
 Określa nazwę klasy, których wiadomości mapowania.    
 `type_name`  
 Nazwa parametru szablonu określony dla klasy.    
 `baseClass`  
 Określa nazwę klasy podstawowej `theClass`.  
   
### <a name="remarks"></a>Uwagi  
 To makro jest podobny do [begin_message_map —](message-map-macros-mfc.md#begin_message_map) makro; jednak to makro jest przeznaczony dla klasy zawierające argumentu w postaci jednego szablonu.  
  
 W sekcji implementacji metody klasy, należy uruchomić Mapa wiadomości z **BEGIN_TEMPLATE_MESSAGE_MAP** makro; następnie dodać wpisów — makro dla każdego z metody obsługi wiadomości, jak w przypadku mapy komunikatów standardowych. Jak **begin_message_map —** makra ukończyć Mapa wiadomości szablonu z [end_message_map —](message-map-macros-mfc.md#end_message_map) makra.  
  
 Aby uzyskać więcej informacji na implementacji mapy komunikatów dla klasy szablonów dotyczą [porady: Tworzenie mapy komunikatów dla klasy szablonów](../how-to-create-a-message-map-for-a-template-class.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
 
## <a name="declare_message_map"></a>DECLARE_MESSAGE_MAP —
 Deklaruje, że klasa definiuje mapy komunikatów. Każdy `CCmdTarget`-klasy pochodnej w programie podać mapy komunikatów do obsługi wiadomości.  
  
### <a name="syntax"></a>Składnia  
  
```    
DECLARE_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj `DECLARE_MESSAGE_MAP` makro końca z deklaracji klasy. Następnie, w pliku .cpp, który definiuje funkcji elementów członkowskich klasy, należy użyć `BEGIN_MESSAGE_MAP` makra, makro wpisy dla każdej funkcji obsługi wiadomości i `END_MESSAGE_MAP` makra.  
  
> [!NOTE]
>  W przypadku dowolnego członka po `DECLARE_MESSAGE_MAP`, należy określić nowy typ dostępu (**publicznego**, `private`, lub `protected`) dla nich.  
  
 Aby uzyskać więcej informacji na temat wiadomości mapuje i `DECLARE_MESSAGE_MAP` makra, zobacz [obsługi wiadomości i mapowania tematy](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Przykład  
```cpp  
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
``` 
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  


## <a name="end_message_map"></a>END_MESSAGE_MAP —
Kończy definicję mapy wiadomości.  
  
### <a name="syntax"></a>Składnia  
  
```   
END_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat wiadomości mapuje i `END_MESSAGE_MAP` makra, zobacz [obsługi wiadomości i mapowania tematy](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  

## <a name="on_command"></a>ON_COMMAND —
To makro mapuje komunikat polecenia do funkcji członkowskiej.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_COMMAND( id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator polecenia.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Wskazuje on, funkcji obsługi wiadomości polecenia polecenie obiektu interfejsu użytkownika na przykład element lub narzędzi przycisk menu.  
  
 Jeśli obiektem docelowym polecenia odbiera systemu Windows **WM_COMMAND** komunikatu o określonym identyfikatorze `ON_COMMAND` spowoduje wywołanie funkcji Członkowskich `memberFxn` , by obsłużyć komunikat.  
  
 Użyj `ON_COMMAND` do mapowania funkcji członkowskiej jednego polecenia. Użyj [on_command_range —](#on_command_range) Aby zmapować zakres identyfikatorów poleceń funkcji jednego członka. Tylko jeden wpis mapy komunikatów można dopasować identyfikatora polecenia. Oznacza to, że nie można zamapować polecenia na więcej niż jednej procedury obsługi. Aby uzyskać dodatkowe informacje i przykłady, zobacz [obsługi wiadomości i mapowania tematy](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Przykład  
```cpp  
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
``` 
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmsg_.h  

 ## <a name="on_command_ex"></a>ON_COMMAND_EX —
Rozszerzona funkcja członkowska programu obsługi poleceń.  
   
### <a name="syntax"></a>Składnia  
  ```  
ON_COMMAND_EX(id, memberFxn);  
```
### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator polecenia.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany polecenia.  
   
### <a name="remarks"></a>Uwagi 
Rozszerzonej formy polecenie Programy obsługi wiadomości jest dostępna do celów zaawansowane. `ON_COMMAND_EX` Makro jest używane dla takich programy obsługi wiadomości i zapewnia podzbiorem funkcji [on_command —] (# on_command —).  Funkcje Członkowskie program obsługi poleceń rozszerzonej przyjmować jeden parametr, **UINT** zawierający identyfikator polecenia, a następnie wróć **BOOL**. Wartość zwracana powinna być TRUE na 

To makro komunikat polecenia jest mapowany na funkcję rozszerzonej członka program obsługi poleceń.  
   
### <a name="syntax"></a>Składnia  
```  
ON_COMMAND_EX(id,  memberFxn);  
```
### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator polecenia.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany polecenia.  
   
### <a name="remarks"></a>Uwagi  
 Rozszerzonej formy polecenie Programy obsługi wiadomości jest dostępna do celów zaawansowane. `ON_COMMAND_EX` Makro jest używane dla takich programy obsługi wiadomości i zapewnia podzbiorem [on_command —](message-map-macros-mfc.md#on_command) funkcji. Funkcje Członkowskie program obsługi poleceń rozszerzonej przyjmować jeden parametr, **UINT** zawierający identyfikator polecenia, a następnie wróć **BOOL**. Wartość zwracana powinna być wartość TRUE, aby wskazać, że polecenie zostało obsłużone; w przeciwnym razie routingu będzie innych obiektów docelowych polecenia.  
Aby uzyskać więcej informacji, zobacz Uwaga techniczna [TN006: mapy komunikatów] tm006-wiadomości maps.md).  
   
### <a name="requirements"></a>Wymagania  
 Plik nagłówka: afxmsg_.h  
   
### <a name="see-also"></a>Zobacz też  
 [ON_COMMAND —](message-map-macros-mfc.md#on_command)   
 [TN006: mapy komunikatów] tm006-wiadomości maps.md)

  
## <a name="on_control"></a>ON_CONTROL —
Wskazuje, funkcji obsługi komunikatów powiadomień formant niestandardowy.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_CONTROL( wNotifyCode, id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `wNotifyCode`  
 Kod powiadomienia formantu.  
  
 `id`  
 Identyfikator polecenia.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Komunikaty powiadomień dotyczących formantu są wysyłane z formantu do okna nadrzędnego.  
  
 Powinien istnieć dokładnie jeden `ON_CONTROL` oświadczenie makra mapy komunikatów dla każdego komunikatu powiadomienia formant, który musi być zamapowany na funkcję obsługi wiadomości.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [obsługi wiadomości i mapowania tematy](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmsg_.h  
  

## <a name="on_message"></a>ON_MESSAGE —  
Wskazuje, funkcji obsługi wiadomości zdefiniowane przez użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `message`  
 Identyfikator komunikatu.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany wiadomości.  
  
 Musi być typu funkcji `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.  
  
### <a name="remarks"></a>Uwagi  
 Zdefiniowane przez użytkownika wiadomości są komunikaty, które nie są standardowe Windows `WM_MESSAGE` wiadomości. Podczas wybierania identyfikator komunikatu, należy użyć wartości spoza zakresu `WM_USER` (0x0400) do 0x7FFF lub `WM_APP` (0x8000) do 0xBFFF. Aby uzyskać więcej informacji dotyczących identyfikatory komunikatów, zobacz [WM_APP](http://msdn.microsoft.com/library/windows/desktop/ms644930).  
  
 Powinien istnieć dokładnie jeden `ON_MESSAGE` oświadczenie makra mapy wiadomości dla każdej wiadomości zdefiniowane przez użytkownika, który musi być zamapowany na funkcję obsługi wiadomości.  
  
> [!NOTE]
>  Oprócz wiadomości zdefiniowane przez użytkownika `ON_MESSAGE` obsługuje mniej typowych komunikatów systemu Windows. Aby uzyskać więcej informacji, zobacz artykule bazy wiedzy [99848: informacje o: Użyj ON_MESSAGE() makra mapy wiadomości mniej typowe](http://go.microsoft.com/fwlink/?linkId=192022).  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [obsługi wiadomości i mapowania tematy](../../mfc/message-handling-and-mapping.md) i [programy obsługi zdefiniowane przez użytkownika](user-defined-handlers.md)  
  
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

## <a name="on_olecmd"></a>ON_OLECMD —  
Kieruje poleceń za pomocą interfejsu wysyłania polecenia `IOleCommandTarget`.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_OLECMD( pguid, olecmdid, id )  
```  
  
### <a name="parameters"></a>Parametry  
 `pguid`  
 Identyfikator grupy polecenia, do której należy polecenie. Użyj **NULL** standardowe grupy.  
  
 *olecmdid*  
 Identyfikator polecenia OLE.  
  
 `id`  
 Identyfikator menu, paska narzędzi identyfikator, identyfikator przycisku lub innych identyfikator zasobu lub obiekt wydanie polecenia.  
  
### <a name="remarks"></a>Uwagi  
 `IOleCommandTarget`Umożliwia kontener służący do odbierania poleceń, które pochodzą z interfejsu użytkownika DocObject i pozwala kontenera do wysyłania tych samych poleceń (takie jak nowy, Otwórz, Zapisz jako i drukowania w menu Plik; i kopiowania, wklejania, itd Cofnij w menu Edycja) do DocObject.  
  
 `IOleCommandTarget`jest łatwiejsze niż w przypadku automatyzacji OLE w `IDispatch`. `IOleCommandTarget`całkowicie zależy zestaw standardowych poleceń to rzadko ma argumentów i uczestniczy nie informacji o typie (typ bezpieczeństwa będzie mniejsza dla argumentów polecenia również). Jeśli potrzebujesz wysyłania poleceń z argumentami, użyj [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).  
  
 `IOleCommandTarget` Polecenia standardowe menu realizowane przez MFC w następujące makra:  
  
 **ON_OLECMD_CLEARSELECTION —)**  
  
 Wywołuje polecenie Edytuj Wyczyść. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`  
  
 **ON_OLECMD_COPY —)**  
  
 Wywołuje polecenie Edytuj kopiowania. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`  
  
 **ON_OLECMD_CUT —)**  
  
 Wywołuje polecenie Edytuj Wytnij. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`  
  
 **ON_OLECMD_NEW —)**  
  
 Wywołuje polecenia nowy plik. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`  
  
 **ON_OLECMD_OPEN —)**  
  
 Wywołuje polecenia Otwórz plik. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`  
  
 **ON_OLECMD_PAGESETUP —)**  
  
 Wywołuje polecenie Ustawienia strony pliku. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`  
  
 **ON_OLECMD_PASTE —)**  
  
 Wywołuje polecenie Edytuj Wklej. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`  
  
 **ON_OLECMD_PASTESPECIAL —)**  
  
 Wywołuje polecenie Edytuj Wklej specjalne. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`  
  
 **ON_OLECMD_PRINT —)**  
  
 Wywołuje polecenie drukowania pliku. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`  
  
 **ON_OLECMD_PRINTPREVIEW —)**  
  
 Wywołuje polecenie Podgląd wydruku z pliku. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`  
  
 **ON_OLECMD_REDO —)**  
  
 Wywołuje polecenie Edytuj wykonaj ponownie. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`  
  
 **ON_OLECMD_SAVE —)**  
  
 Wywołuje polecenie Zapisz plik. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`  
  
 **ON_OLECMD_SAVE_AS —)**  
  
 Wywołuje polecenia Zapisz jako plik. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`  
  
 **ON_OLECMD_SAVE_COPY_AS —)**  
  
 Wywołuje plik polecenia Zapisz jako. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`  
  
 **ON_OLECMD_SELECTALL —)**  
  
 Wywołuje polecenie Edytuj Zaznacz wszystko. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`  
  
 **ON_OLECMD_UNDO —)**  
  
 Wywołuje polecenie Cofnij Edytuj. Zaimplementowane jako:  
  
 `ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdocob.h  
  
### <a name="see-also"></a>Zobacz też  
 [Klasa COleCmdUI](colecmdui-class.md)   
 [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)

## <a name="on_registered_message"></a>ON_REGISTERED_MESSAGE —
Windows **RegisterWindowMessage** funkcja służy do definiowania nowych komunikatów okien, który jest musi być unikatowy w całym systemie.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `nMessageVariable`  
 Zmienna Identyfikatora zarejestrowanych komunikatów okien.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 To makro wskazuje funkcji obsługi komunikatów zarejestrowanych.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [obsługi wiadomości i mapowania tematy](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Przykład  
```cpp  
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));


BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmsg_.h  
  
### <a name="see-also"></a>Zobacz też  
 [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)   
 [Programy obsługi zdefiniowane przez użytkownika](user-defined-handlers.md)

## <a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE —    
Wskazuje, funkcji obsługi wiadomości, w zarejestrowany przez funkcję RegisterWindowMessage systemu Windows.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `nMessageVariable`  
 Zmienna Identyfikatora zarejestrowanych komunikatów okien.  
  
 `memberFxn`  
 Nazwę funkcji cwinthread — program obsługi komunikatów, na który jest mapowany wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 RegisterWindowMessage służy do definiowania nowych komunikatów okien, który jest musi być unikatowy w całym systemie. On_registered_thread_message — należy użyć zamiast on_registered_message — Jeśli masz cwinthread — klasa. 
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmsg_.h  

## <a name="on_thread_message"></a>ON_THREAD_MESSAGE —  
Wskazuje, funkcji obsługi wiadomości zdefiniowane przez użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_THREAD_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `message`  
 Identyfikator komunikatu.  
  
 `memberFxn`  
 Nazwa `CWinThread`-wiadomości-funkcji obsługi zamapowany wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 `ON_THREAD_MESSAGE`należy użyć zamiast `ON_MESSAGE` Jeśli masz `CWinThread` klasy. Zdefiniowane przez użytkownika wiadomości są komunikaty, które nie są standardowe Windows **WM_MESSAGE** wiadomości. Powinien istnieć dokładnie jeden `ON_THREAD_MESSAGE` oświadczenie makra mapy wiadomości dla każdej wiadomości zdefiniowane przez użytkownika, który musi być zamapowany na funkcję obsługi wiadomości.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  

## <a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI —    
To makro wskazuje funkcji obsługi wiadomości polecenia aktualizacji interfejsu użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_UPDATE_COMMAND_UI( id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator komunikatu.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Powinien istnieć dokładnie jeden `ON_UPDATE_COMMAND_UI` oświadczenie makra mapy komunikatów dla każdego polecenia aktualizacji interfejsu użytkownika, które musi być zamapowany na funkcję obsługi wiadomości.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [obsługi wiadomości i mapowania tematy](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
### <a name="see-also"></a>Zobacz też  
 [Ccmdui — klasa](ccmdui-class.md)

## <a name="on_command_range"></a>ON_COMMAND_RANGE —  
Umożliwia to makro zmapować ciągły zakres identyfikatorów poleceń funkcji obsługi wiadomości.  
  
### <a name="syntax"></a>Składnia
  
```  
ON_COMMAND_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `id1`  
 Identyfikator polecenia na początku ciągły zakres identyfikatorów poleceń.  
  
 `id2`  
 Identyfikator polecenia na końcu ciągły zakres identyfikatorów poleceń.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany poleceń.  
  
### <a name="remarks"></a>Uwagi  
 Zakres identyfikatorów rozpoczyna się od `id1` i kończy `id2`.  
  
 Użyj `ON_COMMAND_RANGE` Aby zmapować zakres identyfikatorów poleceń funkcji jednego członka. Użyj [on_command —](#on_command) do mapowania funkcji członkowskiej jednego polecenia. Tylko jeden wpis mapy komunikatów można dopasować identyfikatora dla danego polecenia. Oznacza to, że nie można zamapować polecenia na więcej niż jednej procedury obsługi. Aby uzyskać więcej informacji na zakresy wiadomości mapowania, zobacz [programy obsługi dla zakresów Map komunikatów](../../mfc/handlers-for-message-map-ranges.md).  
  
 Nie automatycznej obsługi dla zakresów map komunikatów, więc możesz makra należy umieścić.  
  
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

## <a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE —    
Mapuje ciągły zakres identyfikatorów poleceń do pojedynczej aktualizacji funkcji obsługi wiadomości.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `id1`  
 Identyfikator polecenia na początku ciągły zakres identyfikatorów poleceń.  
  
 `id2`  
 Identyfikator polecenia na końcu ciągły zakres identyfikatorów poleceń.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości aktualizacji zamapowany poleceń.  
  
### <a name="remarks"></a>Uwagi  
 Programy obsługi wiadomości aktualizacji zaktualizowany stan elementów menu i przycisków paska narzędzi skojarzonego z poleceniem. Zakres identyfikatorów rozpoczyna się od `id1` i kończy `id2`.  
  
 Nie automatycznej obsługi dla zakresów map komunikatów, więc możesz makra należy umieścić.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmsg_.h  

## <a name="on_control_range"></a>ON_CONTROL_RANGE —     
Umożliwia to makro mapy ciągły zakres kontroli identyfikatorów do funkcji obsługi wiadomości dla określonego komunikatu powiadomień systemu Windows, takich jak **BN_CLICKED**.  
  
### <a name="syntax"></a>Składnia  
  
```  
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `wNotifyCode`  
 Kod powiadomienia, któremu odpowiada programu obsługi.  
  
 `id1`  
 Identyfikator polecenia na początku ciągły zakres kontroli identyfikatorów.  
  
 `id2`  
 Identyfikator polecenia na końcu ciągły zakres kontroli identyfikatorów.  
  
 `memberFxn`  
 Nazwa funkcji obsługi wiadomości zamapowany kontrolki.  
  
### <a name="remarks"></a>Uwagi  
 Zakres identyfikatorów rozpoczyna się od `id1` i kończy `id2`. Program obsługi jest wywoływana dla określonego powiadomienia pochodzące od dowolnej spośród zamapowanych formantów.  
  
 Nie automatycznej obsługi dla zakresów map komunikatów, więc możesz makra należy umieścić.  
  
 Aby uzyskać więcej informacji na implementacji funkcji programu obsługi dla zakresu kontroli identyfikatorów odwoływać się do [programy obsługi dla zakresów Map komunikatów](../../mfc/handlers-for-message-map-ranges.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmsg_.h  
  


