---
title: Procedury wymiany danych standardowe okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c79a96439605bcf9ab670c1f75dda2d50169f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377658"
---
# <a name="standard-dialog-data-exchange-routines"></a>Standardowe procedury wymiany danych w oknie dialogowym
W tym temacie wymieniono standardowe procedury okna dialogowego danych programu exchange (DDX) używany dla typowych formantów okna dialogowego MFC.  
  
> [!NOTE]
>  Standardowe procedury wymiany danych są definiowane w afxdd_.h pliku nagłówka. Jednak aplikacje powinny zawierać afxwin.h.  
  
### <a name="ddx-functions"></a>Funkcje DDX  
  
|||  
|-|-|  
|[Ddx_cbindex —](#ddx_cbindex)|Inicjuje i pobiera indeks bieżącego zaznaczenia kontrolki pola kombi.|  
|[Ddx_cbstring —](#ddx_cbstring)|Inicjuje i pobiera bieżącą zawartość pola edycji kontrolki pola kombi.|  
|[Ddx_cbstringexact —](#ddx_cbstringexact)|Inicjuje i pobiera bieżącą zawartość pola edycji kontrolki pola kombi.|  
|[Ddx_check —](#ddx_check)|Inicjuje i pobiera bieżący stan kontrolkę pola wyboru.|  
|[Ddx_control —](#ddx_control)|Podklasy określonej kontrolki w oknie dialogowym.|  
|[Ddx_datetimectrl —](#ddx_datetimectrl)|Inicjuje i pobiera datę i/lub godzinę danych formantu selektora daty i godziny.|  
|[Ddx_ipaddress —](#ddx_ipaddress)|Inicjuje lub pobiera bieżącą wartość formantu adresu IP.|  
|[Ddx_lbindex —](#ddx_lbindex)|Inicjuje i pobiera indeks bieżącego zaznaczenia pole listy.|  
|[Ddx_lbstring —](#ddx_lbstring)|Inicjuje i pobiera bieżące zaznaczenie w formancie pola listy.|  
|[Ddx_lbstringexact —](#ddx_lbstringexact)|Inicjuje i pobiera bieżące zaznaczenie w formancie pola listy.|
|[Ddx_managedcontrol —](#ddx_managedcontrol)|Tworzy kontrolkę .NET dopasowania identyfikatora formantu zasobu.|  
|[Ddx_monthcalctrl —](#ddx_monthcalctrl)|Inicjuje lub pobiera bieżącą wartość formantu kalendarza miesięcznego.|  
|[Ddx_radio —](#ddx_radio)|Inicjuje i pobiera indeksu na podstawie 0 formantu radiowego, który jest aktualnie zaznaczone w grupie kontroli opcji.|  
|[Ddx_scroll —](#ddx_scroll)|Inicjuje i pobiera bieżącej pozycji przycisku przewijania formantu.|  
|[Ddx_slider —](#ddx_slider)|Inicjuje i pobiera bieżącej pozycji przycisku przewijania suwaka.|  
|[Ddx_text —](#ddx_text)|Inicjuje lub pobiera bieżącą wartość formantu edycyjnego.|  
  
##  <a name="ddx_cbindex"></a>  Ddx_cbindex —  
 `DDX_CBIndex` Funkcji zarządzania transferem `int` tworzą dane między kontrolki pola kombi, w oknie dialogowym, widoku lub formantu widoku obiektu i `int` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontrolki pola kombi, które są skojarzone z właściwości formantu.  
  
 *index*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_CBIndex` jest nazywany *indeksu* jest ustawiona na indeks bieżącego zaznaczenia pola kombi. Jeśli nie wybrano elementów, *indeksu* jest równa 0.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_cbstring"></a>  Ddx_cbstring —  
 `DDX_CBString` Funkcji zarządzania transferem `CString` tworzą dane między formancie edycyjnym pola kombi formantu w oknie dialogowym, widoku lub formantu widoku obiektu i `CString` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_CBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontrolki pola kombi, które są skojarzone z właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_CBString` jest nazywany *wartość* ustawiono bieżące zaznaczenie pola kombi. Jeśli nie wybrano elementów, *wartość* jest ustawiona na ciąg o zerowej długości.  
  
> [!NOTE]
>  Jeśli pole listy rozwijanej pola kombi, wartość wymieniane jest maksymalnie 255 znaków.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_cbstringexact"></a>  Ddx_cbstringexact —  
 `DDX_CBStringExact` Funkcji zarządzania transferem `CString` tworzą dane między formancie edycyjnym pola kombi formantu w oknie dialogowym, widoku lub formantu widoku obiektu i `CString` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontrolki pola kombi, które są skojarzone z właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_CBStringExact` jest nazywany *wartość* ustawiono bieżące zaznaczenie pola kombi. Jeśli nie wybrano elementów, *wartość* jest ustawiona na ciąg o zerowej długości.  
  
> [!NOTE]
>  Jeśli pole listy rozwijanej pola kombi, wartość wymieniane jest maksymalnie 255 znaków.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_check"></a>  Ddx_check —  
 `DDX_Check` Funkcji zarządzania transferem `int` tworzą dane między kontrolkę pola wyboru w oknie dialogowym, widoku lub formantu widoku obiektu i `int` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_Check(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontrolkę pola wyboru skojarzone z właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_Check` jest nazywany *wartość* ustawiono bieżący stan kontrolkę pola wyboru. Listę wartości stanu to możliwe, zobacz [BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_control"></a>  Ddx_control —  
 `DDX_Control` Funkcji podklasy formantu, określony przez `nIDC`, okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu.  
  
 `nIDC`  
 Identyfikator zasobu formantu do odziedziczenia.  
  
 *rControl*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu związane z określonego formantu.  
  
### <a name="remarks"></a>Uwagi  
 `pDX` Obiektu jest dostarczane przez platformę, gdy `DoDataExchange` funkcja jest wywoływana. W związku z tym `DDX_Control` powinna być wywoływana tylko w obrębie zastąpienia z `DoDataExchange`.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_datetimectrl"></a>  Ddx_datetimectrl —  
 `DDX_DateTimeCtrl` Funkcji zarządzania transferem danych daty i godziny między formant wyboru daty i godziny ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) w oknie dialogowym pole formularza widok obiektu lub i albo [ctime —](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) elementu członkowskiego danych obiektu okna dialogowego pola lub formularza widoku.  
  
```  
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku. Nie trzeba usunąć ten obiekt.  
  
 `nIDC`  
 Identyfikator zasobu formant wyboru daty i godziny, skojarzone ze zmienną elementu członkowskiego.  
  
 *value*  
 W wersjach pierwsze dwa odwołania do `CTime` lub `COleDateTime` zmiennej członkowskiej, okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych. W trzeciej wersji odwołania do `CString` obiekt widoku formantu elementu członkowskiego danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_DateTimeCtrl` jest wywoływana, *wartość* ma ustawioną wartość bieżącego stanu daty i czasu formant wyboru lub formantu ma ustawioną wartość *wartość*w zależności od kierunku programu exchange.  
  
 W trzeciej wersji powyżej `DDX_DateTimeCtrl` zarządza transferem `CString` danych między datą czasu kontroli i [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) elementu członkowskiego danych obiektu formantu widoku. Ciąg sformatowany przy użyciu bieżących ustawień regionalnych reguły formatowania daty i godziny.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  

   

 
## <a name="ddx_managedcontrol"></a>  Ddx_managedcontrol —
Tworzy kontrolkę .NET dopasowania identyfikatora formantu zasobu.  
   
### <a name="syntax"></a>Składnia  
  ```  
template <typename T>  
void DDX_ManagedControl(  
     CDataExchange* pDX,   
     int nIDC,   
     CWinFormsControl<T>& control );  
```
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do [cdataexchange — klasa](cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontroli powiązanej z właściwością formantu.  
  
 `control`  
 Odwołanie do [klasy CWinFormsControl](cwinformscontrol-class.md) obiektu.  
   
### <a name="remarks"></a>Uwagi  
 `DDX_ManagedControl` wywołania [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) można utworzyć formantu, pasujące z identyfikatorem zasobu formantu. Użyj `DDX_ManagedControl` do tworzenia kontrolek z identyfikatorów zasobów w [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Dla danych programu exchange nie trzeba funkcje DDX/DDV za pomocą formantów formularzy systemu Windows.  
  
 Aby uzyskać więcej informacji, zobacz [porady: czy powiązania danych DDX/ddv za pomocą interfejsu Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h  
   
### <a name="see-also"></a>Zobacz też  
 [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)   
 [CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
 

  
##  <a name="ddx_ipaddress"></a>  Ddx_ipaddress —  
 `DDX_IPAddress` Funkcji zarządza przesyłaniem danych między formantem adresu IP, a element członkowski danych klasy obiektu formantu widoku.  
  
```  
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu formantu adres IP skojarzony z właściwością formantu.  
  
 *value*  
 Odwołanie do `DWORD` zawierający wartość pola czterech formant adresu IP. Pola są wypełnione lub odczytać w następujący sposób.  
  
|Pole|Usługa BITS zawierający wartość pola|  
|-----------|-------------------------------------|  
|3|od 0 do 7|  
|2|8 do 15|  
|1|16 do 23|  
|0|24 do 31|  
  
 Użyj środowiska Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378) do odczytu wartości lub użyć [IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380) do wypełnienia wartość. Komunikaty te są opisane w zestawie SDK systemu Windows.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_IPAddress` po wywołaniu *wartość* jest albo odczytywać formant adresu IP, lub *wartość* są zapisywane do kontrolki, w zależności od kierunku programu exchange.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_lbindex"></a>  Ddx_lbindex —  
 `DDX_LBIndex` Funkcji zarządzania transferem `int` tworzą dane między pole listy w oknie dialogowym, widoku lub formantu widoku obiektu i `int` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontrolkę pola listy, które są skojarzone z właściwości formantu.  
  
 *index*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_LBIndex` jest nazywany *indeksu* jest ustawiona na indeks bieżące zaznaczenie w polu listy. Jeśli nie wybrano elementów, *indeksu* ma ustawioną wartość -1.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_lbstring"></a>  Ddx_lbstring —  
 `DDX_LBString` Funkcji zarządzania transferem `CString` tworzą dane między pole listy w oknie dialogowym, widoku lub formantu widoku obiektu i `CString` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_LBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontrolkę pola listy, które są skojarzone z właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_LBString` jest wywoływana na przesyłanie danych do kontrolki pola listy, pierwszego elementu w formancie, którego początek jest zgodna *wartość* jest zaznaczone. (Aby dopasować cały element, a nie tylko prefiks, użyj [ddx_lbstringexact —](#ddx_lbstringexact).) Jeśli nie ma zgodnych wyników, nie wybrano elementów. Dopasowanie jest rozróżniana wielkość liter.  
  
 Gdy `DDX_LBString` jest wywoływana na przesyłanie danych z formantu pole listy *wartość* ustawiono bieżące zaznaczenie w polu listy. Jeśli nie wybrano elementów, *wartość* jest ustawiona na ciąg o zerowej długości.  
  
> [!NOTE]
>  Jeśli pole listy ma pole listy rozwijanej, wartość wymieniane jest maksymalnie 255 znaków.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_lbstringexact"></a>  Ddx_lbstringexact —  
 `DDX_CBStringExact` Funkcji zarządzania transferem `CString` tworzą dane między kontrolki edycji z pole listy w oknie dialogowym, widoku lub formantu widoku obiektu i `CString` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu kontrolkę pola listy, które są skojarzone z właściwości formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_LBStringExact` jest wywoływana na przesyłanie danych do formantu pole listy pierwszego elementu w formancie, który pasuje *wartość* jest zaznaczone. (Aby dopasować tylko prefiksu, a nie cały element, użyj [ddx_lbstring —](#ddx_lbstring).) Jeśli nie ma zgodnych wyników, nie wybrano elementów. Dopasowanie jest rozróżniana wielkość liter.  
  
 Gdy `DDX_CBStringExact` jest wywoływana na przesyłanie danych z formantu pole listy *wartość* ustawiono bieżące zaznaczenie w polu listy. Jeśli nie wybrano elementów, *wartość* jest ustawiona na ciąg o zerowej długości.  
  
> [!NOTE]
>  Jeśli pole listy ma pole listy rozwijanej, wartość wymieniane jest maksymalnie 255 znaków.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_monthcalctrl"></a>  Ddx_monthcalctrl —  
 `DDX_MonthCalCtrl` Funkcji zarządzania transferem danych Data między formant kalendarza miesięcznego ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) w okno dialogowe, widoku Formularz lub formant widoku obiektu i albo [ctime —](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku. Nie trzeba usunąć ten obiekt.  
  
 `nIDC`  
 Identyfikator zasobu w formancie kalendarza miesięcznego skojarzone ze zmienną elementu członkowskiego.  
  
 *value*  
 Odwołanie do `CTime` lub `COleDateTime` zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Formant zarządza wartości daty. W polach czasu w obiekcie czasu są zestawu do uwzględnienia podczas tworzenia okna formantu, lub niezależnie od czasu został ustawiony w formancie wywołaniem `CMonthCalCtrl::SetCurSel`.  
  
 Gdy `DDX_MonthCalCtrl` jest nazywany *wartość* ustawiono bieżący stan formant kalendarza miesięcznego.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_radio"></a>  Ddx_radio —  
 `DDX_Radio` Funkcji zarządzania transferem `int` tworzą dane między grupą radiowych formantu w oknie dialogowym, widoku lub formantu widoku obiektu i `int` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu. Wartość `int` elementu członkowskiego danych jest określana, zgodnie z opcji, które w grupie jest zaznaczona.  
  
```  
void AFXAPI DDX_Radio(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu pierwszego radiowych formantu w grupie.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant widoku obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_Radio` jest nazywany *wartość* ustawiono bieżący stan grupy opcji kontroli. Wartość jest ustawiona jako indeks 0 na podstawie formantu radiowego, który jest aktualnie zaznaczony lub -1, jeśli żadne formanty radiowych są sprawdzane.  
  
 Na przykład w przypadku, który jest pierwszy przycisk radiowy w grupie zaznaczone (przycisk o stylu ws_group —) wartość `int` element członkowski jest 0 i tak dalej.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_scroll"></a>  Ddx_scroll —  
 `DDX_Scroll` Funkcji zarządzania transferem `int` tworzą dane między formantu paska przewijania w oknie dialogowym, widoku lub formantu widoku obiektu i `int` element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu formantu paska przewijania skojarzony z właściwością formantu.  
  
 *value*  
 Odwołanie do zmiennej członkowskiej — okno dialogowe, widoku Formularz lub formant wyświetlania obiektu wymiany danych.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_Scroll` jest nazywany *wartość* ma ustawioną wartość bieżącej pozycji przycisku przewijania formantu. Aby uzyskać więcej informacji o wartości skojarzone z bieżącego położenia kontrolki thumb, zobacz [GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_slider"></a>  Ddx_slider —  
 `DDX_Slider` Funkcji zarządzania transferem `int` danych między formantu suwaka w widoku okna dialogowego pola lub formularza i `int` elementu członkowskiego danych obiektu okna dialogowego pola lub formularza widoku.  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator zasobu suwaka.  
  
 *value*  
 Odwołanie do wartości, aby wymienić. Ten parametr zawiera lub ustawia bieżącego położenia kontrolki suwaka.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `DDX_Slider` jest nazywany *wartość* ma ustawioną wartość bieżącej pozycji przycisku przewijania formantu, lub wartość odbiera sytuację, w zależności od kierunku programu exchange.  
  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md). Uzyskać informacje o formantach suwaka, zobacz [przy użyciu CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  
  
##  <a name="ddx_text"></a>  Ddx_text —  
 `DDX_Text` Funkcji zarządzania transferem `int`, **UINT**, **długi**, `DWORD`, `CString`, **float**, lub  **Podwójna** danych między kontrolki edycji w oknie dialogowym, widok formularza lub kontrolować widoku i [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) element członkowski danych okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
```  
void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do [cdataexchange —](../../mfc/reference/cdataexchange-class.md) obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `nIDC`  
 Identyfikator formantu edycyjnego w okno dialogowe, widoku Formularz lub formant widoku obiektu.  
  
 *value*  
 Odwołanie do elementu członkowskiego danych w okno dialogowe, widoku Formularz lub formant widoku obiektu. Typ danych miary *wartość* zależy od której zastąpionej wersji `DDX_Text` używasz.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxdd_.h  

## <a name="see-also"></a>Zobacz też  
 [Procedury walidacji danych standardowe okno dialogowe](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
