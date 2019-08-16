---
title: Klasa CSnapInPropertyPageImpl
ms.date: 11/04/2016
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
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: abf4cf5804f6ef7335192feb298f1a4a06f841e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496397"
---
# <a name="csnapinpropertypageimpl-class"></a>Klasa CSnapInPropertyPageImpl

Ta klasa dostarcza metody do implementowania obiektu strony właściwości przystawki.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Zmienia stan przycisków **OK** i **Anuluj** .|
|[CSnapInPropertyPageImpl:: Create](#create)|Inicjuje nowo utworzony `CSnapInPropertyPageImpl` obiekt.|
|[CSnapInPropertyPageImpl:: OnApply](#onapply)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk **Zastosuj teraz** , podczas korzystania z arkusza właściwości typu Kreator.|
|[CSnapInPropertyPageImpl:: OnHelp](#onhelp)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk **Pomoc** w trakcie korzystania z arkusza właściwości typu Kreator.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Wywoływane przez platformę, gdy bieżąca strona nie jest już aktywna.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk **Anuluj** i przed upływem anulowania.|
|[CSnapInPropertyPageImpl:: onreset](#onreset)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk **Resetuj** podczas korzystania z arkusza właściwości typu Kreator.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Wywoływane przez platformę, gdy bieżąca strona zostanie uaktywniona.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk **Wstecz** podczas korzystania z arkusza właściwości typu Kreator.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk **Zakończ** podczas korzystania z arkusza właściwości typu Kreator.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Wywoływane przez platformę, gdy użytkownik klika przycisk **dalej** podczas korzystania z arkusza właściwości typu Kreator.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Przekazuje bieżący komunikat do wszystkich stron arkusza właściwości.|
|[CSnapInPropertyPageImpl:: SetModified](#setmodified)|Wywołaj, aby uaktywnić lub dezaktywować przycisk **Zastosuj teraz** .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Struktura systemu `PROPSHEETPAGE` Windows używana `CSnapInPropertyPageImpl` przez obiekt.|

## <a name="remarks"></a>Uwagi

`CSnapInPropertyPageImpl`udostępnia podstawową implementację obiektu strony właściwości przystawki. Podstawowe funkcje strony właściwości przystawki są implementowane przy użyciu kilku różnych interfejsów i typów map.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsnap. h

##  <a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose

Wywołaj tę funkcję po wprowadzeniu nieodwracalnej zmiany danych na stronie modalnego arkusza właściwości.

```
void CancelToClose();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zmieni przycisk **OK** , aby **zamknąć** i wyłączyć przycisk **Anuluj** . Ta zmiana ostrzega użytkownika o tym, że zmiana jest trwała, a modyfikacje nie mogą być anulowane.

Funkcja członkowska nie ma żadnego niemodalnego arkusza właściwości, ponieważ niemodalny arkusz właściwości domyślnie nie ma przycisku **Anuluj.** `CancelToClose`

##  <a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Konstruuje `CSnapInPropertyPageImpl` obiekt.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
podczas Tytuł strony właściwości.

### <a name="remarks"></a>Uwagi

Aby zainicjować podstawową strukturę, wywołaj [CSnapInPropertyPageImpl:: Create](#create).

##  <a name="create"></a>CSnapInPropertyPageImpl:: Create

Wywołaj tę funkcję, aby zainicjować podstawową strukturę strony właściwości.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do `PROPSHEETPAGE` struktury zawierającej atrybuty nowo utworzonego arkusza właściwości.

### <a name="remarks"></a>Uwagi

Przed wywołaniem tej funkcji należy najpierw wywołać metodę [CSnapInPropertyPageImpl:: CSnapInPropertyPageImpl](#csnapinpropertypageimpl) .

##  <a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp

`m_psp`jest strukturą, której członkowie przechowują cechy `PROPSHEETPAGE`.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Uwagi

Użyj tej struktury, aby zainicjować wygląd strony właściwości po jej skonstruowaniu.

Aby uzyskać więcej informacji na temat tej struktury, łącznie z listą jej elementów członkowskich, zobacz [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) w Windows SDK.

##  <a name="onapply"></a>CSnapInPropertyPageImpl:: OnApply

Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie przycisk **OK** lub **Zastosuj teraz** .

```
BOOL OnApply();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli zmiany są akceptowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zanim `OnApply` będzie można wywołać przez platformę, należy wywołać `SetModified` i ustawić dla jego parametru wartość true. Spowoduje to aktywowanie przycisku **Zastosuj teraz** , gdy tylko użytkownik dokona zmiany na stronie właściwości.

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję podejmowaną przez program, gdy użytkownik kliknie przycisk **Zastosuj teraz** . Podczas zastępowania funkcja powinna zwrócić wartość TRUE, aby akceptować zmiany i FAŁSZ, aby zapobiec wprowadzeniu zmian.

Domyślna implementacja `OnApply` zwraca wartość true.

##  <a name="onhelp"></a>CSnapInPropertyPageImpl:: OnHelp

Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie przycisk **Pomoc** dla strony właściwości.

```
void OnHelp();
```

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby wyświetlić pomoc dla strony właściwości.

##  <a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive

Ta funkcja członkowska jest wywoływana, gdy strona nie jest już aktywna.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli dane zostały pomyślnie zaktualizowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby wykonywać specjalne zadania sprawdzania poprawności danych.

##  <a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel

Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie przycisk **Anuluj** i zostanie wykonana akcja anulowania.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, aby zezwolić na operację anulowania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję podejmowaną przez program, gdy użytkownik kliknie przycisk **Anuluj** .

Domyślna implementacja `OnQueryCancel` zwraca wartość true.

##  <a name="onreset"></a>CSnapInPropertyPageImpl:: onreset

Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie przycisk **Anuluj** .

```
void OnReset();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu tej funkcji zmiany we wszystkich stronach właściwości, które zostały wprowadzone przez użytkownika wcześniej po kliknięciu przycisku **Zastosuj teraz** , są odrzucane, a arkusz właściwości zachowuje fokus.

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję podejmowaną przez program, gdy użytkownik kliknie przycisk **Anuluj** .

##  <a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive

Ta funkcja członkowska jest wywoływana, gdy strona zostanie wybrana przez użytkownika i zostanie uaktywniona.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strona została pomyślnie ustawiona jako aktywna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby wykonywać zadania po aktywowaniu strony. Aby przesłonić tę funkcję członkowską, należy wywołać wersję domyślną przed jakimkolwiek innym przetwarzaniem.

Domyślna implementacja zwraca wartość TRUE.

##  <a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack

Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie przycisk **Wstecz** w kreatorze.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Wartość zwracana

- 0, aby automatycznie przejść do poprzedniej strony.

- -1, aby zapobiec zmienianiu strony.

Aby przejść do strony innej niż Następna, zwróć identyfikator okna dialogowego, które ma zostać wyświetlone.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję, którą użytkownik musi wykonać po kliknięciu przycisku **Wstecz** .

##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish

Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie przycisk **Zakończ** w kreatorze.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli arkusz właściwości zostanie zniszczony po zakończeniu pracy Kreatora; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję, którą użytkownik musi wykonać po kliknięciu przycisku **Zakończ** .

##  <a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext

Ta funkcja członkowska jest wywoływana, gdy użytkownik kliknie przycisk **dalej** w kreatorze.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Wartość zwracana

- 0, aby automatycznie przejść do następnej strony.

- -1, aby zapobiec zmienianiu strony.

Aby przejść do strony innej niż Następna, zwróć identyfikator okna dialogowego, które ma zostać wyświetlone.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję, którą użytkownik musi wykonać po kliknięciu przycisku **dalej** .

##  <a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings

Wywołaj tę funkcję elementu członkowskiego, aby przesłać dalej komunikat do każdej strony w arkuszu właściwości.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
podczas Określa dodatkowe informacje zależne od komunikatów.

*lParam*<br/>
podczas Określa dodatkowe informacje zależne od komunikatów.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli wiadomość nie powinna być przekazywana do następnej strony właściwości; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Jeśli strona zwróci wartość różną od zera, arkusz właściwości nie wyśle komunikatu do kolejnych stron.

##  <a name="setmodified"></a>CSnapInPropertyPageImpl:: SetModified

Wywołaj tę funkcję elementu członkowskiego, aby włączyć lub wyłączyć przycisk **Zastosuj teraz** , w zależności od tego, czy ustawienia na stronie właściwości mają być stosowane do odpowiedniego obiektu zewnętrznego.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bChanged*<br/>
podczas Wartość TRUE oznacza, że ustawienia strony właściwości zostały zmodyfikowane od czasu ostatniego zastosowania. Wartość FAŁSZ oznacza, że ustawienia strony właściwości zostały zastosowane lub powinny być ignorowane.

### <a name="remarks"></a>Uwagi

Arkusz właściwości śledzi, które strony są "zanieczyszczone", czyli strony właściwości, dla których wywołano `SetModified( TRUE )`. Przycisk **Zastosuj teraz** będzie zawsze włączany w przypadku wywołania `SetModified( TRUE )` jednej ze stron. Przycisk **Zastosuj teraz** zostanie wyłączony po wywołaniu `SetModified( FALSE )` jednej ze stron, ale tylko wtedy, gdy żadna z pozostałych stron nie jest "zanieczyszczona".

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
