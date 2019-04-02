---
title: Klasa CFontDialog
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: b711ca65e552d495e466ea2e46a6779cf43ecbe3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767747"
---
# <a name="cfontdialog-class"></a>Klasa CFontDialog

Umożliwia uwzględnienie okna dialogowego wyboru czcionki w aplikacji.

## <a name="syntax"></a>Składnia

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name|Opis|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Konstruuje `CFontDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonać wyboru.|
|[CFontDialog::GetCharFormat](#getcharformat)|Pobiera formatowanie znaków w wybranej czcionki.|
|[CFontDialog::GetColor](#getcolor)|Zwraca kolor wybranej czcionki.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Przypisuje właściwości aktualnie wybranej czcionki do `LOGFONT` struktury.|
|[CFontDialog::GetFaceName](#getfacename)|Zwraca nazwę twarzy wybranej czcionki.|
|[CFontDialog::GetSize](#getsize)|Zwraca rozmiar wybranej czcionki w punktach.|
|[CFontDialog::GetStyleName](#getstylename)|Zwraca nazwę stylu wybranej czcionki.|
|[CFontDialog::GetWeight](#getweight)|Zwraca wartość wagi wybranej czcionki.|
|[CFontDialog::IsBold](#isbold)|Określa, czy czcionka jest pogrubiony.|
|[CFontDialog::IsItalic](#isitalic)|Określa, czy czcionka jest pochylony.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Określa, czy czcionka jest wyświetlana przy użyciu przekreślenie.|
|[CFontDialog::IsUnderline](#isunderline)|Określa, czy czcionka jest podkreślony.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name|Opis|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Struktury używane w celu dostosowania `CFontDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Element `CFontDialog` obiektu to okno dialogowe z listą czcionek, które są aktualnie zainstalowane w systemie. Użytkownik może wybrać określonej czcionki z listy, a następnie zaznacz to pole wyboru jest następnie raportowane do aplikacji.

Do konstruowania `CFontDialog` obiektu, użyj podanych konstruktora lub pobrać nową podklasę i używania niestandardowego konstruktora.

