---
title: Standardowe procedury wymiany danych w oknie dialogowym
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 06153a72ce6ed6e5422022255eec333110709778
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618312"
---
# <a name="standard-dialog-data-exchange-routines"></a>Standardowe procedury wymiany danych w oknie dialogowym

Ten temat zawiera standardowe procedury wymiany danych w (DDX) używany dla typowych formantów okna dialogowego MFC.

> [!NOTE]
>  Procedury wymiany danych w standardowe okno dialogowe, są definiowane w afxdd_.h pliku nagłówka. Jednak aplikacje powinny zawierać afxwin.h.

### <a name="ddx-functions"></a>Funkcje DDX

|||
|-|-|
|[Ddx_cbindex —](#ddx_cbindex)|Inicjuje lub pobiera indeks bieżącego zaznaczenia kontrolki pola kombi.|
|[Ddx_cbstring —](#ddx_cbstring)|Inicjuje lub pobiera bieżącą zawartość pola edycji kontrolki pola kombi.|
|[Ddx_cbstringexact —](#ddx_cbstringexact)|Inicjuje lub pobiera bieżącą zawartość pola edycji kontrolki pola kombi.|
|[Ddx_check —](#ddx_check)|Inicjuje lub pobiera bieżący stan kontrolkę pola wyboru.|
|[Ddx_control —](#ddx_control)|Podklasy określonej kontrolki w oknie dialogowym.|
|[Ddx_datetimectrl —](#ddx_datetimectrl)|Inicjuje lub pobiera dane daty i godziny kontrolki selektora daty i godziny.|
|[Ddx_ipaddress —](#ddx_ipaddress)|Inicjuje lub pobiera bieżącą wartość formant adresu IP.|
|[Ddx_lbindex —](#ddx_lbindex)|Inicjuje lub pobiera indeks bieżącego zaznaczenia formant pola listy.|
|[Ddx_lbstring —](#ddx_lbstring)|Inicjuje lub pobiera bieżące zaznaczenie w kontrolce pola listy.|
|[Ddx_lbstringexact —](#ddx_lbstringexact)|Inicjuje lub pobiera bieżące zaznaczenie w kontrolce pola listy.|
|[Ddx_managedcontrol —](#ddx_managedcontrol)|Tworzy formant .NET dopasowania identyfikator formantu zasobu.|
|[Ddx_monthcalctrl —](#ddx_monthcalctrl)|Inicjuje lub pobiera bieżącą wartość kontrolki kalendarza miesięcznego.|
|[Ddx_radio —](#ddx_radio)|Inicjuje lub pobiera indeks oparty na 0 kontrolce przycisku radiowego, który aktualnie jest ewidencjonowany w grupie sterowania opcji.|
|[Ddx_scroll —](#ddx_scroll)|Inicjuje lub pobiera bieżące położenie kontrolki przewijania thumb.|
|[Ddx_slider —](#ddx_slider)|Inicjuje lub pobiera bieżącej pozycji przycisku przewijania suwaka.|
|[Ddx_text —](#ddx_text)|Inicjuje lub pobiera bieżącą wartość kontrolki edycji.|

##  <a name="ddx_cbindex"></a>  Ddx_cbindex —

`DDX_CBIndex` Funkcja zarządza transferem **int** danych między kontrolki pola kombi w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **int** element członkowski danych okno dialogowe, widok formularza lub formantu Obiekt widoku.

```
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu formant pola kombi, które są skojarzone z właściwością kontrolki.

*index*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBIndex` jest wywoływana, *indeksu* jest ustawiona na indeks bieżącego zaznaczenia pola kombi. Jeśli żaden element nie jest zaznaczone, *indeksu* jest równa 0.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_cbstring"></a>  Ddx_cbstring —

`DDX_CBString` Funkcja zarządza transferem `CString` danych między kontrolki edycji z kontrolki pola kombi w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i `CString` element członkowski danych okno dialogowe, widok formularza lub formantu obiekt widoku.

```
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu formant pola kombi, które są skojarzone z właściwością kontrolki.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBString` jest wywoływana, *wartość* jest ustawiona na bieżące zaznaczenie pola kombi. Jeśli żaden element nie jest zaznaczone, *wartość* jest ustawiony na ciąg o zerowej długości.

> [!NOTE]
>  Jeśli pole kombi pola listy rozwijanej, wartość wymieniane jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_cbstringexact"></a>  Ddx_cbstringexact —

`DDX_CBStringExact` Funkcja zarządza transferem `CString` danych między kontrolki edycji z kontrolki pola kombi w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i `CString` element członkowski danych okno dialogowe, widok formularza lub formantu obiekt widoku.

```
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu formant pola kombi, które są skojarzone z właściwością kontrolki.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBStringExact` jest wywoływana, *wartość* jest ustawiona na bieżące zaznaczenie pola kombi. Jeśli żaden element nie jest zaznaczone, *wartość* jest ustawiony na ciąg o zerowej długości.

> [!NOTE]
>  Jeśli pole kombi pola listy rozwijanej, wartość wymieniane jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_check"></a>  Ddx_check —

`DDX_Check` Funkcja zarządza transferem **int** danych pomiędzy kontrolce pola wyboru w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **int** element członkowski danych okno dialogowe, widok formularza lub formantu Obiekt widoku.

```
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu w kontrolce pola wyboru skojarzone z właściwością kontrolki.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Check` jest wywoływana, *wartość* jest ustawiona na bieżący stan formant pola wyboru. Aby uzyskać listę stan możliwe wartości, zobacz [BM_GETCHECK](/windows/desktop/Controls/bm-getcheck) w zestawie Windows SDK.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_control"></a>  Ddx_control —

`DDX_Control` Funkcji podklasy kontrolki, określonej przez *nIDC*, okno dialogowe, widok formularza lub formantu obiekt widoku.

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu.

*nIDC*<br/>
Identyfikator zasobu formantu do odziedziczenia.

*rControl*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku związane z określoną kontrolkę.

### <a name="remarks"></a>Uwagi

*PDX* obiektu jest dostarczany przez platformę, gdy `DoDataExchange` funkcja jest wywoływana. W związku z tym `DDX_Control` powinna być wywoływana tylko w ramach zastąpienie metody `DoDataExchange`.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_datetimectrl"></a>  Ddx_datetimectrl —

`DDX_DateTimeCtrl` Funkcja zarządza transferem danych daty i godziny między kontrolkę selektora daty i godziny ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) w okna dialogowego pole lub formularza obiektem widoku, a następnie [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) element członkowski danych z obiektu okna dialogowego pole lub formularza widoku.

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

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku. Nie musisz usunąć tego obiektu.

*nIDC*<br/>
Identyfikator zasobu kontrolka selektora daty i godziny, skojarzone ze zmienną elementu członkowskiego.

*value*<br/>
W pierwszych dwóch wersji, odwołanie do `CTime` lub `COleDateTime` zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych. W trzeciej wersji odwołania do `CString` obiekt widoku formantu element członkowski danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_DateTimeCtrl` jest wywoływana, *wartość* jest ustawiona na bieżący stan datę i formant selektora czasu lub kontrolki jest ustawiony na *wartość*, w zależności od kierunku programu exchange.

W trzeciej wersji powyżej `DDX_DateTimeCtrl` zarządza transferem `CString` danych między wartość typu date time kontroli i [CString](../../atl-mfc-shared/reference/cstringt-class.md) element członkowski danych obiektu widoku formantu. Ten ciąg jest formatowana przy użyciu reguł bieżących ustawień regionalnych formatowania daty i godziny.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_managedcontrol"></a>  Ddx_managedcontrol —

Tworzy formant .NET dopasowania identyfikator formantu zasobu.

### <a name="syntax"></a>Składnia

```
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [klasa CDataExchange](cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu kontroli powiązanej z właściwością kontrolki.

*control*<br/>
Odwołanie do [klasa CWinFormsControl](cwinformscontrol-class.md) obiektu.

### <a name="remarks"></a>Uwagi

`DDX_ManagedControl` wywołania [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) utworzyć kontrolkę dopasowania identyfikatora zasobu formantu. Użyj `DDX_ManagedControl` do tworzenia kontrolek z identyfikatorów zasobów w [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Dla danych programu exchange nie musisz funkcje DDX/DDV za pomocą kontrolek formularzy Windows Forms.

Aby uzyskać więcej informacji, zobacz [porady: wykonaj powiązanie danych DDX/DDV za pomocą interfejsu Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h

### <a name="see-also"></a>Zobacz też

[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)

##  <a name="ddx_ipaddress"></a>  Ddx_ipaddress —

`DDX_IPAddress` Funkcja zarządza przesyłaniem danych między formantem adresu IP, a element członkowski danych obiektu widoku kontroli.

```
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu kontrolki adres IP skojarzony z właściwością kontrolki.

*value*<br/>
Odwołanie do DWORD zawierający wartość pola czterech formant adresu IP. Pola są wypełniane lub przeczytać w następujący sposób.

|Pole|Usługa BITS zawierający wartość pola|
|-----------|-------------------------------------|
|3|od 0 do 7|
|2|8 do 15|
|1|16 do 23|
|0|24 do 31|

Używa Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress) odczytać wartości lub użyć [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress) do wypełnienia wartości. Te komunikaty są opisane w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Gdy `DDX_IPAddress` jest wywoływana, *wartość* jest albo odczytywać formant adresu IP lub *wartość* są zapisywane do kontrolki, w zależności od kierunku programu exchange.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_lbindex"></a>  Ddx_lbindex —

`DDX_LBIndex` Funkcja zarządza transferem **int** danych między pole listy w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **int** element członkowski danych okno dialogowe, widok formularza lub formantu Obiekt widoku.

```
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu kontrolkę pola listy, które są skojarzone z właściwością kontrolki.

*index*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBIndex` jest wywoływana, *indeksu* jest ustawiona na indeks bieżące zaznaczenie w polu listy. Jeśli żaden element nie jest zaznaczone, *indeksu* jest ustawiona na wartość -1.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_lbstring"></a>  Ddx_lbstring —

`DDX_LBString` Funkcja zarządza transferem `CString` danych między pole listy w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i `CString` element członkowski danych okno dialogowe, widok formularza lub formantu obiekt widoku.

```
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu kontrolkę pola listy, które są skojarzone z właściwością kontrolki.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBString` jest wywoływana w celu przesyłania danych do kontrolki pola listy, pierwszy element w kontrolce, którego początek jest zgodna *wartość* jest zaznaczone. (Aby dopasować cały element, a nie po prostu prefiks, użyj [ddx_lbstringexact —](#ddx_lbstringexact).) Jeśli nie ma żadnych dopasowań, nie wybrano elementów. Dopasowanie jest rozróżniana wielkość liter.

Gdy `DDX_LBString` jest wywoływana, aby przenieść dane z formantu pola listy *wartość* jest ustawiona na bieżące zaznaczenie w polu listy. Jeśli żaden element nie jest zaznaczone, *wartość* jest ustawiony na ciąg o zerowej długości.

> [!NOTE]
>  Jeśli pole listy ma postać pola listy rozwijanej, wartość wymieniane jest ograniczone do 255 znaków.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_lbstringexact"></a>  Ddx_lbstringexact —

`DDX_CBStringExact` Funkcja zarządza transferem `CString` danych między kontrolki edycji formantu pola listy, w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i `CString` element członkowski danych okno dialogowe, widok formularza lub formantu obiekt widoku.

```
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu kontrolkę pola listy, które są skojarzone z właściwością kontrolki.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBStringExact` jest wywoływana w celu przesyłania danych do kontrolki pola listy, pierwszy element w kontrolce, który odpowiada *wartość* jest zaznaczone. (Aby dopasować tylko prefiksu, a nie cały element, należy użyć [ddx_lbstring —](#ddx_lbstring).) Jeśli nie ma żadnych dopasowań, nie wybrano elementów. Dopasowanie jest rozróżniana wielkość liter.

Gdy `DDX_CBStringExact` jest wywoływana, aby przenieść dane z formantu pola listy *wartość* jest ustawiona na bieżące zaznaczenie w polu listy. Jeśli żaden element nie jest zaznaczone, *wartość* jest ustawiony na ciąg o zerowej długości.

> [!NOTE]
>  Jeśli pole listy ma postać pola listy rozwijanej, wartość wymieniane jest ograniczone do 255 znaków.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_monthcalctrl"></a>  Ddx_monthcalctrl —

`DDX_MonthCalCtrl` Funkcja zarządza transferem danych Data między formant kalendarza miesięcznego ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) w okno dialogowe, widok formularza lub kontrolki widoku obiektu i albo [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) element członkowski danych okno dialogowe, widok formularza lub formantu obiekt widoku.

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

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku. Nie musisz usunąć tego obiektu.

*nIDC*<br/>
Identyfikator zasobu formant kalendarza miesięcznego skojarzone ze zmienną elementu członkowskiego.

*value*<br/>
Odwołanie do `CTime` lub `COleDateTime` zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Kontrolka zarządza wartości daty. Pola czasu w obiekcie czasu są zestawu, aby odzwierciedlić czas tworzenia okna formantu lub niezależnie od czasu został ustawiony w formancie z wywołaniem `CMonthCalCtrl::SetCurSel`.

Gdy `DDX_MonthCalCtrl` jest wywoływana, *wartość* jest ustawiona na bieżący stan formant kalendarza miesięcznego.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_radio"></a>  Ddx_radio —

`DDX_Radio` Funkcja zarządza transferem **int** dane między grupą radiowych formantu w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **int** element członkowski danych okno dialogowe, widok formularza lub formantu Obiekt widoku. Wartość **int** element członkowski danych jest określana zgodnie z opcji, które wybrano znajdującego się w grupie.

```
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu w pierwszej kontrolce przycisku radiowego w grupie.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu obiekt widoku wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Radio` jest wywoływana, *wartość* jest ustawiona na bieżący stan grupy opcji kontroli. Wartość jest ustawiana jako indeks oparty na 0, o kontrolce przycisku radiowego, który jest aktualnie sprawdzany lub -1, jeśli brak kontrolek radiowych są sprawdzane.

Na przykład w przypadku, który jest pierwszy przycisk radiowy w grupie zaznaczone (przycisk ze stylem WS_GROUP) wartość **int** element członkowski jest 0, i tak dalej.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_scroll"></a>  Ddx_scroll —

`DDX_Scroll` Funkcja zarządza transferem **int** danych pomiędzy kontrolce paska przewijania w oknie dialogowym, formularz widoku lub obiekt widoku kontroli i **int** element członkowski danych okno dialogowe, widok formularza lub formantu Obiekt widoku.

```
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu formantu paska przewijania, skojarzony z właściwością kontrolki.

*value*<br/>
Odwołanie do zmiennej składowej, okno dialogowe, widok formularza lub formantu wyświetlić obiekt wymiany danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Scroll` jest wywoływana, *wartość* jest ustawiony do bieżącego położenia kontrolki thumb. Aby uzyskać więcej informacji na temat wartości skojarzone z bieżącego położenia kontrolki thumb, zobacz [GetScrollPos](/windows/desktop/api/winuser/nf-winuser-getscrollpos) w zestawie Windows SDK.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_slider"></a>  Ddx_slider —

`DDX_Slider` Funkcja zarządza transferem **int** danych pomiędzy kontrolce suwaka w widoku okna dialogowego pole lub formularza i **int** element członkowski danych z obiektu okna dialogowego pole lub formularza widoku.

```
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator zasobu kontrolki suwaka.

*value*<br/>
Odwołanie do wartości wymieniane. Ten parametr zawiera lub ustawia bieżące położenie kontrolki suwaka.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Slider` jest wywoływana, *wartość* jest ustawiony do bieżącego położenia kontrolki thumb, lub wartość odbiera sytuację, w zależności od kierunku programu exchange.

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacji na temat kontrolki suwaka, zobacz [korzystanie z CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

##  <a name="ddx_text"></a>  Ddx_text —

`DDX_Text` Funkcja zarządza transferem **int**, **UINT**, **długie**, DWORD, `CString`, **float**, lub **double** danych między formant edycji w oknie dialogowym widok formularza lub kontroli widoku i [CString](../../atl-mfc-shared/reference/cstringt-class.md) element członkowski danych okno dialogowe, widok formularza lub formantu obiekt widoku.

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

*pDX*<br/>
Wskaźnik do [CDataExchange](../../mfc/reference/cdataexchange-class.md) obiektu. Struktura dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.

*nIDC*<br/>
Identyfikator kontrolki edycji w okno dialogowe, widok formularza lub formantu obiekt widoku.

*value*<br/>
Odwołanie do elementu członkowskiego danych w okno dialogowe, widok formularza lub formantu obiekt widoku. Typ danych *wartość* zależy od którego przeciążone wersje `DDX_Text` używasz.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="see-also"></a>Zobacz też

[Standardowe procedury walidacji danych okna dialogowego](../../mfc/reference/standard-dialog-data-validation-routines.md)<br/>
[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
