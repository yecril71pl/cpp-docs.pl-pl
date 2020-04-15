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
ms.openlocfilehash: ab8d934ca0c40c7073f2fc6d88549eb8db595b3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352236"
---
# <a name="ccolordialog-class"></a>Klasa CColorDialog

Umożliwia włączenie okna dialogowego wyboru kolorów do aplikacji.

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
|[CColorDialog::DoModal](#domodal)|Wyświetla kolorowe okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|
|[CColorDialog::GetColor](#getcolor)|Zwraca `COLORREF` strukturę zawierającą wartości wybranego koloru.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Pobiera niestandardowe kolory utworzone przez użytkownika.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Wymusza bieżące zaznaczenie kolorów do określonego koloru.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Zastądnij, aby sprawdzić poprawność koloru wprowadzonego w oknie dialogowym.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Struktura używana do dostosowywania ustawień okna dialogowego.|

## <a name="remarks"></a>Uwagi

Obiekt `CColorDialog` jest oksemeny dialogowej z listą kolorów zdefiniowanych dla systemu wyświetlania. Użytkownik może wybrać lub utworzyć określony kolor z listy, który jest następnie zgłaszany z powrotem do aplikacji po zamknięciu okna dialogowego.

Aby skonstruować `CColorDialog` obiekt, należy użyć dostarczonego konstruktora lub wyprowadzić nową klasę i użyć własnego konstruktora niestandardowego.

Po skonstruowaniu okna dialogowego można ustawić lub zmodyfikować dowolne wartości w strukturze [m_cc,](#m_cc) aby zainicjować wartości formantów okna dialogowego. Struktura *m_cc* jest typu [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1).

Po zainicjowaniu formantów okna dialogowego należy wywołać funkcję `DoModal` elementu członkowskiego, aby wyświetlić okno dialogowe i zezwolić użytkownikowi na wybranie koloru. `DoModal`zwraca wybór przez użytkownika przycisku OK (IDOK) lub Anuluj (IDCANCEL) w oknie dialogowym.

Jeśli `DoModal` zwraca IDOK, można `CColorDialog`użyć jednej z funkcji członkowskich do pobierania informacji wejściowych przez użytkownika.

Za pomocą funkcji [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) systemu Windows można ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i dowiedzieć się więcej o błędzie.

`CColorDialog`opiera się na COMMDLG. DLL, który jest dostarczany z systemem Windows w wersji 3.1 lub nowszej.

Aby dostosować okno dialogowe, wydziel klasę z `CColorDialog`programu , podaj niestandardowy szablon okna dialogowego i dodaj mapę wiadomości, aby przetworzyć wiadomości powiadomień z rozszerzonych formantów. Wszelkie nieprzetworzene wiadomości powinny być przekazywane do klasy podstawowej.

Dostosowywanie funkcji haka nie jest wymagane.

> [!NOTE]
> W niektórych `CColorDialog` instalacjach obiekt nie będzie wyświetlany z szarym tłem, jeśli użyto tej struktury do nałowienia innych `CDialog` obiektów.

Aby uzyskać więcej `CColorDialog`informacji na temat używania programu , zobacz [Typowe klasy okna dialogowego](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColorDialog::CColorDialog

Konstruuje `CColorDialog` obiekt.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*clrJnit (clrInit)*<br/>
Domyślne zaznaczenie koloru. Jeśli żadna wartość nie zostanie określona, wartością domyślną jest RGB(0,0,0) (czarny).

*Dwflags*<br/>
Zestaw flag, które dostosowują funkcję i wygląd okna dialogowego. Aby uzyskać więcej informacji, zobacz [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1) struktury w windows SDK.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub okna właściciela okna okna dialogowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog::DoModal

Wywołanie tej funkcji, aby wyświetlić okno dialogowe kolor wspólny systemu Windows i zezwolić użytkownikowi na wybranie koloru.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL. Jeśli funkcja IDCANCEL jest zwracana, należy wywołać funkcję Programu Windows [CommDlgExtendedError,](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) aby ustalić, czy wystąpił błąd.

IDOK i IDCANCEL to stałe wskazujące, czy użytkownik wybrał przycisk OK, czy Anuluj.

### <a name="remarks"></a>Uwagi

Jeśli chcesz zainicjować różne opcje okna dialogowego kolorów, ustawiając elementy członkowskie [m_cc](#m_cc) struktury, `DoModal` należy to zrobić przed wywołaniem, ale po skonstruowaniu obiektu okna dialogowego.

Po `DoModal`wywołaniu programu można wywołać inne funkcje członkowskie w celu pobrania ustawień lub informacji wprowadzonych przez użytkownika w oknie dialogowym.

### <a name="example"></a>Przykład

  Zobacz przykład [CColorDialog::CColorDialog](#ccolordialog).

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a>CColorDialog::GetColor

Wywołanie tej `DoModal` funkcji po wywołaniu, aby pobrać informacje o kolorze wybranym przez użytkownika.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość [COLORREF](/windows/win32/gdi/colorref) zawierająca informacje RGB dla koloru wybranego w oknie dialogowym kolor.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`obiekty umożliwiają użytkownikowi, oprócz wyboru kolorów, zdefiniowanie do 16 kolorów niestandardowych.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy 16 wartości kolorów RGB, która przechowuje niestandardowe kolory utworzone przez użytkownika.

### <a name="remarks"></a>Uwagi

Funkcja `GetSavedCustomColors` elementu członkowskiego zapewnia dostęp do tych kolorów. Te kolory mogą być pobierane po [DoModal](#domodal) zwraca IDOK.

Każda z 16 wartości RGB w zwróconej macierzy jest inicjowana do RGB(255,255,255) (biały). Niestandardowe kolory wybrane przez użytkownika są zapisywane tylko między wywołaniami okna dialogowego w aplikacji. Jeśli chcesz zapisać te kolory między wywołaniami aplikacji, należy zapisać je w inny sposób, na przykład w inicjacji (. INI).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a>CColorDialog::m_cc

Struktura typu [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1), którego członkowie przechowują cechy i wartości okna dialogowego.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu `CColorDialog` obiektu, można użyć *m_cc,* aby ustawić różne aspekty okna dialogowego przed wywołaniem Funkcji elementu członkowskiego [DoModal.](#domodal)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a>CColorDialog::OnColorOK

Zastądnij, aby sprawdzić poprawność koloru wprowadzonego w oknie dialogowym.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli okno dialogowe nie powinno być odrzucane; w przeciwnym razie 0, aby zaakceptować wprowadzony kolor.

### <a name="remarks"></a>Uwagi

Zastądnij tę funkcję tylko wtedy, gdy chcesz zapewnić niestandardową walidację koloru wybranego przez użytkownika w oknie dialogowym kolorów.

Użytkownik może wybrać kolor za pomocą jednej z następujących dwóch metod:

- Kliknięcie koloru na palecie kolorów. Wartości RGB wybranego koloru są następnie odzwierciedlane w odpowiednich polach edycji RGB.

- Wprowadzanie wartości w polach edycji RGB

Zastępowanie `OnColorOK` umożliwia odrzucenie koloru, który użytkownik wprowadza do wspólnego okna dialogowego kolorów z dowolnego powodu specyficznego dla aplikacji.

Zwykle nie trzeba używać tej funkcji, ponieważ struktura zapewnia domyślną weryfikację kolorów i wyświetla okno komunikatu, jeśli zostanie wprowadzony nieprawidłowy kolor.

Można wywołać [SetCurrentColor](#setcurrentcolor) od wewnątrz, `OnColorOK` aby wymusić wybór kolorów. Po `OnColorOK` zwolnieniu (oznacza to, że użytkownik klika **OK,** aby zaakceptować zmianę koloru), można wywołać [GetColor,](#getcolor) aby uzyskać wartość RGB nowego koloru.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

Wywołanie tej `DoModal` funkcji po wywołaniu, aby wymusić bieżące zaznaczenie koloru do wartości koloru określonej w *clr*.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana z `OnColorOK`poziomu programu obsługi wiadomości lub . Okno dialogowe automatycznie zaktualizuje wybór użytkownika na podstawie wartości parametru *clr.*

### <a name="example"></a>Przykład

  Zobacz przykład [CColorDialog::OnColorOK](#oncolorok).

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
