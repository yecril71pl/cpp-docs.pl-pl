---
title: CRecordView — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3d040f2da622cbfd6d1577729861917a5a03270
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079150"
---
# <a name="crecordview-class"></a>CRecordView — klasa
Widok, który wyświetla rekordów bazy danych w kontrolkach.  
  
## <a name="syntax"></a>Składnia  
  
```  
class AFX_NOVTABLE CRecordView : public CFormView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordView::CRecordView](#crecordview)|Konstruuje `CRecordView` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Zwraca wartość niezerową, jeśli bieżący rekord jest pierwszy rekord w skojarzonych rekordów.|  
|[CRecordView::IsOnLastRecord](#isonlastrecord)|Zwraca wartość niezerową, jeśli bieżący rekord jest ostatni rekord w skojarzonych rekordów.|  
|[CRecordView::OnGetRecordset](#ongetrecordset)|Zwraca wskaźnik do obiektu klasy pochodzącej od `CRecordset`. ClassWizard powoduje zastąpienie tej funkcji i w razie potrzeby utworzyć zestaw rekordów.|  
|[CRecordView::OnMove](#onmove)||  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordView::OnMove](#onmove)|Jeśli bieżący rekord został zmieniony, aktualizuje w źródle danych, a następnie przechodzi do określonego rekordu (następnego, poprzedniego, pierwszego lub ostatniego).|  
  
## <a name="remarks"></a>Uwagi  
 Widok jest widokiem formularza bezpośrednio podłączone do `CRecordset` obiektu. Widok jest tworzony na podstawie zasobu szablonu okna dialogowego i są wyświetlane pola `CRecordset` obiektu w formantach szablonu okna dialogowego. `CRecordView` Obiektu używa wymiana danych okna dialogowego (DDX) i wymiana pól rekordów (RFX) do automatycznego przenoszenia danych między pól zestawu rekordów i kontrolek w formularzu. `CRecordView` również udostępnia domyślną implementację przenoszenia jako pierwszy dalej, poprzedniego lub ostatniego rekordu i interfejs aktualizowania rekordu w widoku.  
  
> [!NOTE]
>  Jeśli pracujesz z klas obiektów DAO (Data Access), a nie klasy otwarte połączenie bazy danych (ODBC), należy użyć klasy [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md).  
  
 Jest to najbardziej typowe sposób tworzenia widoku rekordu przy użyciu Kreatora aplikacji. Kreator aplikacji TGE tworzy w klasie widoku rekordu i jego klasa skojarzonych rekordów w ramach początkowego szkielet aplikacji. Jeśli nie utworzysz klasy widoków rekordów przy użyciu Kreatora aplikacji, można utworzyć go później z ClassWizard. Jeśli potrzebujesz tylko jeden formularz, podejście Kreatora aplikacji jest łatwiejsze. ClassWizard pozwala zdecydować użyć widoku rekordu w dalszej części procesu tworzenia. Tworzenie widoku rekordu i zestaw rekordów oddzielnie, a następnie połącz je za pomocą ClassWizard jest najbardziej elastyczne podejście, ponieważ zapewnia większą kontrolę w nazw klasy zestawu rekordów i jej. H /. Pliki CPP. To rozwiązanie umożliwia również mieć wiele widoków rekordów na tej samej klasy zestawu rekordów.  
  
 Aby ułatwić użytkownikom końcowym przenieść rekordu rekordu w widoku rekordu, Kreator aplikacji tworzy menu (i opcjonalnie paska narzędzi) zasoby do przenoszenia jako pierwszy dalej, poprzedniego lub rekordu. W przypadku utworzenia klasy widoków rekordów z ClassWizard, należy utworzyć te zasoby samodzielnie przy użyciu menu i mapy bitowej edytory.  
  
 Informacje w implementacji domyślnej do przechodzenia między rekordami, zobacz `IsOnFirstRecord` i `IsOnLastRecord` i artykułu [przy użyciu widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).  
  
 `CRecordView` przechowuje informacje o pozycji użytkownika w zestawie rekordów, dzięki czemu widoku rekordu można zaktualizować interfejsu użytkownika. Gdy użytkownik zostanie przeniesiony do jednego z końców zestawu rekordów, widoku rekordu wyłącza obiekty interfejsu użytkownika — takich jak elementy menu lub przycisków paska narzędzi — przenoszenie więcej w tym samym kierunku.  
  
 Aby uzyskać więcej informacji na temat deklarowanie i przy użyciu widoków rekordów i rekordów klas, zobacz "Projektowanie i tworzenie widoku rekordu" w artykule [widoków rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji na temat jak rekord widoków pracy i sposobu ich używania, zobacz artykuł [przy użyciu widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CRecordView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
##  <a name="crecordview"></a>  CRecordView::CRecordView  
 Podczas tworzenia obiektu typu pochodną `CRecordView`, wywołanie jest używana dowolna forma konstruktora do zainicjowania obiektu widoku i identyfikacji zasobu okna dialogowego, na której oparto widoku.  
  
```  
explicit CRecordView(LPCTSTR lpszTemplateName);  
explicit CRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszTemplateName*  
 Zawiera zerem ciąg określający nazwę zasobu szablonu okna dialogowego.  
  
 *nIDTemplate*  
 Zawiera identyfikator zasobu szablonu okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Zasób można zidentyfikować albo według nazwy (pass ciąg jako argument do konstruktora) lub jego identyfikator (pass całkowitą bez znaku jako argument). Użycie zasobów identyfikator jest zalecane.  
  
