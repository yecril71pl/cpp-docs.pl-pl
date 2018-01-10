---
title: "Cdaorecordview — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
dev_langs: C++
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2fffeed33d5b966faf511f60da740c39f2b91581
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdaorecordview-class"></a>Cdaorecordview — klasa
Widok, który wyświetla rekordów bazy danych w kontrolkach.  
  
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
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Zwraca wartość niezerową, jeśli bieżący rekord jest pierwszy rekord w skojarzonych rekordów.|  
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|Zwraca wartość niezerową, jeśli bieżący rekord jest ostatni rekord w skojarzonych rekordów.|  
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Zwraca wskaźnik do obiektu klasy pochodzącej od `CDaoRecordset`. ClassWizard powoduje zastąpienie tej funkcji i w razie potrzeby utworzyć zestaw rekordów.|  
|[CDaoRecordView::OnMove](#onmove)|Jeśli bieżący rekord został zmieniony, aktualizuje w źródle danych, a następnie przechodzi do określonego rekordu (następnego, poprzedniego, pierwszego lub ostatniego).|  
  
## <a name="remarks"></a>Uwagi  
 Widok jest widokiem formularza bezpośrednio podłączone do `CDaoRecordset` obiektu. Widok jest tworzony na podstawie zasobu szablonu okna dialogowego i są wyświetlane pola `CDaoRecordset` obiektu w formantach szablonu okna dialogowego. `CDaoRecordView` Obiektu używa wymiana danych okna dialogowego (DDX) i wymiana pól rekordów DAO (DFX) do automatycznego przenoszenia danych między pól zestawu rekordów i kontrolek w formularzu. `CDaoRecordView`również udostępnia domyślną implementację przenoszenia jako pierwszy dalej, poprzedniego lub ostatniego rekordu i interfejs aktualizowania rekordu w widoku.  
  
> [!NOTE]
>  Klasy baz danych DAO różnią się od klasy baz danych MFC oparte na otwarte połączenie bazy danych (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC z klasy DAO; klasy DAO zazwyczaj oferują możliwości wyższego poziomu, ponieważ korzystają z aparatu bazy danych programu Microsoft Jet.  
  
 Jest to najbardziej typowe sposób tworzenia widoku rekordu przy użyciu Kreatora aplikacji. Kreator aplikacji tworzy w klasie widoku rekordu i jego klasa skojarzonych rekordów w ramach początkowego szkielet aplikacji.  
  
 Jeśli potrzebujesz tylko jeden formularz, podejście Kreatora aplikacji jest łatwiejsze. ClassWizard pozwala zdecydować użyć widoku rekordu w dalszej części procesu tworzenia. Jeśli nie utworzysz klasy widoków rekordów przy użyciu Kreatora aplikacji, można utworzyć go później z ClassWizard. Tworzenie widoku rekordu i zestaw rekordów oddzielnie, a następnie połącz je za pomocą ClassWizard jest najbardziej elastyczne podejście, ponieważ zapewnia większą kontrolę w nazw klasy zestawu rekordów i jej. H /. Pliki CPP. To rozwiązanie umożliwia również mieć wiele widoków rekordów na tej samej klasy zestawu rekordów.  
  
 Aby ułatwić użytkownikom końcowym przenieść rekordu rekordu w widoku rekordu, Kreator aplikacji tworzy menu (i opcjonalnie paska narzędzi) zasoby do przenoszenia jako pierwszy dalej, poprzedniego lub rekordu. W przypadku utworzenia klasy widoków rekordów z ClassWizard, należy utworzyć te zasoby samodzielnie przy użyciu menu i mapy bitowej edytory.  
  
 Uzyskać informacji o implementacji domyślnej do przechodzenia między rekordami, zobacz `IsOnFirstRecord` i `IsOnLastRecord` i artykułu [przy użyciu widoku rekordu](../../data/using-a-record-view-mfc-data-access.md), która ma zastosowanie do obu `CRecordView` i `CDaoRecordView`.  
  
 `CDaoRecordView`przechowuje informacje o pozycji użytkownika w zestawie rekordów, dzięki czemu widoku rekordu można zaktualizować interfejsu użytkownika. Gdy użytkownik zostanie przeniesiony do jednego z końców zestawu rekordów, widoku rekordu wyłącza obiekty interfejsu użytkownika — takich jak elementy menu lub przycisków paska narzędzi — przenoszenie więcej w tym samym kierunku.  
  
 Aby uzyskać więcej informacji na temat deklarowanie i przy użyciu widoków rekordów i rekordów klas, zobacz "Projektowanie i tworzenie widoku rekordu" w artykule [widoków rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji na temat jak rekord widoków pracy i sposobu ich używania, zobacz artykuł [przy użyciu widoku rekordu](../../data/using-a-record-view-mfc-data-access.md). Wszystkie artykuły wymienione powyżej dotyczą zarówno `CRecordView` i `CDaoRecordView`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CDaoRecordView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="cdaorecordview"></a>CDaoRecordView::CDaoRecordView  
 Podczas tworzenia obiektu typu pochodną `CDaoRecordView`, wywołanie jest używana dowolna forma konstruktora do zainicjowania obiektu widoku i identyfikacji zasobu okna dialogowego, na której oparto widoku.  
  
```  
explicit CDaoRecordView(LPCTSTR lpszTemplateName);  
explicit CDaoRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Zawiera zerem ciąg określający nazwę zasobu szablonu okna dialogowego.  
  
 `nIDTemplate`  
 Zawiera identyfikator zasobu szablonu okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Zasób można zidentyfikować albo według nazwy (pass ciąg jako argument do konstruktora) lub jego identyfikator (pass całkowitą bez znaku jako argument). Użycie zasobów identyfikator jest zalecane.  
  
> [!NOTE]
>  Klasy pochodne podać własne konstruktora. W konstruktorze klasy pochodnej, wywołanie konstruktora `CDaoRecordView::CDaoRecordView` o nazwy zasobu lub identyfikatorze jako argument.  
  
 **CDaoRecordView::OnInitialUpdate** wywołania `CWnd::UpdateData`, które wywołuje `CWnd::DoDataExchange`. To wywołanie początkowej `DoDataExchange` łączy `CDaoRecordView` (pośrednio) do kontrolki `CDaoRecordset` utworzone przez ClassWizard elementy członkowskie danych pola. Te elementy członkowskie danych nie można użyć dopiero po wywołaniu metody klasy podstawowej **CFormView::OnInitialUpdate** funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli używasz ClassWizard, Kreator definiuje `enum` wartość `CDaoRecordView::IDD` w deklaracji klasy i używa go w inicjowanie elementu członkowskiego listy dla konstruktora.  
  
 [!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>CDaoRecordView::IsOnFirstRecord  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy bieżący rekord jest pierwszy rekord w obiekcie rekordów skojarzonego z tym widokiem rekordu.  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bieżący rekord jest pierwszy rekord w zestawie rekordów; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatna do zapisywania własnych implementacji domyślnej napisane przez ClassWizard programy obsługi aktualizacji poleceń.  
  
 Jeśli użytkownik przejdzie do pierwszego rekordu, wyłącza framework obiekty interfejsu użytkownika (na przykład elementów menu lub przycisków paska narzędzi) należy do przenoszenia do pierwszej lub poprzedniego rekordu.  
  
##  <a name="isonlastrecord"></a>CDaoRecordView::IsOnLastRecord  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy bieżący rekord jest ostatni rekord w obiekcie rekordów skojarzonego z tym widokiem rekordu.  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bieżący rekord jest ostatni rekord w zestawie rekordów; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatna do zapisywania własnych implementacji domyślnej programy obsługi aktualizacji poleceń, które ClassWizard zapisuje do obsługi interfejsu użytkownika do przechodzenia między rekordami.  
  
> [!CAUTION]
>  Wynik tej funkcji jest niezawodne, z wyjątkiem tego widoku nie można wykryć koniec zestawu rekordów, dopóki użytkownik został przeniesiony poza go. Użytkownik może być konieczne przed widoku rekordu można określić, czy należy wyłączyć wszystkie obiekty interfejsu użytkownika do przechodzenia do następnego lub ostatni rekord przenieść poza ostatniego rekordu. Jeśli użytkownik przenosi poza ostatniego rekordu, a następnie jest przenoszony do ostatniego rekordu (lub przed nim), widoku rekordu można śledzić położenie użytkownika w zestawie rekordów i poprawnie wyłączyć obiekty interfejsu użytkownika.  
  
##  <a name="ongetrecordset"></a>CDaoRecordView::OnGetRecordset  
 Zwraca wskaźnik do `CDaoRecordset`-pochodnych obiekt skojarzony z widokiem rekordów.  
  
```  
virtual CDaoRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CDaoRecordset`-pochodnych obiektu, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie **NULL** wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję elementu członkowskiego, utworzyć lub uzyskać obiekty zestawów rekordów i zwraca wskaźnik do niego. Deklarowanie klasy widoków rekordów z ClassWizard kreator zapisuje zastąpienie domyślnego dla Ciebie. W ClassWizard Domyślna implementacja zwraca wskaźnik rekordów przechowywane w widoku rekordu, jeśli taka istnieje. Jeśli nie, jego tworzy obiekt zestaw rekordów typu określono wywołań i ClassWizard jego **Otwórz** element członkowski funkcji można otworzyć tabeli, lub uruchomić zapytanie, a następnie zwraca wskaźnik do obiektu.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz artykuł [widoków rekordów: Używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>CDaoRecordView::OnMove  
 Wywołanie tej funkcji Członkowskich, aby przenieść do innego rekordu w zestawie rekordów i wyświetlić jego pól w formantach widoku rekordu.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDMoveCommand`  
 Jedna z następujących wartości Identyfikatora standardowego polecenia:  
  
- `ID_RECORD_FIRST`Przenieś na pierwszy rekord w zestawie rekordów.  
  
- `ID_RECORD_LAST`Przejdź do ostatniego rekordu w zestawie rekordów.  
  
- `ID_RECORD_NEXT`Przenieś do następnego rekordu w zestawie rekordów.  
  
- `ID_RECORD_PREV`Przenieś do poprzedniego rekordu w zestawie rekordów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przeniesienie zakończyło się pomyślnie; w przeciwnym razie 0, jeśli żądanie przeniesienia zostało odrzucone.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje odpowiednią funkcję elementu członkowskiego przenoszenia z `CDaoRecordset` obiekt skojarzony z widokiem rekordów.  
  
 Domyślnie `OnMove` aktualizacji bieżącego rekordu w źródle danych, jeśli użytkownik zmienił się on w widoku rekordu.  
  
 Kreator aplikacji tworzy zasobów menu z pierwszego rekordu, ostatni rekord następnego rekordu i poprzedniego rekordu elementów menu. Jeśli wybrano opcję początkowej narzędzi aplikacji Kreator tworzy także paska narzędzi z przyciskami odpowiadający tych poleceń.  
  
 Po przeniesieniu poza ostatni rekord w zestawie rekordów widoku rekordu jest nadal wyświetlana ostatniego rekordu. Po przeniesieniu poza pierwszy rekord wstecz widoku rekordu jest nadal wyświetlana pierwszy rekord.  
  
> [!CAUTION]
>  Wywoływanie `OnMove` zgłasza wyjątek, jeśli zestaw nie zawiera żadnych rekordów. Wywołanie funkcji obsługi aktualizacji interfejsu odpowiedniego użytkownika — **OnUpdateRecordFirst**, **OnUpdateRecordLast**, **OnUpdateRecordNext**, lub  **OnUpdateRecordPrev** — przed odpowiednich operacji przenoszenia w celu określenia, czy zestaw rekordów zawiera rekordy.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CFormView](../../mfc/reference/cformview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cdaorecordset — klasa](../../mfc/reference/cdaorecordset-class.md)   
 [Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)   
 [Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)   
 [Klasa CFormView](../../mfc/reference/cformview-class.md)
