---
title: Klasa CSnapInPropertyPageImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd7f2c708dd3cfe63e40b62912a775fcc120c4ba
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223054"
---
# <a name="csnapinpropertypageimpl-class"></a>Klasa CSnapInPropertyPageImpl
Ta klasa dostarcza metody wykonywania obiekt strony właściwości przystawki.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
CSnapInPropertyPageImpl : public CDialogImplBase
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Zmienia stan **OK** i **anulować** przycisków.|  
|[CSnapInPropertyPageImpl::Create](#create)|Inicjuje nowo utworzony `CSnapInPropertyPageImpl` obiektu.|  
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Wywoływane przez platformę, gdy użytkownik kliknie **Zastosuj teraz** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Wywoływane przez platformę, gdy użytkownik kliknie **pomocy** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Wywoływane przez platformę, gdy bieżąca strona nie jest już aktywna.|  
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Wywoływane przez platformę, gdy użytkownik kliknie **anulować** przycisku i przed anulowanie.|  
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Wywoływane przez platformę, gdy użytkownik kliknie **resetowania** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Wywoływane przez platformę, gdy bieżąca strona stanie się aktywny.|  
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Wywoływane przez platformę, gdy użytkownik kliknie **ponownie** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Wywoływane przez platformę, gdy użytkownik kliknie **Zakończ** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Wywoływane przez platformę, gdy użytkownik kliknie **dalej** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Przekazuje bieżący komunikat do wszystkich stron w arkuszu właściwości.|  
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Wywołanie, aby aktywować lub dezaktywować **Zastosuj teraz** przycisku.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows `PROPSHEETPAGE` struktury używane przez `CSnapInPropertyPageImpl` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CSnapInPropertyPageImpl` udostępnia podstawową implementację obiektu strony właściwości przystawki. Podstawowe funkcje strony właściwości w przystawce są implementowane przy użyciu kilku różnych interfejsów i mapowania typów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsnap.h  
  
##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose  
 Wywołaj tę funkcję, po dokonaniu zmiany nieodwracalny, do danych na stronie modalny arkusz właściwości.  
  
```
void CancelToClose();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja ulegnie zmianie **OK** przycisk, aby **Zamknij** i Wyłącz **anulować** przycisku. Ta zmiana alerty, których nie można anulować użytkownika, że zmiana jest trwałe i modyfikacji.  
  
 `CancelToClose` Funkcji składowej nie wykonuje żadnych czynności w niemodalnego arkusza właściwości, ponieważ nie ma niemodalnego arkusza właściwości **anulować** przycisk domyślny.  
  
##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl  
 Konstruuje `CSnapInPropertyPageImpl` obiektu.  
  
```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszTitle*  
 [in] Tytuł strony właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Aby zainicjować wewnętrzna struktura, należy wywołać [CSnapInPropertyPageImpl::Create](#create).  
  
##  <a name="create"></a>  CSnapInPropertyPageImpl::Create  
 Wywołaj tę funkcję, aby zainicjować wewnętrzna struktura na stronie właściwości.  
  
```
HPROPSHEETPAGE Create();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do `PROPSHEETPAGE` zawierających atrybuty arkusza właściwości nowo utworzonej struktury.  
  
### <a name="remarks"></a>Uwagi  
 Należy najpierw wywołać [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) przed wywołaniem tej funkcji.  
  
##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp  
 `m_psp` jest strukturą, której członkowie przechowywania charakterystyki `PROPSHEETPAGE`.  
  
```
PROPSHEETPAGE m_psp;
```  
  
### <a name="remarks"></a>Uwagi  
 Aby zainicjować wygląd strony właściwości po jest tworzony, należy użyć tej struktury.  
  
 Aby uzyskać więcej informacji na temat tej struktury, w tym listę swoich elementów członkowskich, zobacz [PROPSHEETPAGE](https://msdn.microsoft.com/library/aa815151) w zestawie Windows SDK.  
  
##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply  
 Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie **OK** lub **Zastosuj teraz** przycisku.  
  
```
BOOL OnApply();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli zmiany są akceptowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przed `OnApply` mogą być wywoływane przez platformę, musi być wywołana `SetModified` i jego parametr jest ustawiony na wartość TRUE. To uaktywni **Zastosuj teraz** przycisku tak szybko, jak użytkownik wprowadza zmianę na stronie właściwości.  
  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić, jakie działania programu przyjmuje, gdy użytkownik kliknie **Zastosuj teraz** przycisku. Podczas zastępowania, funkcja powinna zwrócić wartość TRUE, aby zaakceptować zmiany i wartość FALSE, aby uniemożliwić zmiany wpływają.  
  
 Domyślna implementacja klasy `OnApply` zwraca wartość TRUE.  
  
##  <a name="onhelp"></a>  CSnapInPropertyPageImpl::OnHelp  
 Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie **pomocy** przycisk na stronie właściwości.  
  
```
void OnHelp();
```  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby wyświetlić Pomoc dla strony właściwości.  
  
##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive  
 Ta funkcja członkowska jest wywoływana, gdy strona nie jest już stroną aktywną.  
  
```
BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli dane zostały zaktualizowane pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję elementu członkowskiego, aby wykonywać zadania sprawdzania poprawności danych specjalne.  
  
##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel  
 Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie **anulować** przycisk i przed Anuluj działanie miało miejsce.  
  
```
BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, aby umożliwić operacji anulowania; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić akcję program przyjmuje, gdy użytkownik kliknie **anulować** przycisku.  
  
 Domyślna implementacja klasy `OnQueryCancel` zwraca wartość TRUE.  
  
##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset  
 Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie **anulować** przycisku.  
  
```
void OnReset();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy ta funkcja jest wywoływana, zmienia się na wszystkich stronach właściwości, które zostały wprowadzone przez użytkownika, klikając wcześniej **Zastosuj teraz** przycisku zostaną odrzucone i arkusza właściwości zachowuje fokus.  
  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić, jakie działanie ma program, gdy użytkownik kliknie **anulować** przycisku.  
  
##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive  
 Ta funkcja członkowska jest wywoływana, gdy strona jest wybierany przez użytkownika i staje się stroną aktywną.  
  
```
BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli strona została pomyślnie active; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego do wykonywania zadań, gdy strona jest aktywna. Przesłonięcia funkcji składowej powinien wywołać domyślną wersję, zanim dowolne inne procesy przetwarzania jest wykonywane.  
  
 Domyślna implementacja zwraca wartość PRAWDA.  
  
##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack  
 Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie **ponownie** przycisku w kreatorze.  
  
```
BOOL OnWizardBack();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
-   0, aby automatycznie przejść do poprzedniej strony.  
  
-   -1, aby uniemożliwić zmianę na stronie.  
  
 Aby przejść do strony inne niż kolejny, zwróć identyfikator okna dialogowego, które mają być wyświetlane.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić niektóre akcje, które użytkownik musi wykonać, gdy **ponownie** przycisku.  
  
##  <a name="onwizardfinish"></a>  CSnapInPropertyPageImpl::OnWizardFinish  
 Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie **Zakończ** przycisku w kreatorze.  
  
```
BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli arkusz właściwości jest niszczony, kiedy Kreator zakończy pracę; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić niektóre akcje, które użytkownik musi wykonać, gdy **Zakończ** przycisku.  
  
##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext  
 Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie **dalej** przycisku w kreatorze.  
  
```
BOOL OnWizardNext();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
-   0, aby automatycznie przejść do następnej strony.  
  
-   -1, aby uniemożliwić zmianę na stronie.  
  
 Aby przejść do strony inne niż kolejny, zwróć identyfikator okna dialogowego, które mają być wyświetlane.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji elementu członkowskiego, aby określić niektóre akcje, które użytkownik musi wykonać, gdy **dalej** przycisku.  
  
##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings  
 Wywołaj tę funkcję elementu członkowskiego do przesyłania dalej wiadomości do każdej strony w arkuszu właściwości.  
  
```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 *wParam*  
 [in] Określa dodatkowe informacje zależne od wiadomości.  
  
 *lParam*  
 [in] Określa dodatkowe informacje zależne od wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wiadomość, nie powinien być przekazywany do następnej strony właściwości; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli strona zwraca wartość różną od zera, arkusz właściwości nie wysyła komunikat do kolejnych stron.  
  
##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified  
 Wywołaj tę funkcję elementu członkowskiego, aby włączyć lub wyłączyć **Zastosuj teraz** przycisku, oparte na tego, czy ustawienia na stronie właściwości stosuje się do odpowiedniego obiektu zewnętrznego.  
  
```
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bChanged*  
 [in] Wartość TRUE, aby wskazać, że ustawienia strony właściwości zostały zmodyfikowane od czasu ostatniego one zostały zastosowane; FALSE, aby wskazać, że ustawienia strony właściwości zostały zastosowane lub mają być ignorowane.  
  
### <a name="remarks"></a>Uwagi  
 Arkusz właściwości przechowuje ścieżki, które strony są "zanieczyszczony", oznacza to, strony właściwości, dla których wywołaniu `SetModified( TRUE )`. **Zastosuj teraz** przycisk zawsze zostanie włączona, jeśli wywołasz `SetModified( TRUE )` jednej strony. **Zastosuj teraz** przycisk będzie wyłączony podczas wywoływania `SetModified( FALSE )` jednej strony, ale tylko wtedy, gdy żaden z innych stron jest "zakłóconych".  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