Gdy `CFontDialog` obiekt został skonstruowany, możesz użyć `m_cf` strukturę, aby zainicjować wartości lub stany formantów w oknie dialogowym. [M_cf](#m_cf) struktury jest typu [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta). Aby uzyskać więcej informacji na temat tej struktury zobacz zestaw Windows SDK.

Po inicjowanie obiektu okna dialogowego formantów, wywołanie `DoModal` funkcja elementu członkowskiego, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie czcionki. `DoModal` Zwraca, czy użytkownik wybrał przycisk OK (IDOK) lub anulować (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, możesz użyć jednej z `CFontDialog`przez funkcje Członkowskie można pobrać informacji o danych wejściowych przez użytkownika.

Możesz użyć Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkcji, aby ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i Dowiedz się więcej o błędzie. Aby uzyskać więcej informacji na temat tej funkcji zobacz zestaw Windows SDK.

`CFontDialog` opiera się na pliku COMMDLG. Plik DLL, który jest dostarczany z programem Windows w wersji 3.1 lub nowszej.

Aby dostosować okno dialogowe, należy wyprowadzić klasę z `CFontDialog`, udostępniają szablon niestandardowy dialog i dodać mapy wiadomości przetwarzanie komunikatów powiadomień od formantów rozszerzonego. Wszystkie nieprzetworzone komunikaty powinien zostać przekazany do klasy bazowej.

Dostosowywanie funkcji punktów zaczepienia nie jest wymagana.

Aby uzyskać więcej informacji na temat korzystania z `CFontDialog`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog

Konstruuje `CFontDialog` obiektu.

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*plfInitial*<br/>
Wskaźnik do [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktura danych, która pozwala na ustawienie niektórych cech czcionki.

*charFormat*<br/>
Wskaźnik do [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) struktura danych, która pozwala na ustawienie niektórych cech czcionki w Zaawansowane edytowanie kontrolki.

*dwFlags*<br/>
Określa co najmniej jeden flagi wybierz czcionkę. Co najmniej jeden wstępnie zdefiniowane wartości można łączyć przy użyciu bitowego operatora OR. Jeśli zmodyfikujesz `m_cf.Flag`s elementu członkowskiego struktury, należy użyć bitowy operator OR zmiany, aby zachować zachowanie domyślne. Aby uzyskać szczegółowe informacje na każdym z tych flag, zobacz opis [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) struktury w zestawie Windows SDK.

*pdcPrinter*<br/>
Wskaźnik do kontekstu urządzenia drukarki. Jeśli zostanie podany, ten parametr wskazuje kontekst urządzenie drukarki drukarki, na którym można wybrać czcionek.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub właściciela okno dialogowe czcionki.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że Konstruktor automatycznie wypełnia członkowie `CHOOSEFONT` struktury. Tylko powinno to zmienić, jeśli chcesz, okno dialogowe czcionki innych niż domyślne.

> [!NOTE]
>  Pierwsza wersja tej funkcji, istnieje tylko w przypadku, gdy ma nie kontrolki tekstu sformatowanego Lepsza obsługa kontroli.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>  CFontDialog::DoModal

Wywołaj tę funkcję, aby wyświetlić wspólne okno dialogowe czcionki Windows i umożliwia użytkownikowi wybierz czcionkę.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli zwracana jest IDCANCEL, wywołaj Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkcję, aby ustalić, czy wystąpił błąd.

IDOK i IDCANCEL są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.

### <a name="remarks"></a>Uwagi

Aby inicjowanie różne formanty okna dialogowego czcionki, ustawiając członkowie [m_cf](#m_cf) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, może wywołać inny członek funkcje, które można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.

### <a name="example"></a>Przykład

  Zobacz przykłady dla [CFontDialog::CFontDialog](#cfontdialog) i [CFontDialog::GetColor](#getcolor).

##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat

Pobiera formatowanie znaków w wybranej czcionki.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parametry

*cf*<br/>
A [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) struktury zawierającej informacje o formatowanie znaków w wybranej czcionki.

##  <a name="getcolor"></a>  CFontDialog::GetColor

Wywołaj tę funkcję, aby pobrać kolor wybranej czcionki.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor wybranej czcionki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont

Wywołaj tę funkcję, aby przypisać właściwości aktualnie wybranej czcionki do elementów członkowskich [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury.

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parametry

*lplf*<br/>
Wskaźnik do `LOGFONT` struktury.

### <a name="remarks"></a>Uwagi

Inne `CFontDialog` funkcji elementów członkowskich są dostarczane do dostępu do właściwości poszczególnych bieżącej czcionki.

Jeśli ta funkcja jest wywoływana podczas wywoływania [DoModal](#domodal), zwraca bieżące zaznaczenie w czasie (co użytkownik będzie widział lub została zmieniona w oknie dialogowym). Jeśli ta funkcja jest wywoływana po wywołaniu `DoModal` (tylko wtedy, gdy `DoModal` zwraca IDOK), zwraca jakie rzeczywiście wybrany przez użytkownika.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>  CFontDialog::GetFaceName

Wywołaj tę funkcję, aby pobrać nazwę twarzy wybranej czcionki.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa czcionki czcionki wybrane w `CFontDialog` okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>  CFontDialog::GetSize

Wywołaj tę funkcję, by pobrać rozmiar wybranej czcionki.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar czcionki w dziesiątych punktu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>  CFontDialog::GetStyleName

Wywołaj tę funkcję, aby pobrać nazwę stylu wybranej czcionki.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa styl czcionki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>  CFontDialog::GetWeight

Wywołaj tę funkcję, aby pobrać wagę wybranej czcionki.

```
int GetWeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Waga wybranej czcionki.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat grubość czcionki, zobacz [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>  CFontDialog::IsBold

Wywołaj tę funkcję, aby określić, czy wybrana czcionka jest pogrubiony.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wybranej czcionki charakteryzuje się tym Bold włączone; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>  CFontDialog::IsItalic

Wywołaj tę funkcję, aby określić, czy wybrana czcionka jest pochylony.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wybrana czcionka charakteryzuje się tym Italic włączone; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut

Wywołaj tę funkcję, aby określić, jeśli wyświetlony z przekreślenie wybranej czcionki.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli charakterystyka przekreślenie włączony; wybranej czcionki w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>  CFontDialog::IsUnderline

Wywołaj tę funkcję, aby określić, jeśli jest podkreślone wybranej czcionki.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli charakterystyka Podkreślenie włączone; wybranej czcionki w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

Struktura, w której członkowie przechowywania właściwości obiektu okna dialogowego.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Uwagi

Po konstruowanie `CFontDialog` obiektu, możesz użyć `m_cf` do modyfikowania różnych aspektów okno dialogowe przed wywołaniem `DoModal` funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat tej struktury, zobacz [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