> [!NOTE]
>  Klasy pochodne *musi* podać własne konstruktora. W konstruktorze klasy pochodnej, wywołanie konstruktora `CRecordView::CRecordView` o nazwy zasobu lub identyfikatorze jako argument, jak pokazano w poniższym przykładzie.  
  
 **CRecordView::OnInitialUpdate** wywołania `UpdateData`, które wywołuje `DoDataExchange`. To wywołanie początkowej `DoDataExchange` łączy `CRecordView` (pośrednio) do kontrolki `CRecordset` utworzone przez ClassWizard elementy członkowskie danych pola. Te elementy członkowskie danych nie można użyć dopiero po wywołaniu metody klasy podstawowej **CFormView::OnInitialUpdate** funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli używasz ClassWizard, Kreator definiuje **wyliczenia** wartość `CRecordView::IDD`określa go w deklaracji klasy i używa go na liście inicjowanie elementu członkowskiego dla konstruktora.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy bieżący rekord jest pierwszy rekord w obiekcie rekordów skojarzonego z tym widokiem rekordu.  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bieżący rekord jest pierwszy rekord w zestawie rekordów; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatna do zapisywania własnych implementacji domyślnej napisane przez ClassWizard programy obsługi aktualizacji poleceń.  
  
 Jeśli użytkownik przejdzie do pierwszego rekordu, struktury wyłącza wszystkie obiekty interfejsu użytkownika dla przenosząc pierwsza lub poprzedniego rekordu.  
  
##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy bieżący rekord jest ostatni rekord w obiekcie rekordów skojarzonego z tym widokiem rekordu.  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bieżący rekord jest ostatni rekord w zestawie rekordów; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatna do zapisywania własnych implementacji domyślnej programy obsługi aktualizacji poleceń, które ClassWizard zapisuje do obsługi interfejsu użytkownika do przechodzenia między rekordami.  
  
