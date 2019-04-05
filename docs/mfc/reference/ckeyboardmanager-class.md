---
title: Klasa CKeyboardManager
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: 3360a28d50f64546837cc5ef35dcfc761b4fb0f5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58779810"
---
# <a name="ckeyboardmanager-class"></a>Klasa CKeyboardManager

Zarządza tabelami klawiszy skrótów dla głównej ramki okna i okien ramek podrzędnych.

## <a name="syntax"></a>Składnia

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Konstruuje `CKeyboardManager` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CKeyboardManager::CleanUp](#cleanup)|Czyści tabelami klawiszy skrótów.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Pobiera domyślny klucz skrótu dla określonego polecenia i okna.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Określa, czy klucz jest obsługiwany przez tabeli klawiszy skrótu.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Wskazuje, czy znak drukowalny.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Wskazuje, czy menu pokazywania wszystkich klawiszy skrótów dla polecenia lub klawisza skrótu domyślne.|
|[CKeyboardManager::LoadState](#loadstate)|Ładuje tabelami klawiszy skrótów z rejestru Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Ponownie ładuje tabelami klawiszy skrótów z zasobu aplikacji.|
|[CKeyboardManager::SaveState](#savestate)|Zapisuje skrót tabel kluczy rejestru Windows.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Określa, czy ramach Wyświetla wszystkie klawisze skrótów dla wszystkich poleceń, z jednym klawiszem skrótu dla każdego polecenia. Ta metoda nie ma wpływu na polecenia, które mają tylko jeden klucz skojarzony skrótów.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Konwertuje znak do jego górnej rejestru.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualizuje tabelę klawiszy skrótów przy użyciu nowej tabeli klawiszy skrótu.|

## <a name="remarks"></a>Uwagi

Elementy członkowskie tej klasy umożliwiają zapisywanie i ładowanie tabelami klawiszy skrótów do rejestru Windows, zaktualizować tabelami klawiszy skrótów przy użyciu szablonu i Znajdź domyślne klawisz skrótu polecenia w oknie ramki. Ponadto `CKeyboardManager` obiekt umożliwia kontrolowanie sposobu wyświetlania klawiszy skrótów do użytkownika.

Nie należy tworzyć `CKeyboardManager` obiektu ręcznie. Zostanie on utworzony automatycznie przez strukturę aplikacji. Jednakże, należy wywołać [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) podczas procesu inicjowania aplikacji. Aby uzyskać wskaźnik do Menedżera klawiatury dla aplikacji, należy wywołać [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak pobrać wskaźnika do `CKeyboardManager` obiektu z `CWinAppEx` klasy i sposób wyświetlania wszystkich klawiszy skrótów, skojarzone z poleceń menu. Ten fragment kodu jest częścią [przykładowe niestandardowych stron](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeyboardmanager.h

##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager

Konstruuje `CKeyboardManager` obiektu.

```
CKeyboardManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba tworzyć `CKeyboardManager` bezpośrednio. Domyślnie struktura utworzy go dla Ciebie. Aby uzyskać wskaźnik do `CKeyboardManager`, wywołaj [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Jeśli możesz utworzyć ręcznie, należy go zainicjować za pomocą metody [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

##  <a name="cleanup"></a>  CKeyboardManager::CleanUp

Zwalnia `CKeyboardManager` zasobów i czyści wszystkie mapowania klawiszy skrótów.

```
static void CleanUp();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat klawiszy skrótów, zobacz [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md).

Nie trzeba wywołać tę funkcję, gdy aplikacja zakończy działanie, ponieważ struktura wywołuje on automatycznie podczas zamknięcie aplikacji.

##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator

Pobiera domyślny klucz skrótu dla określonego polecenia i okna.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Identyfikator polecenia.

*str*<br/>
[out] Odwołanie do `CString` obiektu.

*pWndFrame*<br/>
[in] Wskaźnik do ramki okna.

*bIsDefaultFrame*<br/>
[in] Określa, czy okno ramowe domyślnego ramki okna.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli skrót zostanie odnaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Metoda ta wyszukuje polecenie określone przez *uiCmd* i pobiera domyślny klawisza skrótu. Następnie metoda przyjmuje ciągu skojarzonego z tym klawisz skrótu i zapisuje wartość *str* parametru.

##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled

Określa, czy określony klucz jest obsługiwany przez [klasa CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*nKey*|[in] Klucz do sprawdzenia.|
|*fVirt*|[in] Określa zachowanie klawisza skrótu. Aby uzyskać listę możliwych wartości, zobacz [struktury AKCELERACJA](/windows/desktop/api/winuser/ns-winuser-tagaccel).|
|*pWndFrame*|[in] Okno ramki. Ta metoda określa, czy klawisz skrótu jest obsługiwana w tej ramce.|
|*bIsDefaultFrame*|[in] Parametr logiczny, który wskazuje, czy *element pWndFrame* domyślny okna ramki.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli klawisz skrótu jest obsługiwany. Wartość FALSE, jeśli klucz nie jest obsługiwany lub *element pWndFrame* ma wartość NULL.

### <a name="remarks"></a>Uwagi

Parametry wejściowe muszą być zgodne wpisu tabeli akceleratora zarówno dla *nKey* i *fVirt* do określenia, czy klawisz skrótu jest obsługiwana w *element pWndFrame*.

##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable

Wskazuje, czy znak drukowalny.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*nChar*|[in] Znak, który sprawdza, czy ta metoda.|

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli znak jest druku, zero, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli wywołanie [GetKeyboardState](/windows/desktop/api/winuser/nf-winuser-getkeyboardstate) zakończy się niepowodzeniem.

##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators

Wskazuje, czy menu Pokazywanie wszystkich klawiszy skrótów, skojarzone z poleceń menu lub klawiszy skrótów domyślne.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli aplikacja wyświetla listę wszystkich klawiszy skrótów do poleceń menu; 0, jeśli aplikacja wyświetla tylko domyślne klawiszy skrótów.

### <a name="remarks"></a>Uwagi

Aplikacja wyświetla klawiszy skrótów do poleceń menu na pasku menu. Użyj funkcji [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) do kontrolowania tego, czy aplikacja wyświetla listę wszystkich klawiszy skrótów albo po prostu domyślne klawisze.

##  <a name="loadstate"></a>  CKeyboardManager::LoadState

Ładuje tabelami klawiszy skrótów z rejestru Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Ścieżka rejestru gdzie `CKeyboardManager` są zapisywane dane.

*pDefaultFrame*<br/>
[in] Wskaźnik do ramki okna do użycia jako domyślnego okna.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli stan został pomyślnie załadowany lub równa 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli *lpszProfileName* parametr ma wartość NULL, ta metoda sprawdza domyślnej lokalizacji rejestru `CKeyboardManager` danych. Domyślna lokalizacja w rejestrze jest określona przez [klasa CWinAppEx](../../mfc/reference/cwinappex-class.md). Dane muszą być wcześniej napisane przy użyciu metody [CKeyboardManager::SaveState](#savestate).

Jeśli okno domyślnego nie jest określony, będą używane ramką głównego okna aplikacji.

##  <a name="resetall"></a>  CKeyboardManager::ResetAll

Ponownie ładuje tabelami klawiszy skrótów z zasobu aplikacji.

```
void ResetAll();
```

### <a name="remarks"></a>Uwagi

Ta funkcja usuwa skróty przechowywane w `CKeyboardManager` wystąpienia. Następnie będzie ponownie załadować stanu Menedżera klawiatury z zasobu aplikacji.

##  <a name="savestate"></a>  CKeyboardManager::SaveState

Zapisuje skrót tabel kluczy rejestru Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Ścieżka rejestru do zapisywania `CKeyboardManager` stanu.

*pDefaultFrame*<br/>
[in] Wskaźnik do ramki okna, które staje się oknem domyślne.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli stan Menedżera klawiatury została zapisana pomyślnie, lub w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *lpszProfileName* parametr ma wartość NULL, ta metoda będzie zapisywać `CKeyboardManager` do domyślnej lokalizacji podanej przez stanu [klasa CWinAppEx](../../mfc/reference/cwinappex-class.md). Jeśli określisz lokalizacji, można załadować danych później za pomocą metody [CKeyboardManager::LoadState](#loadstate).

Jeśli nie określisz w oknie domyślnej, ramką głównego okna będzie służyć jako domyślnego okna.

##  <a name="showallaccelerators"></a>  CKeyboardManager::ShowAllAccelerators

Przedstawia wszystkie klawisze skrótów skojarzone z poleceń menu.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parametry

*bShowAll*<br/>
[in] W przypadku opcji TRUE będą wyświetlane wszystkie klawisze skrótów. Jeśli ma wartość FAŁSZ, zostanie wyświetlony tylko pierwszy klawisza skrótu.

*lpszDelimiter*<br/>
[in] Ciąg, które zostanie wstawione między klawiszy skrótów. To ogranicznik nie obowiązuje, jeśli tylko jeden klawisz skrótu jest wyświetlana.

### <a name="remarks"></a>Uwagi

Domyślnie jeśli polecenie ma więcej niż jeden klawisz skrótu skojarzony z nim, tylko pierwszy klawisz skrótu będą wyświetlane. Ta funkcja umożliwia listę wszystkich klawiszy skrótów, skojarzone z wszystkich poleceń.

Klawisze skrótów będzie wyświetlane obok polecenia na pasku menu. Jeśli nie są wyświetlane wszystkie klawisze skrótów, ciąg udostępniane przez *lpszDelimiter* będzie oddzielić klawiszy skrótów.

##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper

Konwertuje znak do jego górnej rejestru.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
[in] Znak, który ma zostać przekształcony.

### <a name="return-value"></a>Wartość zwracana

Znak, który jest górny rejestru parametr wejściowy.

##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable

Aktualizuje tabelę klawiszy skrótów przy użyciu nowej tabeli klawiszy skrótu.

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
[in] Wskaźnik do szablonu dokumentu.

*lpAccel*<br/>
[in] Wskaźnik do nowego klawisza skrótu.

*nSize*<br/>
[in] Rozmiar nowa tabela skrótów.

*pDefaultFrame*<br/>
[in] Wskaźnik do domyślnego ramki okna.

*hAccelNew*<br/>
[in] Dojście do nowej tabeli skrótów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja ta jest przydatna w celu zastąpienia istniejącej tabeli skrótów za pomocą nowych kluczy skrótów dla wielu obiektów okna ramki. Funkcja odbiera szablon dokumentu, jako parametr w celu uzyskania dostępu do wszystkich obiektów okna ramki podłączone do danego dokumentu szablonu.

## <a name="see-also"></a>Zobacz także

[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md)
