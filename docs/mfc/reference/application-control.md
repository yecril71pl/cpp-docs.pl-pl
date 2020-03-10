---
title: Sterowanie aplikacjami
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855695"
---
# <a name="application-control"></a>Sterowanie aplikacjami

Mechanizm OLE wymaga istotnej kontroli nad aplikacjami i ich obiektami. Biblioteki DLL systemu OLE muszą mieć możliwość automatycznego uruchamiania i zwalniania aplikacji, koordynowania ich produkcji i modyfikacji obiektów itd. Funkcje w tym temacie spełniają te wymagania. Oprócz wywoływania przez biblioteki DLL systemu OLE, funkcje te muszą być również czasami wywoływane przez aplikacje.

### <a name="application-control"></a>Sterowanie aplikacjami

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Wskazuje, czy aplikacja może zostać przerwana.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Pobiera bieżący filtr komunikatów aplikacji.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Pobiera bieżącą flagę kontroli użytkownika.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Ustawia lub czyści flagę kontroli użytkownika.|
|[Metodę AfxOleLockApp](#afxolelockapp)|Zwiększa globalną liczbę aktywnych obiektów w aplikacji.|
|[AfxOleLockControl](#afxolelockcontrol)| Blokuje fabrykę klasy określonej kontrolki. |
|[Funkcję AfxOleUnlockApp](#afxoleunlockapp)|Zmniejsza liczbę aktywnych obiektów w aplikacji na platformie.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Odblokowuje fabrykę klasy określonej kontrolki. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Rejestruje serwer w rejestrze systemu OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementuje interfejs użytkownika dla polecenia obiektu *TypeName* .|

##  <a name="afxolecanexitapp"></a>AfxOleCanExitApp

Wskazuje, czy aplikacja może zostać przerwana.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli aplikacja może zostać zakończona; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacja nie powinna kończyć się, jeśli istnieją zaległe odwołania do jego obiektów. Funkcje globalne `AfxOleLockApp` i `AfxOleUnlockApp` zwiększają i zmniejszają odpowiednio licznik odwołań do obiektów aplikacji. Aplikacja nie powinna kończyć się, gdy ten licznik ma wartość różną od zera. Jeśli licznik ma wartość różną od zera, okno główne aplikacji jest ukryte (nie zostało zniszczone), gdy użytkownik wybierze opcję Zamknij z menu systemowego lub wyjście z menu plik. Struktura wywołuje tę funkcję w `CFrameWnd::OnClose`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek**: AFXDISP. h

##  <a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

Pobiera bieżący filtr komunikatów aplikacji.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do bieżącego filtru komunikatów.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby uzyskać dostęp do bieżącego obiektu pochodnego `COleMessageFilter`, tak jak wywołasz `AfxGetApp`, aby uzyskać dostęp do bieżącego obiektu aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxwin. h

##  <a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

Pobiera bieżącą flagę kontroli użytkownika.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli użytkownik ma kontrolę nad aplikacją; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użytkownik ma kontrolę nad aplikacją, gdy użytkownik jawnie otworzył lub utworzył nowy dokument. Użytkownik jest również w kontrolce, jeśli aplikacja nie została uruchomiona przez biblioteki DLL systemu OLE — innymi słowy, jeśli użytkownik uruchomił aplikację przy użyciu powłoki systemowej.

### <a name="requirements"></a>Wymagania

**Nagłówek**: AFXDISP. h

##  <a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Ustawia lub czyści flagę kontroli użytkownika, która jest wyjaśniona w odwołaniu dla `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parametry

*bUserCtrl*<br/>
Określa, czy flaga kontrolki użytkownika ma być ustawiona lub wyczyszczona.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję, gdy użytkownik tworzy lub ładuje dokument, ale nie gdy dokument jest ładowany lub tworzony za pośrednictwem akcji pośredniej, takiej jak ładowanie osadzonego obiektu z aplikacji kontenera.

Wywołaj tę funkcję, jeśli inne akcje w aplikacji powinny spowodować, że użytkownik będzie kontrolować aplikację.

### <a name="requirements"></a>Wymagania

**Nagłówek**: AFXDISP. h

##  <a name="afxolelockapp"></a>Metodę AfxOleLockApp

Zwiększa globalną liczbę aktywnych obiektów w aplikacji.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Uwagi

Platforma utrzymuje liczbę obiektów aktywnych w aplikacji. `AfxOleLockApp` i `AfxOleUnlockApp` funkcje odpowiednio, zwiększają i zmniejszają liczbę.

Gdy użytkownik próbuje zamknąć aplikację, która ma aktywne obiekty — aplikacja, dla której liczba aktywnych obiektów jest różna od zera — struktura ukrywa aplikację z widoku użytkownika, a nie całkowicie zamyka ją. Funkcja `AfxOleCanExitApp` wskazuje, czy aplikacja może zostać przerwana.

Wywołaj `AfxOleLockApp` z dowolnego obiektu, który uwidacznia interfejsy OLE, jeśli byłoby niepożądane dla tego obiektu, gdy jest nadal używany przez aplikację kliencką. Wywołaj również `AfxOleUnlockApp` w destruktorze dowolnego obiektu, który wywołuje `AfxOleLockApp` w konstruktorze. Domyślnie `COleDocument` (i klasy pochodne) automatycznie blokują i blokują aplikację.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek**: AFXDISP. h

##  <a name="afxoleunlockapp"></a>Funkcję AfxOleUnlockApp

Zmniejsza liczbę aktywnych obiektów w aplikacji.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz `AfxOleLockApp`.

Gdy liczba aktywnych obiektów osiągnie zero, `AfxOleOnReleaseAllObjects` jest wywoływana.

### <a name="example"></a>Przykład

Zobacz przykład dla [metodę AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Wymagania

**Nagłówek**: AFXDISP. h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Blokuje fabrykę klasy określonej kontrolki, tak aby dynamiczne utworzone dane skojarzone z kontrolką pozostawały w pamięci.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Unikatowy identyfikator klasy formantu.

*lpszProgID*<br/>
Unikatowy identyfikator programu kontrolki.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli fabryka klas formantu została pomyślnie zablokowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Może to znacznie przyspieszyć wyświetlanie kontrolek. Na przykład po utworzeniu kontrolki w oknie dialogowym i zablokowaniu kontrolki z `AfxOleLockControl`nie trzeba jej tworzyć i Wykasuj ponownie za każdym razem, gdy okno dialogowe jest wyświetlane lub zniszczone. Jeśli użytkownik otworzy i zamknie okno dialogowe wielokrotnie, zablokowanie kontrolek może znacząco zwiększyć wydajność. Gdy wszystko jest gotowe do zniszczenia kontrolki, wywołaj `AfxOleUnlockControl`.

### <a name="example"></a>Przykład

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

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

*Identyfikator*<br/>
Odwołanie do identyfikatora klasy OLE serwera.

*lpszClassName*<br/>
Wskaźnik na ciąg zawierający nazwę klasy obiektów serwera.

*lpszShortTypeName*<br/>
Wskaźnik do ciągu zawierającego krótką nazwę typu obiektu serwera, na przykład "wykres".

*lpszLongTypeName*<br/>
Wskaźnik na ciąg zawierający długą nazwę typu obiektu serwera, na przykład "wykres programu Microsoft Excel 5,0".

*nAppType*<br/>
Wartość pobierana z wyliczenia OLE_APPTYPE, określając typ aplikacji OLE. Możliwe wartości są następujące:

- Serwer OAT_INPLACE_SERVER ma pełny interfejs użytkownika serwera.

- Serwer OAT_SERVER obsługuje tylko osadzanie.

- Kontener OAT_CONTAINER obsługuje linki do osadzania.

- OAT_DISPATCH_OBJECT obiekt z możliwością `IDispatch`.

*rglpszRegister*<br/>
Tablica wskaźników do ciągów reprezentujących klucze i wartości, które mają zostać dodane do rejestru systemu OLE, jeśli nie zostaną znalezione istniejące wartości kluczy.

*rglpszOverwrite*<br/>
Tablica wskaźników do ciągów reprezentujących klucze i wartości, które mają zostać dodane do rejestru systemu OLE, jeśli Rejestr zawiera istniejące wartości dla danego klucza.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli Klasa serwera została pomyślnie zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Większość aplikacji może używać `COleTemplateServer::Register` do rejestrowania typów dokumentów aplikacji. Jeśli format rejestru systemowego aplikacji nie pasuje do typowego wzorca, można użyć `AfxOleRegisterServerClass`, aby uzyskać większą kontrolę.

Rejestr składa się z zestawu kluczy i wartości. Argumenty *rglpszRegister* i *rglpszOverwrite* są tablicami wskaźników do ciągów, każdy składający się z klucza i wartości oddzielonych znakiem **null** (`'\0'`). Każdy z tych ciągów może mieć wymienne parametry, których miejsca są oznaczone przez sekwencje znaków *%1* za pomocą *%5*.

Symbole są wypełniane w następujący sposób:

|Symbol|Wartość|
|------------|-----------|
|%1|Identyfikator klasy sformatowany jako ciąg|
|%2|Nazwa klasy|
|%3|Ścieżka do pliku wykonywalnego|
|%4|Nazwa typu short|
|%5|Nazwa typu Long|

### <a name="requirements"></a>Wymagania

**Nagłówek**: AFXDISP. h

##  <a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

Implementuje interfejs użytkownika dla polecenia obiektu *TypeName* .

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

*pClient*<br/>
Wskaźnik do elementu OLE klienta.

*pMenu*<br/>
Wskaźnik do obiektu menu, który ma zostać zaktualizowany.

*iMenuItem*<br/>
Indeks elementu menu, który ma zostać zaktualizowany.

*nIDVerbMin*<br/>
Identyfikator polecenia, który odnosi się do podstawowego zlecenia.

*nIDVerbMax*<br/>
Identyfikator polecenia, który odnosi się do ostatniego zlecenia.

*nIDConvert*<br/>
Identyfikator elementu menu konwersji.

### <a name="remarks"></a>Uwagi

Jeśli serwer rozpoznaje tylko zlecenie podstawowe, element menu przyjmuje wartość "obiekt *TypeName* zlecenia" i polecenie *nIDVerbMin* jest wysyłane, gdy użytkownik wybierze polecenie. Jeśli serwer rozpoznaje kilka czasowników, element menu zmieni się na "obiekt *TypeName* " i podmenu wyświetlające wszystkie zlecenia są wyświetlane, gdy użytkownik wybierze polecenie. Gdy użytkownik wybierze czasownik z podmenu, *nIDVerbMin* jest wysyłane w przypadku wybrania pierwszego zlecenia, *nIDVerbMin* + 1 jest wysyłane, jeśli drugie zlecenie zostanie wybrane i tak dalej. Domyślna implementacja `COleDocument` automatycznie obsługuje tę funkcję.

W skrypcie zasobów aplikacji klienta należy wykonać następujące instrukcje: RC):

**#include \<Afxolecl. RC >**

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxole. h

## <a name="afxoleunlockcontrol"></a>AfxOleUnlockControl

Odblokowuje fabrykę klasy określonej kontrolki.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Unikatowy identyfikator klasy formantu.

*lpszProgID*<br/>
Unikatowy identyfikator programu kontrolki.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli fabryka klas formantu została pomyślnie odblokowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Kontrolka jest zablokowana z `AfxOleLockControl`, dzięki czemu dynamiczne utworzone dane skojarzone z kontrolką pozostają w pamięci. Może to znacznie przyspieszyć wyświetlanie kontrolki, ponieważ formant nie musi być tworzony i niszczony za każdym razem, gdy jest wyświetlany. Gdy wszystko jest gotowe do zniszczenia kontrolki, wywołaj `AfxOleUnlockControl`.

### <a name="example"></a>Przykład

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)<br/>
