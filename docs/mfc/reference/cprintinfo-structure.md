---
title: Klasa CPrintInfo
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 3b081b0728514c0fca2eb31462e1bcd9e91a47aa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753013"
---
# <a name="cprintinfo-structure"></a>Klasa CPrintInfo

Przechowuje informacje o zadaniu drukowania lub podglądu wydruku.

## <a name="syntax"></a>Składnia

```
struct CPrintInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPrintInfo::GetFromPage](#getfrompage)|Zwraca numer drukowanej pierwszej strony.|
|[CPrintInfo::GetMaxPage](#getmaxpage)|Zwraca numer ostatniej strony dokumentu.|
|[CPrintInfo::GetMinPage](#getminpage)|Zwraca numer pierwszej strony dokumentu.|
|[CPrintInfo::Strona GetOffset](#getoffsetpage)|Zwraca liczbę stron poprzedzających pierwszą stronę elementu DocObject drukowanego w połączonym zadaniu drukowania DocObject.|
|[CPrintInfo::GetToPage](#gettopage)|Zwraca numer ostatniej drukowanej strony.|
|[CPrintInfo::SetMaxPage](#setmaxpage)|Ustawia numer ostatniej strony dokumentu.|
|[CPrintInfo::SetMinPage](#setminpage)|Ustawia numer pierwszej strony dokumentu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Zawiera flagę wskazującą, czy framework powinien kontynuować pętlę drukowania.|
|[CPrintInfo::m_bDirect](#m_bdirect)|Zawiera flagę wskazującą, czy dokument jest drukowany bezpośrednio (bez wyświetlania okna dialogowego Drukowanie).|
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Zawiera flagę wskazującą, czy drukowany dokument jest docObject.|
|[CPrintInfo::m_bPreview](#m_bpreview)|Zawiera flagę wskazującą, czy dokument jest wyświetlany w podglądzie.|
|[CPrintInfo::m_dwFlags](#m_dwflags)|Określa operacje drukowania DocObject.|
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Zawiera wskaźnik do struktury utworzonej przez użytkownika.|
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Określa numer aktualnie drukowanej strony.|
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Określa numer zadania przypisany przez system operacyjny dla bieżącego zadania drukowania|
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Określa liczbę stron wyświetlanych w oknie podglądu; 1 lub 2.|
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Określa przesunięcie pierwszej strony określonego docObject w połączonym zadaniu drukowania DocObject.|
|[CPrintInfo::m_pPD](#m_ppd)|Zawiera wskaźnik do `CPrintDialog` obiektu używanego w oknie dialogowym Drukowanie.|
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Określa prostokąt definiujący bieżący obszar strony, w którym można konfigurować.|
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Zawiera ciąg formatu dla wyświetlania numeru strony.|

## <a name="remarks"></a>Uwagi

`CPrintInfo`jest strukturą i nie ma klasy podstawowej.

Struktura tworzy obiekt `CPrintInfo` za każdym razem, gdy wybrano polecenie Drukuj lub Podgląd wydruku, i niszczy go po zakończeniu polecenia.

`CPrintInfo`zawiera informacje zarówno o zadaniu drukowania jako całości, takie jak zakres stron do wydrukowania, a bieżący stan zadania drukowania, na przykład aktualnie drukowana strona. Niektóre informacje są przechowywane w skojarzonym [obiekcie CPrintDialog;](../../mfc/reference/cprintdialog-class.md) ten obiekt zawiera wartości wprowadzone przez użytkownika w oknie dialogowym Drukowanie.

Obiekt `CPrintInfo` jest przekazywany między klasą widoku i jest używany do wymiany informacji między nimi. Na przykład struktura informuje klasę widoku, która strona dokumentu do wydrukowania, `m_nCurPage` przypisując wartość do elementu `CPrintInfo`członkowskiego ; klasa widoku pobiera wartość i wykonuje rzeczywiste drukowanie określonej strony.

Innym przykładem jest przypadek, w którym długość dokumentu nie jest znana, dopóki nie zostanie wydrukowany. W tej sytuacji testuje klasę widoku dla końca dokumentu za każdym razem, gdy strona jest drukowana. Po osiągnięciu końca, klasa widoku `m_bContinuePrinting` ustawia `CPrintInfo` element członkowski na FAŁSZ; informuje o platformie, aby zatrzymać pętlę drukowania.

`CPrintInfo`jest używany przez funkcje członkowskie `CView` wymienione w obszarze "Zobacz też". Aby uzyskać więcej informacji na temat architektury drukowania dostarczonej przez bibliotekę klas Programu Microsoft Foundation, zobacz [Frame Windows](../../mfc/frame-windows.md) i [Architektura dokumentu/widoku](../../mfc/document-view-architecture.md) oraz artykuły [Drukowanie](../../mfc/printing.md) i [drukowanie: Dokumenty wielostronicowe](../../mfc/multipage-documents.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CPrintInfo`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo::GetFromPage

