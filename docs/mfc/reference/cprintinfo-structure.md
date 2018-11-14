---
title: Cprintinfo — struktura
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 259dfd6808a5e975fb22d11d0a8c569237733eae
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524524"
---
# <a name="cprintinfo-structure"></a>Cprintinfo — struktura

Przechowuje informacje o zadaniu drukowania i podglądu wydruku.

## <a name="syntax"></a>Składnia

```
struct CPrintInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintInfo::GetFromPage](#getfrompage)|Zwraca numer pierwszej strony drukowanego.|
|[CPrintInfo::GetMaxPage](#getmaxpage)|Zwraca numer ostatniej strony dokumentu.|
|[CPrintInfo::GetMinPage](#getminpage)|Zwraca numer pierwszej strony dokumentu.|
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Zwraca liczbę stron poprzedzających na pierwszej stronie element DocObject drukowanego w scalonej DocObject zadania drukowania.|
|[CPrintInfo::GetToPage](#gettopage)|Zwraca numer ostatniej strony drukowanego.|
|[CPrintInfo::SetMaxPage](#setmaxpage)|Ustawia numer ostatniej strony dokumentu.|
|[CPrintInfo::SetMinPage](#setminpage)|Ustawia numer pierwszej strony dokumentu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Zawiera flagę wskazującą, czy w ramach powinno być kontynuowane drukowania pętli.|
|[CPrintInfo::m_bDirect](#m_bdirect)|Zawiera flagę wskazującą, czy dokument jest drukowany bezpośrednio (bez wyświetlania okna dialogowego drukowania).|
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Zawiera flagę wskazującą, czy drukowany dokument jest obiekt DocObject.|
|[CPrintInfo::m_bPreview](#m_bpreview)|Zawiera flagę wskazującą, czy dokument jest przeglądany.|
|[CPrintInfo::m_dwFlags](#m_dwflags)|Określa DocObject operacji drukowania.|
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Zawiera wskaźnik do struktury utworzone przez użytkownika.|
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Określa liczbę obecnie drukowanej strony.|
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Określa numer zadania przypisaną przez system operacyjny dla bieżącego zadania drukowania|
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Określa liczbę stron wyświetlanych w oknie Podgląd; 1 lub 2.|
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Określa przesunięcie określonego DocObject pierwszą stronę w scalonej DocObject zadania drukowania.|
|[CPrintInfo::m_pPD](#m_ppd)|Zawiera wskaźnik do `CPrintDialog` obiekt używany dla okna dialogowego drukowania.|
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Określa prostokąta obszaru bieżącej strony można używać do definiowania.|
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Zawiera ciąg formatu w celu wyświetlenia numer strony.|

## <a name="remarks"></a>Uwagi

`CPrintInfo` jest to struktura i nie ma klasy bazowej.

Szablon tworzy obiekt `CPrintInfo` każdym Print lub polecenie Podgląd wydruku jest wybierany i niszczy go po zakończeniu polecenia.

`CPrintInfo` zawiera informacje o zadaniu drukowania jako całości, na przykład zakres stron do wydrukowania i bieżący stan zadania drukowania, takich jak strony właśnie drukowane. Niektóre informacje są przechowywane w skojarzoną [CPrintDialog](../../mfc/reference/cprintdialog-class.md) obiektu; ten obiekt zawiera wartości wprowadzone przez użytkownika w oknie dialogowym drukowania.

Element `CPrintInfo` obiektu jest przekazywana między struktury i klasy widoku podczas drukowania i służy do wymiany informacji między nimi. Na przykład platformę informuje klasa widoku strony, która na dokument do wydrukowania przez przypisywanie wartości do `m_nCurPage` członkiem `CPrintInfo`; Widok klas pobiera wartość i przeprowadza rzeczywiste drukowanie określonej strony.

Innym przykładem jest przypadek, w którym długość dokumentu nie jest znany do momentu, wydrukowaniu. W takiej sytuacji widok klasy testy do końca dokumentu każdorazowo, gdy strona zostanie wydrukowany. Po osiągnięciu końca Ustawia widok klasy `m_bContinuePrinting` członkiem `CPrintInfo` false; informuje platformę, by zatrzymać pętlę drukowania.

`CPrintInfo` jest używany przez funkcje elementów członkowskich `CView` wymienionych w sekcji "Zobacz też." Aby uzyskać więcej informacji na temat Architektura drukowania, dostarczone przez bibliotekę Microsoft Foundation Class zobacz [Windows ramki](../../mfc/frame-windows.md) i [architektury dokument/widok](../../mfc/document-view-architecture.md) artykuły [ Drukowanie](../../mfc/printing.md) i [drukowanie: dokumenty wielostronicowe](../../mfc/multipage-documents.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CPrintInfo`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="getfrompage"></a>  CPrintInfo::GetFromPage

Wywołaj tę funkcję, aby pobrać liczbę pierwszą stronę do wydrukowania.

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer pierwszej strony do wydrukowania.

### <a name="remarks"></a>Uwagi

