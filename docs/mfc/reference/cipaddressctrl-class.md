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
ms.openlocfilehash: 28aa0e7137647bc49406dab1e82b9c2b05ca3538
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372339"
---
# <a name="cipaddressctrl-class"></a>Klasa CIPAddressCtrl

Udostępnia funkcje kontroli wspólnego adresu IP systemu Windows.

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
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Czyści zawartość formantu adresu IP.|
|[CIPAddressCtrl::Utwórz](#create)|Tworzy formant adresu IP i `CIPAddressCtrl` dołącza go do obiektu.|
|[CIPAddressCtrl::CreateEx](#createex)|Tworzy kontrolkę adres IP z określonymi stylami `CIPAddressCtrl` rozszerzonymi systemu Windows i dołącza go do obiektu.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Pobiera wartości adresów dla wszystkich czterech pól w formancie adresu IP.|
|[CIPAddressCtrl::IsBlank](#isblank)|Określa, czy wszystkie pola w formancie adresu IP są puste.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Ustawia wartości adresów dla wszystkich czterech pól w formancie adresu IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Ustawia fokus klawiatury na określone pole w formancie adresu IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Ustawia zakres w określonym polu w formancie adresu IP.|

## <a name="remarks"></a>Uwagi

Formant adresu IP, formant podobny do formantu edycji, umożliwia wprowadzanie i manipulowanie adresem numerycznym w formacie protokołu INTERNETOWEGO (IP).

Ten formant (i `CIPAddressCtrl` dlatego klasa) jest dostępny tylko dla programów uruchomionych w programie Microsoft Internet Explorer 4.0 i nowszych. Będą one również dostępne w przyszłych wersjach systemów Windows i Windows NT.

Aby uzyskać bardziej ogólne informacje na temat kontroli adresów IP, zobacz [Formanty adresów IP](/windows/win32/Controls/ip-address-controls) w panelu Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl

Tworzy obiekt `CIPAddressCtrl`.

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a>CIPAddressCtrl::ClearAddress

Czyści zawartość formantu adresu IP.

```
void ClearAddress();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="cipaddressctrlcreate"></a><a name="create"></a>CIPAddressCtrl::Utwórz

Tworzy formant adresu IP i `CIPAddressCtrl` dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Styl formantu adres IP. Stosowanie kombinacji stylów okien. Należy dołączyć styl WS_CHILD, ponieważ formant musi być oknem podrzędnym. Zobacz [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) w zestawie Windows SDK, aby uzyskać listę stylów systemu Windows.

*Rect*<br/>
Odwołanie do rozmiaru i położenia formantu adresu IP. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego formantu adresu IP. Nie może być null.

*Nid*<br/>
Identyfikator kontroli adresów IP.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CIPAddressCtrl` obiektu w dwóch krokach.

1. Wywołaj konstruktora, `CIPAddressCtrl` który tworzy obiekt.

1. Wywołanie `Create`, który tworzy formant adresu IP.

Jeśli chcesz używać rozszerzonych stylów okien z formantem, zadzwoń [do CreateEx](#createex) zamiast `Create`.

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a>CIPAddressCtrl::CreateEx

Wywołanie tej funkcji, aby utworzyć formant (okno `CIPAddressCtrl` podrzędne) i skojarzyć go z obiektem.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwexstyle*<br/>
Określa rozszerzony styl tworzonego formantu. Aby uzyskać listę rozszerzonych stylów systemu Windows, zobacz parametr *dwExStyle* dla [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

*Dwstyle*<br/>
Styl formantu adres IP. Stosowanie kombinacji stylów okien. Należy dołączyć styl WS_CHILD, ponieważ formant musi być oknem podrzędnym. Zobacz [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) w zestawie Windows SDK, aby uzyskać listę stylów systemu Windows.

*Rect*<br/>
Odwołanie do struktury [RECT](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Nid*<br/>
Identyfikator okna podrzędnego formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Create,](#create) aby zastosować rozszerzone style systemu Windows, określone przez przedmową styl rozszerzony systemu Windows **WS_EX_**.

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a>CIPAddressCtrl::GetAddress

Pobiera wartości adresów dla wszystkich czterech pól w formancie adresu IP.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>Parametry

*nPolsze0*<br/>
Odwołanie do wartości pola 0 z spakowanego adresu IP.

*nField1*<br/>
Odwołanie do wartości pola 1 z spakowanego adresu IP.

*nField2 (własnach)*<br/>
Odwołanie do wartości pola 2 z spakowanego adresu IP.

*nField3 ( nField3 )*<br/>
Odwołanie do wartości pola 3 z spakowanego adresu IP.

*dwAddress (adres zdań)*<br/>
Odwołanie do adresu wartości DWORD, która odbiera adres IP. Zobacz **Uwagi** dla tabeli, która pokazuje, jak *dwAddress* jest wypełniona.

### <a name="return-value"></a>Wartość zwracana

Liczba nieokreślone pola w formancie adresu IP.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)komunikatu Win32, zgodnie z opisem w windows SDK. W pierwszym prototypie powyżej liczby w polach od 0 do 3 formantu, odczytywane odpowiednio od lewej do prawej, wypełniają cztery parametry. W drugim prototypie *powyżej, dwAddress* jest wypełniona w następujący sposób.

|Pole|Bity zawierające wartość pola|
|-----------|-------------------------------------|
|0|od 24 do 31|
|1|od 16 do 23|
|2|od 8 do 15|
|3|Od 0 do 7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a>CIPAddressCtrl::IsBlank

Określa, czy wszystkie pola w formancie adresu IP są puste.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wszystkie pola kontroli adresu IP są puste; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a>CIPAddressCtrl::SetAddress

Ustawia wartości adresów dla wszystkich czterech pól w formancie adresu IP.

```
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Parametry

*nPolsze0*<br/>
Wartość pola 0 z spakowanego adresu IP.

*nField1*<br/>
Wartość pola 1 z spakowanego adresu IP.

*nField2 (własnach)*<br/>
Wartość pola 2 z spakowanego adresu IP.

*nField3 ( nField3 )*<br/>
Wartość pola 3 z spakowanego adresu IP.

*dwAddress (adres zdań)*<br/>
Wartość DWORD zawierająca nowy adres IP. Zobacz **Uwagi** dla tabeli, która pokazuje, jak wartość DWORD jest wypełniona.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)komunikatu Win32, zgodnie z opisem w windows SDK. W pierwszym prototypie powyżej liczby w polach od 0 do 3 formantu, odczytywane odpowiednio od lewej do prawej, wypełniają cztery parametry. W drugim prototypie *powyżej, dwAddress* jest wypełniona w następujący sposób.

|Pole|Bity zawierające wartość pola|
|-----------|-------------------------------------|
|0|od 24 do 31|
|1|od 16 do 23|
|2|od 8 do 15|
|3|Od 0 do 7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus

Ustawia fokus klawiatury na określone pole w formancie adresu IP.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parametry

*nPole*<br/>
Indeks pola opartego na wartości zerowej, na który należy ustawić fokus. Jeśli ta wartość jest większa niż liczba pól, fokus jest ustawiony na pierwsze puste pole. Jeśli wszystkie pola nie są puste, fokus jest ustawiony na pierwsze pole.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

Ustawia zakres w określonym polu w formancie adresu IP.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parametry

*nPole*<br/>
Indeks pola od zera, do którego zostanie zastosowany zakres.

*nLower*<br/>
Odwołanie do liczby całkowitej odbierającej dolny limit określonego pola w tym formancie adresu IP.

*nUpper (nUpper)*<br/>
Odwołanie do liczby całkowitej odbierającej górną granicę określonego pola w tym formancie adresu IP.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)komunikatu Win32, zgodnie z opisem w windows SDK. Użyj dwóch parametrów, *nLower* i *nUpper*, aby wskazać dolną i górną granicę pola, zamiast parametru *wRange* używanego z komunikatem Win32.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
