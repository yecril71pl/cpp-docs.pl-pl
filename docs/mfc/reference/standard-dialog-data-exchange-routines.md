---
title: Standardowe procedury wymiany danych w oknie dialogowym
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 83d4a66cd3ec41008506b55f0b351fd9bcbc24b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372929"
---
# <a name="standard-dialog-data-exchange-routines"></a>Standardowe procedury wymiany danych w oknie dialogowym

W tym temacie wymieniono standardowe procedury wymiany danych okna dialogowego (DDX) używane dla typowych kontrolek dialogowych MFC.

> [!NOTE]
> Standardowe procedury wymiany danych w oknie dialogowym są zdefiniowane w pliku nagłówka afxdd_.h. Jednak aplikacje powinny zawierać afxwin.h.

### <a name="ddx-functions"></a>Funkcje DDX

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Inicjuje lub pobiera indeks bieżącego wyboru formantu pola kombi.|
|[DDX_CBString](#ddx_cbstring)|Inicjuje lub pobiera bieżącą zawartość pola edycji formantu pola kombi.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Inicjuje lub pobiera bieżącą zawartość pola edycji formantu pola kombi.|
|[DDX_Check](#ddx_check)|Inicjuje lub pobiera bieżący stan formantu pola wyboru.|
|[DDX_Control](#ddx_control)|Podklasy danego formantu w oknie dialogowym.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Inicjuje lub pobiera dane daty i/lub godziny kontroli selektora daty i godziny.|
|[DDX_IPAddress](#ddx_ipaddress)|Inicjuje lub pobiera bieżącą wartość formantu adresu IP.|
|[DDX_LBIndex](#ddx_lbindex)|Inicjuje lub pobiera indeks bieżącego zaznaczenia formantu pola listy.|
|[DDX_LBString](#ddx_lbstring)|Inicjuje lub pobiera bieżące zaznaczenie w formancie pola listy.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Inicjuje lub pobiera bieżące zaznaczenie w formancie pola listy.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Tworzy formant .NET pasujący do identyfikatora zasobu formantu.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Inicjuje lub pobiera bieżącą wartość kontrolki kalendarza miesiąca.|
|[DDX_Radio](#ddx_radio)|Inicjuje lub pobiera indeks oparty na 0 formantu radiowego, który jest obecnie sprawdzany w grupie sterowania radiowego.|
|[DDX_Scroll](#ddx_scroll)|Inicjuje lub pobiera bieżącą pozycję kciuka formantu przewijania.|
|[DDX_Slider](#ddx_slider)|Inicjuje lub pobiera bieżącą pozycję kciuka formantu suwaka.|
|[DDX_Text](#ddx_text)|Inicjuje lub pobiera bieżącą wartość formantu edycji.|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex

Funkcja `DDX_CBIndex` zarządza transferem danych **int** między formantem pola kombi w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **int** w oknie dialogowym, widoku formularza lub obiekcie widoku sterującego.

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu pola kombi skojarzonego z właściwością formantu.

*Indeks*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBIndex` jest wywoływana, *indeks* jest ustawiony na indeks bieżącego wyboru pola kombi. Jeśli żaden element nie jest zaznaczony, *indeks* jest ustawiony na 0.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a>DDX_CBString

Funkcja `DDX_CBString` zarządza transferem `CString` danych między formantem edycji formantu pola kombi w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem `CString` członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu pola kombi skojarzonego z właściwością formantu.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBString` jest wywoływana, *wartość* jest ustawiona na bieżący wybór pola kombi. Jeśli żaden element nie jest zaznaczony, *wartość* jest ustawiona na ciąg o zerowej długości.

> [!NOTE]
> Jeśli pole kombi jest polem listy rozwijanej, wymieniona wartość jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact

Funkcja `DDX_CBStringExact` zarządza transferem `CString` danych między formantem edycji formantu pola kombi w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem `CString` członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu pola kombi skojarzonego z właściwością formantu.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBStringExact` jest wywoływana, *wartość* jest ustawiona na bieżący wybór pola kombi. Jeśli żaden element nie jest zaznaczony, *wartość* jest ustawiona na ciąg o zerowej długości.

> [!NOTE]
> Jeśli pole kombi jest polem listy rozwijanej, wymieniona wartość jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_check"></a><a name="ddx_check"></a>DDX_Check

Funkcja `DDX_Check` zarządza transferem danych **int** między formantem pola wyboru w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **int** okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu pola wyboru skojarzonego z właściwością formantu.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Check` jest wywoływana, *wartość* jest ustawiona na bieżący stan formantu pola wyboru. Aby uzyskać listę możliwych wartości stanu, zobacz [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) w zestawie Windows SDK.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_control"></a><a name="ddx_control"></a>DDX_Control

Funkcja `DDX_Control` podklasuje formant określony przez *nIDC*, okna dialogowego, widoku formularza lub obiektu widoku kontrolnego.

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu, który ma być podklasyfikowany.

*rKontroluj*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego powiązanego z określonym formantem.

### <a name="remarks"></a>Uwagi

Obiekt *pDX* jest dostarczany przez `DoDataExchange` platformę, gdy wywoływana jest funkcja. W związku `DDX_Control` z tym powinny być wywoływane tylko w ramach zastąpienia `DoDataExchange`.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

Funkcja `DDX_DateTimeCtrl` zarządza transferem danych daty i/lub godziny między formantem selektora daty i godziny [(CDateTimeCtrl)](../../mfc/reference/cdatetimectrl-class.md)w oknie dialogowym lub obiektu widoku formularza oraz [ctime](../../atl-mfc-shared/reference/ctime-class.md) lub [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) elementem członkowskim danych okna dialogowego lub obiektu widoku formularza.

```cpp
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

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku. Nie trzeba usuwać tego obiektu.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu selektora daty i godziny skojarzonego ze zmienną członkowną.

*value*<br/>
W pierwszych dwóch wersjach odwołanie `CTime` `COleDateTime` do zmiennej lub elementu członkowskiego, okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane. W trzeciej wersji odwołanie `CString` do obiektu widoku kontroli elementu członkowskiego danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_DateTimeCtrl` jest wywoływana, *wartość* jest ustawiona na bieżący stan kontrolki selektora daty i godziny lub formant jest ustawiony na *wartość*, w zależności od kierunku wymiany.

W trzeciej wersji `DDX_DateTimeCtrl` powyżej zarządza `CString` transfer danych między formantem daty i [CString](../../atl-mfc-shared/reference/cstringt-class.md) elementu członkowskiego danych obiektu widoku formantu. Ciąg jest formatowany przy użyciu reguł ustawień regionalnych dla dat i godzin formatowania.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a>DDX_ManagedControl

Tworzy formant .NET pasujący do identyfikatora zasobu formantu.

### <a name="syntax"></a>Składnia

```cpp
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange Class.](cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu skojarzonego z właściwością formantu.

*Kontroli*<br/>
Odwołanie do obiektu [CWinFormsControl Class.](cwinformscontrol-class.md)

### <a name="remarks"></a>Uwagi

`DDX_ManagedControl`wywołuje [CWinFormsControl::CreateManagedControl,](cwinformscontrol-class.md#createmanagedcontrol) aby utworzyć formant pasujący do identyfikatora kontroli zasobów. Służy `DDX_ManagedControl` do tworzenia formantów z identyfikatorów zasobów w [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Do wymiany danych nie trzeba używać funkcji DDX/DDV z formantami Windows Forms.

Aby uzyskać więcej informacji, zobacz [Jak: Do powiązania danych DDX/DDV z formularzami systemu Windows](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress

Funkcja `DDX_IPAddress` zarządza transferem danych między formantem adresu IP a członkiem danych obiektu widoku kontrolnego.

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu adres IP skojarzony z właściwością control.

*value*<br/>
Odwołanie do DWORD zawierające wartość czterech pól formantu Adres IP. Pola są wypełniane lub odczytywane w następujący sposób.

|Pole|Bity zawierające wartość pola|
|-----------|-------------------------------------|
|3|Od 0 do 7|
|2|od 8 do 15|
|1|od 16 do 23|
|0|od 24 do 31|

Użyj [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) Win32, aby odczytać wartość, lub użyj [IPM_SETADDRESS,](/windows/win32/Controls/ipm-setaddress) aby wypełnić tę wartość. Te komunikaty są opisane w windows SDK.

### <a name="remarks"></a>Uwagi

Gdy `DDX_IPAddress` jest wywoływana, *wartość* jest odczytywana z formantu adres IP lub *wartość* jest zapisywana do formantu, w zależności od kierunku wymiany.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex

Funkcja `DDX_LBIndex` zarządza transferem danych **int** między formantem pola listy w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **int** okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu pola listy skojarzonego z właściwością formantu.

*Indeks*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBIndex` jest wywoływana, *indeks* jest ustawiony na indeks bieżącego wyboru pola listy. Jeśli nie wybrano żadnego elementu, *indeks* jest ustawiony na -1.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a>DDX_LBString

Funkcja `DDX_LBString` zarządza transferem `CString` danych między formantem pola listy w oknie dialogowym, `CString` widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu pola listy skojarzonego z właściwością formantu.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBString` jest wywoływana do przesyłania danych do formantu pola listy, pierwszy element w formancie, którego początek pasuje *wartość* jest zaznaczona. (Aby dopasować cały element, a nie tylko prefiks, użyj [DDX_LBStringExact](#ddx_lbstringexact).) Jeśli nie ma żadnych dopasowań, nie są wybierane żadne elementy. Dopasowanie jest niewrażliwe na wielkości liter.

Gdy `DDX_LBString` jest wywoływana do przesyłania danych z formantu pola listy, *wartość* jest ustawiona na bieżący wybór pola listy. Jeśli żaden element nie jest zaznaczony, *wartość* jest ustawiona na ciąg o zerowej długości.

> [!NOTE]
> Jeśli pole listy jest polem listy rozwijanej, wymieniona wartość jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact

Funkcja `DDX_CBStringExact` zarządza transferem `CString` danych między formantem edycji formantu pola listy w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem `CString` członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku sterującego.

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu pola listy skojarzonego z właściwością formantu.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBStringExact` jest wywoływana do przesyłania danych do formantu pola listy, wybierany jest pierwszy element w formancie, który pasuje *do wartości.* (Aby dopasować tylko prefiks, a nie cały element, użyj [DDX_LBString](#ddx_lbstring).) Jeśli nie ma żadnych dopasowań, nie są wybierane żadne elementy. Dopasowanie jest niewrażliwe na wielkości liter.

Gdy `DDX_CBStringExact` jest wywoływana do przesyłania danych z formantu pola listy, *wartość* jest ustawiona na bieżący wybór pola listy. Jeśli żaden element nie jest zaznaczony, *wartość* jest ustawiona na ciąg o zerowej długości.

> [!NOTE]
> Jeśli pole listy jest polem listy rozwijanej, wymieniona wartość jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

Funkcja `DDX_MonthCalCtrl` zarządza transferem danych daty między formantem kalendarza miesiąca ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) w oknie dialogowym, widoku formularza lub obiektu widoku sterującego i [ctime](../../atl-mfc-shared/reference/ctime-class.md) lub [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) element członkowski danych okna dialogowego, widoku formularza lub obiektu widoku sterowania.

```cpp
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

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku. Nie trzeba usuwać tego obiektu.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu kalendarza miesiąca skojarzonego ze zmienną elementu członkowskiego.

*value*<br/>
Odwołanie do `CTime` zmiennej lub `COleDateTime` elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Formant zarządza tylko wartością daty. Pola czasu w obiekcie czasu są ustawione tak, aby odzwierciedlały czas utworzenia okna formantu lub dowolną godzinę ustawioną w formancie z wywołaniem `CMonthCalCtrl::SetCurSel`.

Po `DDX_MonthCalCtrl` wywołaniu *wartość* jest ustawiona na bieżący stan kontrolki kalendarza miesiąca.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_radio"></a><a name="ddx_radio"></a>DDX_Radio

Funkcja `DDX_Radio` zarządza transferem danych **int** między grupą sterowania radiowego w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **int** okna dialogowego, widoku formularza lub obiektu widoku sterującego. Wartość elementu członkowskiego danych **int** jest określana zgodnie z wybranym przyciskiem opcji w grupie.

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu pierwszego formantu radiowego w grupie.

*value*<br/>
Odwołanie do zmiennej elementu członkowskiego okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Radio` jest wywoływana, *wartość* jest ustawiona na bieżący stan grupy sterowania radiowego. Wartość jest ustawiana jako indeks oparty na 0 formantu radiowego, który jest obecnie sprawdzany, lub -1, jeśli nie są sprawdzane żadne kontrolki radiowe.

Na przykład w przypadku, gdy pierwszy przycisk radiowy w grupie jest zaznaczony (przycisk z WS_GROUP stylem) wartość elementu członkowskiego **int** wynosi 0 i tak dalej.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a>DDX_Scroll

Funkcja `DDX_Scroll` zarządza transferem danych **int** między formantem paska przewijania w oknie dialogowym, widoku formularza lub obiektu widoku sterującego a elementem członkowskim danych **int** w oknie dialogowym, widoku formularza lub obiekcie widoku sterującego.

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do `CDataExchange` obiektu. Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu paska przewijania skojarzonego z właściwością formantu.

*value*<br/>
Odwołanie do zmiennej członkowskiej okna dialogowego, widoku formularza lub obiektu widoku sterującego, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Scroll` jest wywoływana, *wartość* jest ustawiona na bieżącą pozycję kciuka formantu. Aby uzyskać więcej informacji na temat wartości skojarzonych z bieżącą pozycją kciuka formantu, zobacz [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) w windows SDK.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_slider"></a><a name="ddx_slider"></a>DDX_Slider

Funkcja `DDX_Slider` zarządza transferem danych **int** między formantem suwaka w oknie dialogowym lub widoku formularza a elementem członkowskim danych **int** okna dialogowego lub obiektu widoku formularza.

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator zasobu formantu suwaka.

*value*<br/>
Odwołanie do wartości, która ma zostać wymieniona. Ten parametr przechowuje lub ustawia bieżącą pozycję formantu suwaka.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Slider` jest wywoływana, *wartość* jest ustawiona na bieżącą pozycję kciuka formantu lub wartość odbiera pozycję, w zależności od kierunku wymiany.

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacje na temat kontrolek suwaków, zobacz [Korzystanie z CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="ddx_text"></a><a name="ddx_text"></a>DDX_Text

Funkcja `DDX_Text` zarządza transferem **int**, **UINT**, **long** `CString`, DWORD, **float**, lub **podwójne** dane między formantem edycji w oknie dialogowym, widoku formularza lub widoku sterowania i [CString](../../atl-mfc-shared/reference/cstringt-class.md) element członkowski danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
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

*Pdx*<br/>
Wskaźnik do [obiektu CDataExchange.](../../mfc/reference/cdataexchange-class.md) Ramy dostarcza ten obiekt w celu ustalenia kontekstu wymiany danych, w tym jego kierunku.

*nIDC (nIDC)*<br/>
Identyfikator formantu edycji w oknie dialogowym, widoku formularza lub obiektu widoku sterującego.

*value*<br/>
Odwołanie do elementu członkowskiego danych w oknie dialogowym, widoku formularza lub obiektu widoku sterującego. Typ danych *wartości* zależy od tego, które `DDX_Text` z przeciążonych wersji używasz.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_.h

## <a name="see-also"></a>Zobacz też

[Standardowe procedury walidacji danych okna dialogowego](standard-dialog-data-validation-routines.md)<br/>
[Makra i globals](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