Jest to wartość określoną przez użytkownika w oknie dialogowym drukowania i jest on przechowywany w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego. Jeśli użytkownik nie określił wartości, wartość domyślna to pierwszej strony dokumentu.

##  <a name="getmaxpage"></a>  CPrintInfo::GetMaxPage

Wywołaj tę funkcję, aby pobrać numer ostatniej strony dokumentu.

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer ostatniej strony dokumentu.

### <a name="remarks"></a>Uwagi

Ta wartość jest przechowywana w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego.

##  <a name="getminpage"></a>  CPrintInfo::GetMinPage

Wywołaj tę funkcję, aby pobrać numer pierwszej strony dokumentu.

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer pierwszej strony dokumentu.

### <a name="remarks"></a>Uwagi

Ta wartość jest przechowywana w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego.

##  <a name="getoffsetpage"></a>  CPrintInfo::GetOffsetPage

Wywołaj tę funkcję, aby pobrać przesunięcie podczas drukowania wielu elementów DocObject w kliencie DocObject.

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba stron poprzedzających na pierwszej stronie element DocObject drukowanego w połączonych obiektów DocObject zadanie drukowania.

### <a name="remarks"></a>Uwagi

Ta wartość jest przywoływany przez `m_nOffsetPage` elementu członkowskiego. Pierwsza strona dokumentu będą miały `m_nOffsetPage` wartość + 1 po wydrukowaniu jako obiekt DocObject przy użyciu innych dokumenty aktywne. `m_nOffsetPage` Elementu członkowskiego jest prawidłowa tylko wtedy, gdy `m_bDocObject` ma wartość TRUE.

##  <a name="gettopage"></a>  CPrintInfo::GetToPage

Wywołaj tę funkcję, aby pobrać numer ostatniej strony do wydrukowania.

