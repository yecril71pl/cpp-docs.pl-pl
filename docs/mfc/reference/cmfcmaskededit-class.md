---
title: Klasa CMFCMaskedEdit
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
ms.openlocfilehash: 26617f10605fe2a8a94adcc477cccab7e2ba4919
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754225"
---
# <a name="cmfcmaskededit-class"></a>Klasa CMFCMaskedEdit

Klasa `CMFCMaskedEdit` obsługuje zamaskowany formant edycji, który sprawdza poprawność danych wejściowych użytkownika względem maski i wyświetla zweryfikowane wyniki zgodnie z szablonem.

## <a name="syntax"></a>Składnia

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|Domyślny konstruktor.|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMaskedEdit::DisableMask](#disablemask)|Wyłącza sprawdzanie poprawności danych wejściowych użytkownika.|
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Określa, `GetWindowText` czy metoda pobiera tylko zamaskowane znaki.|
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicjuje zamaskowany formant edycji.|
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Określa, czy zamaskowany formant edycji wybiera określone grupy danych wejściowych użytkownika, czy wszystkie dane wejściowe użytkownika.|
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Określa, czy tekst jest sprawdzany tylko względem zamaskowanych znaków, czy dla całej maski.|
|`CMFCMaskedEdit::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Pobiera zweryfikowany tekst z zamaskowanego formantu edycji.|
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Określa ciąg prawidłowych znaków, który użytkownik może wprowadzić.|
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Wyświetla monit w zamaskowanym formancie edycji.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Wywoływana przez strukturę, aby sprawdzić poprawność określonego znaku względem odpowiedniego znaku maski.|

## <a name="remarks"></a>Uwagi

Wykonaj następujące kroki, `CMFCMaskedEdit` aby użyć formantu w aplikacji:

1. Osadź `CMFCMaskedEdit` obiekt w klasie okna.

2. Wywołanie [METODY CMFCMaskedEdit::EnableMask](#enablemask) w celu określenia maski.

3. Wywołanie [CMFCMaskedEdit::SetValidChars](#setvalidchars) metody, aby określić listę prawidłowych znaków.

4. Wywołanie [metody CMFCMaskedEdit::SetWindowText](#setwindowtext) w celu określenia domyślnego tekstu dla zamaskowanego formantu edycji.

5. Wywołanie [METODY CMFCMaskedEdit::GetWindowText](#getwindowtext) w celu pobrania zweryfikowanego tekstu.

Jeśli nie wywołasz jednej lub więcej metod inicjowania maski, prawidłowych znaków i tekstu domyślnego, zamaskowany formant edycji zachowuje się tak, jak zachowuje się standardowy formant edycji.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować maskę (na przykład `EnableMask` numer telefonu) przy użyciu metody tworzenia `SetValidChars` maski dla zamaskowanego formantu edycji, metody określania ciągu prawidłowych znaków, które użytkownik może wprowadzić, oraz `SetWindowText` metody wyświetlania monitu w zamaskowanym formancie edycji. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cedit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdytuj](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmaskededit.h

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a>CMFCMaskedEdit::DisableMask

Wyłącza sprawdzanie poprawności danych wejściowych użytkownika.

```cpp
void DisableMask();
```

### <a name="remarks"></a>Uwagi

Jeśli sprawdzanie poprawności danych wejściowych użytkownika jest wyłączone, zamaskowany formant edycji zachowuje się jak standardowy formant edycji.

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly

Określa, `GetWindowText` czy metoda pobiera tylko zamaskowane znaki.

```cpp
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby określić, że [metoda CMFCMaskedEdit::GetWindowText](#getwindowtext) pobiera tylko zamaskowane znaki; FALSE, aby określić, że metoda pobrać cały tekst. Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia pobieranie zamaskowanych znaków. Następnie utwórz zamaskowany formant edycji odpowiadający numerowi telefonu, taki jak (425) 555-0187. Jeśli wywołasz `GetWindowText` metodę, zwraca "4255550187". Jeśli pobieranie zamaskowanych znaków `GetWindowText` zostanie wyłączone, metoda zwróci tekst wyświetlany w formancie edycji, na przykład "(425) 555-0187".

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a>CMFCMaskedEdit::EnableMask

Inicjuje zamaskowany formant edycji.

```cpp
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parametry

*lpszMask*<br/>
[w] Ciąg maski, który określa typ znaku, który może pojawić się w każdej pozycji w danych wejściowych użytkownika. Długość ciągów parametrów *lpszInputTemplate* i *lpszMask* musi być taka sama. Zobacz uwagi sekcji, aby uzyskać więcej szczegółów na temat znaków maski.

*płyta lpszInputTemplate*<br/>
[w] Ciąg szablonu maski, który określa znaki literału, które mogą pojawić się w każdej pozycji w danych wejściowych użytkownika. Użyj znaku podkreślenia ('_') jako symbolu zastępczego znaku. Długość ciągów parametrów *lpszInputTemplate* i *lpszMask* musi być taka sama.

*chMaskInputTemplate*<br/>
[w] Domyślny znak, który struktura zastępuje dla każdego nieprawidłowego znaku w danych wejściowych użytkownika. Domyślną wartością tego parametru jest podkreślenie ('_').

*lpszValid (lpszValid)*<br/>
[w] Ciąg zawierający zestaw prawidłowych znaków. Wartość NULL oznacza, że wszystkie znaki są prawidłowe. Domyślną wartością tego parametru jest null.

### <a name="remarks"></a>Uwagi

Ta metoda służy do tworzenia maski dla zamaskowanego formantu edycji. Wyprowadzić klasę z `CMFCMaskedEdit` klasy i zastąpić [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) metody, aby użyć własnego kodu do przetwarzania maski niestandardowej.

W poniższej tabeli znajdują się domyślne znaki maski:

|Znak maski|Definicja|
|--------------------|----------------|
|D|Cyfrowy.|
|d|Cyfra lub spacja.|
|+|Plus (+'), minus ('-') lub spacja.|
|C|Znak alfabetyczny.|
|c|Alfabetyczny znak lub spacja.|
|A|Znak alfanumeryczny.|
|a|Znak alfanumeryczny lub spacja.|
|*|Znak do wydrukowania.|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup

Określa, czy zamaskowany formant edycji umożliwia użytkownikowi wybranie danych wejściowych poszczególnych grup, czy wszystkie dane wejściowe.

```cpp
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby wybrać tylko grupy; FAŁSZ, aby zaznaczyć cały tekst. Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do określania, czy zamaskowany formant edycji umożliwia użytkownikowi zaznaczanie według grupy, czy całego tekstu.

Domyślnie włączone jest zaznaczenie według grupy. W takim przypadku użytkownik może wybrać tylko ciągłe grupy prawidłowych znaków.

Na przykład można użyć następującego zamaskowanego formantu edycji, aby sprawdzić poprawność numeru telefonu:

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

Jeśli wybór według grupy jest włączony, użytkownik może pobrać tylko grupy ciągów "425", "555" lub "0187". Jeśli wybór grupy jest wyłączony, użytkownik może pobrać cały tekst numeru telefonu: "(425) 555-0187".

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly

Określa, czy tekst jest sprawdzany tylko względem zamaskowanych znaków, czy dla całej maski.

```cpp
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] TRUE, aby sprawdzić poprawność danych wejściowych użytkownika względem tylko zamaskowanych znaków; FALSE, aby sprawdzić poprawność względem całej maski. Wartością domyślną jest PRAWDA.

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText

Pobiera zweryfikowany tekst z zamaskowanego formantu edycji.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>Parametry

*lpszStringBuf*<br/>
[na zewnątrz] Wskaźnik do buforu, który odbiera tekst z formantu edycji.

*nMaxCount*<br/>
[w] Maksymalna liczba znaków do odebrania.

*rstrString (rstrstring)*<br/>
[na zewnątrz] Odwołanie do obiektu ciągu, który odbiera tekst z formantu edycji.

### <a name="return-value"></a>Wartość zwracana

Przeciążenie pierwszej metody zwraca liczbę bajtów ciągu, który jest kopiowany do buforu parametru *lpszStringBuf;* 0, jeśli zamaskowany formant edycji nie zawiera tekstu.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje tekst z zamaskowanego formantu edycji do buforu *lpszStringBuf* lub ciągu *rstrString.*

Ta metoda na nowo definiuje [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar

Wywoływana przez strukturę, aby sprawdzić poprawność określonego znaku względem odpowiedniego znaku maski.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>Parametry

*ChChar (chchchar)*<br/>
[w] Znak, który ma zostać zweryfikowany.

*chMaskChar*<br/>
[w] Odpowiedni znak z ciągu maski.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli parametr *char* jest typem znaku dozwolonym przez parametr *chMaskChar;* w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zastąd w tej metodzie należy samodzielnie sprawdzić poprawność znaków wejściowych. Aby uzyskać więcej informacji na temat znaków maski, zobacz [CMFCMaskedEdit::EnableMask](#enablemask) metody.

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars

Określa ciąg prawidłowych znaków, który użytkownik może wprowadzić.

```cpp
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parametry

*lpszValid (lpszValid)*<br/>
[w] Ciąg zawierający zestaw prawidłowych znaków wejściowych. Wartość NULL oznacza, że wszystkie znaki są prawidłowe. Domyślną wartością tego parametru jest null.

### <a name="remarks"></a>Uwagi

Ta metoda służy do definiowania listy prawidłowych znaków. Jeśli znaku wejściowego nie ma na tej liście, zamaskowany formant edycji nie zaakceptuje go.

Poniższy przykład kodu akceptuje tylko liczby szesnastkowe.

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

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText

Wyświetla monit w zamaskowanym formancie edycji.

```cpp
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
[w] Wskazuje ciąg zakończony z wartością null, który będzie używany jako monit.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia tekst kontrolny.

Ta metoda na nowo definiuje [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)
