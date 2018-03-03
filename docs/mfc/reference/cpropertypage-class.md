---
title: "Cpropertypage — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c42a0ba40797312a2108a288fecdea55c6873f3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cpropertypage-class"></a>Cpropertypage — klasa
Reprezentuje poszczególnych stron arkusza właściwości, znanej także jako okno dialogowe kartę.  
  
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
|[CPropertyPage::CancelToClose](#canceltoclose)|Zmienia przycisk OK, aby odczytać Zamknij i wyłącza przycisk Anuluj, po zmianie nieodwracalny na stronie modalny arkusz właściwości.|  
|[CPropertyPage::Construct](#construct)|Konstruuje `CPropertyPage` obiektu. Użyj `Construct` Jeśli chcesz określić parametry w czasie wykonywania, lub jeśli używasz tablic.|  
|[CPropertyPage::GetPSP](#getpsp)|Pobiera systemu Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) struktury skojarzone z `CPropertyPage` obiektu.|  
|[CPropertyPage::OnApply](#onapply)|Wywoływane przez platformę, gdy kliknięto przycisk Zastosuj teraz.|  
|[CPropertyPage::OnCancel](#oncancel)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj.|  
|[CPropertyPage::OnKillActive](#onkillactive)|Wywoływane przez platformę, gdy bieżąca strona nie jest już stroną aktywną. Wykonaj sprawdzanie poprawności danych w tym miejscu.|  
|[CPropertyPage::OnOK](#onok)|Wywoływane przez platformę, gdy zostanie kliknięty OK, Zastosuj teraz lub przycisk Zamknij.|  
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj i zanim akcja została anulowana.|  
|[CPropertyPage::OnReset](#onreset)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj.|  
|[CPropertyPage::OnSetActive](#onsetactive)|Wywoływane przez platformę, gdy strona staje się stroną aktywną.|  
|[CPropertyPage::OnWizardBack](#onwizardback)|Wywoływane przez platformę, gdy kliknięto przycisk Wstecz w czasie korzystania z arkusza właściwości typu Kreator.|  
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Wywoływane przez platformę, po kliknięciu przycisku Zakończ podczas korzystania z arkusza właściwości typu Kreator.|  
|[CPropertyPage::OnWizardNext](#onwizardnext)|Wywoływane przez platformę, gdy kliknięto przycisk Następny w czasie korzystania z arkusza właściwości typu Kreator.|  
|[CPropertyPage::QuerySiblings](#querysiblings)|Przesyła wiadomość na każdej stronie arkusza właściwości.|  
|[CPropertyPage::SetModified](#setmodified)|Wywołanie aktywować lub dezaktywować przycisk Zastosuj teraz.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) struktury. Zapewnia dostęp do parametrów strony właściwości podstawowych.|  
  
## <a name="remarks"></a>Uwagi  
 Zgodnie z polami standardowe okno dialogowe wyprowadzenia klasy z `CPropertyPage` dla każdej strony w arkuszu właściwości. Aby użyć `CPropertyPage`-obiekty pochodne, najpierw utwórz [cpropertysheet —](../../mfc/reference/cpropertysheet-class.md) obiekt, a następnie utwórz obiekt dla każdej strony, który jest przesyłany w arkuszu właściwości. Wywołanie [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) dla każdej strony w arkuszu, a następnie Wyświetl arkusz właściwości, wywołując [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) dla modalny arkusz właściwości, lub [cpropertysheet —:: Utwórz](../../mfc/reference/cpropertysheet-class.md#create) dla niemodalnego arkusza właściwości.  
  
 Można utworzyć typu o nazwie kreatora, który składa się z arkusza właściwości z sekwencją strony właściwości, które prowadzą użytkownika przez kroki operacji, takich jak Konfigurowanie urządzenia lub tworzenia biuletynu okno dialogowe kartę. W oknie dialogowym kartę typu Kreator strony właściwości nie ma karty, a tylko jedna właściwość strona jest widoczna w czasie. Ponadto zamiast przyciski OK i Zastosuj teraz okno dialogowe Kreator typ ma przycisk Wstecz, przycisku Dalej lub Zakończ i przycisk Anuluj.  
  
 Aby uzyskać więcej informacji na ustanawianie arkusz właściwości jako kreatora, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Aby uzyskać więcej informacji na temat używania `CPropertyPage` obiektów, zobacz artykuł [arkusze właściwości i strony właściwości](../../mfc/property-sheets-and-property-pages-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="canceltoclose"></a>CPropertyPage::CancelToClose  
 Wywołanie tej funkcji po dokonaniu zmiany odzyskać danych na stronie modalny arkusz właściwości.  
  
```  
void CancelToClose();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja będzie zmiana na zamknięcie przycisk OK i wyłącza przycisk Anuluj. Ta zmiana alertów, które nie może być anulowana użytkownika, że zmiana jest trwałe i modyfikacji.  
  
 `CancelToClose` Funkcji członkowskiej nie działa w niemodalnego arkusza właściwości, ponieważ domyślnie niemodalnego arkusza właściwości nie ma przycisku Anuluj.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertyPage::QuerySiblings](#querysiblings).  
  
##  <a name="construct"></a>CPropertyPage::Construct  
 Wywołanie tej funkcji Członkowskich do skonstruowania `CPropertyPage` obiektu.  
  
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
 `nIDTemplate`  
 Identyfikator szablonu używany dla tej strony.  
  
 `nIDCaption`  
 Identyfikator nazwy na umieszczenie w karcie tej strony. Jeśli jest to 0, nazwę zostaną pobrane z szablonu okna dialogowego dla tej strony.  
  
 `lpszTemplateName`  
 Zawiera zerem ciąg określający nazwę zasobu szablon.  
  
 `nIDHeaderTitle`  
 Identyfikator nazwy na umieszczenie w lokalizacji tytuł właściwości nagłówka strony. Domyślnie 0.  
  
 `nIDHeaderSubTitle`  
 Identyfikator nazwy na umieszczenie w lokalizacji podtytuł właściwości nagłówka strony. Domyślnie 0.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt jest wyświetlany po są spełnione wszystkie następujące warunki:  
  
-   Strona został dodany do arkusza właściwości przy użyciu [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   Arkusz właściwości [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) lub [Utwórz](../../mfc/reference/cpropertysheet-class.md#create) funkcja została wywołana.  
  
-   Użytkownik wybrał (z kartami na) tej strony.  
  
 Wywołanie **skonstruować** Jeśli jeden z innych konstruktorów klasy nie została wywołana. `Construct` Funkcja członkowska jest elastyczna, ponieważ można jest pusta instrukcja parametrów, a następnie określ wiele parametrów i konstrukcji w dowolnym momencie w kodzie.  
  
 Należy użyć `Construct` podczas pracy z tablicami i należy wywołać **skonstruować** dla każdego elementu członkowskiego tablicy, tak aby elementy członkowskie danych przypisano odpowiednie wartości.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]  
  
##  <a name="cpropertypage"></a>CPropertyPage::CPropertyPage  
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
 `nIDTemplate`  
 Identyfikator szablonu używany dla tej strony.  
  
 `nIDCaption`  
 Identyfikator nazwy na umieszczenie w karcie tej strony. Jeśli jest to 0, nazwę zostaną pobrane z szablonu okna dialogowego dla tej strony.  
  
 `dwSize`  
 `lpszTemplateName`  
 Wskazuje ciąg zawierający nazwę szablonu dla tej strony. Nie może być **NULL**.  
  
 `nIDHeaderTitle`  
 Identyfikator nazwy na umieszczenie w lokalizacji tytuł właściwości nagłówka strony.  
  
 `nIDHeaderSubTitle`  
 Identyfikator nazwy na umieszczenie w lokalizacji podtytuł właściwości nagłówka strony.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt jest wyświetlany po są spełnione wszystkie następujące warunki:  
  
-   Strona został dodany do arkusza właściwości przy użyciu [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   Arkusz właściwości [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) lub [Utwórz](../../mfc/reference/cpropertysheet-class.md#create) funkcja została wywołana.  
  
-   Użytkownik wybrał (z kartami na) tej strony.  
  
 Jeśli masz wiele parametrów (na przykład, jeśli używasz tablicy), użyj [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) zamiast `CPropertyPage`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]  
  
##  <a name="getpsp"></a>CPropertyPage::GetPSP  
 Pobiera systemu Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) struktury skojarzone z `CPropertyPage` obiektu.  
  
```  
const PROPSHEETPAGE& GetPSP() const;  
  
PROPSHEETPAGE& GetPSP();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do **PROPSHEETPAGE** struktury.  
  
##  <a name="m_psp"></a>CPropertyPage::m_psp  
 `m_psp`jest strukturą, której członkowie przechowywania właściwości [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548).  
  
```  
PROPSHEETPAGE m_psp;  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby zainicjować wyglądu strony właściwości po go jest tworzony, należy użyć tej struktury.  
  
 Więcej informacji dotyczących tej struktury, w tym listę jej członków, zobacz **PROPSHEETPAGE** w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]  
  
##  <a name="onapply"></a>CPropertyPage::OnApply  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik wybierze przycisk Zastosuj teraz lub OK.  
  
```  
virtual BOOL OnApply();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zmiany są akceptowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Gdy struktura wywołuje tę funkcję, zmiany wprowadzone na wszystkie strony właściwości w arkuszu właściwości są akceptowane, arkusz właściwości zachowuje fokus, i `OnApply` zwraca **TRUE** (wartość 1). Przed `OnApply` mogą być wywoływane przez platformę, musi być wywołana [SetModified](#setmodified) i ustawić jej parametr **TRUE**. Uaktywni przycisk Zastosuj teraz jak użytkownik dokona zmian na stronie właściwości.  
  
 Przesłonić tę funkcję elementu członkowskiego, aby określić, jakie działanie ma programu, gdy użytkownik kliknie przycisk Zastosuj teraz. Podczas zastępowania, funkcja powinna zwrócić **TRUE** celu zaakceptowania zmian i **FALSE** uniemożliwić podjęcie wpływu zmiany.  
  
 Domyślna implementacja `OnApply` wywołania `OnOK`.  
  
 Aby uzyskać więcej informacji na temat komunikaty powiadomień wysłane, gdy użytkownik naciśnie Zastosuj teraz lub przycisk OK w arkuszu właściwości, zobacz [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertyPage::OnOK](#onok).  
  
##  <a name="oncancel"></a>CPropertyPage::OnCancel  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, po wybraniu przycisku Anuluj.  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego do wykonania akcji przycisk Anuluj. Wartość domyślna Negacja wszelkie zmiany, które zostały wprowadzone.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]  
  
##  <a name="onkillactive"></a>CPropertyPage::OnKillActive  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy strona nie jest już aktywna strona.  
  
```  
virtual BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dane zostały zaktualizowane pomyślnie, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego do wykonywania zadań weryfikacji danych specjalne.  
  
 Domyślna implementacja funkcji członkowskiej kopiuje ustawienia z kontrolki na stronie właściwości ze zmiennymi Członkowskimi strony właściwości. Jeśli dane nie zostały zaktualizowane pomyślnie z powodu błędu sprawdzania poprawności (DDV) danych okna dialogowego, strona zachowuje fokus.  
  
 Po tej funkcji Członkowskich zwraca pomyślnie, platforma wywoła strony [OnOK](#onok) funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]  
  
##  <a name="onok"></a>CPropertyPage::OnOK  
 Ta funkcja członkowska jest wywoływane przez platformę, gdy użytkownik wybierze przycisk Zastosuj teraz lub OK natychmiast po wywołania framework [OnKillActive](#onkillactive).  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik wybierze przycisk Zastosuj teraz lub OK, otrzymuje platformę [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) powiadomienia na stronie właściwości. Wywołanie `OnOK` nie będzie mieć miejsce, gdy należy wywołać [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) ponieważ stronę właściwości nie wysyła powiadomienia w takiej sytuacji.  
  
 Przesłonić tę funkcję elementu członkowskiego do zaimplementowania dodatkowe zachowanie specyficzne dla aktualnie aktywnej strony, gdy użytkownik odrzuci arkusz właściwości całego.  
  
 Domyślna implementacja funkcji członkowskiej oznaczona jako "clean", aby odzwierciedlić, że dane zostały zaktualizowane w `OnKillActive` funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]  
  
##  <a name="onquerycancel"></a>CPropertyPage::OnQueryCancel  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Anuluj i przed Anuluj działanie miało miejsce.  
  
```  
virtual BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **FALSE** Anuluj operację lub wartość TRUE, aby umożliwić jego.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby określić akcję podejmowaną po kliknięciu przycisku Anuluj.  
  
 Domyślna implementacja `OnQueryCancel` zwraca **TRUE**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]  
  
##  <a name="onreset"></a>CPropertyPage::OnReset  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik wybierze przycisk Anuluj.  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy struktura wywołuje tę funkcję, zmiany do wszystkich stron właściwości, które zostały dokonane przez użytkownika, wcześniej wybierając przycisk Zastosuj teraz zostaną odrzucone i arkusza właściwości zachowuje fokus.  
  
 Przesłonić tę funkcję elementu członkowskiego, aby określić, jakie działanie ma program, gdy użytkownik kliknie przycisk Anuluj.  
  
 Domyślna implementacja `OnReset` nie działają.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertyPage::OnCancel](#oncancel).  
  
##  <a name="onsetactive"></a>CPropertyPage::OnSetActive  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy strona jest wybierany przez użytkownika i staje się stroną aktywną.  
  
```  
virtual BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli strona została pomyślnie active; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego do wykonywania zadań, gdy strona jest aktywna. Zastąpienia funkcji członkowskiej zwykle spowodowałoby wywołanie wersja domyślna po zaktualizowaniu elementy członkowskie danych, aby zezwalała na aktualizowanie formantów strony przy użyciu nowych danych.  
  
 Domyślna implementacja tworzy okno strony, jeśli nie wcześniej utworzona i ułatwia aktywnej strony.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).  
  
##  <a name="onwizardback"></a>CPropertyPage::OnWizardBack  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Wstecz w kreatorze.  
  
```  
virtual LRESULT OnWizardBack();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 0, aby automatycznie przejść do następnej strony; -1, aby uniemożliwić zmianę strony. Aby przejść do strony innego niż dalej, zwróć identyfikatora wyświetlania okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby określić niektóre akcje, które musi wykonać użytkownik po naciśnięciu przycisku Wstecz.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia arkusza właściwości typu Kreator, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]  
  
##  <a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Zakończ w kreatorze.  
  
```  
virtual BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli arkusz właściwości jest niszczony po zakończeniu pracy Kreatora; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik kliknie **Zakończ** przycisk w ramach kreatora, wywołania tej funkcji; gdy `OnWizardFinish` zwraca **TRUE** (wartość niezerową), może zostać zniszczone arkusza właściwości (ale nie jest rzeczywiście zniszczone). Wywołanie `DestroyWindow` do zniszczenia arkusza właściwości. Nie wywołuj `DestroyWindow` z `OnWizardFinish`; spowodowałoby uszkodzenie stosu lub inne błędy.  
  
 Można zastąpić tę funkcję elementu członkowskiego, aby określić niektóre akcje, które musi wykonać użytkownik, po kliknięciu przycisku Zakończ. W przypadku przesłaniania tej funkcji, zwracany **FALSE** aby zapobiec niszczony arkusza właściwości.  
  
 Aby uzyskać więcej informacji na temat komunikaty powiadomień wysłane, gdy użytkownik naciśnie przycisk Zakończ w arkuszu właściwości kreatora, zobacz [PSN_WIZFINISH](http://msdn.microsoft.com/library/windows/desktop/bb774571) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia arkusza właściwości typu Kreator, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]  
  
##  <a name="onwizardnext"></a>CPropertyPage::OnWizardNext  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Dalej w kreatorze.  
  
```  
virtual LRESULT OnWizardNext();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 0, aby automatycznie przejść do następnej strony; -1, aby uniemożliwić zmianę strony. Aby przejść do strony innego niż dalej, zwróć identyfikatora wyświetlania okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby określić niektóre akcje, które musi wykonać użytkownik po naciśnięciu przycisku Dalej.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia arkusza właściwości typu Kreator, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]  
  
##  <a name="querysiblings"></a>CPropertyPage::QuerySiblings  
 Wywołanie tej funkcji Członkowskich do przesyłania dalej wiadomości do każdej strony w arkuszu właściwości.  
  
```  
LRESULT QuerySiblings(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `wParam`  
 Określa dodatkowe informacje zależne od wiadomości.  
  
 `lParam`  
 Określa dodatkowe informacje zależne od wiadomości  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość niezerowa ze strony w arkuszu właściwości lub 0, jeśli wszystkie strony zwracają wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli strona zwróci wartość niezerową, arkusza właściwości nie wysyła komunikat do kolejnych stron.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]  
  
##  <a name="setmodified"></a>CPropertyPage::SetModified  
 Wywołanie tej funkcji Członkowskich, aby włączyć lub wyłączyć przycisk Zastosuj teraz według tego, czy do odpowiedniego obiektu zewnętrznego, w którym mają zostać zastosowane ustawienia na stronie właściwości.  
  
```  
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bChanged`  
 **Wartość TRUE,** wskazująca, że od czasu ostatniego zostały one zastosowane; zostały zmodyfikowane ustawienia strony właściwości **FALSE** wskazująca, czy ustawienia strony właściwości zostały zastosowane, lub należy ją ignorować.  
  
### <a name="remarks"></a>Uwagi  
 Platformę przechowuje ścieżki, które strony są "zakłóconych", oznacza to, strony właściwości, dla których wywołaniu **SetModified (PRAWDA)**. Jeśli wywołujesz będzie zawsze włączony przycisk Zastosuj teraz **SetModified (PRAWDA)** dla jednej strony. Przycisk Zastosuj teraz zostanie wyłączony podczas wywoływania **SetModified (FALSE)** dla jednej strony, ale tylko jeśli żaden z innych stron nie jest "zakłóconych".  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL1 próbki MFC](../../visual-cpp-samples.md)   
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Przykładowe MFC PROPDLG](../../visual-cpp-samples.md)   
 [Przykładowe MFC SNAPVW](../../visual-cpp-samples.md)   
 [Cdialog — klasa](../../mfc/reference/cdialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cpropertysheet — klasa](../../mfc/reference/cpropertysheet-class.md)   
 [Klasa CDialog](../../mfc/reference/cdialog-class.md)
