---
title: Klasa CRecordView
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
ms.openlocfilehash: b706a80f91a3c952d80da13f453a807c775b9405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368353"
---
# <a name="crecordview-class"></a>Klasa CRecordView

Widok, który wyświetla rekordy bazy danych w formantach.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CRecordView::CRecordView](#crecordview)|Konstruuje `CRecordView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Zwraca wartość niezerowa, jeśli bieżący rekord jest pierwszym rekordem w skojarzonym z nim ustawie rekordowym.|
|[CRecordView::IsOnLastRecord](#isonlastrecord)|Zwraca wartość niezerowa, jeśli bieżący rekord jest ostatnim rekordem w skojarzonym z nim ustawie rekordowym.|
|[CRecordView::OnGetRecordset](#ongetrecordset)|Zwraca wskaźnik do obiektu klasy pochodnej `CRecordset`. ClassWizard zastępuje tę funkcję dla Ciebie i tworzy plik recordset, jeśli to konieczne.|
|[CRecordView::OnMove](#onmove)||

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CRecordView::OnMove](#onmove)|Jeśli bieżący rekord uległ zmianie, aktualizuje go w źródle danych, a następnie przechodzi do określonego rekordu (następnego, poprzedniego, pierwszego lub ostatniego).|

## <a name="remarks"></a>Uwagi

Widok jest widokiem formularza bezpośrednio połączonym z obiektem. `CRecordset` Widok jest tworzony na podstawie zasobu szablonu `CRecordset` okna dialogowego i wyświetla pola obiektu w formantych szablonu okna dialogowego. Obiekt `CRecordView` używa wymiany danych okna dialogowego (DDX) i wymiany pól rekordów (RFX) do automatyzacji przepływu danych między formantami w formularzu a polami zbioru rekordów. `CRecordView`dostarcza również domyślną implementację do przejścia do pierwszego, następnego, poprzedniego lub ostatniego rekordu oraz interfejs do aktualizowania rekordu aktualnie przeglądanego.

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie z klasami Open Database Connectivity (ODBC), należy użyć klasy [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) Aby uzyskać więcej informacji, zobacz artykuł [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

Najczęstszym sposobem utworzenia widoku rekordu jest Kreator aplikacji. Kreator aplikacji tworzy zarówno klasę widoku rekordów, jak i skojarzoną z nią klasę zestaw rekordów jako część aplikacji startowej szkieletu. Jeśli nie utworzysz klasy widoku rekordu za pomocą Kreatora aplikacji, możesz utworzyć ją później za pomocą ClassWizard. Jeśli potrzebujesz tylko jednego formularza, podejście Kreatora aplikacji jest łatwiejsze. ClassWizard pozwala zdecydować się na użycie widoku rekordu w dalszej części procesu tworzenia. Korzystanie ClassWizard do tworzenia widoku rekordów i akwizycji oddzielnie, a następnie połączyć je jest najbardziej elastyczne podejście, ponieważ daje większą kontrolę w nazewnictwie klasy recordset i jego . H/. pliki CPP. Takie podejście umożliwia również wiele widoków rekordów w tej samej klasie zestaw rekordów.

Aby ułatwić użytkownikom końcowym przechodzenie z rekordu do rekordu w widoku rekordu, Kreator aplikacji tworzy zasoby menu (i opcjonalnie paska narzędzi) do przenoszenia do pierwszego, następnego, poprzedniego lub ostatniego rekordu. Jeśli tworzysz klasę widoku rekordów za pomocą ClassWizard, musisz samodzielnie utworzyć te zasoby za pomocą edytorów menu i bitmap.

Aby uzyskać informacje o domyślnej implementacji `IsOnFirstRecord` przechodzenia z rekordu do rekordu, zobacz i `IsOnLastRecord` artykuł [Korzystanie z widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView`śledzi pozycję użytkownika w zakuła rekord, aby widok rekordu mógł zaktualizować interfejs użytkownika. Gdy użytkownik przesunie się na dowolny koniec zestawu rekordów, widok rekordu wyłącza obiekty interfejsu użytkownika — takie jak elementy menu lub przyciski paska narzędzi — w celu dalszego przesuwania się w tym samym kierunku.

Aby uzyskać więcej informacji na temat deklarowania i używania klas widoku rekordów i tablicy rekordów, zobacz "Projektowanie i tworzenie widoku rekordu" w artykule [Widoki rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji o działaniu widoków rekordów i sposobie ich używania, zobacz artykuł [Korzystanie z widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[Cscrollview](../../mfc/reference/cscrollview-class.md)

[Cformview](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>CRecordView::CRecordView

Podczas tworzenia obiektu typu pochodnego `CRecordView`z , wywołać albo formę konstruktora, aby zainicjować obiekt widoku i zidentyfikować zasób okna dialogowego, na którym jest oparty widok.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony z wartością null, który jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera numer identyfikatora zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Zasób można zidentyfikować według nazwy (przekazać ciąg jako argument do konstruktora) lub jego identyfikator (przekazać niepodpisaną kreślęń całkowitych jako argument). Zaleca się użycie identyfikatora zasobu.

> [!NOTE]
> Klasa pochodna *musi* dostarczyć własny konstruktor. W konstruktorze klasy pochodnej wywołać `CRecordView::CRecordView` konstruktora z nazwą zasobu lub identyfikator jako argument, jak pokazano w poniższym przykładzie.

`CRecordView::OnInitialUpdate`połączeń `UpdateData`, `DoDataExchange`który wywołuje . To początkowe `DoDataExchange` `CRecordView` wywołanie łączy formanty (pośrednio) z `CRecordset` elementami elementów członkowskich danych pola utworzonych przez ClassWizard. Te elementy członkowskie danych nie mogą być `CFormView::OnInitialUpdate` używane, dopóki po wywołaniu funkcji elementu członkowskiego klasy podstawowej.

> [!NOTE]
> Jeśli używasz ClassWizard, kreator definiuje wartość `CRecordView::IDD`wyliczenia, określa ją w deklaracji klasy i używa go na liście inicjowania elementu członkowskiego dla konstruktora. **enum**

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CRecordView::IsOnFirstRecord

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy bieżący rekord jest pierwszym rekordem w obiekcie pliku recordset skojarzonym z tym widokiem rekordu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli bieżący rekord jest pierwszym rekordem w rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do pisania własnych implementacji domyślnych programów obsługi aktualizacji poleceń napisanych przez ClassWizard.

Jeśli użytkownik przeniesie się do pierwszego rekordu, struktura wyłącza wszystkie obiekty interfejsu użytkownika, które masz do przejścia do pierwszego lub poprzedniego rekordu.

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CRecordView::IsOnLastRecord

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy bieżący rekord jest ostatnim rekordem w obiekcie recordet skojarzonym z tym widokiem rekordu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli bieżący rekord jest ostatnim rekordem w rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do pisania własnych implementacji domyślnych programów obsługi aktualizacji poleceń, które ClassWizard zapisuje do obsługi interfejsu użytkownika do przenoszenia z rekordu do rekordu.

> [!CAUTION]
> Wynik tej funkcji jest niezawodny, z tą różnicą, że widok nie może wykryć końca zestawu rekordów, dopóki użytkownik nie przesunie się obok niego. Użytkownik musi wyjść poza ostatni rekord, zanim widok rekordu może stwierdzić, że musi wyłączyć wszystkie obiekty interfejsu użytkownika, aby przenieść się do następnego lub ostatniego rekordu. Jeśli użytkownik przejdzie obok ostatniego rekordu, a następnie powróci do ostatniego rekordu (lub przed nim), widok rekordu może śledzić pozycję użytkownika w zamówieniu i poprawnie wyłączyć obiekty interfejsu użytkownika. `IsOnLastRecord`jest również zawodne po wywołaniu `OnRecordLast`funkcji implementacji, która obsługuje polecenie `CRecordset::MoveLast`ID_RECORD_LAST lub .

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>CRecordView::OnGetRecordset

Zwraca wskaźnik do `CRecordset`obiektu pochodnego skojarzonego z widokiem rekordu.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRecordset`obiektu pochodnego, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie wskaźnik NULL.

### <a name="remarks"></a>Uwagi

Należy zastąpić tę funkcję elementu członkowskiego, aby skonstruować lub uzyskać obiekt aktu recordset i zwrócić do niego wskaźnik. Jeśli zadeklarujesz klasę widoku rekordu za pomocą ClassWizard, kreator zapisze domyślne zastąpienie dla Ciebie. Domyślna implementacja ClassWizard zwraca wskaźnik tablicy rekordów przechowywany w widoku rekordu, jeśli taki istnieje. Jeśli nie, konstruuje obiekt pliku recordset typu określonego za `Open` pomocą ClassWizard i wywołuje jego funkcję elementu członkowskiego, aby otworzyć tabelę lub uruchomić kwerendę, a następnie zwraca wskaźnik do obiektu.

Aby uzyskać więcej informacji i przykładów, zobacz artykuł [Widoki rekordów: Korzystanie z widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

## <a name="crecordviewonmove"></a><a name="onmove"></a>CRecordView::OnMove

Wywołanie tej funkcji elementu członkowskiego, aby przejść do innego rekordu w tablicy rekordów i wyświetlić jego pola w formanty widoku rekordu.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jedna z następujących standardowych wartości identyfikatora polecenia:

- ID_RECORD_FIRST Przenieś do pierwszego rekordu w ach.

- ID_RECORD_LAST Przenieś do ostatniego rekordu w ach.

- ID_RECORD_NEXT Przenieś do następnego rekordu w ach.

- ID_RECORD_PREV Przenieś do poprzedniego rekordu w ach.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli ruch się powiódł; w przeciwnym razie 0, jeśli żądanie przeniesienia zostało odrzucone.

### <a name="remarks"></a>Uwagi

Domyślna implementacja `Move` wywołuje odpowiednią `CRecordset` funkcję elementu członkowskiego obiektu skojarzonego z widokiem rekordu.

Domyślnie `OnMove` aktualizuje bieżący rekord w źródle danych, jeśli użytkownik zmienił go w widoku rekordu.

Kreator aplikacji tworzy zasób menu z elementami menu Pierwszy rekord, Ostatni rekord, Następny rekord i Poprzedni rekord. Jeśli wybierzesz opcję Dockable Toolbar, Kreator aplikacji utworzy również pasek narzędzi z przyciskami odpowiadającymi tym poleceniom.

Jeśli przejdziesz obok ostatniego rekordu w tablicy rekordów, widok rekordu będzie nadal wyświetlał ostatni rekord. Jeśli przejdziesz do tyłu obok pierwszego rekordu, widok rekordu będzie nadal wyświetlał pierwszy rekord.

> [!CAUTION]
> Wywołanie `OnMove` zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Wywołanie odpowiedniej funkcji obsługi `OnUpdateRecordFirst`aktualizacji `OnUpdateRecordLast` `OnUpdateRecordNext`interfejsu `OnUpdateRecordPrev` użytkownika — , , lub — przed odpowiednią operacją przenoszenia, aby ustalić, czy na maciewce rekordów są jakieś rekordy.

## <a name="see-also"></a>Zobacz też

[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
