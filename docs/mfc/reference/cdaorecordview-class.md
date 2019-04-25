---
title: Cdaorecordview — klasa
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
ms.openlocfilehash: f63aa8ed17619a9eef36e36bcc9243a3b973889a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207197"
---
# <a name="cdaorecordview-class"></a>Cdaorecordview — klasa

Widok wyświetlający rekordy bazy danych w kontrolkach.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordView::CDaoRecordView](#cdaorecordview)|Konstruuje `CDaoRecordView` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Zwraca wartość różną od zera, jeżeli bieżący rekord jest pierwszego rekordu w zestawie rekordów skojarzonych.|
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|Zwraca wartość różną od zera, jeżeli bieżący rekord jest ostatni rekord w zestawie rekordów skojarzonych.|
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Zwraca wskaźnik do obiektu klasy pochodzącej od `CDaoRecordset`. ClassWizard powoduje zastąpienie tej funkcji i tworzy zestaw rekordów, jeśli to konieczne.|
|[CDaoRecordView::OnMove](#onmove)|Jeśli bieżący rekord został zmieniony, aktualizuje je w źródle danych, a następnie przechodzi do określonego rekordu (dalej, poprzedniego, pierwszego lub ostatniego).|

## <a name="remarks"></a>Uwagi

Widok jest podłączone bezpośrednio do widoku formularza `CDaoRecordset` obiektu. Widok jest tworzony z zasobu szablonu okna dialogowego i są wyświetlane pola `CDaoRecordset` obiektu w kontrolkach szablonu okna dialogowego. `CDaoRecordView` Obiekt używa wymiana danych okna dialogowego (DDX) i wymiana pól rekordów DAO (DXF) do automatyzowania przenoszenia danych między pól zestawu rekordów i formantów w formularzu. `CDaoRecordView` dostarcza również domyślna implementacja przechodzenia do pierwszego, dalej, poprzednie lub ostatni rekord a interfejsem aktualizowania rekordu aktualnie w widoku.

> [!NOTE]
>  Klasy bazy danych DAO różnią się od klas baz danych MFC, które są oparte na Open Database Connectivity (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC przy użyciu klas DAO; klasy DAO ogólnie oferują możliwości wyższego poziomu, ponieważ jest używany przez aparat bazy danych Microsoft Jet.

Najczęstszym sposobem tworzenia widoku rekordu jest za pomocą Kreatora aplikacji. Kreator aplikacji tworzy zarówno klas widoków rekordów, jak i jej klasa skojarzony zestaw rekordów w ramach początkowego szkielet aplikacji.

Jeśli po prostu potrzebujesz jednego formularza, podejście Kreatora aplikacji jest łatwiejsze. ClassWizard pozwala określić użyć widoku rekordu w dalszej części procesu rozwoju. Jeśli nie utworzysz klas widoków rekordów za pomocą Kreatora aplikacji, można utworzyć ją później za pomocą ClassWizard. Tworzenie widoku rekordu i zestawu rekordów osobno, a następnie połącz je za pomocą ClassWizard jest najbardziej elastycznym podejściem, ponieważ zapewnia większą kontrolę w nazwach klasy zestawu rekordów i jego. GODZ. /. Plikach CPP. Takie podejście umożliwia również mieć wiele widoków rekordów w tej samej klasy zestawu rekordów.

Aby ułatwić użytkownikom końcowym przenieść między rekordami w widoku rekordu, Kreator aplikacji tworzy menu (i opcjonalnie paska narzędzi) zasoby dotyczące przenoszenia do pierwszego, dalej, poprzednie lub ostatni rekord. Jeśli utworzysz klas widoków rekordów z ClassWizard, musisz utworzyć te zasoby samodzielnie za pomocą menu i mapy bitowej edytorów.

Aby uzyskać informacji o implementacji domyślnej przechodzenia między rekordami, zobacz `IsOnFirstRecord` i `IsOnLastRecord` oraz artykuł [używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md), co dotyczy zarówno `CRecordView` i `CDaoRecordView`.

`CDaoRecordView` przechowuje informacje o pozycji użytkownika w zestawie rekordów, tak, aby zaktualizować interfejs użytkownika widoku rekordu. Po użytkownik przenosi się do dowolnego końca zestawu rekordów, widoku rekordu wyłącza obiektów interfejsu użytkownika — np. w menu i przycisków paska narzędzi — przenoszenia w tym samym kierunku.

Aby uzyskać więcej informacji na temat deklarowania i korzystając z widoków rekordów i rekordów klas, zobacz "Projektowanie i tworzenie widoku rekordu" w artykule [widoków rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji na temat jak rekord widoków pracy i sposobu ich używania, zobacz artykuł [używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md). Wszystkie artykuły wymienione powyżej dotyczą zarówno `CRecordView` i `CDaoRecordView`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

##  <a name="cdaorecordview"></a>  CDaoRecordView::CDaoRecordView

Po utworzeniu obiektu typu pochodną `CDaoRecordView`, wywołanie dowolnej postaci konstruktora, aby zainicjować obiekt widoku i identyfikacji zasobu okna dialogowego, na którym bazuje widoku.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony znakiem null, nazwę zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Można albo określ zasób według nazwy (pass ciąg jako argument konstruktora) lub jej identyfikator (pass liczbą całkowitą bez znaku jako argument). Zasób identyfikator zaleca się użycie.

> [!NOTE]
>  Klasy pochodne, musisz podać swój własny konstruktora. W konstruktorze klasy pochodnej, wywołanie konstruktora `CDaoRecordView::CDaoRecordView` przy użyciu nazwy zasobu lub identyfikator jako argument.

`CDaoRecordView::OnInitialUpdate` wywołania `CWnd::UpdateData`, która wywołuje metodę `CWnd::DoDataExchange`. To wywołanie początkowej `DoDataExchange` łączy `CDaoRecordView` kontroluje (pośrednio) do `CDaoRecordset` pól składowych danych utworzonych przez ClassWizard. Te elementy członkowskie danych nie można używać do czasu, po wywołaniu metody klasy bazowej `CFormView::OnInitialUpdate` funkcja elementu członkowskiego.

> [!NOTE]
>  Jeśli używasz ClassWizard, Kreator definiuje **wyliczenia** wartość `CDaoRecordView::IDD` w deklaracji klasy i używa go podczas inicjowania elementu członkowskiego listy dla konstruktora.

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>  CDaoRecordView::IsOnFirstRecord

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy bieżący rekord jest pierwszy rekord w obiekcie rekordów skojarzonego z tym widokiem rekordu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeżeli bieżący rekord jest pierwszy rekord w zestawie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatne przy pisaniu własnych implementacji domyślnej napisane przez ClassWizard programy obsługi aktualizacji poleceń.

Jeśli użytkownik przenosi się do pierwszego rekordu, wyłącza framework żadnego interfejsu użytkownika obiektów (na przykład, elementy menu lub przycisków paska narzędzi) jest dotyczące przechodzenia na pierwszym lub poprzedniego rekordu.

##  <a name="isonlastrecord"></a>  CDaoRecordView::IsOnLastRecord

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy bieżący rekord jest ostatni rekord w obiekcie rekordów skojarzonego z tym widokiem rekordu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeżeli bieżący rekord jest ostatni rekord w zestawie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatne przy pisaniu własne implementacje domyślne programy obsługi aktualizacji poleceń, które ClassWizard zapisuje do obsługi interfejsu użytkownika w przypadku przenoszenia między rekordami.

> [!CAUTION]
>  Wynikiem tej funkcji jest niezawodne, z tą różnicą, że widoku może nie móc wykrywać koniec zestawu rekordów, dopóki użytkownik został przeniesiony poza jej. Użytkownik może być konieczne przed widoków rekordów można stwierdzić, czy należy wyłączyć w niej żadnych obiektów interfejsu użytkownika dla przejście do następnej lub ostatni rekord przenieść poza ostatnim rekordzie. Jeśli użytkownik przenosi ostatnie ostatni rekord, a następnie przechodzi do ostatniego rekordu (lub przed nią) widoku rekordu można śledzić położenie użytkownika w zestawie rekordów i Wyłącz poprawnie obiektów interfejsu użytkownika.

##  <a name="ongetrecordset"></a>  CDaoRecordView::OnGetRecordset

Zwraca wskaźnik do `CDaoRecordset`-pochodzi obiekt skojarzony z widokiem rekordów.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CDaoRecordset`-pochodnych obiektu, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie wskaźnika o wartości NULL.

### <a name="remarks"></a>Uwagi

Konieczne jest przesłonięcie tej funkcji elementu członkowskiego, konstruowania lub uzyskać obiekty zestawów rekordów i zwracają wskaźnik do niego. Deklarowanie klasy widoków rekordów z ClassWizard kreator zapisuje zastąpienia domyślnej dla Ciebie. Firmy ClassWizard Domyślna implementacja zwraca wskaźnik rekordów przechowywanych w widoku rekordu, jeśli taka istnieje. Jeśli nie, jego tworzy obiekt zestawu rekordów typu określono ClassWizard i wywołuje jego `Open` element członkowski funkcji Otwórz tabelę lub uruchom zapytanie, a następnie zwraca wskaźnik do obiektu.

Aby uzyskać więcej informacji i przykładów, zobacz artykuł [widoków rekordów: Używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>  CDaoRecordView::OnMove

Wywołaj tę funkcję elementu członkowskiego, aby przenieść do innego rekordu w zestawie rekordów i wyświetlić jej pola w kontrolkach widoku rekordu.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jeden z następujących wartości Identyfikatora standardowe polecenia:

- ID_RECORD_FIRST przenieść się do pierwszego rekordu w zestawie rekordów.

- ID_RECORD_LAST przenieść się do ostatniego rekordu w zestawie rekordów.

- ID_RECORD_NEXT przejście do następnego rekordu w zestawie rekordów.

- ID_RECORD_PREV przejście do poprzedniego rekordu w zestawie rekordów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli przeniesienie zostało wykonane prawidłowo; w przeciwnym razie 0, jeśli żądanie przeniesienia zostało odrzucone.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje odpowiednią funkcję elementu członkowskiego przenoszenia z `CDaoRecordset` obiekt skojarzony z widokiem rekordów.

Domyślnie `OnMove` aktualizacji bieżący rekord w źródle danych, jeśli użytkownik zmienił się ona w widoku rekordu.

Kreator aplikacji umożliwia utworzenie zasobu menu z elementami menu pierwszy rekord, ostatni rekord, następny rekord i poprzedni rekord. Jeśli wybierzesz opcję początkowej paska narzędzi, Kreator aplikacji tworzy także pasek narzędzi za pomocą przycisków odpowiadający tych poleceń.

Jeśli przenosisz poza ostatni rekord w zestawie, widoku rekordu to jest nadal wyświetlany ostatni rekord. Jeśli możesz przejść wstecz pierwszy rekord, widoku rekordu w dalszym ciągu wyświetlić pierwszy rekord.

> [!CAUTION]
>  Wywoływanie `OnMove` zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Wywołanie funkcji obsługi aktualizacji interfejsu użytkownika odpowiedni — `OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`, lub `OnUpdateRecordPrev` — przed odpowiednimi operacji, aby ustalić, czy zestaw rekordów zawiera wszystkie rekordy przeniesienia.

## <a name="see-also"></a>Zobacz także

[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)<br/>
[Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
