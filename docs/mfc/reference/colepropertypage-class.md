---
title: Klasa COlePropertyPage
ms.date: 11/04/2016
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
ms.openlocfilehash: dbdc889e244b33365756bcbae5b37cf657a6d900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374881"
---
# <a name="colepropertypage-class"></a>Klasa COlePropertyPage

Służy do wyświetlania właściwości formantu niestandardowego w interfejsie graficznym, podobnie jak w oknie dialogowym.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Strona COlePropertyPage::COlePropertyPage](#colepropertypage)|Konstruuje `COlePropertyPage` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Strona COlePropertyPage::GetControlStatus](#getcontrolstatus)|Wskazuje, czy użytkownik zmodyfikował wartość w formancie.|
|[Strona COlePropertyPage::GetObjectArray](#getobjectarray)|Zwraca tablicę obiektów edytowanych przez stronę właściwości.|
|[Strona COlePropertyPage::GetPageWitsite](#getpagesite)|Zwraca wskaźnik do `IPropertyPageSite` interfejsu strony właściwości.|
|[Strona COlePropertyPage::IgnoreApply](#ignoreapply)|Określa, które formanty nie włączają przycisku Zastosuj.|
|[Strona COlePropertyPage::Jestzmodysyfikowana](#ismodified)|Wskazuje, czy użytkownik zmodyfikował stronę właściwości.|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Wywoływana przez platformę, gdy użytkownik edytuje właściwość.|
|[Strona COlePropertyPage::OnHelp](#onhelp)|Wywoływane przez platformę, gdy użytkownik wywołuje pomoc.|
|[Strona COlePropertyPage::OnInitDialog](#oninitdialog)|Wywoływane przez strukturę, gdy strona właściwości jest inicjowany.|
|[COlePropertyPage::OnObjectsZmieniane](#onobjectschanged)|Wywoływana przez platformę, gdy zostanie wybrana inna kontrolka OLE z nowymi właściwościami.|
|[Strona COlePropertyPage::OnSetPageWitosz](#onsetpagesite)|Wywoływana przez strukturę, gdy ramka właściwości udostępnia witrynę strony.|
|[Strona COlePropertyPage::SetControlStatus](#setcontrolstatus)|Ustawia flagę wskazującą, czy użytkownik zmodyfikował wartość w formancie.|
|[Strona COlePropertyPage::SetDialogResource](#setdialogresource)|Ustawia zasób okna dialogowego strony właściwości.|
|[Strona COlePropertyPage::SetHelpInfo](#sethelpinfo)|Ustawia krótki tekst pomocy strony właściwości, nazwę pliku pomocy i kontekst pomocy.|
|[Strona COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Ustawia flagę wskazującą, czy użytkownik zmodyfikował stronę właściwości.|
|[Strona COlePropertyPage::SetPageName](#setpagename)|Ustawia nazwę strony właściwości (podpis).|

## <a name="remarks"></a>Uwagi

Na przykład strona właściwości może zawierać formant edycji, który umożliwia użytkownikowi wyświetlanie i modyfikowanie właściwości podpisu formantu.

Każda właściwość kontroli niestandardowej lub akcji może mieć kontrolkę okna dialogowego, która umożliwia użytkownikowi formantu wyświetlanie bieżącej wartości właściwości i modyfikowanie tej wartości w razie potrzeby.

Aby uzyskać więcej `COlePropertyPage`informacji na temat używania , zobacz artykuł [ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="colepropertypagecolepropertypage"></a><a name="colepropertypage"></a>Strona COlePropertyPage::COlePropertyPage

Konstruuje `COlePropertyPage` obiekt.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parametry

*idDlg ( idDlg )*<br/>
Identyfikator zasobu szablonu okna dialogowego.

*idCaption ( idCaption )*<br/>
Identyfikator zasobu podpisu strony właściwości.

### <a name="remarks"></a>Uwagi

Podczas implementowania podklasy `COlePropertyPage`, konstruktor podklasy należy użyć `COlePropertyPage` konstruktora do identyfikowania zasobu szablonu okna dialogowego, na którym opiera się strona właściwości i zasób ciąg zawierający jego podpis.

## <a name="colepropertypagegetcontrolstatus"></a><a name="getcontrolstatus"></a>Strona COlePropertyPage::GetControlStatus

Określa, czy użytkownik zmodyfikował wartość formantu strony właściwości o określonym identyfikatorze zasobu.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator zasobu formantu strony właściwości.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wartość kontrolna została zmodyfikowana; w przeciwnym razie FALSE.

## <a name="colepropertypagegetobjectarray"></a><a name="getobjectarray"></a>Strona COlePropertyPage::GetObjectArray

Zwraca tablicę obiektów edytowanych przez stronę właściwości.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parametry

*pnObiekty*<br/>
Wskaźnik do niepodpisanej długiej liczby całkowitej, która otrzyma liczbę obiektów edytowanych przez stronę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy `IDispatch` wskaźników, które są używane do uzyskiwania dostępu do właściwości każdego formantu na stronie właściwości. Wywołujący nie może zwolnić te wskaźniki interfejsu.

### <a name="remarks"></a>Uwagi

Każdy obiekt strony właściwości zachowuje tablicę `IDispatch` wskaźników do interfejsów obiektów edytowanych przez stronę. Ta funkcja ustawia jego *argument pnObjects* na liczbę elementów w tej tablicy i zwraca wskaźnik do pierwszego elementu tablicy.

## <a name="colepropertypagegetpagesite"></a><a name="getpagesite"></a>Strona COlePropertyPage::GetPageWitsite

Pobiera wskaźnik do `IPropertyPageSite` interfejsu strony właściwości.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IPropertyPageSite` interfejsu strony właściwości.

### <a name="remarks"></a>Uwagi

Formanty i kontenery współpracują, dzięki czemu użytkownicy mogą przeglądać i edytować właściwości formantu. Formant udostępnia strony właściwości, z których każdy jest obiektem OLE, który umożliwia użytkownikowi edytowanie powiązanego zestawu właściwości. Kontener zawiera ramkę właściwości, która wyświetla strony właściwości. Dla każdej strony ramka właściwości zawiera witrynę `IPropertyPageSite` strony, która obsługuje interfejs.

## <a name="colepropertypageignoreapply"></a><a name="ignoreapply"></a>Strona COlePropertyPage::IgnoreApply

Określa, które formanty nie włączają przycisku Zastosuj.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator formantu, który ma zostać zignorowany.

### <a name="remarks"></a>Uwagi

Przycisk Zastosuj na stronie właściwości jest włączony tylko wtedy, gdy wartości formantów strony właściwości zostały zmienione. Ta funkcja służy do określania formantów, które nie powodują włączenia przycisku Zastosuj po zmianie ich wartości.

## <a name="colepropertypageismodified"></a><a name="ismodified"></a>Strona COlePropertyPage::Jestzmodysyfikowana

Określa, czy użytkownik zmienił żadnych wartości na stronie właściwości.

```
BOOL IsModified();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli strona właściwości została zmodyfikowana.

## <a name="colepropertypageoneditproperty"></a><a name="oneditproperty"></a>COlePropertyPage::OnEditProperty

Struktura wywołuje tę funkcję, gdy określona właściwość ma być edytowany.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
Identyfikator wysyłki edytowanej właściwości.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca WARTOŚĆ FAŁSZ. Zastąpienia tej funkcji powinny zwracać wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Można go zastąpić, aby ustawić fokus na odpowiedni formant na stronie. Domyślna implementacja nic nie robi i zwraca FALSE.

## <a name="colepropertypageonhelp"></a><a name="onhelp"></a>Strona COlePropertyPage::OnHelp

Struktura wywołuje tę funkcję, gdy użytkownik żąda pomocy online.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parametry

*lpszHelpDir (lpszHelpDir)*<br/>
Katalog zawierający plik pomocy strony właściwości.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca WARTOŚĆ FAŁSZ.

### <a name="remarks"></a>Uwagi

Zastąpokaj go, jeśli strona właściwości musi wykonać dowolną akcję specjalną, gdy użytkownik uzyskuje dostęp do pomocy. Domyślna implementacja nic nie robi i zwraca FALSE, który nakazuje platformie do wywołania WinHelp.

## <a name="colepropertypageoninitdialog"></a><a name="oninitdialog"></a>Strona COlePropertyPage::OnInitDialog

Struktura wywołuje tę funkcję, gdy okno dialogowe strony właściwości jest inicjowane.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca WARTOŚĆ FAŁSZ.

### <a name="remarks"></a>Uwagi

Zastąpokaj go, jeśli podczas inicjowania okna dialogowego jest wymagana jakakolwiek akcja specjalna. Domyślna implementacja wywołuje `CDialog::OnInitDialog` i zwraca FALSE.

## <a name="colepropertypageonobjectschanged"></a><a name="onobjectschanged"></a>COlePropertyPage::OnObjectsZmieniane

Wywoływana przez platformę, gdy zostanie wybrana inna kontrolka OLE z nowymi właściwościami.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Uwagi

Podczas przeglądania właściwości formantu OLE w środowisku deweloperskim, niemodless okno dialogowe jest używany do wyświetlania jego stron właściwości. Jeśli wybrano inny formant, dla nowego zestawu właściwości musi być wyświetlany inny zestaw stron właściwości. Struktura wywołuje tę funkcję, aby powiadomić stronę właściwości o zmianie.

Zastąd w tej funkcji należy otrzymywać powiadomienia o tej akcji i wykonywać wszelkie akcje specjalne.

## <a name="colepropertypageonsetpagesite"></a><a name="onsetpagesite"></a>Strona COlePropertyPage::OnSetPageWitosz

Struktura wywołuje tę funkcję, gdy ramka właściwości udostępnia witrynę strony właściwości.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja ładuje podpis strony i próbuje określić rozmiar strony z zasobu okna dialogowego. Zastąp tę funkcję, jeśli strona właściwości wymaga dalszych działań; zastąpienie należy wywołać implementacji klasy podstawowej.

## <a name="colepropertypagesetcontrolstatus"></a><a name="setcontrolstatus"></a>Strona COlePropertyPage::SetControlStatus

Zmienia stan formantu strony właściwości.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Zawiera identyfikator formantu strony właściwości.

*bDirty*<br/>
Określa, czy pole strony właściwości zostało zmodyfikowane. Ustaw wartość PRAWDA, jeśli pole zostało zmodyfikowane, FALSE, jeśli nie zostało zmodyfikowane.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ustawiono określony formant; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli stan formantu strony właściwości jest zabrudzony, gdy strona właściwości jest zamknięta lub wybrano przycisk Zastosuj, właściwość formantu zostanie zaktualizowana o odpowiednią wartość.

## <a name="colepropertypagesetdialogresource"></a><a name="setdialogresource"></a>Strona COlePropertyPage::SetDialogResource

Ustawia zasób okna dialogowego strony właściwości.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parametry

*hDialog*<br/>
Dojście do zasobu okna dialogowego strony właściwości.

## <a name="colepropertypagesethelpinfo"></a><a name="sethelpinfo"></a>Strona COlePropertyPage::SetHelpInfo

Określa informacje o etykietce narzędzia, nazwę pliku pomocy i kontekst pomocy dla strony właściwości.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parametry

*lpszDocString*<br/>
Ciąg zawierający krótkie informacje o pomocy do wyświetlania na pasku stanu lub w innej lokalizacji.

*lpszHelpFile*<br/>
Nazwa pliku pomocy strony właściwości.

*dwHelpContext (Pomoc kontekst)*<br/>
Kontekst pomocy dla strony właściwości.

## <a name="colepropertypagesetmodifiedflag"></a><a name="setmodifiedflag"></a>Strona COlePropertyPage::SetModifiedFlag

Wskazuje, czy użytkownik zmodyfikował stronę właściwości.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bZmodyfikowany*<br/>
Określa nową wartość zmodyfikowanej flagi strony właściwości.

## <a name="colepropertypagesetpagename"></a><a name="setpagename"></a>Strona COlePropertyPage::SetPageName

Ustawia nazwę strony właściwości, którą ramka właściwości będzie zazwyczaj wyświetlana na karcie strony.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
Wskaźnik do ciągu zawierającego nazwę strony właściwości.

## <a name="see-also"></a>Zobacz też

[Przykładowy circ3 MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka TESTHELP MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
