---
title: Coledbrecordview — klasa
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: 1b09599479010f87e396e6f576c9524651923f9f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280380"
---
# <a name="coledbrecordview-class"></a>Coledbrecordview — klasa

Widok wyświetlający rekordy bazy danych w kontrolkach.

## <a name="syntax"></a>Składnia

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Konstruuje `COleDBRecordView` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Zwraca wartość HRESULT standardową.|
|[COleDBRecordView::OnMove](#onmove)|(Jeśli jest zanieczyszczony) aktualizacji bieżący rekord w źródle danych, a następnie przechodzi do określonego rekordu (dalej, poprzedniego, pierwszego lub ostatniego).|

## <a name="remarks"></a>Uwagi

Widok jest podłączone bezpośrednio do widoku formularza `CRowset` obiektu. Widok jest tworzony z zasobu szablonu okna dialogowego i są wyświetlane pola `CRowset` obiektu w kontrolkach szablonu okna dialogowego. `COleDBRecordView` Obiekt używa wymiana danych okna dialogowego (DDX) i wyposażone w funkcję nawigacji `CRowset`, aby zautomatyzować przepływ danych między pól zestawu wierszy i formantów w formularzu. `COleDBRecordView` dostarcza również domyślna implementacja przechodzenia do pierwszego, dalej, poprzednie lub ostatni rekord a interfejsem aktualizowania rekordu aktualnie w widoku.

Można użyć funkcji DDX z `COleDbRecordView` pobieranie danych bezpośrednio z rekordów bazy danych i wyświetlania ich w formantu w oknie dialogowym. Należy używać `DDX_*` metody (takie jak `DDX_Text`), a nie `DDX_Field*` funkcji (takich jak `DDX_FieldText`) przy użyciu `COleDbRecordView`. `DDX_FieldText` nie będzie działać z `COleDbRecordView` ponieważ `DDX_FieldText` ma dodatkowy argument typu `CRecordset*` (dla `CRecordView`) lub `CDaoRecordset*` (dla `CDaoRecordView`).

> [!NOTE]
>  Jeśli pracujesz z klas obiektów dostępu do danych (DAO), a nie klasy OLE DB szablon konsumenta, użyj klasy [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: Baza danych programowania](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView` przechowuje informacje o jego pozycja w zestawie wierszy tak, aby zaktualizować interfejs użytkownika widoku rekordu. Po użytkownik przenosi się do dowolnego końca zestawu wierszy, widoku rekordu wyłącza obiektów interfejsu użytkownika — np. w menu i przycisków paska narzędzi — przenoszenia w tym samym kierunku.

Aby uzyskać więcej informacji na temat klasy zestawów wierszy, zobacz [przy użyciu szablony OLE DB konsumenta](../../data/oledb/ole-db-consumer-templates-cpp.md) artykułu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxoledb.h

##  <a name="coledbrecordview"></a>  COleDBRecordView::COleDBRecordView

Konstruuje `COleDBRecordView` obiektu.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony zerem, która jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera identyfikator zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu typu pochodną `COleDBRecordView`, wywołać za pomocą jednego z konstruktorów do utworzenia obiektu widoku i identyfikacji zasobu okna dialogowego, na którym bazuje widoku. Zasób można zidentyfikować przez nazwę (pass ciąg jako argument konstruktora) lub za pomocą jego Identyfikatora (pass liczbą całkowitą bez znaku jako argument).

> [!NOTE]
>  Klasy pochodne *musi* podać swój własny konstruktora. W konstruktorze, należy wywołać konstruktora, `COleDBRecordView::COleDBRecordView`, przy użyciu nazwy zasobu lub identyfikator jako argument.

##  <a name="ongetrowset"></a>  COleDBRecordView::OnGetRowset

Zwraca uchwyt do **CRowset <>** obiekt skojarzony z widokiem rekordów.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Konieczne jest przesłonięcie tej funkcji elementu członkowskiego, konstruowania lub uzyskać obiektu zestawu wierszy i zwraca uchwyt do niego. Deklarowanie klasy widoków rekordów z ClassWizard kreator zapisuje zastąpienia domyślnej dla Ciebie. ClassWizard firmy Domyślna implementacja zwraca uchwyt zestawu wierszy, przechowywane w widoku rekordu, jeśli taka istnieje. Jeśli nie, jego tworzy typ obiektu zestawu wierszy określono ClassWizard i wywołuje jego `Open` element członkowski funkcji Otwórz tabelę lub uruchom zapytanie, a następnie zwraca uchwyt do obiektu.

> [!NOTE]
>  Wcześniejszych niż MFC 7.0 `OnGetRowset` zwrócony wskaźnik do `CRowset`. Jeśli masz kod, który wywołuje `OnGetRowset`, należy zmienić typ zwracany do szablonowej klasy **CRowset <>**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Aby uzyskać więcej informacji i przykładów, zobacz artykuł [widoków rekordów: Używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>  COleDBRecordView::OnMove

Przechodzi do innego rekordu w zestawie wierszy i wyświetlania jej pola w kontrolkach rekordu w widoku.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jeden z następujących wartości Identyfikatora standardowe polecenia:

- ID_RECORD_FIRST — Przejście do pierwszego rekordu w zestawie rekordów.

- ID_RECORD_LAST — Przejdź do ostatniego rekordu w zestawie rekordów.

- ID_RECORD_NEXT — Przejście do następnego rekordu w zestawie rekordów.

- ID_RECORD_PREV — Przejście do poprzedniego rekordu w zestawie rekordów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli przeniesienie zostało wykonane prawidłowo; w przeciwnym razie 0, jeśli żądanie przeniesienia zostało odrzucone.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje odpowiednią `Move` funkcji składowej typu `CRowset` obiekt skojarzony z widokiem rekordów.

Domyślnie `OnMove` aktualizacji bieżący rekord w źródle danych, jeśli użytkownik zmienił się ona w widoku rekordu.

Kreator aplikacji umożliwia utworzenie zasobu menu z elementami menu pierwszy rekord, ostatni rekord, następny rekord i poprzedni rekord. Jeśli wybierzesz opcję Dokowalne narzędzi, Kreator aplikacji tworzy także paska narzędzi za pomocą przycisków odpowiadający tych poleceń.

Jeśli przenosisz poza ostatni rekord w zestawie, widoku rekordu to jest nadal wyświetlany ostatni rekord. Jeśli możesz przejść wstecz pierwszy rekord, widoku rekordu w dalszym ciągu wyświetlić pierwszy rekord.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
