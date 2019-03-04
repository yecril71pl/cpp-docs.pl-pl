---
title: CIPAddressCtrl Class
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
ms.openlocfilehash: e569829c100a581e24b5ce05df2f90ac7088024b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266298"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl Class

Oferuje funkcje formantu typowego adresu IP Windows.

## <a name="syntax"></a>Składnia

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Konstruuje `CIPAddressCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Czyści zawartość formant adresu IP.|
|[CIPAddressCtrl::Create](#create)|Tworzy formant adresu IP i dołącza je do `CIPAddressCtrl` obiektu.|
|[CIPAddressCtrl::CreateEx](#createex)|Tworzy formant adresu IP z określonego style rozszerzone Windows i dołącza je do `CIPAddressCtrl` obiektu.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Pobiera wartości adresów dla wszystkich czterech pól w formant adresu IP.|
|[CIPAddressCtrl::IsBlank](#isblank)|Określa, czy wszystkie pola w kontrolce adresów IP są puste.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Ustawia wartości adresów dla wszystkich, cztery pola w kontrolce adresu IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Ustawia fokus klawiatury określonego pola w formant adresu IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Ustawia zakres w określonym polu w formant adresu IP.|

## <a name="remarks"></a>Uwagi

Kontrolka w postaci adresu IP, podobnie jak kontrolka edycji kontrolki umożliwia wprowadzanie i manipulowania nimi numeryczny adres w formacie protokołu internetowego (IP).

Ta kontrolka (i w związku z tym `CIPAddressCtrl` klasy) jest dostępna tylko dla programów uruchomionych w ramach programu Microsoft Internet Explorer 4.0 lub nowszy. Będą one również dostępne w przyszłych wersjach systemu Windows i Windows NT.

Aby uzyskać więcej ogólnych informacji na temat formant adresu IP, zobacz [formanty adresów IP](/windows/desktop/Controls/ip-address-controls) w zestawie Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

##  <a name="cipaddressctrl"></a>  CIPAddressCtrl::CIPAddressCtrl

Tworzy `CIPAddressCtrl` obiektu.

```
CIPAddressCtrl();
```

##  <a name="clearaddress"></a>  CIPAddressCtrl::ClearAddress

Czyści zawartość formant adresu IP.

```
void ClearAddress();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [IPM_CLEARADDRESS](/windows/desktop/Controls/ipm-clearaddress), zgodnie z opisem w zestawie Windows SDK.

##  <a name="create"></a>  CIPAddressCtrl::Create

Tworzy formant adresu IP i dołącza je do `CIPAddressCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Styl kontrolki adresu IP. Stosowanie kombinacji Style okna ramowego. Styl WS_CHILD musi zawierać, ponieważ kontrolka musi być okna podrzędnego. Zobacz [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) w zestawie Windows SDK dla listy stylów systemu windows.

*Rect*<br/>
Odwołanie do rozmiaru i położenia formant adresu IP. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego formant adresu IP. Nie może być równa NULL.

*nID*<br/>
Identyfikator formant adresu IP.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli inicjowanie się powiodła. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CIPAddressCtrl` obiektu w dwóch krokach.

1. Wywołaj Konstruktor, który tworzy `CIPAddressCtrl` obiektu.

1. Wywołaj `Create`, która tworzy formant adresu IP.

