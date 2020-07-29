---
title: Klasa formularzy CRecordView
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: 21db03fde267a366d4dd1bf747880951e7546058
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219615"
---
# <a name="crecordview-class"></a>Klasa formularzy CRecordView

Widok, w którym są wyświetlane rekordy bazy danych w kontrolkach.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[Formularzy CRecordView:: formularzy CRecordView](#crecordview)|Konstruuje `CRecordView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Formularzy CRecordView:: IsOnFirstRecord](#isonfirstrecord)|Zwraca wartość różną od zera, jeśli bieżący rekord jest pierwszym rekordem w skojarzonym zestawie rekordów.|
|[Formularzy CRecordView:: IsOnLastRecord](#isonlastrecord)|Zwraca wartość różną od zera, jeśli bieżący rekord jest ostatnim rekordem w skojarzonym zestawie rekordów.|
|[Formularzy CRecordView:: OnGetRecordset](#ongetrecordset)|Zwraca wskaźnik do obiektu klasy pochodzącej od `CRecordset` . ClassWizard przesłania tę funkcję dla Ciebie i w razie potrzeby tworzy zestaw rekordów.|
|[Formularzy CRecordView:: OnMove](#onmove)||

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[Formularzy CRecordView:: OnMove](#onmove)|Jeśli bieżący rekord został zmieniony, program aktualizuje go w źródle danych, a następnie przechodzi do określonego rekordu (Następny, poprzedni, pierwszy lub ostatni).|

## <a name="remarks"></a>Uwagi

Widok to widok formularza połączony bezpośrednio z `CRecordset` obiektem. Widok jest tworzony na podstawie zasobu szablonu okna dialogowego i wyświetla pola `CRecordset` obiektu w kontrolkach szablonu okna dialogowego. `CRecordView`Obiekt używa wymiany danych okna dialogowego (DDX) i wymiany pól rekordów (RFX) w celu zautomatyzowania przenoszenia danych między kontrolkami w formularzu i polami zestawu rekordów. `CRecordView`dostarcza również domyślną implementację do przechodzenia do pierwszego, następnego, poprzedniego lub ostatniego rekordu oraz interfejs do aktualizowania rekordu aktualnie w widoku.

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie klasami Open Database Connectivity (ODBC), zamiast tego użyj klasy [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) . Aby uzyskać więcej informacji, zobacz [Omówienie artykułu: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

Najbardziej typowym sposobem tworzenia widoku rekordów jest Kreator aplikacji. Kreator aplikacji tworzy zarówno klasę widoku rekordu, jak i skojarzoną z nią klasę zestawu rekordów w ramach aplikacji szkieletowej. Jeśli nie utworzysz klasy widoku rekordu przy użyciu Kreatora aplikacji, można utworzyć ją później za pomocą ClassWizard. Jeśli wystarczy tylko jeden formularz, podejście do Kreatora aplikacji jest łatwiejsze. ClassWizard umożliwia wybranie widoku rekordu w dalszej części procesu tworzenia. Użycie ClassWizard do utworzenia widoku rekordu i zestawu rekordów oddzielnie, a następnie połączenie ich jest najbardziej elastycznym podejściem, ponieważ daje większą kontrolę nad nazewnictwem klasy zestawu rekordów i jej. H/. Pliki CPP. Takie podejście umożliwia również posiadanie wielu widoków rekordów w tej samej klasie zestawu rekordów.

Aby ułatwić użytkownikom końcowym przejście z rekordu do rekordu w widoku rekordu, Kreator aplikacji tworzy zasoby menu (i opcjonalne paski narzędzi) przeznaczone do przechodzenia do pierwszego, następnego, poprzedniego lub ostatniego rekordu. W przypadku tworzenia klasy widoku rekordu z ClassWizard należy utworzyć te zasoby samodzielnie za pomocą menu i edytorów map bitowych.

Aby uzyskać informacje na temat domyślnej implementacji przechodzenia z rekordu do rekordu, zobacz `IsOnFirstRecord` i `IsOnLastRecord` i artykułu [przy użyciu widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView`śledzi położenie użytkownika w zestawie rekordów, aby widok rekordu mógł zaktualizować interfejs użytkownika. Gdy użytkownik przejdzie do dowolnego końca zestawu rekordów, widok rekordu wyłącza obiekty interfejsu użytkownika, takie jak elementy menu lub przyciski paska narzędzi — do przenoszenia dalej w tym samym kierunku.

Aby uzyskać więcej informacji na temat deklarowania i używania widoku rekordu oraz klas zestawu rekordów, zobacz "Projektowanie i Tworzenie widoku rekordów" w [widokach rekordów](../../data/record-views-mfc-data-access.md)artykułu. Aby uzyskać więcej informacji o działaniu widoków rekordów i sposobach ich użycia, zobacz artykuł [Korzystanie z widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>Formularzy CRecordView:: formularzy CRecordView

Podczas tworzenia obiektu typu pochodnego `CRecordView` Wywołaj każdą formę konstruktora w celu zainicjowania obiektu widoku i zidentyfikowania zasobu okna dialogowego, w którym jest oparty ten widok.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony znakiem null, który jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera numer IDENTYFIKACYJNy zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Możesz zidentyfikować zasób według nazwy (przekazać ciąg jako argument do konstruktora) lub według jego identyfikatora (przekazać jako argument liczbę całkowitą bez znaku). Zalecane jest użycie identyfikatora zasobu.

> [!NOTE]
> Klasa pochodna *musi* dostarczyć własnego konstruktora. W konstruktorze klasy pochodnej Wywołaj konstruktora `CRecordView::CRecordView` przy użyciu nazwy zasobu lub identyfikatora jako argumentu, jak pokazano w poniższym przykładzie.

`CRecordView::OnInitialUpdate`wywołania `UpdateData` , które wywołuje `DoDataExchange` . To początkowe wywołanie do `DoDataExchange` łączenia `CRecordView` formantów (pośrednio) z `CRecordset` elementami członkowskimi danych pola utworzonymi przez ClassWizard. Tych elementów członkowskich danych nie można używać przed wywołaniem `CFormView::OnInitialUpdate` funkcji składowej klasy bazowej.

> [!NOTE]
> Jeśli używasz ClassWizard, Kreator definiuje **`enum`** wartość `CRecordView::IDD` , określa ją w deklaracji klasy i używa jej na liście inicjalizacji elementu członkowskiego konstruktora.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>Formularzy CRecordView:: IsOnFirstRecord

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy bieżący rekord jest pierwszym rekordem w obiekcie zestawu rekordów skojarzonym z tym widokiem rekordu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli bieżący rekord jest pierwszym rekordem w zestawie rekordów; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do pisania własnych implementacji domyślnych programów obsługi aktualizacji poleceń napisanych przez ClassWizard.

Jeśli użytkownik przejdzie do pierwszego rekordu, struktura wyłącza wszystkie obiekty interfejsu użytkownika, które mają zostać przeniesione do pierwszego lub poprzedniego rekordu.

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>Formularzy CRecordView:: IsOnLastRecord

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy bieżący rekord jest ostatnim rekordem w obiekcie zestawu rekordów skojarzonym z tym widokiem rekordu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli bieżący rekord jest ostatnim rekordem w zestawie rekordów; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do pisania własnych implementacji domyślnych programów obsługi aktualizacji poleceń, które ClassWizard zapisu do obsługi interfejsu użytkownika w celu przechodzenia z rekordu do rekordu.

> [!CAUTION]
> Wynik tej funkcji jest niezawodny, z tą różnicą, że widok nie może wykryć końca zestawu rekordów, dopóki użytkownik nie przeniósł go poza nią. Użytkownik musi przejść poza ostatni rekord, zanim widok rekordu będzie mógł stwierdzić, że musi wyłączyć wszystkie obiekty interfejsu użytkownika w celu przejścia do następnego lub ostatniego rekordu. Jeśli użytkownik przesunie poprzedni rekord, a następnie przeniesie zwrot do ostatniego rekordu (lub przed nim), widok rekordu może śledzić położenie użytkownika w zestawie rekordów i poprawnie wyłączyć obiekty interfejsu użytkownika. `IsOnLastRecord`jest również niezawodna po wywołaniu funkcji implementacji `OnRecordLast` , która obsługuje polecenie ID_RECORD_LAST lub `CRecordset::MoveLast` .

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>Formularzy CRecordView:: OnGetRecordset

Zwraca wskaźnik do `CRecordset` obiektu pochodnego skojarzonego z widokiem rekordu.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRecordset` obiektu pochodnego, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie wskaźnik o wartości null.

### <a name="remarks"></a>Uwagi

Należy zastąpić tę funkcję elementu członkowskiego, aby skonstruować lub uzyskać obiekt zestawu rekordów i zwrócić do niego wskaźnik. Jeśli zadeklarujesz klasę widoku rekordu przy użyciu ClassWizard, Kreator zapisze domyślne przesłonięcie. Domyślna implementacja ClassWizard zwraca wskaźnik zestawu rekordów, który jest przechowywany w widoku rekordu, jeśli taki istnieje. Jeśli nie, konstruuje obiekt zestawu rekordów typu określonego za pomocą ClassWizard i wywołuje jego `Open` funkcję członkowską, aby otworzyć tabelę lub uruchomić zapytanie, a następnie zwraca wskaźnik do obiektu.

Aby uzyskać więcej informacji i przykładów, zobacz widok [rekordu artykułu: Używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

## <a name="crecordviewonmove"></a><a name="onmove"></a>Formularzy CRecordView:: OnMove

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

Domyślna implementacja wywołuje odpowiednią `Move` funkcję elementu członkowskiego `CRecordset` obiektu skojarzonego z widokiem rekordu.

Domyślnie program `OnMove` aktualizuje bieżący rekord w źródle danych, jeśli użytkownik zmienił go w widoku rekordu.

Kreator aplikacji tworzy zasób menu z elementami menu pierwszy rekord, ostatni rekord, następny rekord i poprzedni rekord. W przypadku wybrania opcji paska narzędzi było dokować Kreator aplikacji utworzy również pasek narzędzi z przyciskami odpowiadającymi tym poleceniem.

W przypadku przeniesienia ostatniego rekordu w zestawie rekordów widok rekordu będzie nadal wyświetlał ostatni rekord. W przypadku przeniesienia do tyłu pierwszego rekordu widok rekordu będzie nadal wyświetlał pierwszy rekord.

> [!CAUTION]
> Wywołanie `OnMove` zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Wywołaj odpowiednią funkcję procedury obsługi aktualizacji interfejsu użytkownika — `OnUpdateRecordFirst` ,, `OnUpdateRecordLast` `OnUpdateRecordNext` lub `OnUpdateRecordPrev` — przed odpowiednią operacją przenoszenia, aby określić, czy zestaw rekordów zawiera jakieś rekordy.

## <a name="see-also"></a>Zobacz także

[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