> [!CAUTION]
>  Wynik tej funkcji jest niezawodne, z wyjątkiem tego widoku nie może wykryć koniec zestawu rekordów, dopóki użytkownik został przeniesiony poza jej. Użytkownik musi przenieść poza ostatni rekord przed widoku rekordu można określić, czy należy wyłączyć wszystkie obiekty interfejsu użytkownika do przechodzenia do następnego lub ostatniego rekordu. Jeśli użytkownik przenosi poza ostatniego rekordu, a następnie jest przenoszony do ostatniego rekordu (lub przed nim), widoku rekordu można śledzić położenie użytkownika w zestawie rekordów i poprawnie wyłączyć obiekty interfejsu użytkownika. `IsOnLastRecord` jest również zawodnych po wywołaniu funkcji implementacji `OnRecordLast`, która obsługuje `ID_RECORD_LAST` polecenia, lub `CRecordset::MoveLast`.  
  
##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset  
 Zwraca wskaźnik do `CRecordset`-pochodnych obiekt skojarzony z widokiem rekordów.  
  
```  
virtual CRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CRecordset`-pochodnych obiektu, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie **NULL** wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję elementu członkowskiego, utworzyć lub uzyskać obiekty zestawów rekordów i zwraca wskaźnik do niego. Deklarowanie klasy widoków rekordów z ClassWizard kreator zapisuje zastąpienie domyślnego dla Ciebie. W ClassWizard Domyślna implementacja zwraca wskaźnik rekordów przechowywane w widoku rekordu, jeśli taka istnieje. Jeśli nie, jego tworzy obiekt zestaw rekordów typu określono wywołań i ClassWizard jego `Open` element członkowski funkcji można otworzyć tabeli, lub uruchomić zapytanie, a następnie zwraca wskaźnik do obiektu.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz artykuł [widoków rekordów: Używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>  CRecordView::OnMove  
 Wywołanie tej funkcji Członkowskich, aby przenieść do innego rekordu w zestawie rekordów i wyświetlić jego pól w formantach widoku rekordu.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDMoveCommand`  
 Jedna z następujących wartości Identyfikatora standardowego polecenia:  
  
- `ID_RECORD_FIRST` Przenieś na pierwszy rekord w zestawie rekordów.  
  
- `ID_RECORD_LAST` Przejdź do ostatniego rekordu w zestawie rekordów.  
  
- `ID_RECORD_NEXT` Przenieś do następnego rekordu w zestawie rekordów.  
  
- `ID_RECORD_PREV` Przenieś do poprzedniego rekordu w zestawie rekordów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przeniesienie zakończyło się pomyślnie; w przeciwnym razie 0, jeśli żądanie przeniesienia zostało odrzucone.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje odpowiednie `Move` funkcji członkowskiej klasy `CRecordset` obiekt skojarzony z widokiem rekordów.  
  
 Domyślnie `OnMove` aktualizacji bieżącego rekordu w źródle danych, jeśli użytkownik zmienił się on w widoku rekordu.  
  
 Kreator aplikacji tworzy zasobów menu z pierwszego rekordu, ostatni rekord następnego rekordu i poprzedniego rekordu elementów menu. Jeśli wybrano opcję dokującego paska narzędzi, Kreator aplikacji tworzy przyciskami odpowiadający tych poleceń paska narzędzi.  
  
 Po przeniesieniu poza ostatni rekord w zestawie rekordów widoku rekordu jest nadal wyświetlana ostatniego rekordu. Po przeniesieniu poza pierwszy rekord wstecz widoku rekordu jest nadal wyświetlana pierwszy rekord.  
  
> [!CAUTION]
>  Wywoływanie `OnMove` zgłasza wyjątek, jeśli zestaw nie zawiera żadnych rekordów. Wywołanie funkcji obsługi aktualizacji interfejsu odpowiedniego użytkownika — `OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`, lub `OnUpdateRecordPrev` — przed odpowiednich operacji przenoszenia w celu określenia, czy zestaw rekordów zawiera rekordy.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CFormView](../../mfc/reference/cformview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Crecordset — klasa](../../mfc/reference/crecordset-class.md)   
 [Klasa CFormView](../../mfc/reference/cformview-class.md)
