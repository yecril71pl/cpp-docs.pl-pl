---
title: Klasa CDaoRecordView
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: 95ed9207d0047287e373401da52f05235a817999
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223138"
---
# <a name="cdaorecordview-class"></a>Klasa CDaoRecordView

Widok, w którym są wyświetlane rekordy bazy danych w kontrolkach.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordView:: CDaoRecordView](#cdaorecordview)|Konstruuje `CDaoRecordView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordView:: IsOnFirstRecord](#isonfirstrecord)|Zwraca wartość różną od zera, jeśli bieżący rekord jest pierwszym rekordem w skojarzonym zestawie rekordów.|
|[CDaoRecordView:: IsOnLastRecord](#isonlastrecord)|Zwraca wartość różną od zera, jeśli bieżący rekord jest ostatnim rekordem w skojarzonym zestawie rekordów.|
|[CDaoRecordView:: OnGetRecordset](#ongetrecordset)|Zwraca wskaźnik do obiektu klasy pochodzącej od `CDaoRecordset` . ClassWizard przesłania tę funkcję dla Ciebie i w razie potrzeby tworzy zestaw rekordów.|
|[CDaoRecordView:: OnMove](#onmove)|Jeśli bieżący rekord został zmieniony, program aktualizuje go w źródle danych, a następnie przechodzi do określonego rekordu (Następny, poprzedni, pierwszy lub ostatni).|

## <a name="remarks"></a>Uwagi

Widok to widok formularza połączony bezpośrednio z `CDaoRecordset` obiektem. Widok jest tworzony na podstawie zasobu szablonu okna dialogowego i wyświetla pola `CDaoRecordset` obiektu w kontrolkach szablonu okna dialogowego. `CDaoRecordView`Obiekt używa wymiany danych okna dialogowego (DDX) i wymiany pól rekordów DAO (DFX) w celu zautomatyzowania przenoszenia danych między kontrolkami w formularzu i polami zestawu rekordów. `CDaoRecordView`dostarcza również domyślną implementację do przechodzenia do pierwszego, następnego, poprzedniego lub ostatniego rekordu oraz interfejs do aktualizowania rekordu aktualnie w widoku.

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas baz danych MFC opartych na Open Database Connectivity (ODBC). Wszystkie nazwy klas baz danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC przy użyciu klas DAO; klasy DAO zazwyczaj oferują znakomite możliwości, ponieważ korzystają z aparatu bazy danych Microsoft Jet.

Najbardziej typowym sposobem tworzenia widoku rekordów jest Kreator aplikacji. Kreator aplikacji tworzy zarówno klasę widoku rekordu, jak i skojarzoną z nią klasę zestawu rekordów w ramach aplikacji szkieletowej.

Jeśli wystarczy tylko jeden formularz, podejście do Kreatora aplikacji jest łatwiejsze. ClassWizard umożliwia wybranie widoku rekordu w dalszej części procesu tworzenia. Jeśli nie utworzysz klasy widoku rekordu przy użyciu Kreatora aplikacji, można utworzyć ją później za pomocą ClassWizard. Użycie ClassWizard do utworzenia widoku rekordu i zestawu rekordów oddzielnie, a następnie połączenie ich jest najbardziej elastycznym podejściem, ponieważ daje większą kontrolę nad nazewnictwem klasy zestawu rekordów i jej. H/. Pliki CPP. Takie podejście umożliwia również posiadanie wielu widoków rekordów w tej samej klasie zestawu rekordów.

Aby ułatwić użytkownikom końcowym przejście z rekordu do rekordu w widoku rekordu, Kreator aplikacji tworzy zasoby menu (i opcjonalne paski narzędzi) przeznaczone do przechodzenia do pierwszego, następnego, poprzedniego lub ostatniego rekordu. W przypadku tworzenia klasy widoku rekordu z ClassWizard należy utworzyć te zasoby samodzielnie za pomocą menu i edytorów map bitowych.

Aby uzyskać informacje o domyślnej implementacji dotyczącej przechodzenia z rekordu do rekordu, zobacz `IsOnFirstRecord` i `IsOnLastRecord` i artykułu [przy użyciu widoku rekordu](../../data/using-a-record-view-mfc-data-access.md), który ma zastosowanie do obu `CRecordView` i `CDaoRecordView` .

`CDaoRecordView`śledzi położenie użytkownika w zestawie rekordów, aby widok rekordu mógł zaktualizować interfejs użytkownika. Gdy użytkownik przejdzie do dowolnego końca zestawu rekordów, widok rekordu wyłącza obiekty interfejsu użytkownika, takie jak elementy menu lub przyciski paska narzędzi — do przenoszenia dalej w tym samym kierunku.

Aby uzyskać więcej informacji na temat deklarowania i używania widoku rekordu oraz klas zestawu rekordów, zobacz "Projektowanie i Tworzenie widoku rekordów" w [widokach rekordów](../../data/record-views-mfc-data-access.md)artykułu. Aby uzyskać więcej informacji o działaniu widoków rekordów i sposobach ich użycia, zobacz artykuł [Korzystanie z widoku rekordu](../../data/using-a-record-view-mfc-data-access.md). Wszystkie artykuły wymienione powyżej dotyczą zarówno `CRecordView` , jak i `CDaoRecordView` .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDaoRecordView:: CDaoRecordView

Podczas tworzenia obiektu typu pochodnego `CDaoRecordView` Wywołaj każdą formę konstruktora w celu zainicjowania obiektu widoku i zidentyfikowania zasobu okna dialogowego, w którym jest oparty ten widok.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony znakiem null, który jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera numer IDENTYFIKACYJNy zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Możesz zidentyfikować zasób według nazwy (przekazać ciąg jako argument do konstruktora) lub według jego identyfikatora (przekazać jako argument liczbę całkowitą bez znaku). Zalecane jest użycie identyfikatora zasobu.

> [!NOTE]
> Klasa pochodna musi dostarczyć własnego konstruktora. W konstruktorze klasy pochodnej Wywołaj konstruktora `CDaoRecordView::CDaoRecordView` przy użyciu nazwy zasobu lub identyfikatora jako argumentu.

`CDaoRecordView::OnInitialUpdate`wywołania `CWnd::UpdateData` , które wywołuje `CWnd::DoDataExchange` . To początkowe wywołanie do `DoDataExchange` łączenia `CDaoRecordView` formantów (pośrednio) z `CDaoRecordset` elementami członkowskimi danych pola utworzonymi przez ClassWizard. Tych elementów członkowskich danych nie można używać przed wywołaniem `CFormView::OnInitialUpdate` funkcji składowej klasy bazowej.

> [!NOTE]
> Jeśli używasz ClassWizard, Kreator definiuje **`enum`** wartość `CDaoRecordView::IDD` w deklaracji klasy i używa jej na liście inicjalizacji składowej konstruktora.

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecordView:: IsOnFirstRecord

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy bieżący rekord jest pierwszym rekordem w obiekcie zestawu rekordów skojarzonym z tym widokiem rekordu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli bieżący rekord jest pierwszym rekordem w zestawie rekordów; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do pisania własnych implementacji domyślnych programów obsługi aktualizacji poleceń napisanych przez ClassWizard.

Jeśli użytkownik przejdzie do pierwszego rekordu, struktura wyłącza wszystkie obiekty interfejsu użytkownika (na przykład elementy menu lub przyciski paska narzędzi), które należy przenieść do pierwszego lub poprzedniego rekordu.

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecordView:: IsOnLastRecord

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy bieżący rekord jest ostatnim rekordem w obiekcie zestawu rekordów skojarzonym z tym widokiem rekordu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli bieżący rekord jest ostatnim rekordem w zestawie rekordów; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do pisania własnych implementacji domyślnych programów obsługi aktualizacji poleceń, które ClassWizard zapisu do obsługi interfejsu użytkownika w celu przechodzenia z rekordu do rekordu.

> [!CAUTION]
> Wynik tej funkcji jest niezawodny, z tą różnicą, że widok może nie być w stanie wykryć końca zestawu rekordów, dopóki użytkownik nie przeniósł go poza nią. Użytkownik może chcieć przekroczyć ostatni rekord, zanim widok rekordu będzie mógł stwierdzić, że musi wyłączyć wszystkie obiekty interfejsu użytkownika w celu przechodzenia do następnego lub ostatniego rekordu. Jeśli użytkownik przesunie poprzedni rekord, a następnie przeniesie zwrot do ostatniego rekordu (lub przed nim), widok rekordu może śledzić położenie użytkownika w zestawie rekordów i poprawnie wyłączyć obiekty interfejsu użytkownika.

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView:: OnGetRecordset

Zwraca wskaźnik do `CDaoRecordset` obiektu pochodnego skojarzonego z widokiem rekordu.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CDaoRecordset` obiektu pochodnego, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie wskaźnik o wartości null.

### <a name="remarks"></a>Uwagi

Należy zastąpić tę funkcję elementu członkowskiego, aby skonstruować lub uzyskać obiekt zestawu rekordów i zwrócić do niego wskaźnik. Jeśli zadeklarujesz klasę widoku rekordu przy użyciu ClassWizard, Kreator zapisze domyślne przesłonięcie. Domyślna implementacja ClassWizard zwraca wskaźnik zestawu rekordów, który jest przechowywany w widoku rekordu, jeśli taki istnieje. Jeśli nie, konstruuje obiekt zestawu rekordów typu określonego za pomocą ClassWizard i wywołuje jego `Open` funkcję członkowską, aby otworzyć tabelę lub uruchomić zapytanie, a następnie zwraca wskaźnik do obiektu.

Aby uzyskać więcej informacji i przykładów, zobacz widok [rekordu artykułu: Używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDaoRecordView:: OnMove

Wywołaj tę funkcję elementu członkowskiego, aby przejść do innego rekordu w zestawie rekordów i wyświetlić jego pola w kontrolkach widoku rekordu.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jedna z następujących wartości identyfikatora polecenia standardowego:

- ID_RECORD_FIRST przechodzenie do pierwszego rekordu w zestawie rekordów.

- ID_RECORD_LAST przejść do ostatniego rekordu w zestawie rekordów.

- ID_RECORD_NEXT przejść do następnego rekordu w zestawie rekordów.

- ID_RECORD_PREV przejść do poprzedniego rekordu w zestawie rekordów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przenoszenie zakończyło się pomyślnie; w przeciwnym razie wartość 0, jeśli żądanie przeniesienia zostało odrzucone.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje odpowiednią funkcję przenoszenia elementu członkowskiego `CDaoRecordset` obiektu skojarzonego z widokiem rekordu.

Domyślnie program `OnMove` aktualizuje bieżący rekord w źródle danych, jeśli użytkownik zmienił go w widoku rekordu.

Kreator aplikacji tworzy zasób menu z elementami menu pierwszy rekord, ostatni rekord, następny rekord i poprzedni rekord. Jeśli wybierzesz opcję Początkowy pasek narzędzi, Kreator aplikacji utworzy również pasek narzędzi z przyciskami odpowiadającymi tym poleceniem.

W przypadku przeniesienia ostatniego rekordu w zestawie rekordów widok rekordu będzie nadal wyświetlał ostatni rekord. W przypadku przeniesienia do tyłu pierwszego rekordu widok rekordu będzie nadal wyświetlał pierwszy rekord.

> [!CAUTION]
> Wywołanie `OnMove` zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Wywołaj odpowiednią funkcję procedury obsługi aktualizacji interfejsu użytkownika — `OnUpdateRecordFirst` ,, `OnUpdateRecordLast` `OnUpdateRecordNext` lub `OnUpdateRecordPrev` — przed odpowiednią operacją przenoszenia, aby określić, czy zestaw rekordów zawiera jakieś rekordy.

## <a name="see-also"></a>Zobacz także

[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
