---
title: Sterowanie aplikacjami
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612303"
---
# <a name="application-control"></a>Sterowanie aplikacjami

OLE wymaga znacznej kontroli nad aplikacjami i ich obiektami. OLE systemowych bibliotek DLL musi mieć możliwość uruchamiania i automatyczne wydanie aplikacji, koordynowania ich produkcji i modyfikacji obiektów i tak dalej. Funkcje, w tym temacie spełniają te wymagania. Oprócz wywoływana przez OLE systemowych bibliotek DLL, te funkcje czasami musi zostać wywołany przez aplikacje, jak również.

### <a name="application-control"></a>Sterowanie aplikacjami

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Wskazuje, czy aplikacja może zakończyć.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Pobiera bieżący filtr komunikatów aplikacji.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Pobiera bieżące flagi kontrolki użytkownika.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Ustawia lub czyści flagi kontrolki użytkownika.|
|[AfxOleLockApp](#afxolelockapp)|Zwiększa liczbę globalnego struktury liczby aktywnych obiektów w aplikacji.|
|[AfxOleLockControl](#afxolelockcontrol)| Blokuje fabryki klas z określoną kontrolkę. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Dekrementuje struktury liczbę obiektów aktywnych w aplikacji.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Odblokowuje fabryki klas z określoną kontrolkę. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Rejestruje serwer w rejestrze systemowym OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementuje interfejs użytkownika dla *typename* obiekt polecenia.|

##  <a name="afxolecanexitapp"></a>  Afxolecanexitapp —

Wskazuje, czy aplikacja może zakończyć.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli aplikacja może zakończyć; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aplikacji nie powinna kończyć, w przypadku innych odwołań do obiektów. Funkcje globalne `AfxOleLockApp` i `AfxOleUnlockApp` zwiększyć i zmniejszyć, odpowiednio, licznik odwołań do obiektów w aplikacji. Aplikacji nie powinna zakończyć, gdy ten licznik jest różna od zera. Jeśli licznik jest różna od zera, okna głównego aplikacji jest ukryty (nie zniszczonego), gdy użytkownik wybierze zamknięcia z menu systemowego lub Zakończ w menu Plik. Struktura wywołuje tę funkcję `CFrameWnd::OnClose`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

##  <a name="afxolegetmessagefilter"></a>  Afxolegetmessagefilter —

Pobiera bieżący filtr komunikatów aplikacji.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego filtra wiadomości.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dostęp do bieżącego `COleMessageFilter`-pochodnych obiektu, tak samo, jak możesz wywołać `AfxGetApp` dostępu do bieżącego obiektu aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxwin.h

##  <a name="afxolegetuserctrl"></a>  AfxOleGetUserCtrl

Pobiera bieżące flagi kontrolki użytkownika.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli użytkownik znajduje się w kontrolce aplikacji; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użytkownik znajduje się w kontroli aplikacji, gdy użytkownik ma jawnie otworzyć lub utworzyć nowy dokument. Użytkownik znajduje się również w kontrolce, jeśli aplikacja nie została uruchomiona przez system OLE biblioteki DLL — innymi słowy, jeśli użytkownik uruchomić aplikację z powłoką systemu.

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>  AfxOleSetUserCtrl

Ustawia lub czyści flagi kontrolki użytkownika, które wyjaśniono w odwołaniu do `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parametry

*bUserCtrl*<br/>
Określa, czy flaga kontrolki użytkownika ma być ustawiane lub czyszczone.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję, gdy użytkownik tworzy lub ładuje dokument, ale nie wtedy, gdy dokument jest załadowany lub utworzone za pomocą działań pośrednich, takich jak ładowanie osadzonego obiektu z aplikacji kontenera.

Wywołaj tę funkcję, jeśli inne akcje w aplikacji należy umieścić użytkownika w kontrolce aplikacji.

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

##  <a name="afxolelockapp"></a>  AfxOleLockApp

Zwiększa liczbę globalnego struktury liczby aktywnych obiektów w aplikacji.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Uwagi

Struktura przechowuje liczbę obiektów aktywnych w aplikacji. `AfxOleLockApp` i `AfxOleUnlockApp` funkcje, odpowiednio zwiększyć i zmniejszyć ta liczba.

Gdy użytkownik próbuje zamknąć aplikację, która ma obiekty usługi active — aplikację, dla którego jest różna od zera łącznej liczby aktywnych obiektów — struktura ukrywa aplikację z punktu widzenia użytkownika zamiast całkowicie zamykania. `AfxOleCanExitApp` Funkcji wskazuje, czy aplikacja może zakończyć.

Wywołaj `AfxOleLockApp` z dowolnego obiektu, który uwidacznia interfejsy OLE, jeśli będzie niepożądane dla tego obiektu, które mają zostać zniszczone, gdy był używany przez aplikację kliencką. Również wywołać `AfxOleUnlockApp` w destruktorze dowolnego obiektu, który wywołuje `AfxOleLockApp` w konstruktorze. Domyślnie `COleDocument` (i klas pochodnych) automatyczne blokowanie i odblokowywanie aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

##  <a name="afxoleunlockapp"></a>  AfxOleUnlockApp

Dekrementuje struktury łącznej liczby aktywnych obiektów w aplikacji.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Uwagi

Zobacz `AfxOleLockApp` Aby uzyskać więcej informacji.

Gdy liczba obiektów active osiągnie zero, `AfxOleOnReleaseAllObjects` jest wywoływana.

### <a name="example"></a>Przykład

Zobacz przykład [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Blokuje fabryki klas z określoną kontrolkę tak, aby dynamicznie utworzoną danych skojarzonego z kontrolką pozostaje w pamięci.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
Identyfikator unikatowy klasy kontrolki.

*lpszProgID*<br/>
Unikatowy identyfikator kontrolki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli fabryka klas formantu zostało pomyślnie zablokowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

To znacznie przyspieszyć wyświetlanie kontrolki. Na przykład, po Tworzenie formantu w oknie dialogowym i przy zablokować kontrolki z `AfxOleLockControl`, nie trzeba tworzyć i zamknij go ponownie za każdym razem, gdy okno dialogowe jest wyświetlane lub zniszczenia obiektu. Jeśli użytkownik otwiera i zamyka okno dialogowe wielokrotnie, blokowanie formantów mogą znacznie poprawić wydajność. Gdy wszystko jest gotowe do zniszczenia kontrolki, należy wywołać `AfxOleUnlockControl`.

### <a name="example"></a>Przykład

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="afxoleregisterserverclass"></a>  AfxOleRegisterServerClass

Ta funkcja umożliwia zarejestrować serwer w rejestrze systemowym OLE.

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

*Identyfikator klasy*<br/>
Odwołanie do identyfikator serwera OLE klasy.

*lpszClassName*<br/>
Wskaźnik do ciągu zawierającego nazwę klasy obiektów serwera.

*lpszShortTypeName*<br/>
Wskaźnik do ciągu zawierającego krótką nazwę typu obiektu serwera, na przykład "Chart".

*lpszLongTypeName*<br/>
Wskaźnik do ciągu zawierającego długa nazwa typ obiektu serwera, na przykład "Wykres programu Microsoft Excel 5.0".

*nAppType*<br/>
Wartość z wyliczenia OLE_APPTYPE, określając typ aplikacji OLE. Możliwe wartości są następujące:

- OAT_INPLACE_SERVER serwer ma interfejs użytkownika pełny serwer.

- OAT_SERVER Server obsługuje tylko osadzania.

- Kontener OAT_CONTAINER obsługuje linki do wbudowanych elementów.

- OAT_DISPATCH_OBJECT `IDispatch`— zdolne do obiektu.

*rglpszRegister*<br/>
Tablica wskaźników do ciągów reprezentujących kluczy i wartości, które ma zostać dodany do rejestru systemowego OLE, jeśli nie zostaną znalezione nie istniejące wartości kluczy.

*rglpszOverwrite*<br/>
Tablica wskaźników do ciągów reprezentujących kluczy i wartości, które ma zostać dodany do rejestru systemowego OLE, jeśli rejestr zawiera istniejące wartości dla danych kluczy.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli klasa serwera po pomyślnym zarejestrowaniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Większość aplikacji można użyć `COleTemplateServer::Register` zarejestrować typy dokumentów aplikacji. Jeśli format rejestru systemowego aplikacji nie mieści się typowy wzorzec, możesz użyć `AfxOleRegisterServerClass` Aby uzyskać większą kontrolę.

Rejestr zawiera zestaw kluczy i wartości. *RglpszRegister* i *rglpszOverwrite* argumenty są tablicami, wskaźnikami do ciągów, składający się z klucza i wartości oddzielonych **NULL** znak ( `'\0'`). Każdy z tych ciągów może mieć parametrów zastępowalnych miejsca, w których są oznaczone przez sekwencje znaków *%1* za pośrednictwem *%5*.

Symbole są wypełnione w następujący sposób:

|Symbol|Wartość|
|------------|-----------|
|%1|Identyfikator klasy, sformatowany jako ciąg|
|%2|Nazwa klasy|
|%3|Ścieżka do pliku wykonywalnego|
|%4|Nazwa typu krótkiego|
|%5|Nazwa typu Long|

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>  AfxOleSetEditMenu

Implementuje interfejs użytkownika dla *typename* obiekt polecenia.

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
Wskaźnik do elementu klienta OLE.

*pMenu*<br/>
Wskaźnik do obiektu menu do zaktualizowania.

*iMenuItem*<br/>
Indeks elementu menu aktualizacji.

*nIDVerbMin*<br/>
Identyfikator polecenia, który odpowiada primary — zlecenie.

*nIDVerbMax*<br/>
Identyfikator polecenia, który odnosi się do ostatniego zlecenie.

*nIDConvert*<br/>
Identyfikator elementu menu konwersji.

### <a name="remarks"></a>Uwagi

Jeśli serwer rozpoznaje tylko primary — zlecenie, staje się element menu "zlecenie *typename* obiektu" i *nIDVerbMin* polecenia jest wysyłana, gdy użytkownik wybierze polecenie. Jeśli serwer rozpoznaje kilka poleceń, a następnie staje się element menu " *typename* obiektu" i pojawia się podmenu wszystkie zlecenia, gdy użytkownik wybierze polecenie. Gdy użytkownik wybierze czasownika w podmenu *nIDVerbMin* są wysyłane, jeśli zostanie wybrany pierwsze zlecenie, *nIDVerbMin* + 1 są wysyłane, jeśli drugie polecenie jest wybrana i tak dalej. Wartość domyślna `COleDocument` implementacji automatycznie obsługuje tę funkcję.

Musi mieć następującą instrukcję w skrypcie zasobów aplikacji klienta (. Plik RC):

**#include \<afxolecl.rc >**

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxole.h

## <a name="afxoleunlockcontrol"></a> AfxOleUnlockControl

Odblokowuje fabryki klas z określoną kontrolkę.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
Identyfikator unikatowy klasy kontrolki.

*lpszProgID*<br/>
Unikatowy identyfikator kontrolki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli fabryka klas formantu zostało pomyślnie odblokowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Kontrolka jest zablokowana z `AfxOleLockControl`, dzięki czemu dynamicznie utworzoną danych skojarzonego z kontrolką pozostaje w pamięci. To znacznie przyspieszyć wyświetlanie formantu, ponieważ kontrolki nie muszą być tworzone i zniszczone za każdym razem, gdy jest on wyświetlany. Gdy wszystko jest gotowe do zniszczenia kontrolki, należy wywołać `AfxOleUnlockControl`.

### <a name="example"></a>Przykład

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
