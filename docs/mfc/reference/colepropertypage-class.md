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
ms.openlocfilehash: e8328fb4987044c5a28b1a6a6ce19c674039dea9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376213"
---
# <a name="colepropertypage-class"></a>COlePropertyPage — klasa
Umożliwia wyświetlenie właściwości formantu niestandardowego interfejsu graficznego, podobnie do okna dialogowego.  
  
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
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Wskazuje, czy użytkownik zmienił wartość kontrolki.|  
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Zwraca tablicę obiektów edytowany przez stronę właściwości.|  
|[COlePropertyPage::GetPageSite](#getpagesite)|Zwraca wskaźnik do strony właściwości `IPropertyPageSite` interfejsu.|  
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Określa, które kontrolki nie należy włączać przycisk Zastosuj.|  
|[COlePropertyPage::IsModified](#ismodified)|Wskazuje, czy użytkownik ma stronę właściwości.|  
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Wywoływane przez platformę, gdy użytkownik edytuje właściwość.|  
|[COlePropertyPage::OnHelp](#onhelp)|Wywoływane przez platformę, gdy użytkownik wywoła Pomoc.|  
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Wywoływane przez platformę po zainicjowaniu strony właściwości.|  
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Wywoływane przez platformę, gdy wybrano inną kontrolkę OLE z nowymi właściwościami.|  
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|Wywoływane przez platformę, gdy ramka właściwości dostarcza adres strony Web.|  
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Ustawia flagę wskazującą, czy użytkownik zmienił wartość kontrolki.|  
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Ustawia zasobu okna dialogowego strony właściwości.|  
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Ustawia tekst pomocy krótki strony właściwości, nazwy pliku w jego pomocy i kontekst pomocy.|  
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Ustawia flagę wskazującą, czy użytkownik zmodyfikował stronę właściwości.|  
|[COlePropertyPage::SetPageName](#setpagename)|Ustawia nazwę strony właściwości (podpis).|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład strona właściwości może zawierać formant edycji, który umożliwia użytkownikowi wyświetlanie i modyfikowanie właściwości formantu podpis.  
  
 Każda właściwość Kontrolki niestandardowe lub standardowych może mieć formant okna dialogowego, który umożliwia użytkownikowi formantu wyświetlić bieżącą wartość właściwości i w razie potrzeby zmodyfikuj tę wartość.  
  
 Aby uzyskać więcej informacji na temat używania `COlePropertyPage`, zapoznaj się z artykułem [formantów ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).  
  
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
 *idDlg*  
 Identyfikator zasobu szablonu okna dialogowego.  
  
 *idCaption*  
 Identyfikator zasobu podpisu strony właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Podczas implementacji podklasą `COlePropertyPage`, należy użyć konstruktora z podklasy `COlePropertyPage` konstruktora do identyfikacji zasobu szablonu okna dialogowego na podstawie stronę właściwości i zasobu ciągu zawierającego podpisem.  
  
##  <a name="getcontrolstatus"></a>  COlePropertyPage::GetControlStatus  
 Określa, czy użytkownik zmienił wartość kontrolki strony właściwości o identyfikatorze określonego zasobu.  
  
```  
BOOL GetControlStatus(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator zasobu formantu strony właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli wartość formantu został zmodyfikowany, a w przeciwnym **FALSE**.  
  
##  <a name="getobjectarray"></a>  COlePropertyPage::GetObjectArray  
 Zwraca tablicę obiektów edytowany przez stronę właściwości.  
  
```  
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```  
  
### <a name="parameters"></a>Parametry  
 `pnObjects`  
 Wskaźnik do niepodpisanego długich liczb całkowitych odbioru liczbę obiektów edytowany przez stronę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do tablicy `IDispatch` wskaźników, które są używane do dostępu do właściwości każdej kontrolki na stronie właściwości. Obiekt wywołujący nie trzeba zwolnić te wskaźniki interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Każdy obiekt strony właściwości zachowuje tablicy wskaźników do `IDispatch` interfejsów obiektów edytowany przez stronę. Ta funkcja ustawia jego `pnObjects` argument liczba elementów w tablicy i zwraca wskaźnik do pierwszego elementu tablicy.  
  
##  <a name="getpagesite"></a>  COlePropertyPage::GetPageSite  
 Pobiera wskaźnik do strony właściwości `IPropertyPageSite` interfejsu.  
  
```  
LPPROPERTYPAGESITE GetPageSite();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do strony właściwości `IPropertyPageSite` interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Formanty i kontenery współpracują, aby użytkownicy mogli przeglądanie i edytowanie właściwości formantu. Formant zawiera strony właściwości, z których każdy jest obiektu OLE, który umożliwia użytkownikom edytowanie odpowiedniego zbioru właściwości. Kontener zawiera ramka właściwości, którym są wyświetlane na stronach właściwości. Dla każdej strony ramka właściwości dostarcza lokacji strony, która obsługuje `IPropertyPageSite` interfejsu.  
  
##  <a name="ignoreapply"></a>  COlePropertyPage::IgnoreApply  
 Określa, które kontrolki nie należy włączać przycisk Zastosuj.  
  
```  
void IgnoreApply(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator formantu ma być ignorowane.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk Zastosuj stronę właściwości jest włączona tylko wtedy, gdy zostały zmienione wartości właściwości formantów strony. Ta funkcja umożliwia określenie formantów, które nie powodują przycisk Zastosuj, aby umożliwiać zmiany ich wartości.  
  
##  <a name="ismodified"></a>  COlePropertyPage::IsModified  
 Określa, czy użytkownik zmienił wartości na stronie właściwości.  
  
```  
BOOL IsModified();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli zmodyfikowano stronę właściwości.  
  
##  <a name="oneditproperty"></a>  COlePropertyPage::OnEditProperty  
 Struktura wywołuje tej funkcji w przypadku konkretnej właściwości można edytować.  
  
```  
virtual BOOL OnEditProperty(DISPID dispid);
```  
  
### <a name="parameters"></a>Parametry  
 `dispid`  
 Identyfikator wysyłania właściwości edytowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca **FALSE**. Zastąpienia tej funkcji powinna zwrócić **TRUE**.  
  
### <a name="remarks"></a>Uwagi  
 Można je zastąpić, aby ustawić fokus do odpowiedniej kontrolki na stronie. Domyślna implementacja nie robi nic i zwraca **FALSE**.  
  
##  <a name="onhelp"></a>  COlePropertyPage::OnHelp  
 Struktura wywołuje tej funkcji, gdy użytkownik zażąda pomocy online.  
  
```  
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszHelpDir*  
 Katalog zawierający plik Pomocy strony właściwości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpić go, jeśli strony właściwości, które należy wykonać dowolną akcję specjalną, gdy użytkownik uzyskuje dostęp do pomocy. Domyślna implementacja nie robi nic i zwraca **FALSE**, który powoduje, że framework do wywołania WinHelp.  
  
##  <a name="oninitdialog"></a>  COlePropertyPage::OnInitDialog  
 Struktura wywołuje tej funkcji po zainicjowaniu okno dialogowe strony właściwości.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie go, jeśli dowolną akcję specjalną, jest wymagana podczas inicjowania okna dialogowego. Domyślna implementacja wywołuje `CDialog::OnInitDialog` i zwraca **FALSE**.  
  
##  <a name="onobjectschanged"></a>  COlePropertyPage::OnObjectsChanged  
 Wywoływane przez platformę, gdy wybrano inną kontrolkę OLE z nowymi właściwościami.  
  
```  
virtual void OnObjectsChanged();
```  
  
### <a name="remarks"></a>Uwagi  
 Podczas przeglądania właściwości formantu OLE w Środowisko deweloperskie, niemodalne okno dialogowe służy do wyświetlania stron jej właściwości. Jeśli inny formant jest zaznaczone, inny zestaw stron właściwości musi być wyświetlona nowego zestawu właściwości. Struktura wywołuje tę funkcję, aby powiadomić strony właściwości tej zmiany.  
  
 Należy przesłonić tę funkcję, aby otrzymać powiadomienie o tej akcji i wykonywać żadnych specjalnych działań.  
  
##  <a name="onsetpagesite"></a>  COlePropertyPage::OnSetPageSite  
 Struktura wywołuje tej funkcji, gdy ramka właściwości dostarcza stronę właściwości strony witryny.  
  
```  
virtual void OnSetPageSite();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ładuje podpisu strony i spróbuje określić rozmiar strony z zasobu okna dialogowego. Zastąpienie tej funkcji, jeśli strony właściwości wymaga dalszych działań; zastąpienia powinny wywoływać implementację klasy podstawowej.  
  
##  <a name="setcontrolstatus"></a>  COlePropertyPage::SetControlStatus  
 Zmienia stan formantu strony właściwości.  
  
```  
BOOL SetControlStatus(
    UINT nID,  
    BOOL bDirty);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Zawiera identyfikator formantu strony właściwości.  
  
 `bDirty`  
 Określa, jeśli zmodyfikowano pola strony właściwości. Ustaw **TRUE** w przypadku modyfikacji pola **FALSE** Jeśli nie zostały zmodyfikowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,**, jeśli określony formant został ustawiony; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli stan formantu strony właściwości jest zanieczyszczony po zamknięciu strony właściwości lub zostanie wybrany przycisk Zastosuj, formantu zostanie zaktualizowana na odpowiednią wartość.  
  
##  <a name="setdialogresource"></a>  COlePropertyPage::SetDialogResource  
 Ustawia zasobu okna dialogowego strony właściwości.  
  
```  
void SetDialogResource(HGLOBAL hDialog);
```  
  
### <a name="parameters"></a>Parametry  
 *hDialog*  
 Dojście do zasobu okna dialogowego strony właściwości.  
  
##  <a name="sethelpinfo"></a>  COlePropertyPage::SetHelpInfo  
 Określa informacje etykietka narzędzia, nazwa pliku pomocy i kontekstu Pomoc na stronie właściwości.  
  
```  
void SetHelpInfo(
    LPCTSTR lpszDocString,  
    LPCTSTR lpszHelpFile = NULL,  
    DWORD dwHelpContext = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszDocString*  
 Ciąg zawierający informacje pomocy krótki do wyświetlania na pasku stanu lub innej lokalizacji.  
  
 `lpszHelpFile`  
 Nazwa pliku pomocy strony właściwości.  
  
 *dwHelpContext*  
 Kontekst pomocy dla strony właściwości.  
  
##  <a name="setmodifiedflag"></a>  COlePropertyPage::SetModifiedFlag  
 Wskazuje, czy użytkownik ma stronę właściwości.  
  
```  
void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bModified`  
 Określa nową wartość flagi zmodyfikowane strony właściwości.  
  
##  <a name="setpagename"></a>  COlePropertyPage::SetPageName  
 Ustawia nazwę strony właściwości, która ramka właściwości zazwyczaj będzie wyświetlana na karcie strony.  
  
```  
void SetPageName(LPCTSTR lpszPageName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPageName*  
 Wskaźnik do ciąg zawierający nazwę strony właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [CIRC3 próbki MFC](../../visual-cpp-samples.md)   
 [Przykładowe MFC TESTHELP](../../visual-cpp-samples.md)   
 [Cdialog — klasa](../../mfc/reference/cdialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDialog](../../mfc/reference/cdialog-class.md)