Style rozszerzone systemu windows za pomocą formantu należy wywołać [CreateEx](#createex) zamiast `Create`.

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

Wywołaj tę funkcję, aby utworzyć kontrolkę (okno podrzędne) i powiąż ją z `CIPAddressCtrl` obiektu.

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
Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.

*dwStyle*<br/>
Styl kontrolki adresu IP. Stosowanie kombinacji Style okna ramowego. Styl WS_CHILD musi zawierać, ponieważ kontrolka musi być okna podrzędnego. Zobacz [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) w zestawie Windows SDK dla listy stylów systemu windows.

*Rect*<br/>
Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator formantu okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

Pobiera wartości adresów dla wszystkich czterech pól w formant adresu IP.

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
Odwołanie do wartości pola 0 z upakowaną adresu IP.

*nField1*<br/>
Odwołanie do wartości pola 1 z upakowaną adresu IP.

*nField2*<br/>
Odwołanie do wartości pola 2 z upakowaną adresu IP.

*nField3*<br/>
Odwołanie do wartości pola 3 z upakowaną adresu IP.

*dwAddress*<br/>
Odwołanie do adresu wartość DWORD, która otrzymuje adres IP. Zobacz **uwagi** dla tabeli, który pokazuje, jak *dwAddress* jest wypełnione.

### <a name="return-value"></a>Wartość zwracana

Liczba pól nie jest pusty w formant adresu IP.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress), zgodnie z opisem w zestawie Windows SDK. W pierwszym prototypie powyżej liczb w polach od 0 do 3 kontrolki, przeczytaj od lewej do prawej odpowiednio, wypełnij cztery parametry. W drugim prototypie powyżej *dwAddress* jest wypełniana w następujący sposób.

|Pole|Usługa BITS zawierający wartość pola|
|-----------|-------------------------------------|
|0|24 do 31|
|1|16 do 23|
|2|8 do 15|
|3|od 0 do 7|

##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank

Określa, czy wszystkie pola w kontrolce adresów IP są puste.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wszystkie pola formant adresu IP są puste; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [IPM_ISBLANK](/windows/desktop/Controls/ipm-isblank), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

Ustawia wartości adresów dla wszystkich, cztery pola w kontrolce adresu IP.

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
Wartość pola 0 z upakowaną adresu IP.

*nField1*<br/>
Wartość pola 1 z upakowaną adresu IP.

*nField2*<br/>
Wartość pola 2 z upakowaną adresu IP.

*nField3*<br/>
Wartość pola 3 z upakowaną adresu IP.

*dwAddress*<br/>
Wartość DWORD, który zawiera nowy adres IP. Zobacz **uwagi** dla tabeli, który pokazuje, jak wprowadzono wartość DWORD.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress), zgodnie z opisem w zestawie Windows SDK. W pierwszym prototypie powyżej liczb w polach od 0 do 3 kontrolki, przeczytaj od lewej do prawej odpowiednio, wypełnij cztery parametry. W drugim prototypie powyżej *dwAddress* jest wypełniana w następujący sposób.

|Pole|Usługa BITS zawierający wartość pola|
|-----------|-------------------------------------|
|0|24 do 31|
|1|16 do 23|
|2|8 do 15|
|3|od 0 do 7|

##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus

Ustawia fokus klawiatury określonego pola w formant adresu IP.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parametry

*nField*<br/>
Pole liczony od zera indeks, do której należy ustawić fokus. Jeśli ta wartość jest większa niż liczba pól, fokus jest ustawiony do pierwszego pola puste. Jeśli wszystkie pola nie jest pusty, fokus jest ustawiony do pierwszego pola.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [IPM_SETFOCUS](/windows/desktop/Controls/ipm-setfocus), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setfieldrange"></a>  CIPAddressCtrl::SetFieldRange

Ustawia zakres w określonym polu w formant adresu IP.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parametry

*nField*<br/>
Indeks zaczynający się od zera pola, do którego zostaną zastosowane zakresu.

*nLower*<br/>
Odwołanie do wartości całkowitej odbieranie dolną granicę określonego pola w tym formant adresu IP.

*nUpper*<br/>
Odwołanie do wartości całkowitej odbieranie górnego limitu określonego pola w tym formant adresu IP.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [IPM_SETRANGE](/windows/desktop/Controls/ipm-setrange), zgodnie z opisem w zestawie Windows SDK. Użyj dwóch parametrów *nLower* i *nUpper*, aby wskazać dolny i górny limit pola, zamiast *wRange* parametrem komunikat Win32.

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
