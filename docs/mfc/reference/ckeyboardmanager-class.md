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
ms.openlocfilehash: 5d0f544943cc8584960bb2668ee7ce326547e2fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372312"
---
# <a name="ckeyboardmanager-class"></a>Klasa CKeyboardManager

Zarządza tabelami klawiszy skrótów dla okna ramki głównej i okien ramek podrzędnych.

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
|[CKeyboardManager::CleanUp](#cleanup)|Czyści tabele klawiszy skrótów.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Pobiera domyślny klawisz skrótu dla określonego polecenia i okna.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Określa, czy klucz jest obsługiwany przez tabelę akceleratora.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Wskazuje, czy znak można wydrukować.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Wskazuje, czy w menu są wyświetlane wszystkie klawisze skrótów dla polecenia, czy tylko domyślny klawisz skrótu.|
|[CKeyboardManager::LoadState](#loadstate)|Ładuje tabele klawiszy skrótów z rejestru systemu Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Ponownie ładuje tabele klawiszy skrótów z zasobu aplikacji.|
|[CKeyboardManager::Zapisz stan](#savestate)|Zapisuje tabele klawiszy skrótów w rejestrze systemu Windows.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Określa, czy w ramach są wyświetlane wszystkie klawisze skrótów dla wszystkich poleceń, czy pojedynczy klawisz skrótu dla każdego polecenia. Ta metoda nie wpływa na polecenia, które mają tylko jeden skojarzony klawisz skrótu.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Konwertuje znak do jego górnego rejestru.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualizuje tabelę klawiszy skrótów za pomocą nowej tabeli klawiszy skrótów.|

## <a name="remarks"></a>Uwagi

Członkowie tej klasy umożliwiają zapisywanie i ładowanie tabel klawiszy skrótów do rejestru systemu Windows, aktualizowanie skróconych tabel kluczy za pomocą szablonu oraz znajdowanie domyślnego klawisza skrótu dla polecenia w oknie ramki. Ponadto obiekt `CKeyboardManager` umożliwia kontrolowanie sposobu wyświetlania klawiszy skrótów użytkownikowi.

Obiektu nie należy `CKeyboardManager` tworzyć ręcznie. Zostanie on utworzony automatycznie przez ramy aplikacji. Jednak należy wywołać [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) podczas procesu inicjowania aplikacji. Aby uzyskać wskaźnik do menedżera klawiatury dla aplikacji, zadzwoń [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CKeyboardManager` pobrać wskaźnik `CWinAppEx` do obiektu z klasy i jak wyświetlić wszystkie klawisze skrótów skojarzone z poleceniami menu. Ten fragment kodu jest częścią [przykładu Strony niestandardowe](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ckeyboardmanager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxkeyboardmanager.h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a>CKeyboardManager::CKeyboardManager

Konstruuje `CKeyboardManager` obiekt.

```
CKeyboardManager();
```

### <a name="remarks"></a>Uwagi

W większości przypadków nie trzeba tworzyć `CKeyboardManager` bezpośrednio. Domyślnie struktura tworzy jeden dla Ciebie. Aby uzyskać wskaźnik `CKeyboardManager`do , wywołać [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Jeśli utworzysz go ręcznie, należy go zainicjować za pomocą metody [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a>CKeyboardManager::CleanUp

Zwalnia `CKeyboardManager` zasoby i czyści wszystkie mapowania klawiszy skrótów.

```
static void CleanUp();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat klawiszy skrótów, zobacz [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md).

Nie trzeba wywoływać tej funkcji, gdy aplikacja kończy działanie, ponieważ struktura wywołuje ją automatycznie podczas zamykania aplikacji.

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a>CKeyboardManager::FindDefaultAccelerator

Pobiera domyślny klawisz skrótu dla określonego polecenia i okna.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia.

*Str*<br/>
[na zewnątrz] Odwołanie do `CString` obiektu.

*pWndFrame (Klatka pWndFrame)*<br/>
[w] Wskaźnik do okna ramki.

*bIsDefaultFrame*<br/>
[w] Określa, czy okno ramki jest domyślnym oknem ramki.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli skrót zostanie znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda wyszukuje polecenie określone przez *uiCmd* i pobiera domyślny klawisz skrótu. Następnie metoda przyjmuje ciąg skojarzony z tym klawiszem skrótu i zapisuje wartość do *parametru str.*

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a>CKeyboardManager::IsKeyHandled

Określa, czy określony klucz jest obsługiwany przez [klasę CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

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
|*klawisze*|[w] Klucz do sprawdzenia.|
|*fVirt (*|[w] Określa zachowanie klawisza skrótu. Aby uzyskać listę możliwych wartości, zobacz [Struktura ACCEL](/windows/win32/api/winuser/ns-winuser-accel).|
|*pWndFrame (Klatka pWndFrame)*|[w] Okno ramki. Ta metoda określa, czy klawisz skrótu jest obsługiwany w tej ramce.|
|*bIsDefaultFrame*|[w] Parametr logiczny wskazujący, czy *pWndFrame* jest domyślnym oknem ramki.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obsługiwany jest klawisz skrótu. FALSE, jeśli klucz nie jest obsługiwany lub jeśli *pWndFrame* ma wartość NULL.

### <a name="remarks"></a>Uwagi

Parametry wejściowe muszą być zgodne z zapisem w tabeli akceleratora zarówno dla *nKey,* jak i *fVirt,* aby określić, czy klawisz skrótu jest obsługiwany w *pWndFrame*.

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a>CKeyboardManager::IsKeyPrintable

Wskazuje, czy znak można wydrukować.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Nchar*|[w] Znak, który sprawdza ta metoda.|

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli znak jest drukowalny, zero, jeśli nie.

### <a name="remarks"></a>Uwagi

Ta metoda kończy się niepowodzeniem, jeśli wywołanie [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) nie powiedzie się.

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a>CKeyboardManager::IsShowAllAccelerators

Wskazuje, czy w menu są wyświetlane wszystkie klawisze skrótów skojarzone z poleceniami menu, czy tylko domyślne klawisze skrótów.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli aplikacja zawiera listę wszystkich klawiszy skrótów dla poleceń menu; 0, jeśli aplikacja wyświetla tylko domyślne klawisze skrótów.

### <a name="remarks"></a>Uwagi

Aplikacja wyświetla na pasku menu klawisze skrótów dla poleceń menu. Użyj funkcji [CKeyboardManager::ShowAllAccelerators,](#showallaccelerators) aby kontrolować, czy aplikacja zawiera listę wszystkich klawiszy skrótów, czy tylko domyślne klawisze skrótów.

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a>CKeyboardManager::LoadState

Ładuje tabele klawiszy skrótów z rejestru systemu Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ścieżka rejestru, `CKeyboardManager` w której zapisywane są dane.

*pDefaultFrame*<br/>
[w] Wskaźnik do okna ramki, który ma być używany jako okno domyślne.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli stan został załadowany pomyślnie lub 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli parametr *lpszProfileName* ma wartość NULL, ta `CKeyboardManager` metoda sprawdza domyślną lokalizację rejestru dla danych. Domyślna lokalizacja rejestru jest określona przez [klasę CWinAppEx](../../mfc/reference/cwinappex-class.md). Dane muszą być wcześniej zapisywane metodą [CKeyboardManager::SaveState](#savestate).

Jeśli nie określisz okna domyślnego, zostanie użyte okno ramki głównej aplikacji.

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a>CKeyboardManager::ResetAll

Ponownie ładuje tabele klawiszy skrótów z zasobu aplikacji.

```
void ResetAll();
```

### <a name="remarks"></a>Uwagi

Ta funkcja czyści skróty `CKeyboardManager` przechowywane w wystąpieniu. Następnie ponownie załaduje stan menedżera klawiatury z zasobu aplikacji.

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a>CKeyboardManager::Zapisz stan

Zapisuje tabele klawiszy skrótów w rejestrze systemu Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Ścieżka rejestru do `CKeyboardManager` zapisywania stanu.

*pDefaultFrame*<br/>
[w] Wskaźnik do okna ramki, które staje się domyślnym oknem.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli stan menedżera klawiatury został pomyślnie zapisany lub 0 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli parametr *lpszProfileName* ma wartość NULL, `CKeyboardManager` ta metoda zapisze stan do domyślnej lokalizacji określonej przez [klasę CWinAppEx](../../mfc/reference/cwinappex-class.md). Jeśli określisz lokalizację, można załadować dane później przy użyciu metody [CKeyboardManager::LoadState](#loadstate).

Jeśli okno domyślne nie zostanie określone, okno ramki głównej będzie używane jako okno domyślne.

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a>CKeyboardManager::ShowAllAccelerators

Pokazuje wszystkie klawisze skrótów skojarzone z poleceniami menu.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parametry

*bShowAll*<br/>
[w] Jeśli true, zostaną wyświetlone wszystkie klawisze skrótów. Jeśli FALSE, zostanie wyświetlony tylko pierwszy klawisz skrótu.

*lpszDelimiter*<br/>
[w] Ciąg do wstawienia między klawiszami skrótów. Ten ogranicznik nie ma wpływu, jeśli wyświetlany jest tylko jeden klawisz skrótu.

### <a name="remarks"></a>Uwagi

Domyślnie, jeśli polecenie ma więcej niż jeden klawisz skrótu skojarzone z nim, tylko pierwszy klawisz skrótu zostanie wyświetlony. Ta funkcja umożliwia wyświetlanie listy wszystkich klawiszy skrótów skojarzonych ze wszystkimi poleceniami.

Klawisze skrótów zostaną wyświetlone obok polecenia na pasku menu. Jeśli zostaną wyświetlone wszystkie klawisze skrótów, ciąg dostarczony przez *lpszDelimiter oddzieli* poszczególne klawisze skrótów.

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a>CKeyboardManager::TranslateCharToUpper

Konwertuje znak do jego górnego rejestru.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parametry

*Nchar*<br/>
[w] Znak do konwersji.

### <a name="return-value"></a>Wartość zwracana

Znak, który jest górny rejestr parametru wejściowego.

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a>CKeyboardManager::UpdateAccelTable

Aktualizuje tabelę klawiszy skrótów za pomocą nowej tabeli klawiszy skrótów.

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
[w] Wskaźnik do szablonu dokumentu.

*lpAccel (lpAccel)*<br/>
[w] Wskaźnik do nowego klawisza skrótu.

*nSize (rozmiar)*<br/>
[w] Rozmiar nowej tabeli skrótów.

*pDefaultFrame*<br/>
[w] Wskaźnik do domyślnego okna ramki.

*hAccelNowy*<br/>
[w] Uchwyt do nowej tabeli skrótów.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do zastępowania istniejącej tabeli skrótów nowymi klawiszami skrótów dla kilku obiektów okna ramki. Funkcja odbiera szablon dokumentu jako parametr, aby uzyskać dostęp do wszystkich obiektów okna ramki połączonych z danym szablonem dokumentu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md)
