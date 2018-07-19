---
title: Klasa CRecordView | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f5908427a256595a032821d947ddad79ec588b6a
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853509"
---
# <a name="crecordview-class"></a>Crecordview — klasa
Widok wyświetlający rekordy bazy danych w kontrolkach.  
  
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
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Zwraca wartość różną od zera, jeżeli bieżący rekord jest pierwszego rekordu w zestawie rekordów skojarzonych.|  
|[CRecordView::IsOnLastRecord](#isonlastrecord)|Zwraca wartość różną od zera, jeżeli bieżący rekord jest ostatni rekord w zestawie rekordów skojarzonych.|  
|[CRecordView::OnGetRecordset](#ongetrecordset)|Zwraca wskaźnik do obiektu klasy pochodzącej od `CRecordset`. ClassWizard powoduje zastąpienie tej funkcji i tworzy zestaw rekordów, jeśli to konieczne.|  
|[CRecordView::OnMove](#onmove)||  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRecordView::OnMove](#onmove)|Jeśli bieżący rekord został zmieniony, aktualizuje je w źródle danych, a następnie przechodzi do określonego rekordu (dalej, poprzedniego, pierwszego lub ostatniego).|  
  
## <a name="remarks"></a>Uwagi  
 Widok jest podłączone bezpośrednio do widoku formularza `CRecordset` obiektu. Widok jest tworzony z zasobu szablonu okna dialogowego i są wyświetlane pola `CRecordset` obiektu w kontrolkach szablonu okna dialogowego. `CRecordView` Obiekt używa wymiana danych okna dialogowego (DDX) i wymiana pól rekordów (RFX) do automatyzowania przenoszenia danych między pól zestawu rekordów i formantów w formularzu. `CRecordView` dostarcza również domyślna implementacja przechodzenia do pierwszego, dalej, poprzednie lub ostatni rekord a interfejsem aktualizowania rekordu aktualnie w widoku.  
  
> [!NOTE]
>  Jeśli pracujesz z klas obiektów dostępu do danych (DAO), a nie klasy Open Database Connectivity (ODBC), należy użyć klasy [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md).  
  
 Najczęstszym sposobem tworzenia widoku rekordu jest za pomocą Kreatora aplikacji. Kreatora aplikacji TGE tworzy zarówno w klas widoków rekordów, jak i w swojej klasie skojarzony zestaw rekordów w ramach początkowego szkielet aplikacji. Jeśli nie utworzysz klas widoków rekordów za pomocą Kreatora aplikacji, można utworzyć ją później za pomocą ClassWizard. Jeśli po prostu potrzebujesz jednego formularza, podejście Kreatora aplikacji jest łatwiejsze. ClassWizard pozwala określić użyć widoku rekordu w dalszej części procesu rozwoju. Tworzenie widoku rekordu i zestawu rekordów osobno, a następnie połącz je za pomocą ClassWizard jest najbardziej elastycznym podejściem, ponieważ zapewnia większą kontrolę w nazwach klasy zestawu rekordów i jego. GODZ. /. Plikach CPP. Takie podejście umożliwia również mieć wiele widoków rekordów w tej samej klasy zestawu rekordów.  
  
 Aby ułatwić użytkownikom końcowym przenieść między rekordami w widoku rekordu, Kreator aplikacji tworzy menu (i opcjonalnie paska narzędzi) zasoby dotyczące przenoszenia do pierwszego, dalej, poprzednie lub ostatni rekord. Jeśli utworzysz klas widoków rekordów z ClassWizard, musisz utworzyć te zasoby samodzielnie za pomocą menu i mapy bitowej edytorów.  
  
 Aby uzyskać informacji o implementacji domyślnej przechodzenia między rekordami, zobacz `IsOnFirstRecord` i `IsOnLastRecord` oraz artykuł [używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).  
  
 `CRecordView` przechowuje informacje o pozycji użytkownika w zestawie rekordów, tak, aby zaktualizować interfejs użytkownika widoku rekordu. Po użytkownik przenosi się do dowolnego końca zestawu rekordów, widoku rekordu wyłącza obiektów interfejsu użytkownika — np. w menu i przycisków paska narzędzi — przenoszenia w tym samym kierunku.  
  
 Aby uzyskać więcej informacji na temat deklarowania i korzystając z widoków rekordów i rekordów klas, zobacz "Projektowanie i tworzenie widoku rekordu" w artykule [widoków rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji na temat jak rekord widoków pracy i sposobu ich używania, zobacz artykuł [używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CRecordView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
##  <a name="crecordview"></a>  CRecordView::CRecordView  
 Po utworzeniu obiektu typu pochodną `CRecordView`, wywołanie dowolnej postaci konstruktora, aby zainicjować obiekt widoku i identyfikacji zasobu okna dialogowego, na którym bazuje widoku.  
  
```  
explicit CRecordView(LPCTSTR lpszTemplateName);  
explicit CRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszTemplateName*  
 Zawiera ciąg zakończony znakiem null, nazwę zasobu szablonu okna dialogowego.  
  
 *nIDTemplate*  
 Zawiera identyfikator zasobu szablonu okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Można albo określ zasób według nazwy (pass ciąg jako argument konstruktora) lub jej identyfikator (pass liczbą całkowitą bez znaku jako argument). Zasób identyfikator zaleca się użycie.  
  
> [!NOTE]
>  Klasy pochodne *musi* podać swój własny konstruktora. W konstruktorze klasy pochodnej, wywołanie konstruktora `CRecordView::CRecordView` przy użyciu nazwy zasobu lub identyfikator jako argument, jak pokazano w poniższym przykładzie.  
  
 `CRecordView::OnInitialUpdate` wywołania `UpdateData`, która wywołuje metodę `DoDataExchange`. To wywołanie początkowej `DoDataExchange` łączy `CRecordView` kontroluje (pośrednio) do `CRecordset` pól składowych danych utworzonych przez ClassWizard. Te elementy członkowskie danych nie można używać do czasu, po wywołaniu metody klasy bazowej `CFormView::OnInitialUpdate` funkcja elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli używasz ClassWizard, Kreator definiuje **wyliczenia** wartość `CRecordView::IDD`określa go w deklaracji klasy i używa go na liście inicjowanie elementów członkowskich dla konstruktora.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord  
 Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy bieżący rekord jest pierwszy rekord w obiekcie rekordów skojarzonego z tym widokiem rekordu.  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeżeli bieżący rekord jest pierwszy rekord w zestawie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatne przy pisaniu własnych implementacji domyślnej napisane przez ClassWizard programy obsługi aktualizacji poleceń.  
  
 Jeśli użytkownik przenosi się do pierwszego rekordu, struktura wyłącza obiektów interfejsu użytkownika, wszystkie posiadane dotyczące przechodzenia na pierwszym lub poprzedniego rekordu.  
  
##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord  
 Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy bieżący rekord jest ostatni rekord w obiekcie rekordów skojarzonego z tym widokiem rekordu.  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeżeli bieżący rekord jest ostatni rekord w zestawie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatne przy pisaniu własne implementacje domyślne programy obsługi aktualizacji poleceń, które ClassWizard zapisuje do obsługi interfejsu użytkownika w przypadku przenoszenia między rekordami.  
  
> [!CAUTION]
>  Wynikiem tej funkcji jest niezawodne, z tą różnicą, że widok nie może wykryć koniec zestawu rekordów, dopóki użytkownik został przeniesiony poza jej. Użytkownik musi przenieść poza ostatnim rekordzie, przed widoków rekordów można stwierdzić, czy należy wyłączyć w niej żadnych obiektów interfejsu użytkownika dla przejście do następnej lub ostatni rekord. Jeśli użytkownik przenosi ostatnie ostatni rekord, a następnie przechodzi do ostatniego rekordu (lub przed nią) widoku rekordu można śledzić położenie użytkownika w zestawie rekordów i Wyłącz poprawnie obiektów interfejsu użytkownika. `IsOnLastRecord` jest również zawodnych po wywołaniu funkcji implementacji `OnRecordLast`, która obsługuje polecenie ID_RECORD_LAST lub `CRecordset::MoveLast`.  
  
##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset  
 Zwraca wskaźnik do `CRecordset`-pochodzi obiekt skojarzony z widokiem rekordów.  
  
```  
virtual CRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CRecordset`-pochodnych obiektu, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie wskaźnika o wartości NULL.  
  
### <a name="remarks"></a>Uwagi  
 Konieczne jest przesłonięcie tej funkcji elementu członkowskiego, konstruowania lub uzyskać obiekty zestawów rekordów i zwracają wskaźnik do niego. Deklarowanie klasy widoków rekordów z ClassWizard kreator zapisuje zastąpienia domyślnej dla Ciebie. Firmy ClassWizard Domyślna implementacja zwraca wskaźnik rekordów przechowywanych w widoku rekordu, jeśli taka istnieje. Jeśli nie, jego tworzy obiekt zestawu rekordów typu określono ClassWizard i wywołuje jego `Open` element członkowski funkcji Otwórz tabelę lub uruchom zapytanie, a następnie zwraca wskaźnik do obiektu.  
  
 Aby uzyskać więcej informacji i przykładów, zobacz artykuł [widoków rekordów: Używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>  CRecordView::OnMove  
 Wywołaj tę funkcję elementu członkowskiego, aby przenieść do innego rekordu w zestawie rekordów i wyświetlić jej pola w kontrolkach widoku rekordu.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDMoveCommand*  
 Jeden z następujących wartości Identyfikatora standardowe polecenia:  
  
- ID_RECORD_FIRST przenieść się do pierwszego rekordu w zestawie rekordów.  
  
- ID_RECORD_LAST przenieść się do ostatniego rekordu w zestawie rekordów.  
  
- ID_RECORD_NEXT przejście do następnego rekordu w zestawie rekordów.  
  
- ID_RECORD_PREV przejście do poprzedniego rekordu w zestawie rekordów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przeniesienie zostało wykonane prawidłowo; w przeciwnym razie 0, jeśli żądanie przeniesienia zostało odrzucone.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje odpowiednią `Move` funkcji składowej typu `CRecordset` obiekt skojarzony z widokiem rekordów.  
  
 Domyślnie `OnMove` aktualizacji bieżący rekord w źródle danych, jeśli użytkownik zmienił się ona w widoku rekordu.  
  
 Kreator aplikacji umożliwia utworzenie zasobu menu z elementami menu pierwszy rekord, ostatni rekord, następny rekord i poprzedni rekord. Jeśli wybierzesz opcję Dokowalne narzędzi, Kreator aplikacji tworzy także pasek narzędzi za pomocą przycisków odpowiadający tych poleceń.  
  
 Jeśli przenosisz poza ostatni rekord w zestawie, widoku rekordu to jest nadal wyświetlany ostatni rekord. Jeśli możesz przejść wstecz pierwszy rekord, widoku rekordu w dalszym ciągu wyświetlić pierwszy rekord.  
  
> [!CAUTION]
>  Wywoływanie `OnMove` zgłasza wyjątek, jeśli zestaw rekordów nie zawiera żadnych rekordów. Wywołanie funkcji obsługi aktualizacji interfejsu użytkownika odpowiedni — `OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`, lub `OnUpdateRecordPrev` — przed odpowiednimi operacji, aby ustalić, czy zestaw rekordów zawiera wszystkie rekordy przeniesienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CFormView](../../mfc/reference/cformview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CRecordset](../../mfc/reference/crecordset-class.md)   
 [Klasa CFormView](../../mfc/reference/cformview-class.md)
