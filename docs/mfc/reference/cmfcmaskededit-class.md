---
title: CMFCMaskedEdit Class
ms.date: 11/04/2016
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
ms.openlocfilehash: c1dcf89811fa5225283cb5bec120d3bd2fdfb003
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773791"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit Class

`CMFCMaskedEdit` Klasa obsługuje formant edycji maskowanej, który sprawdza poprawność danych wejściowych użytkownika w oparciu o maskę i wyświetla zatwierdzone wyniki zgodnie ze wzorcem.

## <a name="syntax"></a>Składnia

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|Domyślny konstruktor.|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMaskedEdit::DisableMask](#disablemask)|Wyłącza sprawdzanie poprawności danych wejściowych użytkownika.|
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Określa, czy `GetWindowText` metoda pobiera tylko maskowanego znaków.|
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicjuje maskowanego formant edycji.|
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Określa, czy maskowana kontrolka edycji wybiera określonych grup danych wejściowych użytkownika lub wszystkich danych wejściowych użytkownika.|
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Określa, czy tekst jest sprawdzana tylko maskowane znaków lub przed całego maski.|
|`CMFCMaskedEdit::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Pobiera zweryfikować tekst z maskowana kontrolka edycji.|
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Określa ciąg prawidłowe znaki, które użytkownik może wprowadzić.|
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Wyświetla monit w maskowana kontrolka edycji.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Metoda wywoływana przez platformę, by sprawdzić poprawność określonego znaku w stosunku do odpowiedniego znaku maski.|

## <a name="remarks"></a>Uwagi

Wykonaj poniższe kroki, aby użyć `CMFCMaskedEdit` kontrolki w aplikacji:

1. Osadzanie `CMFCMaskedEdit` obiektu do klasy okna.

2. Wywołaj [CMFCMaskedEdit::EnableMask](#enablemask) metodę, aby określić maskę.

3. Wywołaj [CMFCMaskedEdit::SetValidChars](#setvalidchars) metodę, aby określić listę prawidłowych znaków.

4. Wywołaj [CMFCMaskedEdit::SetWindowText](#setwindowtext) metodę, aby określić domyślny tekst w przypadku maskowana formant edycji.

5. Wywołaj [CMFCMaskedEdit::GetWindowText](#getwindowtext) metodę, aby pobrać zweryfikowanych tekstu.

Jeśli co najmniej jednej metody do zainicjowania maska prawidłowe znaki i domyślny tekst nie zostanie wywołana, maskowana kontrolka edycji zachowuje się tak samo, jak działa formant edycji standard.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować maski (na przykład numer telefonu) przy użyciu `EnableMask` metodę, aby utworzyć maska Edycja maskowana kontrolki, `SetValidChars` metodę, aby określić ciąg prawidłowe znaki, które użytkownik może wprowadzić i `SetWindowText` metodę w celu wyświetlenia monitu w maskowanego formant edycji. W tym przykładzie jest częścią [przykładowe nowych formantów](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmaskededit.h

##  <a name="disablemask"></a>  CMFCMaskedEdit::DisableMask

Wyłącza sprawdzanie poprawności danych wejściowych użytkownika.

```
void DisableMask();
```

### <a name="remarks"></a>Uwagi

Jeśli sprawdzenie poprawności danych wejściowych użytkownika jest wyłączona, zachowuje się maskowana kontrolka edycji, takie jak formant edycji standard.

##  <a name="enablegetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableGetMaskedCharsOnly

Określa, czy `GetWindowText` metoda pobiera tylko maskowanego znaków.

```
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE, aby określić, że [CMFCMaskedEdit::GetWindowText](#getwindowtext) metody pobierania tylko maskowane znaków. Wartość FALSE, aby określić, że metoda pobieranie całego tekstu. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia pobieranie maskowanego znaków. Następnie należy utworzyć formant edycji maskowanej, który odpowiada numer telefonu, takich jak (425) 555-0187. Jeśli wywołasz `GetWindowText` metody, zwraca "4255550187". Po wyłączeniu pobierania maskowanego znaków `GetWindowText` metoda zwraca tekst, który jest wyświetlany w formancie edycji, na przykład "(425) 555-0187".

##  <a name="enablemask"></a>  CMFCMaskedEdit::EnableMask

Inicjuje maskowanego formant edycji.

```
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parametry

*lpszMask*<br/>
[in] Ciąg maska, który określa typ znaku, który może znajdować się w każdej pozycji w danych wejściowych użytkownika. Długość *lpszInputTemplate* i *lpszMask* ciągi parametru musi być taka sama. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji na temat maski znaków.

*lpszInputTemplate*<br/>
[in] Ciąg szablonu maski, określający, że znaków literału, które mogą być wyświetlane w każdej pozycji w danych wejściowych użytkownika. Użyj znaku podkreślenia (_) jako symbolu zastępczego znaków. Długość *lpszInputTemplate* i *lpszMask* ciągi parametru musi być taka sama.

*chMaskInputTemplate*<br/>
[in] Domyślny znak ramach zastępuje każdy nieprawidłowy znak w danych wejściowych użytkownika. Wartość domyślna tego parametru to znak podkreślenia (_).

*lpszValid*<br/>
[in] Ciąg, który zawiera zestaw prawidłowych znaków. Wartości NULL wskazuje, że wszystkie znaki są prawidłowe. Wartość domyślna tego parametru ma wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia tworzenie maski dla maskowana kontrolka edycji. Wyprowadzić klasę z `CMFCMaskedEdit` klasy, a także Przesłoń [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) metoda do użycia z własnego kodu podczas przetwarzania niestandardowej maski.

Następująca tabela zawiera listę znaków maski domyślnych:

|Znak maski|Definicja|
|--------------------|----------------|
|D|Cyfry.|
|d|Cyfra lub spacja.|
|+|Znak plus ("+") minus ("-"), czy miejsce.|
|C|Znaku alfabetycznego.|
|c|Od litery lub znaku miejsca.|
|ELEMENT|Znak alfanumeryczny.|
|a|Znak alfanumeryczny lub miejsca.|
|*|Znak drukowalny.|

##  <a name="enableselectbygroup"></a>  CMFCMaskedEdit::EnableSelectByGroup

Określa, czy maskowana kontrolka edycji zezwala użytkownikowi na dane wejściowe wybierz grupę, w szczególności lub wszystkie dane wejściowe.

```
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE, aby wybrać tylko grupy; Wartość FALSE, aby zaznaczyć cały tekst. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia określenie, czy maskowana kontrolka edycji zezwala użytkownikowi na wybranie, grupie lub Zaznaczanie całego tekstu.

Domyślnie wybór grupy jest włączony. W takim przypadku użytkownik może wybrać tylko ciągłe grupy prawidłowych znaków.

Na przykład może użyć następującego formantu edycyjnego można zweryfikować numer telefonu:

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

Wybór grupy jest włączony, użytkownik przywrócić tylko "425", "555" lub "0187" ciągu grup. Jeśli Zaznaczanie grupowe jest wyłączone użytkownik może pobrać cały tekst numer telefonu: "(425) 555-0187".

##  <a name="enablesetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableSetMaskedCharsOnly

Określa, czy tekst jest weryfikowane względem zamaskowanych znaki lub względem całej maski.

```
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE, aby zweryfikować użytkownika dane wejściowe względem tylko maskowane znaków. Wartość FAŁSZ, aby przeprowadzić walidacji względem całej maski. Wartość domyślna to TRUE.

##  <a name="getwindowtext"></a>  CMFCMaskedEdit::GetWindowText

Pobiera zweryfikować tekst z maskowana kontrolka edycji.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>Parametry

*lpszStringBuf*<br/>
[out] Wskaźnik do buforu, który odbiera tekstu z kontrolki edycji.

*nMaxCount*<br/>
[in] Maksymalna liczba znaków do odbierania.

*rstrString*<br/>
[out] Odwołanie do obiektu ciągu, który odbiera tekstu z kontrolki edycji.

### <a name="return-value"></a>Wartość zwracana

Pierwsze przeciążenie metody zwraca liczbę bajtów w ciągu, który jest kopiowany do *lpszStringBuf* bufor parametru; 0, jeśli maskowana kontrolka edycji nie zawiera tekstu.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje tekst z formantu edycyjnego do *lpszStringBuf* buforu lub *rstrString* ciągu.

Ta metoda redefiniuje [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).

##  <a name="ismaskedchar"></a>  CMFCMaskedEdit::IsMaskedChar

Metoda wywoływana przez platformę, by sprawdzić poprawność określonego znaku w stosunku do odpowiedniego znaku maski.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>Parametry

*chChar*<br/>
[in] Znak, który ma zostać zweryfikowana.

*chMaskChar*<br/>
[in] Odpowiedniego znaku w ciągu maski.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli *chChar* parametr jest typem znaków dozwoloną przez *chMaskChar* parametru; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Zastępuje tę metodę do sprawdzania poprawności danych wejściowych znaków na własną rękę. Aby uzyskać więcej informacji na temat znaków maski zobacz [CMFCMaskedEdit::EnableMask](#enablemask) metody.

##  <a name="setvalidchars"></a>  CMFCMaskedEdit::SetValidChars

Określa ciąg prawidłowe znaki, które użytkownik może wprowadzić.

```
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parametry

*lpszValid*<br/>
[in] Ciąg, który zawiera zestaw prawidłowych znaków danych wejściowych. Wartość NULL oznacza, że wszystkie znaki są prawidłowe. Wartość domyślna tego parametru ma wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia definiowanie listy prawidłowych znaków. Jeśli wprowadzanych znaków nie ma na tej liście, maskowana kontrolka edit nie akceptuje je.

Poniższy przykład kodu akceptuje tylko liczby szesnastkowej.

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

##  <a name="setwindowtext"></a>  CMFCMaskedEdit::SetWindowText

Wyświetla monit w maskowana kontrolka edycji.

```
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
[in] Wskazuje ciąg zakończony zerem, która będzie służyć jako wiersz.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia tekst kontrolki.

Ta metoda redefiniuje [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).

## <a name="see-also"></a>Zobacz także

[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)
