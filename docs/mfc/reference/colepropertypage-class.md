---
title: Klasa COlePropertyPage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
dev_langs:
- C++
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7db08ae9b9c2899709f4c6511478714869475ae7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386434"
---
# <a name="colepropertypage-class"></a>Klasa COlePropertyPage

Używany do wyświetlania właściwości kontrolki niestandardowej w interfejsie graficznym, zbliżonym do okna dialogowego.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|Konstruuje `COlePropertyPage` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Wskazuje, czy użytkownik zmienił wartość w formancie.|
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Zwraca tablicę obiektów edytowanych przez stronę właściwości.|
|[COlePropertyPage::GetPageSite](#getpagesite)|Zwraca wskaźnik do strony właściwości `IPropertyPageSite` interfejsu.|
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Określa, które kontrolki nie należy włączać przycisku Zastosuj.|
|[COlePropertyPage::IsModified](#ismodified)|Wskazuje, czy użytkownik zmienił się na stronie właściwości.|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Wywoływane przez platformę, gdy użytkownik edytuje właściwość.|
|[COlePropertyPage::OnHelp](#onhelp)|Wywoływane przez platformę, gdy użytkownik wywołuje Pomoc.|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Wywoływane przez platformę, gdy strona właściwości jest inicjowany.|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Wywoływane przez platformę, gdy wybrano inną kontrolkę OLE z nowymi właściwościami.|
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|Wywoływane przez platformę, gdy ramka właściwości dostarcza adres strony Web.|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Ustawia flagę wskazującą, czy użytkownik zmienił wartość w formancie.|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Ustawia zasobu okna dialogowego strony właściwości.|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Ustawia tekst krótki tekst pomocy na stronie właściwości, nazwa jego pliku pomocy, a jego Pomoc kontekstowa.|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Ustawia flagę wskazującą, czy użytkownik zmienił się na stronie właściwości.|
|[COlePropertyPage::SetPageName](#setpagename)|Ustawia nazwę strony właściwości (podpis).|

## <a name="remarks"></a>Uwagi

Na przykład strona właściwości mogą obejmować formant edycji, który umożliwia użytkownikowi wyświetlanie i modyfikowanie właściwości podpisu formantu.

Każda właściwość formantu niestandardowych lub standardowych może mieć formantu w oknie dialogowym, który umożliwia użytkownikowi kontrolki wyświetlić bieżącą wartość właściwości i zmodyfikować tę wartość, jeśli to konieczne.

Aby uzyskać więcej informacji na temat korzystania z `COlePropertyPage`, zapoznaj się z artykułem [kontrolek ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

##  <a name="colepropertypage"></a>  COlePropertyPage::COlePropertyPage

Konstruuje `COlePropertyPage` obiektu.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parametry

*idDlg*<br/>
Identyfikator zasobu szablonu okna dialogowego.

*idCaption*<br/>
Identyfikator zasobu podpisu strony właściwości.

### <a name="remarks"></a>Uwagi

Podczas implementacji podklasa klasy `COlePropertyPage`, należy używać konstruktora z podklasy `COlePropertyPage` konstruktora do identyfikacji zasobu szablonu okna dialogowego na której opiera się na stronie właściwości i zasobu ciągu zawierającego jego podpis.

##  <a name="getcontrolstatus"></a>  COlePropertyPage::GetControlStatus

Określa, czy użytkownik zmienił wartość kontrolki strony właściwości o identyfikatorze określonego zasobu.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator zasobu strony właściwości kontrolki.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli wartość kontrolki została zmodyfikowana; w przeciwnym razie wartość FALSE.

##  <a name="getobjectarray"></a>  COlePropertyPage::GetObjectArray

Zwraca tablicę obiektów edytowanych przez stronę właściwości.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parametry

*pnObjects*<br/>
Wskaźnik do niepodpisane długa liczba całkowita, otrzyma liczbę obiektów edytowany przez stronę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy `IDispatch` wskaźników, które są używane do dostępu do właściwości każdej kontrolki na stronie właściwości. Obiekt wywołujący nie musi zwolnić te wskaźniki interfejsu.

### <a name="remarks"></a>Uwagi

Każdy obiekt strony właściwości przechowuje tablicę wskaźników do `IDispatch` interfejsów obiektów edytowany przez stronę. Funkcja ta ustawia jego *pnObjects* argument na liczbę elementów w tablicy i zwraca wskaźnik do pierwszego elementu tablicy.

##  <a name="getpagesite"></a>  COlePropertyPage::GetPageSite

Pobiera wskaźnik do strony właściwości `IPropertyPageSite` interfejsu.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do strony właściwości `IPropertyPageSite` interfejsu.

### <a name="remarks"></a>Uwagi

Formanty i kontenery współpracować, aby użytkownicy mogą przeglądać i edytować właściwości formantu. Kontrolka zawiera strony właściwości, z których każdy jest obiekt OLE, który umożliwia użytkownikowi edytowanie powiązanych zbiór właściwości. Kontener zawiera ramka właściwości, w którym są wyświetlane na stronach właściwości. Dla każdej strony ramka właściwości dostarcza witryny strony, która obsługuje `IPropertyPageSite` interfejsu.

##  <a name="ignoreapply"></a>  COlePropertyPage::IgnoreApply

Określa, które kontrolki nie należy włączać przycisku Zastosuj.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator kontrolki mają być ignorowane.

### <a name="remarks"></a>Uwagi

Na stronie właściwości przycisku Zastosuj jest włączona tylko wtedy, gdy wartości formantów strony właściwości zostały zmienione. Ta funkcja umożliwia określenie kontrolek, które nie powodują przycisk Zastosuj, aby włączyć podczas ich wartości zmieniają się.

##  <a name="ismodified"></a>  COlePropertyPage::IsModified

Określa, czy użytkownik zmienił żadnych wartości na stronie właściwości.

```
BOOL IsModified();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli został zmodyfikowany na stronie właściwości.

##  <a name="oneditproperty"></a>  COlePropertyPage::OnEditProperty

Struktura wywołuje tę funkcję, po można edytować określoną właściwość.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*identyfikator DISPID*<br/>
Wyślij identyfikator właściwości edytowany.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość FALSE. Zastąpienia tej funkcji powinna zwrócić wartość TRUE.

### <a name="remarks"></a>Uwagi

Można zastąpić go, aby ustawić fokus do odpowiedniej kontrolki na stronie. Domyślna implementacja nic nie robi i zwraca wartość FALSE.

##  <a name="onhelp"></a>  COlePropertyPage::OnHelp

Struktura wywołuje tę funkcję, gdy użytkownik zażąda pomocy online.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parametry

*lpszHelpDir*<br/>
Katalog zawierający plik pomocy na stronie właściwości.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Go zastąpić, jeśli Twoja strona właściwości, które należy wykonać dowolną akcję specjalną, gdy użytkownik uzyskuje dostęp do pomocy. Domyślna implementacja nic nie robi i zwraca wartość FALSE, co powoduje, że platformę, by wywołać WinHelp.

##  <a name="oninitdialog"></a>  COlePropertyPage::OnInitDialog

Struktura wywołuje tę funkcję, po zainicjowaniu okno dialogowe strony właściwości.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Go zastąpić, jeśli dowolną akcję specjalną, jest wymagany, gdy okno dialogowe jest zainicjowany. Domyślna implementacja wywołuje `CDialog::OnInitDialog` i zwraca wartość FALSE.

##  <a name="onobjectschanged"></a>  COlePropertyPage::OnObjectsChanged

Wywoływane przez platformę, gdy wybrano inną kontrolkę OLE z nowymi właściwościami.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Uwagi

Podczas przeglądania właściwości kontrolki OLE w Środowisko deweloperskie, niemodalne okno dialogowe służy do wyświetlania stron jej właściwości. Jeśli wybrano inną kontrolkę, inny zbiór stron właściwości musi być wyświetlona nowego zestawu właściwości. Struktura wywołuje tę funkcję, aby powiadomić strona właściwości zmiany.

Należy przesłonić tę funkcję, aby otrzymać powiadomienie o tej akcji i wykonywać żadnych specjalnych działań.

##  <a name="onsetpagesite"></a>  COlePropertyPage::OnSetPageSite

Struktura wywołuje tę funkcję, gdy ramka właściwości dostarcza na stronie właściwości strony witryny.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja ładuje podpisu strony i próbuje określić rozmiar strony z zasobu okna dialogowego. Przesłonić tę funkcję, jeśli Twoja strona właściwości wymaga dalszych działań; przesłonięcia powinny wywoływać implementację klasy bazowej.

##  <a name="setcontrolstatus"></a>  COlePropertyPage::SetControlStatus

Zmienia stan formantu strony właściwości.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Zawiera identyfikator formantu strony właściwości.

*bDirty*<br/>
Określa, jeśli zmodyfikowano pola na stronie właściwości. Ustaw wartość TRUE, jeśli pole zmodyfikowano, FALSE, jeśli nie zostały zmodyfikowane.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ustawiono określoną kontrolkę; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli stan formantu strony właściwości został zmieniony, gdy strona właściwości jest zamknięty lub wciśnięcia przycisku Zastosuj, będzie można zaktualizować właściwości formantu w odpowiednią wartość.

##  <a name="setdialogresource"></a>  COlePropertyPage::SetDialogResource

Ustawia zasobu okna dialogowego strony właściwości.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parametry

*hDialog*<br/>
Dojście do zasobu okna dialogowego strony właściwości.

##  <a name="sethelpinfo"></a>  COlePropertyPage::SetHelpInfo

Określa informacje, nazwa_pliku pomocy i kontekstu pomocy dla strony właściwości.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parametry

*lpszDocString*<br/>
Ciąg zawierający zwięzłe informacje do wyświetlenia w pasku stanu lub w innej lokalizacji.

*lpszHelpFile*<br/>
Nazwa pliku pomocy na stronie właściwości.

*dwHelpContext*<br/>
Kontekst pomocy dla strony właściwości.

##  <a name="setmodifiedflag"></a>  COlePropertyPage::SetModifiedFlag

Wskazuje, czy użytkownik zmienił się na stronie właściwości.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Określa nową wartość dla flagi zmodyfikowane strony właściwości.

##  <a name="setpagename"></a>  COlePropertyPage::SetPageName

Ustawia nazwę strony właściwości, która ramka właściwości będą one zazwyczaj wyświetlane na karcie strony.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
Wskaźnik do ciągu zawierającego nazwę strony właściwości.

## <a name="see-also"></a>Zobacz też

[CIRC3 próbki MFC](../../visual-cpp-samples.md)<br/>
[Próbki MFC TESTHELP](../../visual-cpp-samples.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
