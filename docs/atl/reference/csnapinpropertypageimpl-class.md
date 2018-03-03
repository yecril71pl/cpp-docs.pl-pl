---
title: Klasa CSnapInPropertyPageImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fc1135f02c31c644d7d149900bbaa755a52c579
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csnapinpropertypageimpl-class"></a>Klasa CSnapInPropertyPageImpl
Ta klasa dostarcza metody wykonywania obiekt strony właściwości przystawki.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
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
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Wywoływane przez platformę, gdy użytkownik kliknie **anulować** przycisk i zanim akcja została anulowana.|  
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Wywoływane przez platformę, gdy użytkownik kliknie **zresetować** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Wywoływane przez platformę, gdy bieżąca strona stanie się aktywny.|  
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Wywoływane przez platformę, gdy użytkownik kliknie **ponownie** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Wywoływane przez platformę, gdy użytkownik kliknie **Zakończ** przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Wywoływane przez platformę, gdy użytkownik kliknie `Next` przycisk podczas korzystania z arkusza właściwości typu Kreator.|  
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Przekazuje bieżącego komunikatu do wszystkich stron arkusza właściwości.|  
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Wywołanie aktywować lub dezaktywować **Zastosuj teraz** przycisku.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows **PROPSHEETPAGE** struktury używane przez `CSnapInPropertyPageImpl` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CSnapInPropertyPageImpl`udostępnia podstawową implementację dla obiekt strony właściwości przystawki. Podstawowe funkcje strony właściwości przystawki są implementowane za pomocą kilku różnych interfejsach i mapowania typów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsnap.h  
  
##  <a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose  
 Wywołanie tej funkcji po dokonaniu zmiany odzyskać danych na stronie modalny arkusz właściwości.  
  
```
void CancelToClose();
```  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji ulegnie zmianie **OK** przycisk, aby **Zamknij** i Wyłącz **anulować** przycisku. Ta zmiana alertów, które nie może być anulowana użytkownika, że zmiana jest trwałe i modyfikacji.  
  
 `CancelToClose` Funkcji członkowskiej nie działa w niemodalnego arkusza właściwości, ponieważ nie ma niemodalnego arkusza właściwości **anulować** przycisk domyślny.  
  
##  <a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl  
 Konstruuje `CSnapInPropertyPageImpl` obiektu.  
  
```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTitle`  
 [in] Tytuł strony właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Aby zainicjować podstawowej struktury, należy wywołać [CSnapInPropertyPageImpl::Create](#create).  
  
##  <a name="create"></a>CSnapInPropertyPageImpl::Create  
 Wywołanie tej funkcji, aby zainicjować struktury strony właściwości.  
  
```
HPROPSHEETPAGE Create();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do **PROPSHEETPAGE** struktury zawierających atrybuty arkusza właściwości nowo utworzony.  
  
### <a name="remarks"></a>Uwagi  
 Należy najpierw wywołać [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) przed wywołaniem tej funkcji.  
  
##  <a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp  
 `m_psp`jest strukturą, której członkowie przechowywania właściwości **PROPSHEETPAGE**.  
  
```
PROPSHEETPAGE m_psp;
```  
  
