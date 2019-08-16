---
title: Klasa CIPAddressCtrl
ms.date: 11/04/2016
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
ms.openlocfilehash: fe8e3109b110c27ab32dc1a4f9a132f1e1c18638
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505816"
---
# <a name="cipaddressctrl-class"></a>Klasa CIPAddressCtrl

Oferuje funkcje kontroli wspólnego adresu IP systemu Windows.

## <a name="syntax"></a>Składnia

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Konstruuje `CIPAddressCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Czyści zawartość kontroli adresów IP.|
|[CIPAddressCtrl:: Create](#create)|Tworzy kontrolę adresów IP i dołącza ją do `CIPAddressCtrl` obiektu.|
|[CIPAddressCtrl::CreateEx](#createex)|Tworzy kontrolę adresu IP z określonymi stylami rozszerzonymi systemu Windows i dołącza je do `CIPAddressCtrl` obiektu.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Pobiera wartości adresów dla wszystkich czterech pól w kontroli adresów IP.|
|[CIPAddressCtrl::IsBlank](#isblank)|Określa, czy wszystkie pola w kontrolce adresu IP są puste.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Ustawia wartości adresów dla wszystkich czterech pól w kontroli adresów IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Ustawia fokus klawiatury do określonego pola w kontrolce adresu IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Ustawia zakres w określonym polu w kontrolce adresu IP.|

## <a name="remarks"></a>Uwagi

Kontrolka adresu IP, kontrolka podobna do kontrolki edycji, umożliwia wprowadzanie i manipulowanie adresem numerycznym w formacie protokołu internetowego (IP).

Ten formant (i w związku `CIPAddressCtrl` z tym Klasa) jest dostępny tylko dla programów uruchomionych w ramach programu Microsoft Internet Explorer 4,0 i nowszych. Będą one również dostępne w przyszłych wersjach systemu Windows i Windows NT.

Aby uzyskać ogólne informacje na temat kontroli adresów IP, zobacz [kontrolki adresu IP](/windows/win32/Controls/ip-address-controls) w Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl

`CIPAddressCtrl` Tworzy obiekt.

```
CIPAddressCtrl();
```

##  <a name="clearaddress"></a>CIPAddressCtrl::ClearAddress

Czyści zawartość kontroli adresów IP.

```
void ClearAddress();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress), zgodnie z opisem w Windows SDK.

##  <a name="create"></a>CIPAddressCtrl:: Create

Tworzy kontrolę adresów IP i dołącza ją do `CIPAddressCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Styl kontroli adresów IP. Zastosuj kombinację stylów okna. Musisz dołączyć styl WS_CHILD, ponieważ kontrolka musi być oknem podrzędnym. Aby [](/windows/win32/api/winuser/nf-winuser-createwindoww) uzyskać listę stylów systemu Windows, zobacz sekcję w Windows SDK.

*cinania*<br/>
Odwołanie do rozmiaru i pozycji kontrolki adresu IP. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub struktura. [](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego kontroli adresu IP. Nie może mieć wartości NULL.

*nID*<br/>
Identyfikator kontroli adresów IP.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CIPAddressCtrl` Obiekt jest konstruowany w dwóch krokach.

1. Wywołaj konstruktora, który tworzy `CIPAddressCtrl` obiekt.

1. Wywołanie `Create`, które tworzy kontrolę adresów IP.

