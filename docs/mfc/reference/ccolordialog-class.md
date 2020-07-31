---
title: Klasa CColorDialog
ms.date: 11/04/2016
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
ms.openlocfilehash: 54fd987d683a9236531baee3afbb9ee61be623e2
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470761"
---
# <a name="ccolordialog-class"></a>Klasa CColorDialog

Umożliwia dołączenie okna dialogowego wyboru koloru do aplikacji.

## <a name="syntax"></a>Składnia

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|Konstruuje `CColorDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::D oModal](#domodal)|Wyświetla okno dialogowe koloru i umożliwia użytkownikowi wybranie.|
|[CColorDialog:: GetColor](#getcolor)|Zwraca `COLORREF` strukturę zawierającą wartości wybranego koloru.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Pobiera kolory niestandardowe utworzone przez użytkownika.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Wymusza bieżący wybór koloru do określonego koloru.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Przesłoń, aby sprawdzić poprawność wprowadzonego koloru do okna dialogowego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog:: m_cc](#m_cc)|Struktura używana do dostosowywania ustawień okna dialogowego.|

## <a name="remarks"></a>Uwagi

`CColorDialog`Obiekt to okno dialogowe z listą kolorów, które są zdefiniowane dla systemu wyświetlania. Użytkownik może wybrać lub utworzyć określony kolor z listy, który następnie zostanie zgłoszony z powrotem do aplikacji po zakończeniu działania okna dialogowego.

Aby skonstruować `CColorDialog` obiekt, użyj dostarczonego konstruktora lub Utwórz nową klasę i użyj własnego konstruktora niestandardowego.

Po skonstruowaniu okna dialogowego można ustawić lub zmodyfikować dowolne wartości w strukturze [m_cc](#m_cc) , aby zainicjować wartości kontrolek okna dialogowego. Struktura *m_cc* jest typu [chooseColor](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1).

Po zainicjowaniu kontrolek okna dialogowego Wywołaj `DoModal` funkcję członkowską, aby wyświetlić okno dialogowe i umożliwić użytkownikowi wybranie koloru. `DoModal`zwraca wybór użytkownika okna dialogowego OK (IDOK) lub przycisk Anuluj (IDCANCEL).

Jeśli `DoModal` zwraca IDOK, można użyć jednej z `CColorDialog` funkcji Członkowskich, aby pobrać informacje wprowadzane przez użytkownika.

Można użyć funkcji [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) systemu Windows, aby określić, czy wystąpił błąd podczas inicjowania okna dialogowego i dowiedzieć się więcej o błędzie.

`CColorDialog`opiera się na pliku COMMDLG.DLL, który jest dostarczany z systemem Windows w wersji 3,1 lub nowszej.

Aby dostosować okno dialogowe, wyprowadzić klasę z `CColorDialog` , udostępnić niestandardowy szablon okna dialogowego i dodać mapę komunikatów do przetwarzania komunikatów powiadomień z formantów rozszerzonych. Wszystkie nieprzetworzone komunikaty powinny być przesyłane do klasy bazowej.

Dostosowywanie funkcji Hook nie jest wymagane.

> [!NOTE]
> W przypadku niektórych instalacji `CColorDialog` obiekt nie będzie wyświetlany z szarym tłem, jeśli użyto struktury, aby inne obiekty były `CDialog` szare.

Aby uzyskać więcej informacji na temat korzystania z programu `CColorDialog` , zobacz [wspólne klasy okien dialogowych](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs. h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColorDialog::CColorDialog

Konstruuje `CColorDialog` obiekt.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*clrInit*<br/>
Domyślny wybór koloru. Jeśli żadna wartość nie zostanie określona, wartością domyślną jest RGB (0, 0, 0) (czerń).

*flagiDW*<br/>
Zestaw flag, które dostosowują funkcję i wygląd okna dialogowego. Aby uzyskać więcej informacji, zapoznaj się ze strukturą [chooseColor](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1) w Windows SDK.

*pParentWnd*<br/>
Wskaźnik do okna dialogowego nadrzędnego lub właściciela.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog::D oModal

Wywołaj tę funkcję, aby wyświetlić okno dialogowe typowy kolor systemu Windows i umożliwić użytkownikowi wybranie koloru.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli IDCANCEL jest zwracany, wywołaj funkcję Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) , aby określić, czy wystąpił błąd.

IDOK i IDCANCEL są stałymi, które wskazują, czy użytkownik zaznaczył przycisk OK lub Anuluj.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne opcje okna dialogowego koloru, ustawiając elementy członkowskie struktury [m_cc](#m_cc) , należy to zrobić przed wywołaniem, `DoModal` ale po skonstruowaniu obiektu okna dialogowego.

Po wywołaniu `DoModal` można wywołać inne funkcje członkowskie, aby pobrać ustawienia lub dane wejściowe użytkownika w oknie dialogowym.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CColorDialog:: CColorDialog](#ccolordialog).

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a>CColorDialog:: GetColor

Wywołaj tę funkcję po wywołaniu, `DoModal` Aby pobrać informacje o wybranym przez użytkownika kolorze.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) , która zawiera informacje RGB dotyczące koloru wybranego w oknie dialogowym koloru.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`obiekty zezwalają użytkownikowi, oprócz wybierania kolorów, definiować do 16 kolorów niestandardowych.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy o 16 wartościach koloru RGB, który przechowuje kolory niestandardowe utworzone przez użytkownika.