### <a name="remarks"></a>Uwagi  
 Aby zainicjować wyglądu strony właściwości po go jest tworzony, należy użyć tej struktury.  
  
 Więcej informacji dotyczących tej struktury, w tym listę jej członków, zobacz [PROPSHEETPAGE](http://msdn.microsoft.com/library/aa815151) w zestawie Windows SDK.  
  
##  <a name="onapply"></a>CSnapInPropertyPageImpl::OnApply  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie **OK** lub **Zastosuj teraz** przycisku.  
  
```
BOOL OnApply();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zmiany są akceptowane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przed `OnApply` mogą być wywoływane przez platformę, musi być wywołana `SetModified` i ustawić jej parametr **TRUE**. Spowoduje to uaktywnienie **Zastosuj teraz** przycisku, gdy użytkownik zmieni na stronie właściwości.  
  
 Przesłonić tę funkcję elementu członkowskiego, aby określić, jakie działanie ma programu, gdy użytkownik kliknie **Zastosuj teraz** przycisku. Podczas zastępowania, funkcja powinna zwrócić **TRUE** celu zaakceptowania zmian i **FALSE** uniemożliwić podjęcie wpływu zmiany.  
  
 Domyślna implementacja `OnApply` zwraca **TRUE**.  
  
##  <a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie **pomocy** przycisk strony właściwości.  
  
```
void OnHelp();
```  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby wyświetlić Pomoc do strony właściwości.  
  
##  <a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy strona nie jest już stroną aktywną.  
  
```
BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dane zostały zaktualizowane pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego do wykonywania zadań weryfikacji danych specjalne.  
  
##  <a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie **anulować** przycisk i przed Anuluj działanie miało miejsce.  
  
```
BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, aby umożliwić operacji anulowania; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby określić akcję program tworzy, gdy użytkownik kliknie **anulować** przycisku.  
  
 Domyślna implementacja `OnQueryCancel` zwraca **TRUE**.  
  
##  <a name="onreset"></a>CSnapInPropertyPageImpl::OnReset  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie **anulować** przycisku.  
  
```
void OnReset();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy ta funkcja jest wywoływana, zmiany dla wszystkich stron właściwości, które zostały wprowadzone przez użytkownika, klikając wcześniej **Zastosuj teraz** przycisk zostaną odrzucone i arkusza właściwości zachowuje fokus.  
  
 Przesłonić tę funkcję elementu członkowskiego, aby określić, jakie działanie ma program, gdy użytkownik kliknie **anulować** przycisku.  
  
##  <a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy strona jest wybierany przez użytkownika i staje się stroną aktywną.  
  
```
BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli strona została pomyślnie active; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego do wykonywania zadań, gdy strona jest aktywna. Zastąpienia funkcji członkowskiej powinny wywoływać wersja domyślna, przed odbywa się żadnych innych operacji.  
  
 Domyślna implementacja zwraca **TRUE**.  
  
##  <a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie **ponownie** przycisk w kreatorze.  
  
```
BOOL OnWizardBack();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
-   0, aby automatycznie przejść do poprzedniej strony.  
  
-   -1, aby uniemożliwić zmianę strony.  
  
 Aby przejść do strony innego niż dalej, zwróć identyfikator okno dialogowe, które mają być wyświetlane.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby określić niektóre akcje, użytkownik musi wykonać, gdy **ponownie** kliknięciu przycisku.  
  
##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie **Zakończ** przycisk w kreatorze.  
  
```
BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli arkusz właściwości jest niszczony po zakończeniu pracy Kreatora; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby określić niektóre akcje, użytkownik musi wykonać, gdy **Zakończ** kliknięciu przycisku.  
  
##  <a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext  
 Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie `Next` przycisk w kreatorze.  
  
```
BOOL OnWizardNext();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
-   0, aby automatycznie przejść do następnej strony.  
  
-   -1, aby uniemożliwić zmianę strony.  
  
 Aby przejść do strony innego niż dalej, zwróć identyfikator okno dialogowe, które mają być wyświetlane.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję elementu członkowskiego, aby określić niektóre akcje, użytkownik musi wykonać, gdy `Next` kliknięciu przycisku.  
  
##  <a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings  
 Wywołanie tej funkcji Członkowskich do przesyłania dalej wiadomości do każdej strony w arkuszu właściwości.  
  
```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `wParam`  
 [in] Określa dodatkowe informacje zależne od wiadomości.  
  
 `lParam`  
 [in] Określa dodatkowe informacje zależne od wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wiadomości nie powinny być przekazane do następnej strony właściwości; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli strona zwróci wartość niezerową, arkusza właściwości nie wysyła komunikat do kolejnych stron.  
  
##  <a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified  
 Wywołanie tej funkcji Członkowskich, aby włączyć lub wyłączyć **Zastosuj teraz** przycisk według tego, czy do odpowiedniego obiektu zewnętrznego, w którym mają zostać zastosowane ustawienia na stronie właściwości.  
  
```
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bChanged`  
 [in] **TRUE** wskazująca, że od czasu ostatniego zostały one zastosowane; zostały zmodyfikowane ustawienia strony właściwości **FALSE** wskazująca, czy ustawienia strony właściwości zostały zastosowane, lub należy ją ignorować.  
  
### <a name="remarks"></a>Uwagi  
 Arkusz właściwości przechowuje ścieżki, które strony są "zakłóconych", oznacza to, strony właściwości, dla których wywołaniu **SetModified (PRAWDA)**. **Zastosuj teraz** wywołanie będzie zawsze włączony przycisk **SetModified (PRAWDA)** dla jednej strony. **Zastosuj teraz** przycisk zostanie wyłączony podczas wywoływania **SetModified (FALSE)** dla jednej strony, ale tylko jeśli żaden z innych stron nie jest "zakłóconych".  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
