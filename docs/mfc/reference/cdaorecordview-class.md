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
ms.openlocfilehash: b8c411dbd29316219759351f1f1633b6e57b92e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377145"
---
# <a name="cdaorecordview-class"></a>Klasa CDaoRecordView

Widok, który wyświetla rekordy bazy danych w formantach.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordView::CDaoRecordView](#cdaorecordview)|Konstruuje `CDaoRecordView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Zwraca wartość niezerowa, jeśli bieżący rekord jest pierwszym rekordem w skojarzonym z nim ustawie rekordowym.|
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|Zwraca wartość niezerowa, jeśli bieżący rekord jest ostatnim rekordem w skojarzonym z nim ustawie rekordowym.|
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Zwraca wskaźnik do obiektu klasy pochodnej `CDaoRecordset`. ClassWizard zastępuje tę funkcję dla Ciebie i tworzy plik recordset, jeśli to konieczne.|
|[CDaoRecordView::OnMove](#onmove)|Jeśli bieżący rekord uległ zmianie, aktualizuje go w źródle danych, a następnie przechodzi do określonego rekordu (następnego, poprzedniego, pierwszego lub ostatniego).|

## <a name="remarks"></a>Uwagi

Widok jest widokiem formularza bezpośrednio połączonym z obiektem. `CDaoRecordset` Widok jest tworzony na podstawie zasobu szablonu `CDaoRecordset` okna dialogowego i wyświetla pola obiektu w formantych szablonu okna dialogowego. Obiekt `CDaoRecordView` używa wymiany danych dialogowych (DDX) i wymiany pól rekordów DAO (DFX) do automatyzacji przepływu danych między formantami w formularzu a polami zbioru rekordów. `CDaoRecordView`dostarcza również domyślną implementację do przejścia do pierwszego, następnego, poprzedniego lub ostatniego rekordu oraz interfejs do aktualizowania aktualnie przeglądanego rekordu.

> [!NOTE]
> Klasy bazy danych DAO różnią się od klas bazy danych MFC na podstawie łączności otwartej bazy danych (ODBC). Wszystkie nazwy klas bazy danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC z klasami DAO; klasy DAO zazwyczaj oferują doskonałe możliwości, ponieważ używają aparatu bazy danych Microsoft Jet.

Najczęstszym sposobem utworzenia widoku rekordu jest Kreator aplikacji. Kreator aplikacji tworzy zarówno klasę widoku rekordów, jak i skojarzoną z nią klasę zestaw rekordów jako część aplikacji startowej szkieletu.

Jeśli potrzebujesz tylko jednego formularza, podejście Kreatora aplikacji jest łatwiejsze. ClassWizard pozwala zdecydować się na użycie widoku rekordu w dalszej części procesu tworzenia. Jeśli nie utworzysz klasy widoku rekordu za pomocą Kreatora aplikacji, możesz utworzyć ją później za pomocą ClassWizard. Korzystanie ClassWizard do tworzenia widoku rekordów i akwizycji oddzielnie, a następnie połączyć je jest najbardziej elastyczne podejście, ponieważ daje większą kontrolę w nazewnictwie klasy recordset i jego . H/. pliki CPP. Takie podejście umożliwia również wiele widoków rekordów w tej samej klasie zestaw rekordów.

Aby ułatwić użytkownikom końcowym przechodzenie z rekordu do rekordu w widoku rekordu, Kreator aplikacji tworzy zasoby menu (i opcjonalnie paska narzędzi) do przenoszenia do pierwszego, następnego, poprzedniego lub ostatniego rekordu. Jeśli tworzysz klasę widoku rekordów za pomocą ClassWizard, musisz samodzielnie utworzyć te zasoby za pomocą edytorów menu i bitmap.

Aby uzyskać informacje o domyślnej implementacji `IsOnFirstRecord` przechodzenia z rekordu do rekordu, `IsOnLastRecord` zobacz i `CDaoRecordView`artykuł Korzystanie z widoku [rekordu](../../data/using-a-record-view-mfc-data-access.md), który ma zastosowanie do obu `CRecordView` i .

`CDaoRecordView`śledzi pozycję użytkownika w zakuła rekord, aby widok rekordu mógł zaktualizować interfejs użytkownika. Gdy użytkownik przesunie się na dowolny koniec zestawu rekordów, widok rekordu wyłącza obiekty interfejsu użytkownika — takie jak elementy menu lub przyciski paska narzędzi — w celu dalszego przesuwania się w tym samym kierunku.

Aby uzyskać więcej informacji na temat deklarowania i używania klas widoku rekordów i tablicy rekordów, zobacz "Projektowanie i tworzenie widoku rekordu" w artykule [Widoki rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji o działaniu widoków rekordów i sposobie ich używania, zobacz artykuł [Korzystanie z widoku rekordu](../../data/using-a-record-view-mfc-data-access.md). Wszystkie artykuły wymienione powyżej mają `CRecordView` `CDaoRecordView`zastosowanie zarówno do .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[Cscrollview](../../mfc/reference/cscrollview-class.md)

[Cformview](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDaoRecordView::CDaoRecordView

Podczas tworzenia obiektu typu pochodnego `CDaoRecordView`z , wywołać albo formę konstruktora, aby zainicjować obiekt widoku i zidentyfikować zasób okna dialogowego, na którym jest oparty widok.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony z wartością null, który jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera numer identyfikatora zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Zasób można zidentyfikować według nazwy (przekazać ciąg jako argument do konstruktora) lub jego identyfikator (przekazać niepodpisaną kreślęń całkowitych jako argument). Zaleca się użycie identyfikatora zasobu.

> [!NOTE]
> Klasa pochodna musi dostarczyć własny konstruktor. W konstruktorze klasy pochodnej wywołać `CDaoRecordView::CDaoRecordView` konstruktora z nazwą zasobu lub identyfikator jako argument.

`CDaoRecordView::OnInitialUpdate`połączeń `CWnd::UpdateData`, `CWnd::DoDataExchange`który wywołuje . To początkowe `DoDataExchange` `CDaoRecordView` wywołanie łączy formanty (pośrednio) z `CDaoRecordset` elementami elementów członkowskich danych pola utworzonych przez ClassWizard. Te elementy członkowskie danych nie mogą być `CFormView::OnInitialUpdate` używane, dopóki po wywołaniu funkcji elementu członkowskiego klasy podstawowej.

> [!NOTE]
> Jeśli używasz ClassWizard, kreator definiuje wartość `CDaoRecordView::IDD` wyliczenia w deklaracji klasy i używa go na liście inicjowania elementu członkowskiego dla konstruktora. **enum**

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecordView::IsOnFirstRecord

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy bieżący rekord jest pierwszym rekordem w obiekcie pliku recordset skojarzonym z tym widokiem rekordu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli bieżący rekord jest pierwszym rekordem w rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do pisania własnych implementacji domyślnych programów obsługi aktualizacji poleceń napisanych przez ClassWizard.

Jeśli użytkownik przeniesie się do pierwszego rekordu, struktura wyłącza wszystkie obiekty interfejsu użytkownika (na przykład elementy menu lub przyciski paska narzędzi) do przejścia do pierwszego lub poprzedniego rekordu.

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecordView::IsOnLastRecord

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy bieżący rekord jest ostatnim rekordem w obiekcie recordet skojarzonym z tym widokiem rekordu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli bieżący rekord jest ostatnim rekordem w rekordzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna do pisania własnych implementacji domyślnych programów obsługi aktualizacji poleceń, które ClassWizard zapisuje do obsługi interfejsu użytkownika do przenoszenia z rekordu do rekordu.

> [!CAUTION]
> Wynik tej funkcji jest niezawodny, z tą różnicą, że widok może nie być w stanie wykryć końca zestawu rekordów, dopóki użytkownik nie przesunie się poza niego. Użytkownik może być konieczne przejście poza ostatni rekord, zanim widok rekordu może stwierdzić, że musi wyłączyć wszystkie obiekty interfejsu użytkownika do przejścia do następnego lub ostatniego rekordu. Jeśli użytkownik przejdzie obok ostatniego rekordu, a następnie powróci do ostatniego rekordu (lub przed nim), widok rekordu może śledzić pozycję użytkownika w zamówieniu i poprawnie wyłączyć obiekty interfejsu użytkownika.

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView::OnGetRecordset

Zwraca wskaźnik do `CDaoRecordset`obiektu pochodnego skojarzonego z widokiem rekordu.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CDaoRecordset`obiektu pochodnego, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie wskaźnik NULL.

### <a name="remarks"></a>Uwagi

Należy zastąpić tę funkcję elementu członkowskiego, aby skonstruować lub uzyskać obiekt aktu recordset i zwrócić do niego wskaźnik. Jeśli zadeklarujesz klasę widoku rekordu za pomocą ClassWizard, kreator zapisze domyślne zastąpienie dla Ciebie. Domyślna implementacja ClassWizard zwraca wskaźnik tablicy rekordów przechowywany w widoku rekordu, jeśli taki istnieje. Jeśli nie, konstruuje obiekt pliku recordset typu określonego za `Open` pomocą ClassWizard i wywołuje jego funkcję elementu członkowskiego, aby otworzyć tabelę lub uruchomić kwerendę, a następnie zwraca wskaźnik do obiektu.

Aby uzyskać więcej informacji i przykładów, zobacz artykuł [Widoki rekordów: Korzystanie z widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDaoRecordView::OnMove

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

Domyślna implementacja wywołuje odpowiednią funkcję `CDaoRecordset` Move member obiektu skojarzonego z widokiem rekordu.

Domyślnie `OnMove` aktualizuje bieżący rekord w źródle danych, jeśli użytkownik zmienił go w widoku rekordu.

Kreator aplikacji tworzy zasób menu z elementami menu Pierwszy rekord, Ostatni rekord, Następny rekord i Poprzedni rekord. Jeśli wybierzesz opcję Początkowy pasek narzędzi, Kreator aplikacji utworzy również pasek narzędzi z przyciskami odpowiadającymi tym poleceniom.

Jeśli przejdziesz obok ostatniego rekordu w tablicy rekordów, widok rekordu będzie nadal wyświetlał ostatni rekord. Jeśli przejdziesz do tyłu obok pierwszego rekordu, widok rekordu będzie nadal wyświetlał pierwszy rekord.

> [!CAUTION]
> Wywołanie `OnMove` zgłasza wyjątek, jeśli plik recordset nie ma rekordów. Wywołanie odpowiedniej funkcji obsługi `OnUpdateRecordFirst`aktualizacji `OnUpdateRecordLast` `OnUpdateRecordNext`interfejsu `OnUpdateRecordPrev` użytkownika — , , lub — przed odpowiednią operacją przenoszenia, aby ustalić, czy na maciewce rekordów są jakieś rekordy.

## <a name="see-also"></a>Zobacz też

[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
