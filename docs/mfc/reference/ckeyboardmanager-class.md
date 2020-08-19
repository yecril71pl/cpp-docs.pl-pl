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
ms.openlocfilehash: a2d2ae8133310f3a93b6eefc30c67045a47cd94f
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561469"
---
# <a name="ckeyboardmanager-class"></a>Klasa CKeyboardManager

Zarządza tabelami klawiszy skrótów dla okna głównego ramki i podrzędnych okien ramowych.

## <a name="syntax"></a>Składnia

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Konstruuje `CKeyboardManager` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CKeyboardManager:: CleanUp](#cleanup)|Czyści tabele klawiszy skrótów.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Pobiera domyślny klawisz skrótu dla określonego polecenia i okna.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Określa, czy klucz jest obsługiwany przez tabelę akceleratora.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Wskazuje, czy znak jest drukowany.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Wskazuje, czy menu pokaże wszystkie klawisze skrótów dla polecenia, czy tylko domyślnego klawisza skrótu.|
|[CKeyboardManager:: LoadState](#loadstate)|Ładuje tabele klawiszy skrótów z rejestru systemu Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Ponownie ładuje tabele klawiszy skrótów z zasobu aplikacji.|
|[CKeyboardManager:: SaveState](#savestate)|Zapisuje tabele klawiszy skrótów do rejestru systemu Windows.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Określa, czy w strukturze są wyświetlane wszystkie klawisze skrótów dla wszystkich poleceń, czy jeden klawisz skrótu dla każdego polecenia. Ta metoda nie ma wpływu na polecenia z tylko jednym skojarzonym klawiszem skrótu.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Konwertuje znak na jego górny rejestr.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualizuje tablicę klawiszy skrótów za pomocą nowej tabeli klawiszy skrótów.|

## <a name="remarks"></a>Uwagi

Elementy członkowskie tej klasy umożliwiają zapisywanie i załadowanie tabel skrótów do rejestru systemu Windows, używanie szablonu do aktualizowania krótkich tabel z wyciętym kluczem i znajdowanie domyślnego klawisza skrótu dla polecenia w oknie ramki. Ponadto `CKeyboardManager` obiekt umożliwia kontrolowanie sposobu wyświetlania przez użytkownika klawiszy skrótów.

Nie należy tworzyć `CKeyboardManager` obiektu ręcznie. Zostanie ona utworzona automatycznie przez strukturę aplikacji. Należy jednak wywołać [CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) podczas procesu inicjowania aplikacji. Aby uzyskać wskaźnik do Menedżera klawiatury dla aplikacji, wywołaj [CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak pobrać wskaźnik do `CKeyboardManager` obiektu z `CWinAppEx` klasy i jak pokazać wszystkie klawisze skrótów skojarzone z poleceniami menu. Ten fragment kodu jest częścią [przykładu stron niestandardowych](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeyboardmanager. h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a> CKeyboardManager::CKeyboardManager

Konstruuje `CKeyboardManager` obiekt.

```
CKeyboardManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba tworzyć `CKeyboardManager` bezpośredniego. Domyślnie struktura tworzy jedną dla siebie. Aby uzyskać wskaźnik do `CKeyboardManager` , wywołaj [CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Jeśli utworzysz je ręcznie, musisz ją zainicjować przy użyciu metody [CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a> CKeyboardManager:: CleanUp

Zwalnia `CKeyboardManager` zasoby i czyści wszystkie mapowania klawiszy skrótów.

```
static void CleanUp();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat klawiszy skrótów, zobacz [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md).

Nie musisz wywoływać tej funkcji, gdy aplikacja zostanie zakończona, ponieważ struktura wywołuje ją automatycznie podczas kończenia aplikacji.

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a> CKeyboardManager::FindDefaultAccelerator

Pobiera domyślny klawisz skrótu dla określonego polecenia i okna.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia.

*str*<br/>
określoną Odwołanie do `CString` obiektu.

*pWndFrame*<br/>
podczas Wskaźnik do okna ramki.

*bIsDefaultFrame*<br/>
podczas Określa, czy okno ramki jest domyślnym oknem ramek.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zostanie znaleziony skrót; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda wyszukuje polecenie określone przez *uiCmd* i Pobiera domyślny klawisz skrótu. Następnie metoda przyjmuje ciąg skojarzony z tym klawiszem skrótu i zapisuje wartość w parametrze *str* .

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a> CKeyboardManager::IsKeyHandled

Określa, czy określony klucz jest obsługiwany przez [klasę CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parametry

*nKey*\
podczas Klucz do sprawdzenia.

*fVirt*\
podczas Określa zachowanie klawisza skrótu. Aby uzyskać listę możliwych wartości, zobacz [akceleracja Structure](/windows/win32/api/winuser/ns-winuser-accel).

*pWndFrame*\
podczas Okno ramek. Ta metoda określa, czy klawisz skrótu jest obsługiwany w tej ramce.

*bIsDefaultFrame*\
podczas Parametr logiczny, który wskazuje, czy *pWndFrame* jest domyślnym oknem ramek.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli klawisz skrótu jest obsługiwany. Wartość FALSE, jeśli klucz nie jest obsługiwany lub jeśli *pWndFrame* ma wartość null.

### <a name="remarks"></a>Uwagi

Parametry wejściowe muszą być zgodne z wpisem w tabeli akceleratorów dla *nKey* i *fVirt* , aby określić, czy klawisz skrótu jest obsługiwany w *pWndFrame*.

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a> CKeyboardManager::IsKeyPrintable

Wskazuje, czy znak jest drukowany.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*\
podczas Znak, który jest sprawdzany przez tę metodę.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli znak jest drukowany, zero, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli wywołanie [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) zakończy się niepowodzeniem.

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a> CKeyboardManager::IsShowAllAccelerators

Wskazuje, czy menu pokazują wszystkie klawisze skrótów skojarzone z poleceniami menu, czy tylko domyślne klawisze skrótów.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli aplikacja wyświetla wszystkie klawisze skrótów dla poleceń menu; 0, jeśli aplikacja wyświetla tylko domyślne klawisze skrótów.

### <a name="remarks"></a>Uwagi

Aplikacja wyświetla listę klawiszy skrótów dla poleceń menu na pasku menu. Użyj funkcji [CKeyboardManager:: ShowAllAccelerators](#showallaccelerators) , aby określić, czy aplikacja wyświetla wszystkie skróty klawiaturowe, czy tylko domyślne klawisze skrótów.

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a> CKeyboardManager:: LoadState

Ładuje tabele klawiszy skrótów z rejestru systemu Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Ścieżka rejestru, w której `CKeyboardManager` zapisywane są dane.

*pDefaultFrame*<br/>
podczas Wskaźnik do okna ramki, który ma być używany jako okno domyślne.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli stan został pomyślnie załadowany lub 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli parametr *lpszProfileName* ma wartość null, ta metoda sprawdza domyślną lokalizację rejestru dla `CKeyboardManager` danych. Domyślna lokalizacja rejestru jest określana przez [klasę CWinAppEx](../../mfc/reference/cwinappex-class.md). Dane muszą być wcześniej zapisywane przy użyciu metody [CKeyboardManager:: SaveState](#savestate).

Jeśli nie określisz okna domyślnego, zostanie użyte okno głównej ramki aplikacji.

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a> CKeyboardManager::ResetAll

Ponownie ładuje tabele klawiszy skrótów z zasobu aplikacji.

```cpp
void ResetAll();
```

### <a name="remarks"></a>Uwagi

Ta funkcja czyści skróty przechowywane w `CKeyboardManager` wystąpieniu. Spowoduje to ponowne załadowanie stanu Menedżera klawiatury z zasobu aplikacji.

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a> CKeyboardManager:: SaveState

Zapisuje tabele klawiszy skrótów do rejestru systemu Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Ścieżka rejestru służąca do zapisywania `CKeyboardManager` stanu.

*pDefaultFrame*<br/>
podczas Wskaźnik do okna ramki, które jest oknem domyślnym.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli stan Menedżera klawiatury został pomyślnie zapisany lub 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli parametr *lpszProfileName* ma wartość null, Metoda zapisze stan w `CKeyboardManager` domyślnej lokalizacji określonej przez [klasę CWinAppEx](../../mfc/reference/cwinappex-class.md). Jeśli określisz lokalizację, możesz załadować dane później przy użyciu metody [CKeyboardManager:: LoadState](#loadstate).

Jeśli nie określisz okna domyślnego, okno głównej ramki będzie używane jako okno domyślne.

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a> CKeyboardManager::ShowAllAccelerators

Pokazuje wszystkie klawisze skrótów skojarzone z poleceniami menu.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parametry

*bShowAll*<br/>
podczas W przypadku wartości TRUE zostaną wyświetlone wszystkie klawisze skrótów. W przypadku wartości FALSE zostanie wyświetlony tylko pierwszy klawisz skrótu.

*lpszDelimiter*<br/>
podczas Ciąg do wstawienia między klawiszami skrótów. Ten ogranicznik nie ma wpływu, jeśli jest wyświetlany tylko jeden klawisz skrótu.

### <a name="remarks"></a>Uwagi

Domyślnie, jeśli polecenie zawiera więcej niż jeden przypisany do niego klucz skrótu, zostanie wyświetlony tylko pierwszy klawisz skrótu. Ta funkcja umożliwia wyświetlenie listy wszystkich klawiszy skrótów skojarzonych ze wszystkimi poleceniami.

Skróty klawiaturowe będą wyświetlane obok polecenia na pasku menu. Jeśli wszystkie klawisze skrótów są wyświetlane, ciąg dostarczony przez *lpszDelimiter* będzie oddzielał poszczególne klawisze skrótów.

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a> CKeyboardManager::TranslateCharToUpper

Konwertuje znak na jego górny rejestr.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
podczas Znak do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Znak, który jest górnym rejestrem parametru wejściowego.

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a> CKeyboardManager::UpdateAccelTable

Aktualizuje tablicę klawiszy skrótów za pomocą nowej tabeli klawiszy skrótów.

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
podczas Wskaźnik do szablonu dokumentu.

*lpAccel*<br/>
podczas Wskaźnik do nowego klawisza skrótu.

*nSize*<br/>
podczas Rozmiar nowej tabeli skrótów.

*pDefaultFrame*<br/>
podczas Wskaźnik do domyślnego okna ramki.

*hAccelNew*<br/>
podczas Dojście do nowej tabeli skrótów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby zastąpić istniejącą tabelę skrótów nowymi klawiszami skrótów dla kilku obiektów okien ramowych. Funkcja otrzymuje szablon dokumentu jako parametr w celu uzyskania dostępu do wszystkich obiektów okien ramowych połączonych z danym szablonem dokumentu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md)
