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
ms.openlocfilehash: bc9bc76b328359d4c8ec7796de7dfaa7d3a9cf2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207728"
---
# <a name="ccolordialog-class"></a>Klasa CColorDialog

Umożliwia uwzględnienie okna dialogowego wyboru koloru w aplikacji.

## <a name="syntax"></a>Składnia

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|Konstruuje `CColorDialog` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|Wyświetla okno dialogowe kolorów i umożliwia użytkownikowi dokonać wyboru.|
|[CColorDialog::GetColor](#getcolor)|Zwraca `COLORREF` struktury zawierającej wartości kolorów.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Pobiera kolorów niestandardowych utworzonych przez użytkownika.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Wymusza bieżący wybór koloru określony kolor.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Przesłonić, aby zweryfikować kolor wprowadzane do okna dialogowego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Struktura służące do dostosowywania ustawień w oknie dialogowym.|

## <a name="remarks"></a>Uwagi

Element `CColorDialog` obiektu to okno dialogowe z listą kolorów, które są zdefiniowane dla systemu wyświetlania. Użytkownika można wybrać lub utworzyć konkretny kolor z listy, który jest następnie odsyłane do aplikacji podczas zamyka okno dialogowe.

Do konstruowania `CColorDialog` obiektu, użyć dostarczonego konstruktora lub nową klasę pochodną i używania niestandardowego konstruktora.

Gdy okno dialogowe został skonstruowany, można ustawić lub zmodyfikować dowolne wartości na [m_cc](#m_cc) strukturę, aby zainicjować wartości formantów w oknie dialogowym. *M_cc* struktury jest typu [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora).

Po inicjalizacji formantów w oknie dialogowym, należy wywołać `DoModal` funkcja elementu członkowskiego, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie koloru. `DoModal` Zwraca wybranych przez użytkownika przycisku OK (IDOK) lub anulować (IDCANCEL) albo okno dialogowe.

Jeśli `DoModal` zwraca IDOK, możesz użyć jednej z `CColorDialog`przez funkcje Członkowskie można pobrać informacji o danych wejściowych przez użytkownika.

Możesz użyć Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkcji, aby ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i Dowiedz się więcej o błędzie.

`CColorDialog` opiera się na pliku COMMDLG. Plik DLL, który jest dostarczany z programem Windows w wersji 3.1 lub nowszej.

Aby dostosować okno dialogowe, należy wyprowadzić klasę z `CColorDialog`, udostępniają szablon niestandardowy dialog i dodać mapy wiadomości, przetwarzanie komunikatów powiadomień od formantów rozszerzonego. Wszystkie nieprzetworzone komunikaty powinien zostać przekazany do klasy bazowej.

Dostosowywanie funkcji punktów zaczepienia nie jest wymagana.

> [!NOTE]
>  W przypadku niektórych instalacji `CColorDialog` obiektu nie będą wyświetlane na szarym tle, jeśli używasz programu framework się inne `CDialog` szary obiektów.

Aby uzyskać więcej informacji na temat korzystania z `CColorDialog`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

##  <a name="ccolordialog"></a>  CColorDialog::CColorDialog

Konstruuje `CColorDialog` obiektu.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*clrInit*<br/>
Domyślny wybór kolorów. Jeśli nie określono wartości, wartość domyślna to RGB(0,0,0) (czarny).

*dwFlags*<br/>
Zestaw flag, umożliwiające dostosowanie funkcji i wygląd okna dialogowego. Aby uzyskać więcej informacji, zobacz [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora) struktury w zestawie Windows SDK.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub właściciela okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>  CColorDialog::DoModal

Wywołaj tę funkcję, aby wyświetlić wspólne okno dialogowe kolorów Windows i Zezwalaj użytkownikowi na wybranie koloru.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli zwracana jest IDCANCEL, wywołaj Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkcję, aby ustalić, czy wystąpił błąd.

IDOK i IDCANCEL są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne opcje Okno dialogowe kolorów, ustawiając członkowie [m_cc](#m_cc) struktury, należy to zrobić przed wywołaniem `DoModal` , ale po obiekt okno dialogowe jest konstruowany.

Po wywołaniu `DoModal`, może wywołać inny członek funkcje, które można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.

### <a name="example"></a>Przykład

  Zobacz przykład [CColorDialog::CColorDialog](#ccolordialog).

##  <a name="getcolor"></a>  CColorDialog::GetColor

Wywołaj tę funkcję, po wywołaniu `DoModal` można pobrać informacji o kolor wybrany przez użytkownika.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

A [COLORREF](/windows/desktop/gdi/colorref) wartość, która zawiera informacje o RGB na kolor wybrany w oknie dialogowym koloru.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>  CColorDialog::GetSavedCustomColors

`CColorDialog` obiekty zezwolić użytkownikowi, oprócz możliwości wyboru kolorów, definiowanie kolorów niestandardowych do 16.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy 16 wartości kolorów RGB, która przechowuje kolorów niestandardowych utworzonych przez użytkownika.

### <a name="remarks"></a>Uwagi

`GetSavedCustomColors` Funkcji składowej zapewnia dostęp do tych kolorów. Te kolory mogą być pobierane po [DoModal](#domodal) zwraca IDOK.

16 wartości RGB w zwróconej tablicy jest ustawiana na RGB(255,255,255) (biały). Kolory niestandardowe wybierany przez użytkownika są zapisywane tylko między wywołań okno dialogowe w aplikacji. Jeśli chcesz zapisać te kolory między wywołań aplikacji, musisz zapisać je w inny sposób, takie jak w inicjalizacji (. Plik INI).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>  CColorDialog::m_cc

Struktury typu [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora), której członkowie przechowywania właściwości i wartości w oknie dialogowym.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Uwagi

Po konstruowanie `CColorDialog` obiektu, możesz użyć *m_cc* można ustawić różne aspekty okno dialogowe przed wywołaniem [DoModal](#domodal) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>  CColorDialog::OnColorOK

Przesłonić, aby zweryfikować kolor wprowadzane do okna dialogowego.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli okno dialogowe nie powinien być ukryty; w przeciwnym razie 0, aby zaakceptować kolor, który został wprowadzony.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, tylko wtedy, gdy chcesz zapewnić niestandardowego sprawdzania poprawności koloru, wybranego przez użytkownika w oknie dialogowym koloru.

Użytkownik może wybrać kolor, za pomocą jednej z następujących dwóch metod:

- Kliknięcie kolor w palecie kolorów. Wybrany kolor wartości RGB następnie są odzwierciedlane w odpowiednich polach edycji RGB.

- Wprowadzanie wartości RGB pól edycji

Zastępowanie `OnColorOK` umożliwia odrzucanie kolor wprowadzonych przez użytkownika w wspólne okno dialogowe kolorów, jakiejkolwiek przyczyny specyficzne dla aplikacji.

Zwykle nie trzeba używać tej funkcji, ponieważ struktura zawiera domyślnego procesu sprawdzania poprawności kolorów i wyświetla okno komunikatu, jeśli podano nieprawidłowy kolor.

Możesz wywołać [SetCurrentColor](#setcurrentcolor) z poziomu `OnColorOK` wymusić wybór koloru. Raz `OnColorOK` zostało wyzwolone (czyli użytkownik klika polecenie **OK** aby zaakceptować zmianę koloru), można wywołać [getcolor —](#getcolor) można pobrać wartości RGB nowy kolor.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>  CColorDialog::SetCurrentColor

Wywołaj tę funkcję, po wywołaniu `DoModal` wymusić bieżący wybór koloru wartość koloru, określoną w *clr*.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*clr*<br/>
Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana z w ramach programu obsługi komunikatów lub `OnColorOK`. Okno dialogowe zostanie automatycznie zaktualizowana wybranych przez użytkownika w oparciu o wartość *clr* parametru.

### <a name="example"></a>Przykład

  Zobacz przykład [CColorDialog::OnColorOK](#oncolorok).

## <a name="see-also"></a>Zobacz także

[Próbki MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
