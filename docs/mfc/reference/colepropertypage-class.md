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
ms.openlocfilehash: 8253b2c2fa6b93ec51c7ede983ef710eed039970
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421094"
---
# <a name="colepropertypage-class"></a>Klasa COlePropertyPage

Służy do wyświetlania właściwości kontrolki niestandardowej w interfejsie graficznym podobnym do okna dialogowego.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COlePropertyPage:: COlePropertyPage](#colepropertypage)|Konstruuje obiekt `COlePropertyPage`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COlePropertyPage:: GetControlStatus](#getcontrolstatus)|Wskazuje, czy użytkownik zmodyfikował wartość w kontrolce.|
|[COlePropertyPage:: GetObjectArray](#getobjectarray)|Zwraca tablicę obiektów, które są edytowane przez stronę właściwości.|
|[COlePropertyPage:: GetPageSite](#getpagesite)|Zwraca wskaźnik do interfejsu `IPropertyPageSite` strony właściwości.|
|[COlePropertyPage:: IgnoreApply](#ignoreapply)|Określa, które kontrolki nie włączają przycisku Zastosuj.|
|[COlePropertyPage:: IsModified](#ismodified)|Wskazuje, czy użytkownik zmodyfikował stronę właściwości.|
|[COlePropertyPage:: OnEditProperty](#oneditproperty)|Wywoływane przez platformę, gdy użytkownik edytuje właściwość.|
|[COlePropertyPage:: OnHelp](#onhelp)|Wywoływane przez platformę, gdy użytkownik wywołuje pomoc.|
|[COlePropertyPage:: OnInitDialog](#oninitdialog)|Wywoływane przez platformę po zainicjowaniu strony właściwości.|
|[COlePropertyPage:: OnObjectsChanged](#onobjectschanged)|Wywoływane przez platformę, gdy jest wybierana inna kontrolka OLE z nowymi właściwościami.|
|[COlePropertyPage:: OnSetPageSite](#onsetpagesite)|Wywoływane przez platformę, gdy ramka właściwości udostępnia witrynę strony.|
|[COlePropertyPage:: SetControlStatus](#setcontrolstatus)|Ustawia flagę wskazującą, czy użytkownik zmodyfikował wartość w kontrolce.|
|[COlePropertyPage:: SetDialogResource](#setdialogresource)|Ustawia zasób okna dialogowego strony właściwości.|
|[COlePropertyPage:: SetHelpInfo](#sethelpinfo)|Ustawia krótki tekst pomocy strony właściwości, nazwę pliku pomocy oraz jego kontekst pomocy.|
|[COlePropertyPage:: SetModifiedFlag](#setmodifiedflag)|Ustawia flagę wskazującą, czy użytkownik zmodyfikował stronę właściwości.|
|[COlePropertyPage:: SetPageName](#setpagename)|Ustawia nazwę strony właściwości (podpis).|

## <a name="remarks"></a>Uwagi

Na przykład strona właściwości może zawierać kontrolkę edycji, która umożliwia użytkownikowi wyświetlanie i modyfikowanie właściwości Caption kontrolki.

Każda właściwość formantu niestandardowego lub giełdowego może mieć kontrolkę okna dialogowego, która umożliwia użytkownikowi kontrolce wyświetlanie bieżącej wartości właściwości i modyfikowanie tej wartości w razie potrzeby.

Aby uzyskać więcej informacji na temat korzystania z `COlePropertyPage`, zobacz artykuł [formanty ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Wymagania

**Nagłówek:** 'afxctl. h

##  <a name="colepropertypage"></a>COlePropertyPage:: COlePropertyPage

Konstruuje obiekt `COlePropertyPage`.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parametry

*idDlg*<br/>
Identyfikator zasobu szablonu okna dialogowego.

*idCaption*<br/>
Identyfikator zasobu napisu strony właściwości.

### <a name="remarks"></a>Uwagi

W przypadku zaimplementowania podklasy `COlePropertyPage`, Konstruktor podklasy powinien używać konstruktora `COlePropertyPage` do identyfikowania zasobu szablonu okna dialogowego, w którym bazuje Strona właściwości i zasób ciągu zawierający jego podpis.

##  <a name="getcontrolstatus"></a>COlePropertyPage:: GetControlStatus

Określa, czy użytkownik zmodyfikował wartość kontrolki strony właściwości z określonym IDENTYFIKATORem zasobu.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator zasobu kontrolki strony właściwości.

### <a name="return-value"></a>Wartość zwrócona

PRAWDA, jeśli wartość kontrolki została zmodyfikowana; w przeciwnym razie FALSE.

##  <a name="getobjectarray"></a>COlePropertyPage:: GetObjectArray

Zwraca tablicę obiektów, które są edytowane przez stronę właściwości.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parametry

*pnObjects*<br/>
Wskaźnik do bezcyfrowej liczby całkowitej bez znaku, która będzie otrzymywać liczbę obiektów edytowanych przez stronę.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do tablicy wskaźników `IDispatch`, które są używane do uzyskiwania dostępu do właściwości każdej kontrolki na stronie właściwości. Obiekt wywołujący nie może zwolnić tych wskaźników interfejsu.

### <a name="remarks"></a>Uwagi

Każdy obiekt strony właściwości zachowuje tablicę wskaźników do `IDispatch` interfejsów obiektów, które są edytowane przez stronę. Ta funkcja ustawia swój argument *pnObjects* na liczbę elementów w tej tablicy i zwraca wskaźnik do pierwszego elementu tablicy.

##  <a name="getpagesite"></a>COlePropertyPage:: GetPageSite

Pobiera wskaźnik do interfejsu `IPropertyPageSite` strony właściwości.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do `IPropertyPageSite` interfejsu strony właściwości.

### <a name="remarks"></a>Uwagi

Kontrolki i kontenery współpracują tak, aby użytkownicy mogli przeglądać i edytować właściwości kontrolek. Formant zawiera strony właściwości, z których każdy jest obiektem OLE, który umożliwia użytkownikowi edytowanie powiązanego zestawu właściwości. Kontener zawiera ramkę właściwości, która wyświetla strony właściwości. Dla każdej strony ramka właściwości zawiera witrynę strony, która obsługuje interfejs `IPropertyPageSite`.

##  <a name="ignoreapply"></a>COlePropertyPage:: IgnoreApply

Określa, które kontrolki nie włączają przycisku Zastosuj.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator formantu, który ma zostać zignorowany.

### <a name="remarks"></a>Uwagi

Przycisk Zastosuj strony właściwości jest włączony tylko wtedy, gdy zmieniono wartości kontrolek strony właściwości. Użyj tej funkcji, aby określić kontrolki, które nie powodują włączenia przycisku Zastosuj, gdy ich wartości zmienią się.

##  <a name="ismodified"></a>COlePropertyPage:: IsModified

Określa, czy użytkownik zmienił wszystkie wartości na stronie właściwości.

```
BOOL IsModified();
```

### <a name="return-value"></a>Wartość zwrócona

Ma wartość TRUE, jeśli strona właściwości została zmodyfikowana.

##  <a name="oneditproperty"></a>COlePropertyPage:: OnEditProperty

Struktura wywołuje tę funkcję, gdy określona właściwość ma być edytowana.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
Identyfikator wysyłania edytowanej właściwości.

### <a name="return-value"></a>Wartość zwrócona

Domyślna implementacja zwraca wartość FALSE. Zastąpienia tej funkcji powinny zwrócić wartość TRUE.

### <a name="remarks"></a>Uwagi

Można zastąpić tę wartość, aby ustawić fokus na odpowiedniej kontrolce na stronie. Domyślna implementacja nie robi niczego i zwraca wartość FALSE.

##  <a name="onhelp"></a>COlePropertyPage:: OnHelp

Struktura wywołuje tę funkcję, gdy użytkownik zażąda pomocy online.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parametry

*lpszHelpDir*<br/>
Katalog zawierający plik pomocy strony właściwości.

### <a name="return-value"></a>Wartość zwrócona

Domyślna implementacja zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Zastąp go, jeśli strona właściwości musi wykonać wszelkie specjalne akcje, gdy użytkownik uzyskuje dostęp do pomocy. Implementacja domyślna nie robi niczego i zwraca wartość FALSE, co sprawia, że struktura wywołuje polecenie WinHelp.

##  <a name="oninitdialog"></a>COlePropertyPage:: OnInitDialog

Struktura wywołuje tę funkcję po zainicjowaniu okna dialogowego strony właściwości.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwrócona

Domyślna implementacja zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Zastąp go, jeśli jakakolwiek akcja specjalna jest wymagana po zainicjowaniu okna dialogowego. Domyślne wywołania implementacji `CDialog::OnInitDialog` i zwracają wartość FALSE.

##  <a name="onobjectschanged"></a>COlePropertyPage:: OnObjectsChanged

Wywoływane przez platformę, gdy jest wybierana inna kontrolka OLE z nowymi właściwościami.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Uwagi

Podczas wyświetlania właściwości kontrolki OLE w środowisku deweloperskim, niemodalne okno dialogowe służy do wyświetlania jego stron właściwości. Jeśli wybrana jest inna kontrolka, dla nowego zestawu właściwości muszą być wyświetlane różne zestawy stron właściwości. Struktura wywołuje tę funkcję, aby powiadomić stronę właściwości zmiany.

Przesłoń tę funkcję, aby otrzymać powiadomienie o tej akcji i wykonać wszelkie specjalne działania.

##  <a name="onsetpagesite"></a>COlePropertyPage:: OnSetPageSite

Struktura wywołuje tę funkcję, gdy ramka właściwości udostępnia witrynę strony właściwości.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Uwagi

Implementacja domyślna ładuje podpis strony i próbuje określić rozmiar strony z zasobu okna dialogowego. Przesłoń tę funkcję, jeśli strona właściwości wymaga dalszych akcji. przesłonięcie powinno wywoływać implementację klasy podstawowej.

##  <a name="setcontrolstatus"></a>COlePropertyPage:: SetControlStatus

Zmienia stan kontrolki strony właściwości.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Zawiera identyfikator kontrolki strony właściwości.

*bDirty*<br/>
Określa, czy pole strony właściwości zostało zmodyfikowane. Ustaw wartość TRUE, jeśli pole zostało zmodyfikowane, wartość FALSE, jeśli nie została zmodyfikowana.

### <a name="return-value"></a>Wartość zwrócona

PRAWDA, jeśli ustawiono określony formant; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli stan kontrolki strony właściwości jest zanieczyszczony, gdy strona właściwości jest ZAMKNIĘTA lub wybrano przycisk Zastosuj, właściwość kontrolki zostanie zaktualizowana o odpowiednią wartość.

##  <a name="setdialogresource"></a>COlePropertyPage:: SetDialogResource

Ustawia zasób okna dialogowego strony właściwości.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parametry

*hDialog*<br/>
Dojście do zasobu okna dialogowego strony właściwości.

##  <a name="sethelpinfo"></a>COlePropertyPage:: SetHelpInfo

Określa informacje o etykietce narzędzia, nazwę pliku pomocy i kontekst pomocy dla strony właściwości.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parametry

*lpszDocString*<br/>
Ciąg zawierający krótkie informacje pomocy, które mają być wyświetlane na pasku stanu lub w innej lokalizacji.

*lpszHelpFile*<br/>
Nazwa pliku pomocy strony właściwości.

*dwHelpContext*<br/>
Kontekst pomocy dla strony właściwości.

##  <a name="setmodifiedflag"></a>COlePropertyPage:: SetModifiedFlag

Wskazuje, czy użytkownik zmodyfikował stronę właściwości.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Określa nową wartość flagi modyfikacji strony właściwości.

##  <a name="setpagename"></a>COlePropertyPage:: SetPageName

Ustawia nazwę strony właściwości, która jest zwykle wyświetlana na karcie strony.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
Wskaźnik na ciąg zawierający nazwę strony właściwości.

## <a name="see-also"></a>Zobacz też

[Przykład CIRC3 MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład TESTHELP MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
