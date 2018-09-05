---
title: Klasa CPropertyPage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
dev_langs:
- C++
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 632e8c0039dc0cac35fe46cff1fc539e534f8e20
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757513"
---
# <a name="cpropertypage-class"></a>Cpropertypage — klasa
Przedstawia pojedyncze strony arkusza właściwości, znane również jako zakładki okna dialogowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPropertyPage : public CDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropertyPage::CPropertyPage](#cpropertypage)|Konstruuje `CPropertyPage` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropertyPage::CancelToClose](#canceltoclose)|Zmienia przycisk OK, aby odczytać Zamknij i wyłącza przycisk Anuluj, po zmianie nieodwracalny, na stronie modalny arkusz właściwości.|  
|[CPropertyPage::Construct](#construct)|Konstruuje `CPropertyPage` obiektu. Użyj `Construct` czy chcesz określić parametry w czasie wykonywania, czy używasz tablic.|  
|[CPropertyPage::GetPSP](#getpsp)|Pobiera Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) struktury skojarzone z `CPropertyPage` obiektu.|  
|[CPropertyPage::OnApply](#onapply)|Wywoływane przez platformę, gdy kliknięto przycisk Zastosuj teraz.|  
|[CPropertyPage::OnCancel](#oncancel)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj.|  
|[CPropertyPage::OnKillActive](#onkillactive)|Wywoływane przez platformę, gdy bieżąca strona nie jest już stroną aktywną. Wykonaj sprawdzanie poprawności danych w tym miejscu.|  
|[CPropertyPage::OnOK](#onok)|Wywoływane przez platformę, gdy kliknięto OK, Zastosuj teraz lub przycisk Zamknij.|  
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj i przed anulowanie.|  
|[CPropertyPage::OnReset](#onreset)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj.|  
|[CPropertyPage::OnSetActive](#onsetactive)|Wywoływane przez platformę, gdy strona staje się stroną aktywną.|  
|[CPropertyPage::OnWizardBack](#onwizardback)|Wywoływane przez platformę, gdy kliknięto przycisk Wróć w czasie korzystania z arkusza właściwości typu Kreator.|  
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Wywoływane przez platformę, gdy kliknięto przycisk Zakończ w czasie korzystania z arkusza właściwości typu Kreator.|  
|[CPropertyPage::OnWizardNext](#onwizardnext)|Wywoływane przez platformę, gdy kliknięto przycisk Następny w czasie korzystania z arkusza właściwości typu Kreator.|  
|[CPropertyPage::QuerySiblings](#querysiblings)|Przekazuje komunikat do każdej strony arkusza właściwości.|  
|[CPropertyPage::SetModified](#setmodified)|Wywołanie, aby aktywować lub dezaktywować przycisk Zastosuj teraz.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) struktury. Zapewnia dostęp do właściwości podstawowe parametry strony.|  
  
## <a name="remarks"></a>Uwagi  
 Jak za pomocą standardowych oknach dialogowych, należy wyprowadzić klasę z `CPropertyPage` dla każdej strony w arkuszu właściwości. Aby użyć `CPropertyPage`-obiektów pochodnych, należy najpierw utworzyć [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) obiektu, a następnie utwórz obiekt, dla każdej strony, który znajduje się w arkuszu właściwości. Wywołaj [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) dla każdej strony w arkuszu, a następnie wyświetlić arkusz właściwości, wywołując [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) dla modalny arkusz właściwości, lub [CPropertySheet:: Utwórz](../../mfc/reference/cpropertysheet-class.md#create) dla niemodalnego arkusza właściwości.  
  
 Można utworzyć typu zakładki okna dialogowego o nazwie Kreator, który składa się z arkusza właściwości, za pomocą sekwencji stron właściwości, które prowadzą użytkownika przez kroki operacji, takich jak Konfigurowanie urządzenia lub tworzenia biuletynu. W oknie dialogowym kartę Typ kreatora na stronach właściwości nie ma karty, a tylko jedną właściwość strona jest widoczna w danym momencie. Dodatkowo zamiast OK, Zastosuj teraz przyciski, typ kreatora zakładki okna dialogowego posiada przycisku Wstecz, przycisk Dalej albo Zakończ i przycisk Anuluj.  
  
 Aby uzyskać więcej informacji na temat ustanawiania arkusz właściwości jako kreatora, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Aby uzyskać więcej informacji na temat korzystania z `CPropertyPage` obiektów, zobacz artykuł [arkusze właściwości i strony właściwości](../../mfc/property-sheets-and-property-pages-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="canceltoclose"></a>  CPropertyPage::CancelToClose  
 Wywołaj tę funkcję, po dokonaniu zmiany nieodwracalny, do danych na stronie modalny arkusz właściwości.  
  
```  
void CancelToClose();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja będzie zmiana przycisku OK na zamknięcie i wyłączyć przycisk Anuluj. Ta zmiana alerty, których nie można anulować użytkownika, że zmiana jest trwałe i modyfikacji.  
  
 `CancelToClose` Funkcji składowej nie wykonuje żadnych czynności w niemodalnego arkusza właściwości, ponieważ domyślnie niemodalnego arkusza właściwości nie ma przycisk Anuluj.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertyPage::QuerySiblings](#querysiblings).  
  
##  <a name="construct"></a>  CPropertyPage::Construct  
 Wywołaj tę funkcję elementu członkowskiego do konstruowania `CPropertyPage` obiektu.  
  
```  
void Construct(
    UINT nIDTemplate,  
    UINT nIDCaption = 0);

 
void Construct(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption = 0);

 
void Construct(
    UINT nIDTemplate,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0);

 
void Construct(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDTemplate*  
 Identyfikator szablonu użytego dla tej strony.  
  
 *nIDCaption*  
 Identyfikator nazwy mają być umieszczone w karcie tej strony. Jeśli jest to 0, nazwy będą pobierane z szablonu okna dialogowego na tej stronie.  
  
 *lpszTemplateName*  
 Zawiera ciąg zakończony znakiem null, nazwę zasobu szablon.  
  
 *nIDHeaderTitle*  
 Identyfikator nazwy należy umieścić w lokalizacji tytuł właściwości nagłówka strony. Domyślnie 0.  
  
 *nIDHeaderSubTitle*  
 Identyfikator nazwy należy umieścić w lokalizacji napisów właściwości nagłówka strony. Domyślnie 0.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt jest wyświetlany po są spełnione wszystkie następujące warunki:  
  
-   Strona została dodana do arkusza właściwości przy użyciu [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   Arkusz właściwości [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) lub [Utwórz](../../mfc/reference/cpropertysheet-class.md#create) funkcja została wywołana.  
  
-   Użytkownik wybrał (z kartami na) na tej stronie.  
  
 Wywołaj `Construct` Jeśli jeden z innych Konstruktory klasy nie została wywołana. `Construct` Funkcja członkowska jest elastyczny, ponieważ jest pusta instrukcja parametrów, a następnie określić wiele parametrów i konstrukcji, w dowolnym momencie w kodzie.  
  
 Należy użyć `Construct` podczas pracy z tablicami i należy wywołać `Construct` dla każdego elementu członkowskiego tablicy, aby elementy członkowskie danych są przypisywane odpowiednimi wartościami.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]  
  
##  <a name="cpropertypage"></a>  CPropertyPage::CPropertyPage  
 Konstruuje `CPropertyPage` obiektu.  
  
```  
CPropertyPage();

 
explicit CPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
explicit CPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
CPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
CPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```  
  
### <a name="parameters"></a>Parametry  
 *nIDTemplate*  
 Identyfikator szablonu użytego dla tej strony.  
  
 *nIDCaption*  
 Identyfikator nazwy mają być umieszczone w karcie tej strony. Jeśli jest to 0, nazwy będą pobierane z szablonu okna dialogowego na tej stronie.  
  
 *niezerowego*  
 *lpszTemplateName*  
 Wskazuje ciąg zawierający nazwę szablonu dla tej strony. Nie może mieć wartości NULL.  
  
 *nIDHeaderTitle*  
 Identyfikator nazwy należy umieścić w lokalizacji tytuł właściwości nagłówka strony.  
  
 *nIDHeaderSubTitle*  
 Identyfikator nazwy należy umieścić w lokalizacji napisów właściwości nagłówka strony.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt jest wyświetlany po są spełnione wszystkie następujące warunki:  
  
-   Strona została dodana do arkusza właściwości przy użyciu [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   Arkusz właściwości [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) lub [Utwórz](../../mfc/reference/cpropertysheet-class.md#create) funkcja została wywołana.  
  
-   Użytkownik wybrał (z kartami na) na tej stronie.  
  
 Jeśli masz wiele parametrów (na przykład, jeśli używasz tablicy), użyj [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) zamiast `CPropertyPage`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]  
  
##  <a name="getpsp"></a>  CPropertyPage::GetPSP  
 Pobiera Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) struktury skojarzone z `CPropertyPage` obiektu.  
  
```  
const PROPSHEETPAGE& GetPSP() const;  
  
PROPSHEETPAGE& GetPSP();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `PROPSHEETPAGE` struktury.  
  
##  <a name="m_psp"></a>  CPropertyPage::m_psp  
 `m_psp` jest strukturą, której członkowie przechowywania charakterystyki [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2).  
  
```  
PROPSHEETPAGE m_psp;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby zainicjować wygląd strony właściwości po jest tworzony, należy użyć tej struktury.  
  
 Aby uzyskać więcej informacji na temat tej struktury, w tym listę swoich elementów członkowskich, zobacz `PROPSHEETPAGE` w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]  
  
##  <a name="onapply"></a>  CPropertyPage::OnApply  
 Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik wybierze przycisk Zastosuj teraz lub OK.  
  
```  
virtual BOOL OnApply();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zmiany są akceptowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Gdy struktura wywołuje tę funkcję, zmiany wprowadzone na wszystkich stronach właściwości arkusza właściwości są akceptowane, arkusz właściwości zachowuje fokus, a `OnApply` zwraca wartość TRUE (wartość 1). Przed `OnApply` mogą być wywoływane przez platformę, musi być wywołana [SetModified](#setmodified) i jego parametr jest ustawiony na wartość TRUE. To uaktywni przycisk Zastosuj teraz, jak najszybciej po użytkownik wprowadza zmianę na stronie właściwości.  
  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić, jakie działanie ma program, gdy użytkownik kliknie przycisk Zastosuj teraz. Podczas zastępowania, funkcja powinna zwrócić wartość TRUE, aby zaakceptować zmiany i wartość FALSE, aby uniemożliwić zmiany wpływają.  
  
 Domyślna implementacja klasy `OnApply` wywołania `OnOK`.  
  
 Aby uzyskać więcej informacji na temat komunikaty powiadomień wysłane, gdy użytkownik naciśnie Zastosuj teraz lub przycisk OK w arkuszu właściwości, zobacz [PSN_APPLY](/windows/desktop/Controls/psn-apply) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertyPage::OnOK](#onok).  
  
##  <a name="oncancel"></a>  CPropertyPage::OnCancel  
 Ta funkcja członkowska jest wywoływana przez platformę, po wybraniu przycisku Anuluj.  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby wykonać akcje przycisk Anuluj. Wartość domyślna neguje wszelkie zmiany, które zostały wprowadzone.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]  
  
##  <a name="onkillactive"></a>  CPropertyPage::OnKillActive  
 Ta funkcja członkowska jest wywoływana przez platformę, gdy strona nie jest już stroną aktywną.  
  
```  
virtual BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli dane zostały zaktualizowane pomyślnie, w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję elementu członkowskiego, aby wykonywać zadania sprawdzania poprawności danych specjalne.  
  
 Domyślna implementacja tej funkcji elementu członkowskiego kopiuje ustawienia z formantów na stronie właściwości do zmiennych na stronie właściwości. Jeśli dane nie zostały pomyślnie zaktualizowane z powodu błędu sprawdzania poprawności (DDV) danych okna dialogowego, strona zachowuje fokus.  
  
 Po tej funkcji elementu członkowskiego zwraca pomyślnie, w ramach będzie wywoływać strony [onok —](#onok) funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]  
  
##  <a name="onok"></a>  CPropertyPage::OnOK  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik wybierze przycisk Zastosuj teraz lub OK natychmiast po struktura wywołuje [onkillactive —](#onkillactive).  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik wybierze przycisk Zastosuj teraz lub OK, struktura odbiera [PSN_APPLY](/windows/desktop/Controls/psn-apply) powiadomień z poziomu strony właściwości. Wywołanie `OnOK` nie będzie mieć miejsce, gdy wywołujesz [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) ponieważ strona właściwości wysyłał powiadomienie w takiej sytuacji.  
  
 Zastąp tę funkcję elementu członkowskiego, aby zaimplementować dodatkowe zachowania specyficzne dla obecnie aktywnej strony po użytkownik odrzuci arkusza właściwości całego.  
  
 Domyślna implementacja tej funkcji elementu członkowskiego oznaczona jako "Wyczyść", aby odzwierciedlić, że dane zostały zaktualizowane w `OnKillActive` funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]  
  
##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Anuluj i przed Anuluj działanie miało miejsce.  
  
```  
virtual BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość FALSE, aby uniemożliwić operacji anulowania lub wartość PRAWDA, aby umożliwić mu.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić akcję podejmowaną po użytkownik kliknie przycisk Anuluj.  
  
 Domyślna implementacja klasy `OnQueryCancel` zwraca wartość TRUE.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]  
  
##  <a name="onreset"></a>  CPropertyPage::OnReset  
 Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik wybierze przycisk Anuluj.  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy struktura wywołuje tę funkcję, zmiany do wszystkich stron właściwości, które zostały wprowadzone przez użytkownika, wcześniej wybierając przycisk Zastosuj teraz zostaną odrzucone i arkusza właściwości zachowuje fokus.  
  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić, jakie działanie ma program, gdy użytkownik kliknie przycisk Anuluj.  
  
 Domyślna implementacja klasy `OnReset` nic nie robi.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertyPage::OnCancel](#oncancel).  
  
##  <a name="onsetactive"></a>  CPropertyPage::OnSetActive  
 Ta funkcja członkowska jest wywoływana przez platformę, gdy strona jest wybierany przez użytkownika i staje się stroną aktywną.  
  
```  
virtual BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli strona została pomyślnie active; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego do wykonywania zadań, gdy strona jest aktywna. Zastąpienie metody tej funkcji elementu członkowskiego wywoływałby zazwyczaj domyślna wersja po zaktualizowaniu składowe danych, aby zezwalała na aktualizowanie formantów strony z nowymi danymi.  
  
 Domyślna implementacja tworzy okno dla tej strony, w przeciwnym razie utworzone wcześniej i sprawia, że się stroną aktywną.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).  
  
##  <a name="onwizardback"></a>  CPropertyPage::OnWizardBack  
 Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Wstecz w kreatorze.  
  
```  
virtual LRESULT OnWizardBack();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 0, aby automatycznie przejść do następnej strony; -1, aby uniemożliwić zmianę na stronie. Aby przejść do strony inne niż kolejny, zwróć identyfikator okna dialogowego, które mają być wyświetlane.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić niektóre akcje, które użytkownik musi wykonać po naciśnięciu przycisku Wstecz.  
  
 Aby uzyskać więcej informacji na temat sposobu wykonywania arkusza właściwości typu Kreator, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]  
  
##  <a name="onwizardfinish"></a>  CPropertyPage::OnWizardFinish  
 Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Zakończ, w kreatorze.  
  
```  
virtual BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli arkusz właściwości jest niszczony, kiedy Kreator zakończy pracę; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Kiedy użytkownik kliknie **Zakończ** przycisku w kreatorze, struktura wywołuje tę funkcję; gdy `OnWizardFinish` zwraca wartość TRUE (wartość różną od zera), arkusz właściwości może zostać zniszczone (ale nie jest faktycznie niszczony). Wywołaj `DestroyWindow` zniszczyć arkusza właściwości. Nie wywołuj `DestroyWindow` z `OnWizardFinish`; spowodowałoby uszkodzenie sterty lub inne błędy.  
  
 Można zastąpić, ta funkcja elementu członkowskiego, aby określić niektóre akcje, które użytkownik musi wykonać po naciśnięciu przycisku Zakończ. Podczas zastępowania tej funkcji, zwraca wartość FALSE, aby uniemożliwić niszczone arkusza właściwości.  
  
 Aby uzyskać więcej informacji na temat komunikaty powiadomień wysłane, gdy użytkownik naciśnie przycisk Zakończ w arkuszu właściwości kreatora, zobacz [PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat sposobu wykonywania arkusza właściwości typu Kreator, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]  
  
##  <a name="onwizardnext"></a>  CPropertyPage::OnWizardNext  
 Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Dalej w kreatorze.  
  
```  
virtual LRESULT OnWizardNext();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 0, aby automatycznie przejść do następnej strony; -1, aby uniemożliwić zmianę na stronie. Aby przejść do strony inne niż kolejny, zwróć identyfikator okna dialogowego, które mają być wyświetlane.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić niektóre akcje, które użytkownik musi wykonać, po kliknięciu przycisku Dalej.  
  
 Aby uzyskać więcej informacji na temat sposobu wykonywania arkusza właściwości typu Kreator, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]  
  
##  <a name="querysiblings"></a>  CPropertyPage::QuerySiblings  
 Wywołaj tę funkcję elementu członkowskiego do przesyłania dalej wiadomości do każdej strony w arkuszu właściwości.  
  
```  
LRESULT QuerySiblings(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 *wParam*  
 Określa dodatkowe informacje zależne od wiadomości.  
  
 *lParam*  
 Określa dodatkowe informacje zależne od wiadomości  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, ze strony w arkuszu właściwości lub 0, jeśli wszystkie strony zwracają wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli strona zwraca wartość różną od zera, arkusz właściwości nie wysyła komunikat do kolejnych stron.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]  
  
##  <a name="setmodified"></a>  CPropertyPage::SetModified  
 Wywołaj tę funkcję elementu członkowskiego, aby włączyć lub wyłączyć przycisk Zastosuj teraz oparte na tego, czy ustawienia na stronie właściwości stosuje się do odpowiedniego obiektu zewnętrznego.  
  
```  
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bChanged*  
 Wartość TRUE, aby wskazać, że ustawienia strony właściwości zostały zmodyfikowane od czasu ostatniego one zostały zastosowane; FALSE, aby wskazać, że ustawienia strony właściwości zostały zastosowane lub mają być ignorowane.  
  
### <a name="remarks"></a>Uwagi  
 Struktura zapewnia śledzenia, które strony są "zanieczyszczony", oznacza to, strony właściwości, dla których mają o nazwie `SetModified( TRUE )`. Jeśli wywołasz będzie zawsze włączony przycisk Zastosuj teraz `SetModified( TRUE )` jednej strony. Przycisk Zastosuj teraz zostanie wyłączona po wywołaniu `SetModified( FALSE )` jednej strony, ale tylko wtedy, gdy żaden z innych stron jest "zakłóconych".  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL1 próbki MFC](../../visual-cpp-samples.md)   
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Próbki MFC PROPDLG](../../visual-cpp-samples.md)   
 [Próbki MFC SNAPVW](../../visual-cpp-samples.md)   
 [Cdialog — klasa](../../mfc/reference/cdialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cpropertysheet — klasa](../../mfc/reference/cpropertysheet-class.md)   
 [Klasa CDialog](../../mfc/reference/cdialog-class.md)