### <a name="remarks"></a>Uwagi

`GetSavedCustomColors`Funkcja członkowska zapewnia dostęp do tych kolorów. Te kolory można pobrać po [DoModal](#domodal) zwraca IDOK.

Każda z 16 wartości RGB w zwróconej tablicy jest inicjowana do RGB (255255255) (biały). Kolory niestandardowe wybrane przez użytkownika są zapisywane tylko między wywołaniami okna dialogowego w aplikacji. Jeśli chcesz zapisać te kolory między wywołaniami aplikacji, musisz zapisać je w inny sposób, na przykład w przypadku inicjalizacji (. INI).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a>CColorDialog:: m_cc

Struktura typu [chooseColor](/windows/win32/api/commdlg/ns-commdlg-choosecolora-r1), której członkowie przechowują cechy i wartości okna dialogowego.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CColorDialog` obiektu można użyć *m_cc* , aby ustawić różne aspekty okna dialogowego przed wywołaniem funkcji składowej [DoModal](#domodal) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a>CColorDialog::OnColorOK

Przesłoń, aby sprawdzić poprawność wprowadzonego koloru do okna dialogowego.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli okno dialogowe nie powinno być odrzucane; w przeciwnym razie wartość 0 powoduje zaakceptowanie wprowadzonego koloru.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję tylko wtedy, gdy chcesz zapewnić niestandardową weryfikację koloru wybieranego przez użytkownika w oknie dialogowym kolor.

Użytkownik może wybrać kolor przy użyciu jednej z następujących dwóch metod:

- Kliknięcie koloru na palecie kolorów. Wartości RGB wybranego koloru są następnie odzwierciedlone w odpowiednich polach edycji RGB.

- Wprowadzanie wartości w polach edycji RGB

Zastępowanie `OnColorOK` pozwala odrzucić kolor wprowadzony przez użytkownika w oknie dialogowym wspólnego koloru dla każdej przyczyny specyficznej dla aplikacji.

Zwykle nie trzeba używać tej funkcji, ponieważ struktura zapewnia domyślną weryfikację kolorów i wyświetla okno komunikatu, jeśli wprowadzono nieprawidłowy kolor.

Możesz wywołać [SetCurrentColor](#setcurrentcolor) z wewnątrz `OnColorOK` , aby wymusić wybór koloru. Po uruchomieniu `OnColorOK` (oznacza to, że użytkownik klika **przycisk OK** , aby zaakceptować zmianę koloru), można wywołać metodę [GetColor](#getcolor) , aby uzyskać wartość RGB nowego koloru.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

Wywołaj tę funkcję po wywołaniu, `DoModal` Aby wymusić bieżące zaznaczenie koloru do wartości koloru określonej w *CLR*.

```cpp
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana z poziomu procedury obsługi komunikatów lub `OnColorOK` . Okno dialogowe automatycznie zaktualizuje wybór użytkownika na podstawie wartości parametru *CLR* .

### <a name="example"></a>Przykład

  Zobacz przykład dla [CColorDialog:: OnColorOK](#oncolorok).

## <a name="see-also"></a>Zobacz także

[Przykładowy interfejs MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład DRAWCLI MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
