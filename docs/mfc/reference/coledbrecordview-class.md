---
title: "Coledbrecordview — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
dev_langs: C++
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd827d729af5186d6872536cdaa3d8863d1f8d10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coledbrecordview-class"></a>Coledbrecordview — klasa
Widok, który wyświetla rekordów bazy danych w kontrolkach.  
  
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
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Zwraca standard `HRESULT` wartość.|  
|[COleDBRecordView::OnMove](#onmove)|Aktualizuje bieżącego rekordu (jeśli jest zanieczyszczony) w źródle danych, a następnie przechodzi do określonego rekordu (następnego, poprzedniego, pierwszego lub ostatniego).|  
  
## <a name="remarks"></a>Uwagi  
 Widok jest widokiem formularza bezpośrednio podłączone do `CRowset` obiektu. Widok jest tworzony na podstawie zasobu szablonu okna dialogowego i są wyświetlane pola `CRowset` obiektu w formantach szablonu okna dialogowego. `COleDBRecordView` Obiekt używa wymiana danych okna dialogowego (DDX) i nawigacyjne funkcje wbudowane w `CRowset`, aby zautomatyzować przepływ danych między kontrolek w formularzu i pola zestawu wierszy. `COleDBRecordView`również udostępnia domyślną implementację przenoszenia jako pierwszy dalej, poprzedniego lub ostatniego rekordu i interfejs aktualizowania rekordu w widoku.  
  
 Możesz użyć funkcji DDX z **coledbrecordview —** Pobierz dane bezpośrednio z rekordów bazy danych i wyświetlić je w formancie okna dialogowego. Należy używać **DDX_\***  metod (takich jak `DDX_Text`), a nie **ddx_field —\***  funkcje (takie jak `DDX_FieldText`) z **coledbrecordview —** . `DDX_FieldText`nie będzie działać z **coledbrecordview —** ponieważ `DDX_FieldText` ma dodatkowy argument typu **crecordset —\***  (dla `CRecordView`) lub **cdaorecordset — \***  (dla `CDaoRecordView`).  
  
> [!NOTE]
>  Jeśli pracujesz z klas obiektów DAO (Data Access), a nie klasy OLE DB szablon konsumenta, należy użyć klasy [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md).  
  
 `COleDBRecordView`przechowuje informacje o pozycji użytkownika w zestawie wierszy, dzięki czemu widoku rekordu można zaktualizować interfejsu użytkownika. Gdy użytkownik zostanie przeniesiony do jednego z końców zestawu wierszy, widoku rekordu wyłącza obiekty interfejsu użytkownika — takich jak elementy menu lub przycisków paska narzędzi — przenoszenie więcej w tym samym kierunku.  
  
 Aby uzyskać więcej informacji na temat klasy zestawów wierszy, zobacz [przy użyciu OLE DB szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md) artykułu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `COleDBRecordView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxoledb.h  
  
##  <a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView  
 Konstruuje `COleDBRecordView` obiektu.  
  
```  
COleDBRecordView(LPCTSTR lpszTemplateName);  
COleDBRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Zawiera ciąg zerem, który jest nazwa zasobu szablonu okna dialogowego.  
  
 `nIDTemplate`  
 Zawiera identyfikator zasobu szablonu okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Podczas tworzenia obiektu typu pochodną `COleDBRecordView`, wywołać za pomocą jednego z konstruktorów do utworzenia obiektu widoku i identyfikacji zasobu okna dialogowego, na której oparto widoku. Zasób można zidentyfikować przez nazwę (pass ciąg jako argument do konstruktora) lub za pomocą jego Identyfikatora (pass całkowitą bez znaku jako argument).  
  
> [!NOTE]
>  Klasy pochodne *musi* podać własne konstruktora. W konstruktorze, należy wywołać konstruktora, `COleDBRecordView::COleDBRecordView`, o nazwy zasobu lub identyfikatorze jako argument.  
  
##  <a name="ongetrowset"></a>COleDBRecordView::OnGetRowset  
 Zwraca uchwyt dla **CRowset <>** obiekt skojarzony z widokiem rekordów.  
  
```  
virtual CRowset<>* OnGetRowset() = 0;  
 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję elementu członkowskiego, utworzyć lub uzyskać obiektu zestawu wierszy i przywrócenie dojścia. Deklarowanie klasy widoków rekordów z ClassWizard kreator zapisuje zastąpienie domyślnego dla Ciebie. W ClassWizard Domyślna implementacja zwraca dojście wierszy przechowywane w widoku rekordu, jeśli taka istnieje. Jeśli nie, tworzy go typu obiektu zestawu wierszy określono wywołań i ClassWizard jego **Otwórz** element członkowski funkcji można otworzyć tabeli, lub uruchomić zapytanie, a następnie zwraca uchwyt do obiektu.  
  
> [!NOTE]
>  Wstecz, aby MFC 7.0 `OnGetRowset` zwrócił wskaźnik do `CRowset`. Jeśli masz kod, który wywołuje `OnGetRowset`, należy zmienić typ zwracany do szablonowej klasy **CRowset <>**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz artykuł [widoków rekordów: Używanie widoku rekordu](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>COleDBRecordView::OnMove  
 Przenosi do innego rekordu w zestawie wierszy i wyświetlić jego pola w formantach rekordu w widoku.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDMoveCommand`  
 Jedna z następujących wartości Identyfikatora standardowego polecenia:  
  
- `ID_RECORD_FIRST`— Przejście do pierwszego rekordu w zestawie rekordów.  
  
- `ID_RECORD_LAST`— Przejdź do ostatniego rekordu w zestawie rekordów.  
  
- `ID_RECORD_NEXT`— Przejście do następnego rekordu w zestawie rekordów.  
  
- `ID_RECORD_PREV`— Przejście do poprzedniego rekordu w zestawie rekordów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przeniesienie zakończyło się pomyślnie; w przeciwnym razie 0, jeśli żądanie przeniesienia zostało odrzucone.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje odpowiednie **Przenieś** funkcji członkowskiej klasy `CRowset` obiekt skojarzony z widokiem rekordów.  
  
 Domyślnie `OnMove` aktualizacji bieżącego rekordu w źródle danych, jeśli użytkownik zmienił się on w widoku rekordu.  
  
 Kreator aplikacji tworzy zasobów menu z pierwszego rekordu, ostatni rekord następnego rekordu i poprzedniego rekordu elementów menu. Jeśli wybrano opcję dokującego paska narzędzi, Kreator aplikacji tworzy przyciskami odpowiadający tych poleceń paska narzędzi.  
  
 Po przeniesieniu poza ostatni rekord w zestawie rekordów widoku rekordu jest nadal wyświetlana ostatniego rekordu. Po przeniesieniu poza pierwszy rekord wstecz widoku rekordu jest nadal wyświetlana pierwszy rekord.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