```
UINT GetToPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer ostatniej strony do wydrukowania.

### <a name="remarks"></a>Uwagi

Jest to wartość określoną przez użytkownika w oknie dialogowym drukowania i jest on przechowywany w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego. Jeśli użytkownik nie określił wartości, wartość domyślna to ostatniej strony dokumentu.

##  <a name="m_bcontinueprinting"></a>  CPrintInfo::m_bContinuePrinting

Zawiera flagę wskazującą, czy w ramach powinno być kontynuowane drukowania pętli.

### <a name="remarks"></a>Uwagi

Jeśli przeprowadzasz wydruku w czasie dzielenia na strony można ustawić tego elementu członkowskiego na wartość FALSE w zastąpienie metody `CView::OnPrepareDC` po osiągnięto koniec dokumentu. Nie należy modyfikować tej zmiennej, jeśli podano długość dokumentu na początku używając zadania drukowania `SetMaxPage` funkcja elementu członkowskiego. `m_bContinuePrinting` Element członkowski jest publiczną zmienną typu wartość logiczna.

##  <a name="m_bdirect"></a>  CPrintInfo::m_bDirect

Struktura ustawia ten element członkowski na wartość TRUE, jeśli okno dialogowe Drukuj będą pomijane dla funkcji drukowania bezpośredniego; Wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Okno dialogowe drukowania zwykle jest pomijane podczas drukowania z powłoki lub gdy jest wykonywane drukowanie za pomocą polecenia ID_FILE_PRINT_DIRECT identyfikator.

Możesz normalnie nie zmieniaj tego elementu członkowskiego, ale, zmiana jego przed wywołanie [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) w zastąpienie metody [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

##  <a name="m_bdocobject"></a>  CPrintInfo::m_bDocObject

Zawiera flagę wskazującą, czy drukowany dokument jest obiekt DocObject.

### <a name="remarks"></a>Uwagi

Elementy członkowskie danych `m_dwFlags` i `m_nOffsetPage` są niepoprawne, chyba że ta flaga ma wartość TRUE.

##  <a name="m_bpreview"></a>  CPrintInfo::m_bPreview

Zawiera flagę wskazującą, czy dokument jest przeglądany.

### <a name="remarks"></a>Uwagi

Zostało to określone przez framework, w zależności od tego, które jest wykonywane polecenie użytkownika. Zadania Podgląd wydruku nie zostanie wyświetlone okno dialogowe drukowania. `m_bPreview` Element członkowski jest publiczną zmienną typu wartość logiczna.

##  <a name="m_dwflags"></a>  CPrintInfo::m_dwFlags

Zawiera kombinację flagi określające DocObject operacji drukowania.

### <a name="remarks"></a>Uwagi

Prawidłowe tylko wtedy, gdy element członkowski danych `m_bDocObject` ma wartość TRUE.

Flagi może być co najmniej jeden z następujących wartości:

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

##  <a name="m_lpuserdata"></a>  CPrintInfo::m_lpUserData

Zawiera wskaźnik do struktury utworzone przez użytkownika.

### <a name="remarks"></a>Uwagi

Służy to do przechowywania danych specyficznych dla drukowania, które nie chcesz przechowywać w klasie widoku. `m_lpUserData` Element członkowski jest publiczną zmienną typu LPVoid —.

##  <a name="m_ncurpage"></a>  CPrintInfo::m_nCurPage

Zawiera numer bieżącej strony.

### <a name="remarks"></a>Uwagi

Struktura wywołuje `CView::OnPrepareDC` i `CView::OnPrint` raz dla każdej strony dokumentu, określając inną wartość dla tego elementu członkowskiego za każdym razem; jej wartości w zakresie od wartości zwracanej przez `GetFromPage` , zwracany przez `GetToPage`. Użyj tego elementu członkowskiego w przesłonięć z `CView::OnPrepareDC` i `CView::OnPrint` do drukowania strony określonego dokumentu.

Podczas pierwszego wywołania tryb podglądu, struktura odczytuje wartość tego elementu członkowskiego, aby określić, które strony dokumentu należy można wyświetlić podglądu początkowo. Można ustawić wartość tego elementu członkowskiego w zastąpienie metody `CView::OnPreparePrinting` do zachowania użytkownika bieżącej pozycji w dokumencie, podczas wprowadzania tryb podglądu. `m_nCurPage` Element członkowski jest publiczną zmienną typu UINT.

##  <a name="m_njobnumber"></a>  CPrintInfo::m_nJobNumber

Określa liczbę zadań przypisaną przez system operacyjny dla bieżącego zadania drukowania.

### <a name="remarks"></a>Uwagi

Ta wartość może być SP_ERROR, jeśli zadanie nie zostało jeszcze zrealizowane (to znaczy, jeśli `CPrintInfo` jest nowo skonstruowany obiekt i nie został jeszcze użyty do drukowania), lub jeśli wystąpił błąd podczas uruchamiania zadania.

##  <a name="m_nnumpreviewpages"></a>  CPrintInfo::m_nNumPreviewPages

Zawiera liczbę stron wyświetlanych w wersji zapoznawczej; może być równy 1 albo 2.

### <a name="remarks"></a>Uwagi

`m_nNumPreviewPages` Element członkowski jest publiczną zmienną typu UINT.

##  <a name="m_noffsetpage"></a>  CPrintInfo::m_nOffsetPage

Zawiera liczbę stron poprzedzające pierwszej strony określonego DocObject połączone DocObject zadania drukowania.

##  <a name="m_ppd"></a>  CPrintInfo::m_pPD

Zawiera wskaźnik do `CPrintDialog` obiekt używany do wyświetlenia okna dialogowego drukowania dla zadania drukowania.

### <a name="remarks"></a>Uwagi

`m_pPD` Elementu członkowskiego jest publiczną zmienną zadeklarowane jako wskaźnik do `CPrintDialog`.

##  <a name="m_rectdraw"></a>  CPrintInfo::m_rectDraw

Określa rysowania powierzchnia użytkowa strony w logiczne współrzędnych.

### <a name="remarks"></a>Uwagi

Warto zapoznać się z tym w zastąpienie metody `CView::OnPrint`. Ten element członkowski służy do śledzenia jaki obszar jest nadal można używać po drukowaniu nagłówki, stopki i tak dalej. `m_rectDraw` Element członkowski jest publiczną zmienną typu `CRect`.

##  <a name="m_strpagedesc"></a>  CPrintInfo::m_strPageDesc

Zawiera ciąg formatu używany do wyświetlania numery stron w okresie zapoznawczym drukowania. Ten ciąg składa się z dwóch podciągów, jeden dla wyświetlania pojedynczej strony i jeden do wyświetlania strony podwójnej precyzji, każdy zakończony przez znak '\n'.

### <a name="remarks"></a>Uwagi

Środowisko wykorzystuje "Strony %u\nPages % u-%u\n" jako wartości domyślnej. Jeśli ma inny format numerów stron, należy określić ciąg formatu w zastąpienie metody `CView::OnPreparePrinting`. `m_strPageDesc` Element członkowski jest publiczną zmienną typu `CString`.

##  <a name="setmaxpage"></a>  CPrintInfo::SetMaxPage

Wywołaj tę funkcję, aby określić numer ostatniej strony dokumentu.

```
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>Parametry

*nMaxPage*<br/>
Numer ostatniej strony dokumentu.

### <a name="remarks"></a>Uwagi

Ta wartość jest przechowywana w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego. Jeśli długość dokumentu jest znany, przed wydrukowaniem, należy wywołać tę funkcję z zastąpienie metody `CView::OnPreparePrinting`. Jeśli długość dokumentu zależy od ustawienia określone przez użytkownika w oknie dialogowym drukowania, należy wywołać tę funkcję z zastąpienie metody `CView::OnBeginPrinting`. Jeśli długość dokumentu nie jest znany, przed wydrukowaniem, użyj `m_bContinuePrinting` elementu członkowskiego do sterowania pętlą drukowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

##  <a name="setminpage"></a>  CPrintInfo::SetMinPage

Wywołaj tę funkcję, aby określić numer pierwszej strony dokumentu.

```
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>Parametry

*nMinPage*<br/>
Numer pierwszej strony dokumentu.

### <a name="remarks"></a>Uwagi

Numery stron są zwykle liczone od 1. Ta wartość jest przechowywana w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Próbki MFC DIBLOOK](../../visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)

