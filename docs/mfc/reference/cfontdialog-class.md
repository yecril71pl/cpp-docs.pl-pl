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
ms.openlocfilehash: c0d0c37d055d9b337f7b709b4ee3d299daae7658
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741555"
---
# <a name="cfontdialog-class"></a>Klasa CFontDialog

Umożliwia włączenie okna dialogowego wyboru czcionki do aplikacji.

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
|[CFontDialog::D oModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi wybranie.|
|[CFontDialog::GetCharFormat](#getcharformat)|Pobiera formatowanie znaku wybranej czcionki.|
|[CFontDialog:: GetColor](#getcolor)|Zwraca kolor wybranej czcionki.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Przypisuje charakterystykę aktualnie wybranej czcionki do `LOGFONT` struktury.|
|[CFontDialog:: getkrojuname](#getfacename)|Zwraca nazwę kroju zaznaczonej czcionki.|
|[CFontDialog:: GetSize](#getsize)|Zwraca rozmiar wybranego czcionki.|
|[CFontDialog:: GetStyleName](#getstylename)|Zwraca nazwę stylu wybranej czcionki.|
|[CFontDialog:: getwagi](#getweight)|Zwraca grubość wybranej czcionki.|
|[CFontDialog:: isbold](#isbold)|Określa, czy czcionka jest pogrubiona.|
|[CFontDialog:: iskursywa](#isitalic)|Określa, czy czcionka jest kursywą.|
|[CFontDialog:: isprzekreolenie](#isstrikeout)|Określa, czy czcionka jest wyświetlana z przekreśleniem.|
|[CFontDialog:: ispodkreolenie](#isunderline)|Określa, czy czcionka jest podkreślona.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Struktura używana do dostosowywania `CFontDialog` obiektu.|

## <a name="remarks"></a>Uwagi

`CFontDialog` Obiekt to okno dialogowe z listą czcionek, które są obecnie zainstalowane w systemie. Użytkownik może wybrać konkretną czcionkę z listy, a następnie ponownie zgłosić ten wybór do aplikacji.

Aby skonstruować `CFontDialog` obiekt, użyj dostarczonego konstruktora lub Utwórz nową podklasę i użyj własnego konstruktora niestandardowego.

Gdy obiekt został skonstruowany, można `m_cf` użyć struktury, aby zainicjować wartości lub Stany kontrolek w oknie dialogowym. `CFontDialog` Struktura [m_cf](#m_cf) jest typu [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

Po zainicjowaniu kontrolek obiektu okna dialogowego Wywołaj `DoModal` funkcję członkowską, aby wyświetlić okno dialogowe i umożliwić użytkownikowi wybranie czcionki. `DoModal`Zwraca czy użytkownik zaznaczył przycisk OK (IDOK) lub Anuluj (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, można użyć jednej z `CFontDialog`funkcji Członkowskich, aby pobrać informacje wprowadzane przez użytkownika.

Można użyć funkcji [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) systemu Windows, aby określić, czy wystąpił błąd podczas inicjowania okna dialogowego i dowiedzieć się więcej o błędzie. Aby uzyskać więcej informacji na temat tej funkcji, zobacz Windows SDK.

`CFontDialog`opiera się na COMMDLG. Plik DLL, który jest dostarczany z systemem Windows w wersji 3,1 lub nowszej.

Aby dostosować okno dialogowe, wyprowadzić klasę z `CFontDialog`, udostępnić niestandardowy szablon okna dialogowego i dodać mapę komunikatów do przetwarzania komunikatów powiadomień z formantów rozszerzonych. Wszystkie nieprzetworzone komunikaty powinny być przesyłane do klasy bazowej.

Dostosowywanie funkcji Hook nie jest wymagane.

Aby uzyskać więcej informacji na `CFontDialog`temat korzystania z programu, zobacz [wspólne klasy okien dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs. h

##  <a name="cfontdialog"></a>CFontDialog::CFontDialog

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

*plfInitial*<br/>
Wskaźnik do struktury danych [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) , który umożliwia ustawienie niektórych charakterystyk czcionki.

*charFormat*<br/>
Wskaźnik do struktury danych [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) , który umożliwia ustawienie niektórych charakterystyk czcionki w kontrolce edycji wzbogaconej.

*flagiDW*<br/>
Określa co najmniej jedną flagę wybierania czcionki. Jedną lub więcej wartości wstępnie ustawionych można łączyć za pomocą operatora bitowego or. Jeśli zmodyfikujesz `m_cf.Flag`element członkowski struktury s, pamiętaj, aby użyć operatora bitowego lub w zmianach, aby zachować zachowanie domyślne bez zmian. Aby uzyskać szczegółowe informacje na temat każdej z tych flag, zobacz opis struktury [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) w Windows SDK.

*pdcPrinter*<br/>
Wskaźnik do kontekstu drukarki i urządzenia. Jeśli jest podany, ten parametr wskazuje kontekst urządzenia drukarka dla drukarki, na której mają zostać wybrane czcionki.

*pParentWnd*<br/>
Wskaźnik do okna dialogowego czcionka lub okno dialogowe.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że Konstruktor automatycznie wypełnia elementy członkowskie `CHOOSEFONT` struktury. Należy je zmienić tylko wtedy, gdy chcesz, aby okno dialogowe czcionki było inne niż domyślne.

> [!NOTE]
>  Pierwsza wersja tej funkcji istnieje tylko wtedy, gdy nie ma obsługi kontrolki edycji wzbogaconej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>CFontDialog::D oModal

Wywołaj tę funkcję, aby wyświetlić okno dialogowe typowe czcionki systemu Windows i umożliwić użytkownikowi wybranie czcionki.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli IDCANCEL jest zwracany, wywołaj funkcję Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) , aby określić, czy wystąpił błąd.

IDOK i IDCANCEL są stałymi, które wskazują, czy użytkownik zaznaczył przycisk OK lub Anuluj.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne kontrolki okna dialogowego z czcionkami, ustawiając elementy członkowskie struktury [m_cf](#m_cf) , należy to zrobić przed wywołaniem `DoModal`, ale po skonstruowaniu obiektu okna dialogowego.

Jeśli `DoModal` zwraca IDOK, można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub dane wejściowe użytkownika w oknie dialogowym.

### <a name="example"></a>Przykład

  Zobacz przykłady dla [CFontDialog:: CFontDialog](#cfontdialog) i [CFontDialog:: GetColor](#getcolor).

##  <a name="getcharformat"></a>CFontDialog::GetCharFormat

Pobiera formatowanie znaku wybranej czcionki.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Struktura [CHARFORMATa](/windows/win32/api/richedit/ns-richedit-charformata) zawierająca informacje o formatowaniu znaków zaznaczonej czcionki.

##  <a name="getcolor"></a>CFontDialog:: GetColor

Wywołaj tę funkcję, aby pobrać wybrany kolor czcionki.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor wybranej czcionki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

Wywołaj tę funkcję, aby przypisać charakterystykę aktualnie wybranej czcionki do elementów członkowskich struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parametry

*lplf*<br/>
Wskaźnik do `LOGFONT` struktury.

### <a name="remarks"></a>Uwagi

Inne `CFontDialog` funkcje członkowskie są udostępniane w celu uzyskania dostępu do poszczególnych charakterystyk bieżącej czcionki.

Jeśli ta funkcja jest wywoływana podczas wywołania do [DoModal](#domodal), zwraca bieżące zaznaczenie w czasie (co użytkownik widzi lub zmieniło się w oknie dialogowym). Jeśli ta funkcja jest wywoływana po wywołaniu metody `DoModal` (tylko wtedy, gdy `DoModal` zwróci IDOK), zwraca wartość, która rzeczywiście została wybrana przez użytkownika.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>CFontDialog:: getkrojuname

Wywołaj tę funkcję, aby pobrać nazwę kroju zaznaczonej czcionki.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa kroju czcionki zaznaczonej w `CFontDialog` oknie dialogowym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>CFontDialog:: GetSize

Wywołaj tę funkcję, aby pobrać rozmiar wybranej czcionki.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar czcionki w dziesiątych punktach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>CFontDialog:: GetStyleName

Wywołaj tę funkcję, aby pobrać nazwę stylu wybranej czcionki.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa stylu czcionki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>CFontDialog:: getwagi

Wywołaj tę funkcję, aby pobrać wagę wybranej czcionki.

```
int GetWeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Grubość wybranej czcionki.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat wagi czcionki, zobacz [CFont:: Font](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>CFontDialog:: isbold

Wywołaj tę funkcję, aby określić, czy wybrana czcionka jest pogrubiona.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli wybrana czcionka ma włączoną cechę pogrubioną; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>CFontDialog:: iskursywa

Wywołaj tę funkcję, aby określić, czy wybrana czcionka jest kursywą.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli wybrana czcionka ma włączoną cechę kursywy; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>CFontDialog:: isprzekreolenie

Wywołaj tę funkcję, aby określić, czy wybrana czcionka jest wyświetlana z przekreśleniem.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli wybrana czcionka ma włączoną cechę przekreolenie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>CFontDialog:: ispodkreolenie

Wywołaj tę funkcję, aby określić, czy wybrana czcionka jest podkreślona.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli wybrana czcionka ma włączoną cechę podkreolenia; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>CFontDialog::m_cf

Struktura, której członkowie przechowują charakterystykę obiektu okna dialogowego.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CFontDialog` obiektu można użyć `m_cf` , aby zmodyfikować różne aspekty okna `DoModal` dialogowego przed wywołaniem funkcji składowej. Aby uzyskać więcej informacji na temat tej struktury, zobacz [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
