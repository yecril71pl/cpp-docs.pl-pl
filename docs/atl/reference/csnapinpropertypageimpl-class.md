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
ms.openlocfilehash: 3f09e8500eadd36eec53db95f10261834d672101
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747582"
---
# <a name="csnapinpropertypageimpl-class"></a>Klasa CSnapInPropertyPageImpl

Ta klasa zawiera metody implementowania obiektu strony właściwości przystawki.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

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
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Zmienia stan przycisków **OK** i **Anuluj.**|
|[CSnapInPropertyPageImpl::Tworzenie](#create)|Inicjuje nowo `CSnapInPropertyPageImpl` utworzony obiekt.|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Zastosuj teraz** podczas korzystania z arkusza właściwości typu kreatora.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Pomocy** podczas korzystania z arkusza właściwości typu kreatora.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Wywoływana przez platformę, gdy bieżąca strona nie jest już aktywna.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Anuluj** i przed anuluj miało miejsce.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Reset** podczas korzystania z arkusza właściwości typu kreatora.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Wywoływana przez platformę, gdy bieżąca strona staje się aktywna.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Wstecz** podczas korzystania z arkusza właściwości typu kreatora.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Zakończ** podczas korzystania z arkusza właściwości typu kreatora.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk **Dalej** podczas korzystania z arkusza właściwości typu kreatora.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Przekazuje bieżącą wiadomość do wszystkich stron arkusza właściwości.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Zadzwoń, aby aktywować lub dezaktywować przycisk **Zastosuj teraz.**|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Struktura `PROPSHEETPAGE` systemu Windows `CSnapInPropertyPageImpl` używana przez obiekt.|

## <a name="remarks"></a>Uwagi

`CSnapInPropertyPageImpl`zapewnia podstawową implementację obiektu strony właściwości przystawki. Podstawowe funkcje strony właściwości przystawki są implementowane przy użyciu kilku różnych interfejsów i typów map.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsnap.h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose

Wywołanie tej funkcji po nieodwracalnej zmiany zostały wprowadzone do danych na stronie arkusza właściwości modalnych.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zmieni przycisk **OK,** aby **zamknąć** i wyłączyć przycisk **Anuluj.** Ta zmiana ostrzega użytkownika, że zmiana jest trwała i modyfikacje nie mogą zostać anulowane.

Funkcja `CancelToClose` elementu członkowskiego nie robi nic w arkuszu właściwości bez trybu, ponieważ arkusz właściwości bez trybu nie ma domyślnie przycisku **Anuluj.**

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Konstruuje `CSnapInPropertyPageImpl` obiekt.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Parametry

*lpszTitle (lpszTitle)*<br/>
[w] Tytuł strony właściwości.

### <a name="remarks"></a>Uwagi

Aby zainicjować podstawową strukturę, wywołanie [CSnapInPropertyPageImpl::Create](#create).

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapInPropertyPageImpl::Tworzenie

Wywołanie tej funkcji, aby zainicjować podstawową strukturę strony właściwości.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Wartość zwracana

Dojście `PROPSHEETPAGE` do struktury zawierającej atrybuty nowo utworzonego arkusza właściwości.

### <a name="remarks"></a>Uwagi

Przed wywołaniem tej funkcji należy najpierw wywołać [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl.](#csnapinpropertypageimpl)

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp

`m_psp`jest strukturą, której członkowie `PROPSHEETPAGE`przechowują cechy .

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Uwagi

Ta struktura służy do inicjowania wyglądu strony właściwości po jej skonstruowaniu.

Aby uzyskać więcej informacji na temat tej struktury, w tym listę jej członków, zobacz [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) w zestawie Windows SDK.

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapInPropertyPageImpl::OnApply

Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie przycisk **OK** lub **Zastosuj teraz.**

```
BOOL OnApply();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zmiany są akceptowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zanim `OnApply` może być wywołana przez platformę, musisz wywołać `SetModified` i ustawić jego parametr na TRUE. Spowoduje to aktywowanie przycisku **Zastosuj teraz,** gdy tylko użytkownik zmieni się na stronie właściwości.

Zastąp tę funkcję elementu członkowskiego, aby określić, jakie działania wykonuje program, gdy użytkownik kliknie przycisk **Zastosuj teraz.** Podczas zastępowania funkcja powinna zwracać wartość PRAWDA, aby zaakceptować zmiany i fałsz, aby zapobiec wprowadzaniu zmian.

Domyślna implementacja `OnApply` zwraca wartość TRUE.

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp

Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie przycisk **Pomoc** dla strony właściwości.

```cpp
void OnHelp();
```

### <a name="remarks"></a>Uwagi

Zastąpokaj tę funkcję elementu członkowskiego, aby wyświetlić pomoc dla strony właściwości.

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive

Ta funkcja elementu członkowskiego jest wywoływana, gdy strona nie jest już aktywną stroną.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dane zostały pomyślnie zaktualizowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąpojąć tę funkcję elementu członkowskiego do wykonywania zadań sprawdzania poprawności danych specjalnych.

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel

Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie przycisk **Anuluj** i przed anuluj akcję.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, aby umożliwić operację anulowania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, aby określić akcję, która zostanie wykonaniu przez program, gdy użytkownik kliknie przycisk **Anuluj.**

Domyślna implementacja `OnQueryCancel` zwraca wartość TRUE.

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a>CSnapInPropertyPageImpl::OnReset

Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie przycisk **Anuluj.**

```cpp
void OnReset();
```

### <a name="remarks"></a>Uwagi

Gdy ta funkcja jest wywoływana, zmiany na wszystkich stronach właściwości, które zostały wprowadzone przez użytkownika wcześniej klikając przycisk **Zastosuj teraz** są odrzucane, a arkusz właściwości zachowuje fokus.

Zastąp tę funkcję elementu członkowskiego, aby określić, jakie działania program wykonuje, gdy użytkownik kliknie przycisk **Anuluj.**

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive

Ta funkcja elementu członkowskiego jest wywoływana, gdy strona jest wybierana przez użytkownika i staje się aktywną stroną.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strona została pomyślnie ustawiona jako aktywna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąpojąć tę funkcję elementu członkowskiego do wykonywania zadań, gdy strona jest aktywowana. Zastąpienie tej funkcji elementu członkowskiego należy wywołać wersję domyślną przed każdym innym przetwarzania jest wykonywana.

Domyślna implementacja zwraca wartość TRUE.

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack

Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie przycisk **Wstecz** w kreatorze.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Wartość zwracana

- 0, aby automatycznie przejść do poprzedniej strony.

- -1, aby zapobiec zmianie strony.

Aby przejść do strony innej niż następna, zwróć identyfikator okna dialogowego, które ma być wyświetlane.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, aby określić niektóre działania, które użytkownik musi podjąć po kliknięciu przycisku **Wstecz.**

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish

Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie przycisk **Zakończ** w kreatorze.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli arkusz właściwości zostanie zniszczony po zakończeniu pracy kreatora; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, aby określić niektóre działania, które użytkownik musi podjąć po kliknięciu przycisku **Zakończ.**

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext

Ta funkcja elementu członkowskiego jest wywoływana, gdy użytkownik kliknie przycisk **Dalej** w kreatorze.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Wartość zwracana

- 0, aby automatycznie przejść do następnej strony.

- -1, aby zapobiec zmianie strony.

Aby przejść do strony innej niż następna, zwróć identyfikator okna dialogowego, które ma być wyświetlane.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, aby określić niektóre działania, które użytkownik musi podjąć po kliknięciu przycisku **Dalej.**

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings

Wywołanie tej funkcji elementu członkowskiego, aby przesłać dalej wiadomość do każdej strony w arkuszu właściwości.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Wparam*<br/>
[w] Określa dodatkowe informacje zależne od wiadomości.

*Lparam*<br/>
[w] Określa dodatkowe informacje zależne od wiadomości.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość nie powinna być przekazycona do następnej strony właściwości; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Jeśli strona zwraca wartość niezerową, arkusz właściwości nie wysyła wiadomości do kolejnych stron.

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified

Wywołanie tej funkcji elementu członkowskiego, aby włączyć lub wyłączyć przycisk **Zastosuj teraz,** w zależności od tego, czy ustawienia na stronie właściwości powinny być stosowane do odpowiedniego obiektu zewnętrznego.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bZmienione*<br/>
[w] PRAWDA, aby wskazać, że ustawienia strony właściwości zostały zmodyfikowane od czasu ostatniego ich zastosowania; FALSE, aby wskazać, że ustawienia strony właściwości zostały zastosowane lub powinny zostać zignorowane.

### <a name="remarks"></a>Uwagi

Arkusz właściwości śledzi, które strony są "brudne", czyli strony `SetModified( TRUE )`właściwości, dla których został wywołany . Przycisk **Zastosuj teraz** będzie zawsze włączony, `SetModified( TRUE )` jeśli zadzwonisz na jedną ze stron. Przycisk **Zastosuj teraz** zostanie wyłączony, `SetModified( FALSE )` gdy wywołasz jedną ze stron, ale tylko wtedy, gdy żadna z pozostałych stron nie jest "brudna".

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
