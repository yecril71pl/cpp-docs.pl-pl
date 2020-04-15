---
title: Klasa COleDBRecordView
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
ms.openlocfilehash: de9c602cb747ee3d4449df479530e55ce907cb8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366102"
---
# <a name="coledbrecordview-class"></a>Klasa COleDBRecordView

Widok, który wyświetla rekordy bazy danych w formantach.

## <a name="syntax"></a>Składnia

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Konstruuje `COleDBRecordView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Zwraca standardową wartość HRESULT.|
|[COleDBRecordView::OnMove](#onmove)|Aktualizuje bieżący rekord (jeśli jest zabrudzony) w źródle danych, a następnie przechodzi do określonego rekordu (następnego, poprzedniego, pierwszego lub ostatniego).|

## <a name="remarks"></a>Uwagi

Widok jest widokiem formularza bezpośrednio połączonym z obiektem. `CRowset` Widok jest tworzony na podstawie zasobu szablonu `CRowset` okna dialogowego i wyświetla pola obiektu w formantych szablonu okna dialogowego. Obiekt `COleDBRecordView` używa wymiany danych okna dialogowego (DDX) i `CRowset`wbudowanej funkcji nawigacyjnej, aby zautomatyzować przenoszenie danych między formantami w formularzu a polami zestawu wierszy. `COleDBRecordView`dostarcza również domyślną implementację do przejścia do pierwszego, następnego, poprzedniego lub ostatniego rekordu oraz interfejs do aktualizowania rekordu aktualnie przeglądanego.

Za pomocą funkcji DDX można uzyskać dane bezpośrednio z bazy danych i `COleDbRecordView` wyświetlić je w formancie okna dialogowego. Należy użyć `DDX_*` metod (takich `DDX_Text`jak `DDX_Field*` ), a `DDX_FieldText`nie `COleDbRecordView`funkcji (takich jak ) z . `DDX_FieldText`nie będzie `COleDbRecordView` działać, ponieważ `DDX_FieldText` przyjmuje `CRecordset*` dodatkowy `CRecordView`argument `CDaoRecordset*` typu `CDaoRecordView`(dla) lub (dla ).

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie klas szablonów konsumenta OLE DB, należy użyć klasy [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) Aby uzyskać więcej informacji, zobacz artykuł [Omówienie: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView`śledzi pozycję użytkownika w zestawie wierszy, dzięki czemu widok rekordu może zaktualizować interfejs użytkownika. Gdy użytkownik przesunie się na koniec zestawu wierszy, widok rekordu wyłącza obiekty interfejsu użytkownika — takie jak elementy menu lub przyciski paska narzędzi — w celu dalszego przesuwania się w tym samym kierunku.

Aby uzyskać więcej informacji na temat klas zestawu wierszy, zobacz [using OLE DB Consumer Templates](../../data/oledb/ole-db-consumer-templates-cpp.md) artykułu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[Cscrollview](../../mfc/reference/cscrollview-class.md)

[Cformview](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxoledb.h

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView

Konstruuje `COleDBRecordView` obiekt.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Zawiera ciąg zakończony zerem, który jest nazwą zasobu szablonu okna dialogowego.

*nIDTemplate*<br/>
Zawiera numer identyfikatora zasobu szablonu okna dialogowego.

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu typu pochodnego `COleDBRecordView`z , wywołać jeden z konstruktorów, aby utworzyć obiekt widoku i zidentyfikować zasób okna dialogowego, na którym opiera się widok. Zasób można zidentyfikować według nazwy (przekazać ciąg jako argument do konstruktora) lub jego identyfikator (przekazać niepodpisaną kreślęń całkowitych jako argument).

> [!NOTE]
> Klasa pochodna *musi* dostarczyć własny konstruktor. W konstruktorze wywołać konstruktora, `COleDBRecordView::COleDBRecordView`z nazwą zasobu lub identyfikator jako argument.

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a>COleDBRecordView::OnGetRowset

Zwraca dojście dla obiektu **CRowset<>** skojarzonego z widokiem rekordu.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Należy zastąpić tę funkcję elementu członkowskiego, aby skonstruować lub uzyskać obiekt zestawu wierszy i zwrócić do niego dojście. Jeśli zadeklarujesz klasę widoku rekordu za pomocą ClassWizard, kreator zapisze domyślne zastąpienie dla Ciebie. Domyślna implementacja ClassWizard zwraca dojście zestawu wierszy przechowywane w widoku rekordu, jeśli istnieje. Jeśli nie, tworzy obiekt zestawu wierszy typu określonego za pomocą `Open` ClassWizard i wywołuje jego funkcję elementu członkowskiego, aby otworzyć tabelę lub uruchomić kwerendę, a następnie zwraca dojście do obiektu.

> [!NOTE]
> Poprzedni do MFC 7.0, `OnGetRowset` `CRowset`zwrócił wskaźnik do . Jeśli masz kod, `OnGetRowset`który wywołuje, należy zmienić typ powrotu do klasy **crowset **templatized<>.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Aby uzyskać więcej informacji i przykładów, zobacz artykuł [Widoki rekordów: Korzystanie z widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a>COleDBRecordView::OnMove

Przechodzi do innego rekordu w zestawie wierszy i wyświetla jego pola w formantych widoku rekordu.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jedna z następujących standardowych wartości identyfikatora polecenia:

- ID_RECORD_FIRST — przejście do pierwszego rekordu w ach recordset.

- ID_RECORD_LAST — przejście do ostatniego rekordu w ach recordset.

- ID_RECORD_NEXT — przejście do następnego rekordu w ach.

- ID_RECORD_PREV — przejście do poprzedniego rekordu w ach.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli ruch się powiódł; w przeciwnym razie 0, jeśli żądanie przeniesienia zostało odrzucone.

### <a name="remarks"></a>Uwagi

Domyślna implementacja `Move` wywołuje odpowiednią `CRowset` funkcję elementu członkowskiego obiektu skojarzonego z widokiem rekordu.

Domyślnie `OnMove` aktualizuje bieżący rekord w źródle danych, jeśli użytkownik zmienił go w widoku rekordu.

Kreator aplikacji tworzy zasób menu z elementami menu Pierwszy rekord, Ostatni rekord, Następny rekord i Poprzedni rekord. Jeśli wybierzesz opcję Dockable Toolbar, Kreator aplikacji utworzy również pasek narzędzi z przyciskami odpowiadającymi tym poleceniom.

Jeśli przejdziesz obok ostatniego rekordu w tablicy rekordów, widok rekordu będzie nadal wyświetlał ostatni rekord. Jeśli przejdziesz do tyłu obok pierwszego rekordu, widok rekordu będzie nadal wyświetlał pierwszy rekord.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