Jeśli chcesz użyć rozszerzonych stylów systemu Windows z kontrolką, wywołaj [CreateEx](#createex) zamiast `Create`.

##  <a name="createex"></a>CIPAddressCtrl::CreateEx

Wywołaj tę funkcję, aby utworzyć kontrolkę (okno podrzędne) i skojarzyć ją z `CIPAddressCtrl` obiektem.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Określa rozszerzony styl formantu, który jest tworzony. Aby zapoznać się z listą rozszerzonych stylów systemu Windows, zobacz *dwExStyle* parametru [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK.

*dwStyle*<br/>
Styl kontroli adresów IP. Zastosuj kombinację stylów okna. Musisz dołączyć styl WS_CHILD, ponieważ kontrolka musi być oknem podrzędnym. Aby [](/windows/win32/api/winuser/nf-winuser-createwindoww) uzyskać listę stylów systemu Windows, zobacz sekcję w Windows SDK.

*cinania*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator okna podrzędnego kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [tworzenia](#create) , aby zastosować rozszerzone style systemu Windows, które są określone przez **WS_EX_** styl rozszerzony systemu Windows.

##  <a name="getaddress"></a>CIPAddressCtrl:: GetAddress

Pobiera wartości adresów dla wszystkich czterech pól w kontroli adresów IP.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>Parametry

*nField0*<br/>
Odwołanie do wartości pola 0 z spakowanego adresu IP.

*nField1*<br/>
Odwołanie do wartości pola 1 z spakowanego adresu IP.

*nField2*<br/>
Odwołanie do wartości pola 2 ze spakowanego adresu IP.

*nField3*<br/>
Odwołanie do wartości pola 3 z spakowanego adresu IP.

*dwAddress*<br/>
Odwołanie do adresu wartości DWORD, która odbiera adres IP. Zobacz **uwagi** dotyczące tabeli, która pokazuje, jak *dwAddress* jest wypełnione.

### <a name="return-value"></a>Wartość zwracana

Liczba pól, które nie są puste w kontrolce adresu IP.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress), zgodnie z opisem w Windows SDK. W pierwszym prototypie powyżej liczby w polach od 0 do 3 kontrolki, Odczytaj odpowiednio do prawej, Wypełnij cztery parametry. W drugim prototypie powyżej *dwAddress* jest wypełniany w następujący sposób.

|Pole|Bity zawierające wartość pola|
|-----------|-------------------------------------|
|0|od 24 do 31|
|1|16 do 23|
|2|od 8 do 15|
|3|od 0 do 7|

##  <a name="isblank"></a>CIPAddressCtrl:: ISBLANK

Określa, czy wszystkie pola w kontrolce adresu IP są puste.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wszystkie pola kontroli adresów IP są puste; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank), zgodnie z opisem w Windows SDK.

##  <a name="setaddress"></a>CIPAddressCtrl:: SetAddress

Ustawia wartości adresów dla wszystkich czterech pól w kontroli adresów IP.

```
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Parametry

*nField0*<br/>
Wartość pola 0 z spakowanego adresu IP.

*nField1*<br/>
Wartość pola 1 z spakowanego adresu IP.

*nField2*<br/>
Wartość pola 2 ze spakowanego adresu IP.

*nField3*<br/>
Wartość pola 3 z spakowanego adresu IP.

*dwAddress*<br/>
Wartość DWORD, która zawiera nowy adres IP. Zobacz **uwagi** dotyczące tabeli, która pokazuje, jak jest wypełniana wartość DWORD.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress), zgodnie z opisem w Windows SDK. W pierwszym prototypie powyżej liczby w polach od 0 do 3 kontrolki, Odczytaj odpowiednio do prawej, Wypełnij cztery parametry. W drugim prototypie powyżej *dwAddress* jest wypełniany w następujący sposób.

|Pole|Bity zawierające wartość pola|
|-----------|-------------------------------------|
|0|od 24 do 31|
|1|16 do 23|
|2|od 8 do 15|
|3|od 0 do 7|

##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus

Ustawia fokus klawiatury do określonego pola w kontrolce adresu IP.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parametry

*nField*<br/>
Indeks pola (liczony od zera), do którego ma zostać ustawiony fokus. Jeśli wartość jest większa niż liczba pól, fokus jest ustawiany na pierwsze puste pole. Jeśli wszystkie pola nie są puste, fokus jest ustawiany na pierwsze pole.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus), zgodnie z opisem w Windows SDK.

##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

Ustawia zakres w określonym polu w kontrolce adresu IP.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parametry

*nField*<br/>
Indeks pola (liczony od zera), do którego zostanie zastosowany zakres.

*nLower*<br/>
Odwołanie do liczby całkowitej otrzymującej dolny limit określonego pola w tej kontrolce adresu IP.

*nUpper*<br/>
Odwołanie do liczby całkowitej otrzymującej górny limit określonego pola w tej kontrolce adresu IP.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange), zgodnie z opisem w Windows SDK. Użyj dwóch parametrów, *nLower* i *nUpper*, aby wskazać dolne i górne limity pola, zamiast parametru *wRange* użytego w komunikacie systemu Win32.

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