Wywołanie tej funkcji, aby pobrać numer pierwszej strony do wydrukowania.

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer pierwszej strony do wydrukowania.

### <a name="remarks"></a>Uwagi

Jest to wartość określona przez użytkownika w oknie dialogowym `CPrintDialog` Drukowanie i `m_pPD` jest przechowywana w obiekcie, do którego odwołuje się element członkowski. Jeśli użytkownik nie określił wartości, wartością domyślną jest pierwsza strona dokumentu.

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo::GetMaxPage

Wywołanie tej funkcji, aby pobrać numer ostatniej strony dokumentu.

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer ostatniej strony dokumentu.

### <a name="remarks"></a>Uwagi

Ta wartość jest `CPrintDialog` przechowywana w `m_pPD` obiekcie, do którego odwołuje się element członkowski.

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo::GetMinPage

Wywołanie tej funkcji, aby pobrać numer pierwszej strony dokumentu.

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer pierwszej strony dokumentu.

### <a name="remarks"></a>Uwagi

Ta wartość jest `CPrintDialog` przechowywana w `m_pPD` obiekcie, do którego odwołuje się element członkowski.

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo::Strona GetOffset

Wywołanie tej funkcji, aby pobrać przesunięcie podczas drukowania wielu elementów DocObject z klienta DocObject.

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba stron poprzedzających pierwszą stronę elementu DocObject drukowanego w połączonym zadaniu drukowania DocObject.

### <a name="remarks"></a>Uwagi

Ta wartość jest odwoływana przez element członkowski. `m_nOffsetPage` Pierwsza strona dokumentu zostanie ponumerowana `m_nOffsetPage` jako wartość + 1 po wydrukowaniu jako DocObject z innymi aktywnymi dokumentami. Element `m_nOffsetPage` członkowski jest `m_bDocObject` prawidłowy tylko wtedy, gdy wartość ma wartość PRAWDA.

## <a name="cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo::GetToPage

Wywołanie tej funkcji, aby pobrać numer ostatniej strony do wydrukowania.

