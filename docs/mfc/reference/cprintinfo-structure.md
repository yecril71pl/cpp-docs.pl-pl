---
title: "Cprintinfo — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrintInfo
dev_langs:
- C++
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4943554e67d43b6dc1652a984a0e758af9d6951b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cprintinfo-structure"></a>Cprintinfo — struktura
Przechowuje informacje o zadaniu drukowania lub podglądu wydruku.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CPrintInfo  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPrintInfo::GetFromPage](#getfrompage)|Zwraca numer pierwszej strony drukowanej.|  
|[CPrintInfo::GetMaxPage](#getmaxpage)|Zwraca numer ostatniej strony dokumentu.|  
|[CPrintInfo::GetMinPage](#getminpage)|Zwraca numer pierwszej strony dokumentu.|  
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Zwraca liczbę stron poprzedzających na pierwszej stronie elementu DocObject drukowanie w scalonej DocObject zadania drukowania.|  
|[CPrintInfo::GetToPage](#gettopage)|Zwraca numer ostatniej strony drukowanej.|  
|[CPrintInfo::SetMaxPage](#setmaxpage)|Ustawia numer ostatniej strony dokumentu.|  
|[CPrintInfo::SetMinPage](#setminpage)|Ustawia numer pierwszej strony dokumentu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Zawiera nieobsługiwaną flagę wskazującą, czy w ramach powinno być kontynuowane wydruku pętli.|  
|[CPrintInfo::m_bDirect](#m_bdirect)|Zawiera nieobsługiwaną flagę wskazującą, czy dokument jest drukowany bezpośrednio (bez wyświetlania okna dialogowego drukowania).|  
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Zawiera nieobsługiwaną flagę wskazującą, czy drukowany dokument jest DocObject.|  
|[CPrintInfo::m_bPreview](#m_bpreview)|Zawiera nieobsługiwaną flagę wskazującą, czy jest przeglądany dokument.|  
|[CPrintInfo::m_dwFlags](#m_dwflags)|Określa DocObject operacji drukowania.|  
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Zawiera wskaźnik do struktury utworzonych przez użytkownika.|  
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Określa liczbę obecnie drukowanej strony.|  
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Określa numer przypisany przez system operacyjny dla bieżącego zadania drukowania|  
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Określa liczbę stron wyświetlanych w oknie Podgląd; 1 lub 2.|  
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Określa przesunięcie określonego DocObject pierwszej strony w scalonej DocObject zadania drukowania.|  
|[CPrintInfo::m_pPD](#m_ppd)|Zawiera wskaźnik do `CPrintDialog` obiekt używany dla okna dialogowego drukowania.|  
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Określa prostokąt Definiowanie bieżącego obszaru można używać strony.|  
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Zawiera ciąg formatu w celu wyświetlenia numer strony.|  
  
## <a name="remarks"></a>Uwagi  
 `CPrintInfo`jest to struktura i nie ma klasy podstawowej.  
  
 Platformę tworzy obiekt `CPrintInfo` Print po każdej aktualizacji lub polecenie Podgląd wydruku jest wybierany i niszczy ją po zakończeniu polecenia.  
  
 `CPrintInfo`zawiera informacje o zadaniu drukowania w całości, na przykład zakres stron, które mają być drukowane i bieżący stan zadania drukowania, takie jak obecnie drukowanej strony. Niektóre informacje są przechowywane w skojarzonych [CPrintDialog](../../mfc/reference/cprintdialog-class.md) obiekt; ten obiekt zawiera wartości wprowadzone przez użytkownika w oknie dialogowym drukowania.  
  
 A `CPrintInfo` obiekt jest przekazywane między struktury i klasy widok podczas drukowania i jest używany do wymiany informacji między nimi. Na przykład platformę informuje klasa widoku strony, która dokumentu do drukowania przez przypisanie wartości do `m_nCurPage` członkiem `CPrintInfo`; widoku klasy pobiera wartość i wykonuje rzeczywiste drukowanie określonej strony.  
  
 Innym przykładem jest przypadek, w którym długość dokumentu nie jest znany przed wydrukowaniem. W takim przypadku klasa widoku testy do końca dokumentu każdym razem, gdy strona jest drukowana. Po osiągnięciu końcu klasa widoku ustawia `m_bContinuePrinting` członkiem `CPrintInfo` do **FALSE**; informuje platformę, by zatrzymać wydruku pętli.  
  
 `CPrintInfo`jest używany przez funkcje Członkowskie `CView` wymienionych w sekcji "Zobacz też." Aby uzyskać więcej informacji o architekturze drukowania udostępniane przez Microsoft Foundation Class Library, zobacz [okien ramowych](../../mfc/frame-windows.md) i [architektury dokument/widok](../../mfc/document-view-architecture.md) i artykułów [ Drukowanie](../../mfc/printing.md) i [drukowanie: dokumenty wielostronicowe](../../mfc/multipage-documents.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CPrintInfo`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="getfrompage"></a>CPrintInfo::GetFromPage  
 Wywołanie tej funkcji można pobrać numer pierwszej strony ma być drukowana.  
  
```  
UINT GetFromPage() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer pierwszej strony ma być drukowana.  
  
### <a name="remarks"></a>Uwagi  
 Jest to wartość określoną przez użytkownika w oknie dialogowym drukowania i jest on przechowywany w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego. Jeśli użytkownik nie określił wartości, wartość domyślna to na pierwszej stronie dokumentu.  
  
##  <a name="getmaxpage"></a>CPrintInfo::GetMaxPage  
 Wywołanie tej funkcji można pobrać numer ostatniej strony dokumentu.  
  
```  
UINT GetMaxPage() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer ostatniej strony dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest przechowywana w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego.  
  
##  <a name="getminpage"></a>CPrintInfo::GetMinPage  
 Wywołanie tej funkcji, aby pobrać liczbę na pierwszej stronie dokumentu.  
  
```  
UINT GetMinPage() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer pierwszej strony dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest przechowywana w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego.  
  
##  <a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage  
 Wywołanie tej funkcji można pobrać przesunięcie podczas drukowania wielu elementów DocObject DocObject klienta.  
  
```  
UINT GetOffsetPage() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba stron poprzedzających na pierwszej stronie elementu DocObject drukowanie w scalonej DocObject zadania drukowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość odwołuje się do niego **m_nOffsetPage** elementu członkowskiego. Na pierwszej stronie dokumentu będą miały **m_nOffsetPage** wartość + 1 po wydrukowaniu jako DocObject z innych dokumentów aktywnych. **M_nOffsetPage** elementu członkowskiego jest prawidłowa tylko wtedy, gdy **m_bDocObject** wartość jest **TRUE**.  
  
##  <a name="gettopage"></a>CPrintInfo::GetToPage  
 Wywołanie tej funkcji można pobrać numer ostatniej strony ma być drukowana.  
  
```  
UINT GetToPage() const;

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer ostatniej strony ma być drukowana.  
  
### <a name="remarks"></a>Uwagi  
 Jest to wartość określoną przez użytkownika w oknie dialogowym drukowania i jest on przechowywany w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego. Jeśli użytkownik nie określił wartości, wartość domyślna to na ostatniej stronie dokumentu.  
  
##  <a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting  
 Zawiera nieobsługiwaną flagę wskazującą, czy w ramach powinno być kontynuowane wydruku pętli.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli przeprowadzasz podział na strony godzina drukowania, można ustawić tego elementu członkowskiego **FALSE** w zastąpienia z `CView::OnPrepareDC` po osiągnięto koniec dokumentu. Nie masz do zmodyfikowania tej zmiennej, jeśli określono długość dokumentu na początku zadania drukowania za pomocą polecenia `SetMaxPage` funkcję elementu członkowskiego. `m_bContinuePrinting` Element członkowski jest publiczny zmiennej typu **BOOL**.  
  
##  <a name="m_bdirect"></a>CPrintInfo::m_bDirect  
 Platformę ustawia ten element członkowski **TRUE** Jeśli okno dialogowe Drukuj będzie pomijana dla funkcji drukowania bezpośredniego; **FALSE** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Okno dialogowe drukowania pomijana jest zwykle podczas drukowania z poziomu powłoki lub gdy jest wykonywane drukowanie za pomocą Identyfikatora polecenia **ID_FILE_PRINT_DIRECT**.  
  
 Należy zwykle nie należy zmieniać tego elementu członkowskiego, ale w przypadku zmiany, zmienić przed wywołania [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) w zastąpienia z [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="m_bdocobject"></a>CPrintInfo::m_bDocObject  
 Zawiera nieobsługiwaną flagę wskazującą, czy drukowany dokument jest DocObject.  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie danych `m_dwFlags` i **m_nOffsetPage** są nieprawidłowe, jeśli ta flaga jest **TRUE**.  
  
##  <a name="m_bpreview"></a>CPrintInfo::m_bPreview  
 Zawiera nieobsługiwaną flagę wskazującą, czy jest przeglądany dokument.  
  
### <a name="remarks"></a>Uwagi  
 Zostało to określone przez platformę, w zależności od tego, które jest wykonywane polecenie użytkownika. Podgląd wydruku zadania nie zostanie wyświetlone okno dialogowe drukowania. **M_bPreview** element członkowski jest publiczny zmiennej typu **BOOL**.  
  
##  <a name="m_dwflags"></a>CPrintInfo::m_dwFlags  
 Zawiera kombinacją flag określając DocObject operacji drukowania.  
  
### <a name="remarks"></a>Uwagi  
 Prawidłowe tylko wtedy, gdy element członkowski danych **m_bDocObject** jest **TRUE**.  
  
 Flagi może być co najmniej jeden z następujących wartości:  
  
- **PRINTFLAG_MAYBOTHERUSER**  
  
- **PRINTFLAG_PROMPTUSER**  
  
- **PRINTFLAG_USERMAYCHANGEPRINTER**  
  
- **PRINTFLAG_RECOMPOSETODEVICE**  
  
- **PRINTFLAG_DONTACTUALLYPRINT**  
  
- **PRINTFLAG_FORCEPROPERTIES**  
  
- **PRINTFLAG_PRINTTOFILE**  
  
##  <a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData  
 Zawiera wskaźnik do struktury utworzonych przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Możesz użyć tego, aby przechowywać dane dotyczące drukowania, które chcesz przechowywać w klasie widoku. **M_lpUserData** element członkowski jest publiczny zmiennej typu **LPVoid —**.  
  
##  <a name="m_ncurpage"></a>CPrintInfo::m_nCurPage  
 Zawiera numer bieżącej strony.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania framework `CView::OnPrepareDC` i `CView::OnPrint` raz dla każdej strony dokumentu, określając inną wartość dla tego elementu członkowskiego w każdym; jego wartości należeć do zakresu od wartości zwróconej przez `GetFromPage` do zwróconą przez `GetToPage`. Użyj tego elementu członkowskiego w Twojej przesłonięcia `CView::OnPrepareDC` i `CView::OnPrint` Aby wydrukować stronę określonego dokumentu.  
  
 Podczas pierwszego wywołania trybu podglądu, platformę odczytuje wartość tego elementu członkowskiego, aby określić strony, która dokumentu należy wyświetlić podgląd początkowo. Można ustawić wartość tego elementu członkowskiego w zastąpienia z `CView::OnPreparePrinting` do zachowania użytkownika bieżącego położenia w dokumencie, wprowadzając trybu podglądu. `m_nCurPage` Element członkowski jest publiczny zmiennej typu **UINT**.  
  
##  <a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber  
 Określa liczbę zadań przypisywane przez system operacyjny dla bieżącego zadania drukowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość może być **SP_ERROR** Jeśli jeszcze nie wydrukowane zadania (to znaczy, jeśli `CPrintInfo` obiektu jest nowo utworzony i jeszcze nie został użyty do drukowania), lub jeśli wystąpił błąd podczas uruchamiania zadania.  
  
##  <a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages  
 Liczba stron wyświetlanych w wersji zapoznawczej; można go 1 lub 2.  
  
### <a name="remarks"></a>Uwagi  
 **M_nNumPreviewPages** element członkowski jest publiczny zmiennej typu **UINT**.  
  
##  <a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage  
 Zawiera liczbę stron poprzedzających na pierwszej stronie DocObject określonego w scalonej DocObject zadania drukowania.  
  
##  <a name="m_ppd"></a>CPrintInfo::m_pPD  
 Zawiera wskaźnik do `CPrintDialog` obiekt używany do wyświetlenia okna dialogowego drukowania w zadaniu drukowania.  
  
### <a name="remarks"></a>Uwagi  
 `m_pPD` Element członkowski jest zadeklarowany jako wskaźnik do zmiennej publicznej `CPrintDialog`.  
  
##  <a name="m_rectdraw"></a>CPrintInfo::m_rectDraw  
 Określa powierzchnia użytkowa rysowania strony we współrzędnych logiczne.  
  
### <a name="remarks"></a>Uwagi  
 Możesz odwoływać się do tego w zastąpienia z `CView::OnPrint`. Ten element służy do śledzenia co pozostaje można używać po wydrukowaniu nagłówków, stopek i tak dalej. **M_rectDraw** element członkowski jest publiczny zmiennej typu `CRect`.  
  
##  <a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc  
 Zawiera ciąg formatu używany do wyświetlania numerów stron podczas podglądu wydruku; Ten ciąg składa się z dwóch podciągów, jeden dla pojedynczej strony i jeden do wyświetlenia strony o podwójnej precyzji, każdy zakończony znakiem "\n".  
  
### <a name="remarks"></a>Uwagi  
 Platformę używa "Strony %u\nPages % u-%u\n" jako wartości domyślnej. Jeśli ma inny format numerów stron, określ ciąg formatu w zastąpienia z `CView::OnPreparePrinting`. **M_strPageDesc** element członkowski jest publiczny zmiennej typu `CString`.  
  
##  <a name="setmaxpage"></a>CPrintInfo::SetMaxPage  
 Wywołanie tej funkcji, aby określić numer ostatniej strony dokumentu.  
  
```  
void SetMaxPage(UINT nMaxPage);
```  
  
### <a name="parameters"></a>Parametry  
 *nMaxPage*  
 Numer ostatniej strony dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest przechowywana w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego. Jeśli długość dokumentu jest znana przed wydrukowaniem, wywołania tej funkcji z zastąpienia z `CView::OnPreparePrinting`. Jeśli długość dokumentu zależy od ustawienia określone przez użytkownika w oknie dialogowym drukowania, wywołania tej funkcji z zastąpienia z `CView::OnBeginPrinting`. Jeśli długość dokumentu nie jest znany, przed wydrukowaniem, użyj `m_bContinuePrinting` elementu członkowskiego do kontrolowania wydruku pętli.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="setminpage"></a>CPrintInfo::SetMinPage  
 Wywołanie tej funkcji, aby określić numer pierwszej strony dokumentu.  
  
```  
void SetMinPage(UINT nMinPage);
```  
  
### <a name="parameters"></a>Parametry  
 *nMinPage*  
 Numer pierwszej strony dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Numery strony zazwyczaj są liczone od 1. Ta wartość jest przechowywana w `CPrintDialog` zawiera odwołanie do obiektu `m_pPD` elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)   
 [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)   
 [CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)   
 [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)   
 [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)   
 [CView::OnPrint](../../mfc/reference/cview-class.md#onprint)



