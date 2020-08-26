---
title: Standardowe procedury wymiany danych w oknie dialogowym
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: bed60094b25bcc3b1994aa904a8c20324be2abae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844499"
---
# <a name="standard-dialog-data-exchange-routines"></a>Standardowe procedury wymiany danych w oknie dialogowym

W tym temacie wymieniono standardowe procedury wymiany danych (DDX), które są używane dla wspólnych kontrolek okna dialogowego MFC.

> [!NOTE]
> Standardowe procedury wymiany danych w oknie dialogowym są zdefiniowane w pliku nagłówkowym afxdd_. h. Aplikacje powinny jednak zawierać afxwin. h.

### <a name="ddx-functions"></a>Funkcje DDX

|Nazwa|Opis|
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Inicjuje lub Pobiera indeks bieżącego zaznaczenia kontrolki pola kombi.|
|[DDX_CBString](#ddx_cbstring)|Inicjuje lub pobiera bieżącą zawartość pola edycji kontrolki pola kombi.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Inicjuje lub pobiera bieżącą zawartość pola edycji kontrolki pola kombi.|
|[DDX_Check](#ddx_check)|Inicjuje lub pobiera bieżący stan kontrolki pola wyboru.|
|[DDX_Control](#ddx_control)|Podklasy danej kontrolki w oknie dialogowym.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Inicjuje lub pobiera dane daty i/lub godziny dla kontrolki selektora daty i godziny.|
|[DDX_IPAddress](#ddx_ipaddress)|Inicjuje lub pobiera bieżącą wartość kontrolki adresu IP.|
|[DDX_LBIndex](#ddx_lbindex)|Inicjuje lub Pobiera indeks bieżącego zaznaczenia kontrolki pole listy.|
|[DDX_LBString](#ddx_lbstring)|Inicjuje lub pobiera bieżące zaznaczenie w kontrolce pole listy.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Inicjuje lub pobiera bieżące zaznaczenie w kontrolce pole listy.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Tworzy kontrolkę .NET zgodną z IDENTYFIKATORem zasobu kontrolki.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Inicjuje lub pobiera bieżącą wartość kontrolki kalendarza miesięcznego.|
|[DDX_Radio](#ddx_radio)|Inicjuje lub Pobiera indeks kontrolki przycisku radiowego, który jest aktualnie sprawdzany w grupie kontrolek radiowych (0).|
|[DDX_Scroll](#ddx_scroll)|Inicjuje lub pobiera bieżącą pozycję przycisku przewijania kontrolki Scroll.|
|[DDX_Slider](#ddx_slider)|Inicjuje lub pobiera bieżącą pozycję przycisku przewijania kontrolki suwaka.|
|[DDX_Text](#ddx_text)|Inicjuje lub pobiera bieżącą wartość kontrolki edycji.|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a> DDX_CBIndex

`DDX_CBIndex`Funkcja zarządza przesyłaniem **`int`** danych między kontrolką pola kombi w oknie dialogowym, widoku Formularz lub obiektem widoku formantu i **`int`** elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki pola kombi skojarzonej z właściwością kontrolki.

*index*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBIndex` jest wywoływana, *indeks* jest ustawiany na indeks bieżącego zaznaczenia pola kombi. Jeśli nie wybrano żadnego elementu, *indeks* jest ustawiony na 0.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a> DDX_CBString

`DDX_CBString`Funkcja zarządza przesyłaniem `CString` danych między kontrolką edycji kontrolki pola kombi w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki i `CString` elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki pola kombi skojarzonej z właściwością kontrolki.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBString` jest wywoływana, *wartość* jest ustawiana na bieżące zaznaczenie pola kombi. Jeśli nie wybrano żadnego elementu, *wartość* jest ustawiana na ciąg o zerowej długości.

> [!NOTE]
> Jeśli pole kombi jest polem listy rozwijanej, wartość wymieniana jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a> DDX_CBStringExact

`DDX_CBStringExact`Funkcja zarządza przesyłaniem `CString` danych między kontrolką edycji kontrolki pola kombi w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki i `CString` elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki pola kombi skojarzonej z właściwością kontrolki.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_CBStringExact` jest wywoływana, *wartość* jest ustawiana na bieżące zaznaczenie pola kombi. Jeśli nie wybrano żadnego elementu, *wartość* jest ustawiana na ciąg o zerowej długości.

> [!NOTE]
> Jeśli pole kombi jest polem listy rozwijanej, wartość wymieniana jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_check"></a><a name="ddx_check"></a> DDX_Check

`DDX_Check`Funkcja zarządza przesyłaniem **`int`** danych między kontrolką pola wyboru w oknie dialogowym, widoku Formularz lub obiektem widoku formantu i **`int`** elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki pola wyboru skojarzonej z właściwością kontrolki.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Check` jest wywoływana, *wartość* jest ustawiana na bieżący stan kontrolki pola wyboru. Listę możliwych wartości stanu można znaleźć w [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) w Windows SDK.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_control"></a><a name="ddx_control"></a> DDX_Control

`DDX_Control`Funkcja podklasa kontrolki, określona przez *nIDC*, okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*nIDC*<br/>
Identyfikator zasobu formantu, który ma zostać podklasą.

*rControl*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu powiązanego z określoną kontrolką.

### <a name="remarks"></a>Uwagi

Obiekt *PDX* jest dostarczany przez platformę, gdy `DoDataExchange` wywoływana jest funkcja. W związku `DDX_Control` z tym, powinny być wywoływane tylko w ramach przesłonięcia `DoDataExchange` .

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a> DDX_DateTimeCtrl

`DDX_DateTimeCtrl`Funkcja zarządza transferem danych daty i/lub czasu między kontrolką selektora daty i godziny ( [Korzystanie CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) w oknie dialogowym lub w obiekcie widoku formularza, a element członkowski danych [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) w tym oknie dialogowym lub w obiekcie widoku formularza.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek. Nie musisz usuwać tego obiektu.

*nIDC*<br/>
Identyfikator zasobu kontrolki selektora daty i godziny skojarzonej ze zmienną członkowską.

*wartościami*<br/>
W pierwszych dwóch wersjach, odwołanie do `CTime` `COleDateTime` zmiennej składowej lub, okno dialogowe, widok formularza lub obiekt widoku kontrolki, z którym są wymieniane dane. W trzeciej wersji, odwołanie do `CString` obiektu widoku kontrolki elementu członkowskiego danych.

### <a name="remarks"></a>Uwagi

Gdy `DDX_DateTimeCtrl` jest wywoływana, *wartość* jest ustawiana na bieżący stan kontrolki selektora daty i godziny lub kontrolka jest ustawiona na *wartość*, w zależności od kierunku wymiany.

W trzeciej wersji powyżej program `DDX_DateTimeCtrl` zarządza transferem `CString` danych między kontrolą daty i godziny a elementem członkowskim danych [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu widoku sterowania. Ciąg jest formatowany przy użyciu bieżących reguł regionalnych do formatowania dat i godzin.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a> DDX_ManagedControl

Tworzy kontrolkę .NET zgodną z IDENTYFIKATORem zasobu kontrolki.

### <a name="syntax"></a>Składnia

```cpp
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [klasy CDataExchange](cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki skojarzonej z właściwością kontrolki.

*kontroli*<br/>
Odwołanie do obiektu [klasy CWinFormsControl](cwinformscontrol-class.md) .

### <a name="remarks"></a>Uwagi

`DDX_ManagedControl` wywołuje [CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) , aby utworzyć kontrolkę ODPOWIADAJĄCą identyfikatorowi kontroli zasobów. Służy `DDX_ManagedControl` do tworzenia kontrolek z identyfikatorów zasobów w [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog). W przypadku wymiany danych nie trzeba używać funkcji DDX/DDV z kontrolkami Windows Forms.

Aby uzyskać więcej informacji, zobacz [How to: DDX/DDV Binding danych with Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a> DDX_IPAddress

`DDX_IPAddress`Funkcja zarządza transferem danych między kontrolą adresu IP a elementem członkowskim danych obiektu widoku kontroli.

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontroli adresów IP skojarzony z właściwością kontrolki.

*wartościami*<br/>
Odwołanie do wartości DWORD zawierającej wartość pola czwarty kontroli adresów IP. Pola są wypełniane lub odczytywane w następujący sposób.

|Pole|Bity zawierające wartość pola|
|-----------|-------------------------------------|
|3|od 0 do 7|
|2|od 8 do 15|
|1|16 do 23|
|0|od 24 do 31|

Użyj [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) Win32, aby odczytać wartość, lub Użyj [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) , aby wypełnić wartość. Te komunikaty są opisane w Windows SDK.

### <a name="remarks"></a>Uwagi

Gdy `DDX_IPAddress` jest wywoływana, *wartość* jest odczytywana z kontroli adresu IP lub *wartość* jest zapisywana w kontrolce, w zależności od kierunku wymiany.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a> DDX_LBIndex

`DDX_LBIndex`Funkcja zarządza przesyłaniem **`int`** danych między kontrolką pola listy w oknie dialogowym, widoku Formularz lub obiektem widoku formantu i **`int`** elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki pole listy skojarzonej z właściwością kontrolki.

*index*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBIndex` jest wywoływana, *indeks* jest ustawiany na indeks bieżącego wyboru pola listy. Jeśli nie wybrano żadnego elementu, *indeks* jest ustawiony na wartość-1.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a> DDX_LBString

`DDX_LBString`Funkcja zarządza przesyłaniem `CString` danych między kontrolką pola listy w oknie dialogowym, widoku Formularz lub obiektem widoku formantu i `CString` elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki pole listy skojarzonej z właściwością kontrolki.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBString` jest wywoływana w celu transferu danych do kontrolki pole listy, pierwszy element w kontrolce, której *wartość* początkowa pasuje jest zaznaczone. (Aby dopasować cały element, a nie tylko prefiks, użyj [DDX_LBStringExact](#ddx_lbstringexact).) Jeśli nie ma żadnych dopasowań, żadne elementy nie są zaznaczone. W dopasowaniu nie jest rozróżniana wielkość liter.

Gdy `DDX_LBString` jest wywoływana w celu transferu danych z kontrolki pole listy, *wartość* jest ustawiana na bieżące zaznaczenie pola listy. Jeśli nie wybrano żadnego elementu, *wartość* jest ustawiana na ciąg o zerowej długości.

> [!NOTE]
> Jeśli pole listy jest polem listy rozwijanej, wartość wymieniana jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a> DDX_LBStringExact

`DDX_CBStringExact`Funkcja zarządza transferem `CString` danych między kontrolką Edycja kontrolki pole listy w oknie dialogowym, widoku Formularz lub obiektem widoku kontrolki i `CString` elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki pole listy skojarzonej z właściwością kontrolki.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_LBStringExact` jest wywoływana w celu transferu danych do kontrolki pole listy, wybierany jest pierwszy element w kontrolce pasującej do *wartości* . (Aby dopasować tylko prefiks, a nie cały element, użyj [DDX_LBString](#ddx_lbstring).) Jeśli nie ma żadnych dopasowań, żadne elementy nie są zaznaczone. W dopasowaniu nie jest rozróżniana wielkość liter.

Gdy `DDX_CBStringExact` jest wywoływana w celu transferu danych z kontrolki pole listy, *wartość* jest ustawiana na bieżące zaznaczenie pola listy. Jeśli nie wybrano żadnego elementu, *wartość* jest ustawiana na ciąg o zerowej długości.

> [!NOTE]
> Jeśli pole listy jest polem listy rozwijanej, wartość wymieniana jest ograniczona do 255 znaków.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a> DDX_MonthCalCtrl

`DDX_MonthCalCtrl`Funkcja zarządza transferem danych daty między kontrolką kalendarza miesięcznego ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) w oknie dialogowym, widoku formularza lub obiektem widoku kontrolki oraz elementem członkowskim danych [CTime](../../atl-mfc-shared/reference/ctime-class.md) lub [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) w oknie dialogowym, widoku formularza lub w obiekcie widoku formantu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek. Nie musisz usuwać tego obiektu.

*nIDC*<br/>
Identyfikator zasobu kontrolki kalendarza miesięcznego skojarzonej ze zmienną elementu członkowskiego.

*wartościami*<br/>
Odwołanie do `CTime` `COleDateTime` zmiennej składowej lub okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Kontrolka zarządza tylko wartością daty. Pola czasu w obiekcie czasu są ustawiane tak, aby odzwierciedlały czas utworzenia okna kontroli, lub niezależnie od tego, jaki czas został ustawiony w formancie z wywołaniem do `CMonthCalCtrl::SetCurSel` .

Gdy `DDX_MonthCalCtrl` jest wywoływana, *wartość* jest ustawiany na bieżący stan kontrolki kalendarza miesięcznego.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_radio"></a><a name="ddx_radio"></a> DDX_Radio

`DDX_Radio`Funkcja zarządza transferem **`int`** danych między grupą kontrolek radiowych w oknie dialogowym, widoku Formularz lub obiektem widoku formantu i **`int`** elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu. Wartość **`int`** elementu członkowskiego danych jest określana na podstawie zaznaczenia przycisku radiowego w grupie.

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu pierwszej kontrolki radia w grupie.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku formantu, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Radio` jest wywoływana, *wartość* jest ustawiany na bieżący stan grupy kontrolek radiowych. Wartość jest ustawiana jako indeks (0) kontrolki radio, która jest aktualnie zaznaczona, lub-1, jeśli nie zaznaczono żadnych kontrolek radiowych.

Na przykład w przypadku zaznaczenia pierwszego przycisku radiowego w grupie (przycisk z stylem WS_GROUP) wartością **`int`** elementu członkowskiego jest 0 i tak dalej.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a> DDX_Scroll

`DDX_Scroll`Funkcja zarządza transferem **`int`** danych między kontrolką paska przewijania w oknie dialogowym, widoku Formularz lub obiektem widoku formantu i **`int`** elementem członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do `CDataExchange` obiektu. Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki paska przewijania skojarzonej z właściwością kontrolki.

*wartościami*<br/>
Odwołanie do zmiennej składowej okna dialogowego, widoku formularza lub obiektu widoku kontrolki, z którym są wymieniane dane.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Scroll` jest wywoływana, *wartość* jest ustawiana na bieżącą pozycję przycisku przewijania kontrolki. Aby uzyskać więcej informacji na temat wartości skojarzonych z bieżącą pozycją przycisku przewijania kontrolki, zobacz [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) w Windows SDK.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_slider"></a><a name="ddx_slider"></a> DDX_Slider

`DDX_Slider`Funkcja zarządza transferem **`int`** danych między kontrolką suwaka w oknie dialogowym lub widoku Formularz i **`int`** elementem członkowskim danych okna dialogowego lub widoku formularza.

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator zasobu kontrolki suwaka.

*wartościami*<br/>
Odwołanie do wartości, która ma zostać nadana wymianie. Ten parametr zawiera lub ustawia bieżącą pozycję kontrolki suwaka.

### <a name="remarks"></a>Uwagi

Gdy `DDX_Slider` jest wywoływana, *wartość* jest ustawiana na bieżącą pozycję przycisku przewijania kontrolki lub wartość otrzymuje pozycję, w zależności od kierunku wymiany.

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md). Aby uzyskać informacje o kontrolkach suwaka, zobacz [using korzystanie CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="ddx_text"></a><a name="ddx_text"></a> DDX_Text

`DDX_Text`Funkcja zarządza transferem **`int`** , **uint**, **`long`** , DWORD, `CString` , **`float`** , lub **`double`** danych między kontrolką edycji w oknie dialogowym, widoku formularza lub widoku kontrolnym i [CString](../../atl-mfc-shared/reference/cstringt-class.md) członkowskim danych okna dialogowego, widoku formularza lub obiektu widoku formantu.

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

*pDX*<br/>
Wskaźnik do obiektu [CDataExchange](../../mfc/reference/cdataexchange-class.md) . Platforma dostarcza ten obiekt, aby ustalić kontekst wymiany danych, w tym jej kierunek.

*nIDC*<br/>
Identyfikator kontrolki edycji w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu.

*wartościami*<br/>
Odwołanie do elementu członkowskiego danych w oknie dialogowym, widoku Formularz lub w obiekcie widoku formantu. Typ danych *wartości* zależy od tego, które z przeciążonych wersji są `DDX_Text` używane.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxdd_. h

## <a name="see-also"></a>Zobacz też

[Standardowe procedury walidacji danych w oknie dialogowym](standard-dialog-data-validation-routines.md)<br/>
[Makra i Globals](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog:: OnInitDialog](cdialog-class.md#oninitdialog)