```
UINT GetToPage() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer ostatniej strony do wydrukowania.

### <a name="remarks"></a>Uwagi

Jest to wartość określona przez użytkownika w oknie dialogowym `CPrintDialog` Drukowanie i `m_pPD` jest przechowywana w obiekcie, do którego odwołuje się element członkowski. Jeśli użytkownik nie określił wartości, wartością domyślną jest ostatnia strona dokumentu.

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting

Zawiera flagę wskazującą, czy framework powinien kontynuować pętlę drukowania.

### <a name="remarks"></a>Uwagi

Jeśli robisz podział na strony w czasie drukowania, można ustawić ten `CView::OnPrepareDC` element członkowski na FALSE w zastąpieniu po osiągnięciu końca dokumentu. Nie trzeba modyfikować tej zmiennej, jeśli określono długość dokumentu na początku zadania `SetMaxPage` drukowania przy użyciu funkcji elementu członkowskiego. Element `m_bContinuePrinting` członkowski jest zmienną publiczną typu BOOL.

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a>CPrintInfo::m_bDirect

Struktura ustawia tego elementu członkowskiego na WARTOŚĆ TRUE, jeśli okno dialogowe Drukowanie zostanie pominięte w przypadku drukowania bezpośredniego; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Okno dialogowe Drukuj jest zwykle pomijane podczas drukowania z powłoki lub podczas drukowania przy użyciu ID_FILE_PRINT_DIRECT identyfikatora polecenia.

Zwykle nie zmieniasz tego elementu członkowskiego, ale jeśli go zmienisz, zmień go przed wywołaniem [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) w nadpisaniu [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a>CPrintInfo::m_bDocObject

Zawiera flagę wskazującą, czy drukowany dokument jest docObject.

### <a name="remarks"></a>Uwagi

Elementy `m_dwFlags` członkowskie `m_nOffsetPage` danych i są nieprawidłowe, chyba że ta flaga ma wartość PRAWDA.

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a>CPrintInfo::m_bPreview

Zawiera flagę wskazującą, czy dokument jest wyświetlany w podglądzie.

### <a name="remarks"></a>Uwagi

Jest to ustawiane przez strukturę w zależności od tego, które polecenie użytkownik wykonał. Okno dialogowe Drukowanie nie jest wyświetlane dla zadania podglądu wydruku. Element `m_bPreview` członkowski jest zmienną publiczną typu BOOL.

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a>CPrintInfo::m_dwFlags

Zawiera kombinację flag określających operacje drukowania DocObject.

### <a name="remarks"></a>Uwagi

Prawidłowy tylko `m_bDocObject` wtedy, gdy element członkowski danych ma wartość PRAWDA.

Flagi mogą być jedną lub kilkoma z następujących wartości:

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData

Zawiera wskaźnik do struktury utworzonej przez użytkownika.

### <a name="remarks"></a>Uwagi

Służy do przechowywania danych specyficznych dla drukowania, które nie mają być przechowywane w klasie widoku. Element `m_lpUserData` członkowski jest zmienną publiczną typu LPVOID.

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a>CPrintInfo::m_nCurPage

Zawiera numer bieżącej strony.

### <a name="remarks"></a>Uwagi

Framework wywołuje `CView::OnPrepareDC` `CView::OnPrint` i raz dla każdej strony dokumentu, określając inną wartość dla tego elementu członkowskiego za każdym razem; jego wartości wahają się `GetFromPage` od wartości `GetToPage`zwróconej przez wartość zwróconą przez . Użyj tego elementu członkowskiego w `CView::OnPrepareDC` `CView::OnPrint` zastąpieniach i wydrukować określoną stronę dokumentu.

Gdy tryb podglądu jest wywoływany po raz pierwszy, struktura odczytuje wartość tego elementu członkowskiego, aby określić, która strona dokumentu powinna być początkowo wyświetlona podglądem. Można ustawić wartość tego elementu członkowskiego w `CView::OnPreparePrinting` zastąpieniu, aby zachować bieżącą pozycję użytkownika w dokumencie podczas wchodzenia w tryb podglądu. Element `m_nCurPage` członkowski jest zmienną publiczną typu UINT.

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber

Wskazuje numer zadania przypisany przez system operacyjny dla bieżącego zadania drukowania.

### <a name="remarks"></a>Uwagi

Ta wartość może być SP_ERROR, jeśli zadanie nie zostało jeszcze wydrukowane `CPrintInfo` (oznacza to, że obiekt jest nowo skonstruowany i nie został jeszcze użyty do wydrukowania) lub jeśli wystąpił błąd podczas uruchamiania zadania.

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages

Zawiera liczbę stron wyświetlanych w trybie podglądu; może to być 1 lub 2.

### <a name="remarks"></a>Uwagi

Element `m_nNumPreviewPages` członkowski jest zmienną publiczną typu UINT.

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage

Zawiera liczbę stron poprzedzających pierwszą stronę określonego docObject w połączonym zadaniu drukowania DocObject.

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a>CPrintInfo::m_pPD

Zawiera wskaźnik do `CPrintDialog` obiektu używanego do wyświetlania okna dialogowego Drukowanie zadania drukowania.

### <a name="remarks"></a>Uwagi

Element `m_pPD` członkowski jest zmienną publiczną zadeklarowaną jako wskaźnik do `CPrintDialog`.

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a>CPrintInfo::m_rectDraw

Określa użyteczny obszar rysunku strony we współrzędnych logicznych.

### <a name="remarks"></a>Uwagi

Możesz odnieść się do tego w zastąpione . `CView::OnPrint` Za pomocą tego elementu członkowskiego można śledzić, który obszar pozostaje użyteczny po wydrukowaniu nagłówków, stopek itd. Element `m_rectDraw` członkowski jest zmienną publiczną typu `CRect`.

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc

Zawiera ciąg formatu używany do wyświetlania numerów stron podczas podglądu wydruku; ten ciąg składa się z dwóch podciągów, jednego do wyświetlania jednostronicowego i jednego do wyświetlania dwustronicowego, z których każdy jest zakończony znakiem '\n'.

### <a name="remarks"></a>Uwagi

Jako wartość domyślną używa "Page %u\nPages %u-%u\n". Jeśli chcesz mieć inny format numerów stron, określ ciąg formatu w zastąpieniu pliku `CView::OnPreparePrinting`. Element `m_strPageDesc` członkowski jest zmienną publiczną typu `CString`.

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo::SetMaxPage

Wywołanie tej funkcji, aby określić numer ostatniej strony dokumentu.

```cpp
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>Parametry

*strona nMaxPage*<br/>
Numer ostatniej strony dokumentu.

### <a name="remarks"></a>Uwagi

Ta wartość jest `CPrintDialog` przechowywana w `m_pPD` obiekcie, do którego odwołuje się element członkowski. Jeśli długość dokumentu jest znana przed wydrukowaniem, należy wywołać tę `CView::OnPreparePrinting`funkcję z zastąpienia . Jeśli długość dokumentu zależy od ustawienia określonego przez użytkownika w oknie dialogowym Drukowanie, `CView::OnBeginPrinting`należy wywołać tę funkcję z zastąpienia . Jeśli długość dokumentu nie jest znana, dopóki nie `m_bContinuePrinting` zostanie wydrukowany, użyj elementu członkowskiego, aby sterować pętlą drukowania.

### <a name="example"></a>Przykład

  Zobacz przykład [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo::SetMinPage

Wywołanie tej funkcji, aby określić numer pierwszej strony dokumentu.

```cpp
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>Parametry

*strona nMinPage*<br/>
Numer pierwszej strony dokumentu.

### <a name="remarks"></a>Uwagi

Numery stron zwykle zaczynają się od 1. Ta wartość jest `CPrintDialog` przechowywana w `m_pPD` obiekcie, do którego odwołuje się element członkowski.

## <a name="see-also"></a>Zobacz też

[Przykładowy DIBLOOK MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)
