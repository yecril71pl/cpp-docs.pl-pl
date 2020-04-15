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
ms.openlocfilehash: 6ece239496def9fd65a95a622ac3c475fe5becea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373821"
---
# <a name="cfontdialog-class"></a>Klasa CFontDialog

Umożliwia włączenie okna dialogowego wyboru czcionek do aplikacji.

## <a name="syntax"></a>Składnia

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Konstruuje `CFontDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|
|[CFontDialog::GetCharFormat](#getcharformat)|Pobiera formatowanie znaków wybranej czcionki.|
|[CFontDialog::GetColor](#getcolor)|Zwraca kolor wybranej czcionki.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Przypisuje do `LOGFONT` struktury charakterystyki aktualnie wybranej czcionki.|
|[CFontDialog::GetFaceName](#getfacename)|Zwraca nazwę twarzy wybranej czcionki.|
|[CFontDialog::GetSize](#getsize)|Zwraca rozmiar punktu wybranej czcionki.|
|[CFontDialog::GetStyleName](#getstylename)|Zwraca nazwę stylu wybranej czcionki.|
|[CFontDialog::GetWeight](#getweight)|Zwraca wagę wybranej czcionki.|
|[CFontDialog::IsBold](#isbold)|Określa, czy czcionka jest pogrubiona.|
|[CFontDialog::IsItalic](#isitalic)|Określa, czy czcionka jest kursywą.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Określa, czy czcionka jest wyświetlana z przekreślenia.|
|[CFontDialog::IsUnderline](#isunderline)|Określa, czy czcionka jest podkreślona.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Struktura używana do dostosowywania `CFontDialog` obiektu.|

## <a name="remarks"></a>Uwagi

Obiekt `CFontDialog` to okno dialogowe z listą czcionek aktualnie zainstalowanych w systemie. Użytkownik może wybrać określoną czcionkę z listy, a ten wybór jest następnie zgłaszany z powrotem do aplikacji.

Aby skonstruować `CFontDialog` obiekt, należy użyć dostarczonego konstruktora lub wyprowadzić nową podklasę i użyć własnego konstruktora niestandardowego.

Po `CFontDialog` skonstruowaniu obiektu można użyć `m_cf` struktury do zainicjowania wartości lub stanów formantów w oknie dialogowym. Struktura [m_cf](#m_cf) jest typu [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

Po zainicjowaniu formanty obiektu okna `DoModal` dialogowego wywołaj funkcję elementu członkowskiego, aby wyświetlić okno dialogowe i zezwolić użytkownikowi na wybranie czcionki. `DoModal`zwraca, czy użytkownik wybrał przycisk OK (IDOK) czy Anuluj (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, można `CFontDialog`użyć jednej z funkcji członkowskich do pobierania informacji wejściowych przez użytkownika.

Za pomocą funkcji [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) systemu Windows można ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i dowiedzieć się więcej o błędzie. Aby uzyskać więcej informacji na temat tej funkcji, zobacz SDK systemu Windows.

`CFontDialog`opiera się na COMMDLG. DLL, który jest dostarczany z systemem Windows w wersji 3.1 lub nowszej.

Aby dostosować okno dialogowe, należy `CFontDialog`wyprowadzić klasę z programu , podaj niestandardowy szablon okna dialogowego i dodaj mapę wiadomości do przetwarzania wiadomości powiadomień z rozszerzonych formantów. Wszelkie nieprzetworzene wiadomości powinny być przekazywane do klasy podstawowej.

Dostosowywanie funkcji haka nie jest wymagane.

Aby uzyskać więcej `CFontDialog`informacji na temat używania programu , zobacz [Typowe klasy dialogów dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a>CFontDialog::CFontDialog

Konstruuje `CFontDialog` obiekt.

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

*plfInitial plfInitial plfInitial plf*<br/>
Wskaźnik do struktury danych [LOGFONT,](/windows/win32/api/wingdi/ns-wingdi-logfontw) który pozwala ustawić niektóre właściwości czcionki.

*charFormat (charFormat)*<br/>
Wskaźnik do struktury danych [CHARFORMAT,](/windows/win32/api/richedit/ns-richedit-charformata) który pozwala ustawić niektóre właściwości czcionki w formant edycji bogatej.

*Dwflags*<br/>
Określa co najmniej jedną flagę choose-font. Co najmniej jedna wstępnie ustawiona wartość może być łączona za pomocą operatora or bitowego. Jeśli zmodyfikujesz `m_cf.Flag`element członkowski struktury s, należy użyć operatora or bitowego w zmianach, aby zachować domyślne zachowanie nienaruszone. Szczegółowe informacje na temat każdej z tych flag można znaleźć w opisie struktury [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) w zestaw windows SDK.

*pdcPrinter*<br/>
Wskaźnik do kontekstu drukarki i urządzenia. Jeśli podano, ten parametr wskazuje kontekst drukarki i urządzenia dla drukarki, na której mają być wybrane czcionki.

*pParentWnd*<br/>
A pointer to the font dialog box's parent or owner window.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że konstruktor automatycznie wypełnia `CHOOSEFONT` elementy członkowskie struktury. Należy je zmienić tylko wtedy, gdy okno dialogowe czcionki ma być inne niż domyślne.

> [!NOTE]
> Pierwsza wersja tej funkcji istnieje tylko wtedy, gdy nie ma obsługi kontroli edycji rozszerzonej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a>CFontDialog::DoModal

Wywołanie tej funkcji, aby wyświetlić okno dialogowe typowe czcionki systemu Windows i zezwolić użytkownikowi na wybranie czcionki.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli funkcja IDCANCEL jest zwracana, należy wywołać funkcję Programu Windows [CommDlgExtendedError,](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) aby ustalić, czy wystąpił błąd.

IDOK i IDCANCEL to stałe wskazujące, czy użytkownik wybrał przycisk OK, czy Anuluj.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne formanty okna dialogowego czcionki, ustawiając elementy członkowskie `DoModal`struktury [m_cf,](#m_cf) należy to zrobić przed wywołaniem , ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub informacje wprowadzone przez użytkownika w oknie dialogowym.

### <a name="example"></a>Przykład

  Zobacz przykłady [CFontDialog::CFontDialog](#cfontdialog) i [CFontDialog::GetColor](#getcolor).

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a>CFontDialog::GetCharFormat

Pobiera formatowanie znaków wybranej czcionki.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parametry

*Por*<br/>
Struktura [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) zawierająca informacje o formatowaniu znaków wybranej czcionki.

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a>CFontDialog::GetColor

Wywołanie tej funkcji w celu pobrania wybranego koloru czcionki.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor wybranej czcionki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

Wywołanie tej funkcji, aby przypisać cechy aktualnie wybranej czcionki do elementów członkowskich struktury [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parametry

*lplf*<br/>
Wskaźnik do `LOGFONT` struktury.

### <a name="remarks"></a>Uwagi

Inne `CFontDialog` funkcje członkowskie są dostarczane w celu uzyskania dostępu do indywidualnych cech bieżącej czcionki.

Jeśli ta funkcja jest wywoływana podczas wywołania [DoModal](#domodal), zwraca bieżące zaznaczenie w czasie (co użytkownik widzi lub zmienił w oknie dialogowym). Jeśli ta funkcja jest wywoływana po wywołaniu `DoModal` (tylko wtedy, gdy `DoModal` zwraca IDOK), zwraca to, co użytkownik faktycznie wybrany.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a>CFontDialog::GetFaceName

Wywołanie tej funkcji, aby pobrać nazwę twarzy wybranej czcionki.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa twarzy czcionki zaznaczonej `CFontDialog` w oknie dialogowym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a>CFontDialog::GetSize

Wywołanie tej funkcji, aby pobrać rozmiar wybranej czcionki.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar czcionki w dziesiątych częściach punktu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a>CFontDialog::GetStyleName

Wywołanie tej funkcji, aby pobrać nazwę stylu wybranej czcionki.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa stylu czcionki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a>CFontDialog::GetWeight

Wywołanie tej funkcji, aby pobrać wagę wybranej czcionki.

```
int GetWeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Waga wybranej czcionki.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat wagi czcionki, zobacz [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a>CFontDialog::IsBold

Wywołanie tej funkcji, aby ustalić, czy wybrana czcionka jest pogrubiona.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Wartość zwracana

Opcja niezerowa, jeśli wybrana czcionka ma włączoną charakterystykę Pogrubienia; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a>CFontDialog::IsItalic

Wywołanie tej funkcji, aby ustalić, czy wybrana czcionka jest kursywa.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli wybrana czcionka ma włączoną charakterystykę kursywa; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a>CFontDialog::IsStrikeOut

Wywołanie tej funkcji, aby ustalić, czy wybrana czcionka jest wyświetlana z przekreślenia.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Wartość zwracana

Opcja niezerowa, jeśli wybrana czcionka ma włączoną charakterystykę Przekreślenia; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a>CFontDialog::IsUnderline

Wywołanie tej funkcji, aby ustalić, czy wybrana czcionka jest podkreślona.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli wybrana czcionka ma włączoną charakterystykę Podkreślenia; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a>CFontDialog::m_cf

Struktura, której członkowie przechowują właściwości obiektu okna dialogowego.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CFontDialog` obiektu, można `m_cf` użyć do modyfikowania różnych aspektów `DoModal` okna dialogowego przed wywołaniem funkcji elementu członkowskiego. Aby uzyskać więcej informacji na temat tej struktury, zobacz [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
