---
title: Klasa CNetAddressCtrl
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: 30fc510272afc90ae37b583e807d10c3374df052
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562132"
---
# <a name="cnetaddressctrl-class"></a>Klasa CNetAddressCtrl

`CNetAddressCtrl`Klasa reprezentuje kontrolę adresów sieciowych, za pomocą której można wprowadzać dane w formacie IPv4, IPv6 i nazwanych adresów DNS oraz sprawdzać ich poprawność.

## <a name="syntax"></a>Składnia

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNetAddressCtrl:: CNetAddressCtrl](#cnetaddressctrl)|Konstruuje `CNetAddressCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNetAddressCtrl:: Create](#create)|Tworzy kontrolę adresów sieciowych z określonymi stylami i dołącza je do bieżącego `CNetAddressCtrl` obiektu.|
|[CNetAddressCtrl:: CreateEx](#createex)|Tworzy kontrolę adresów sieciowych z określonymi stylami rozszerzonymi i dołącza je do bieżącego `CNetAddressCtrl` obiektu.|
|[CNetAddressCtrl::D isplayErrorTip](#displayerrortip)|Wyświetla wskazówkę dymek błędu, gdy użytkownik wprowadza nieobsługiwany adres sieciowy w bieżącej kontroli adresu sieciowego.|
|[CNetAddressCtrl:: GetAddress](#getaddress)|Pobiera zweryfikowaną i przeanalizowana reprezentację adresu sieciowego skojarzonego z bieżącą kontrolą adresu sieciowego.|
|[CNetAddressCtrl:: getallowtype](#getallowtype)|Pobiera typ adresu sieciowego, który może być obsługiwany przez bieżącą kontrolę adresu sieciowego.|
|[CNetAddressCtrl:: SetAllowType](#setallowtype)|Ustawia typ adresu sieciowego, który może być obsługiwany przez bieżącą kontrolę adresu sieciowego.|

## <a name="remarks"></a>Uwagi

Kontrolka adres sieciowy sprawdza, czy format adresu, który wprowadza użytkownik, jest poprawny. Kontrolka nie łączy się w rzeczywistości z adresem sieciowym. Metoda [CNetAddressCtrl:: SetAllowType](#setallowtype) określa jeden lub więcej typów adresów, które Metoda [CNetAddressCtrl:: GetAddress](#getaddress) może przeanalizować i zweryfikować. Adres może mieć postać adresu IPv4, IPv6 lub nazwanego adresu dla docelowej lokalizacji serwera, sieci, hosta lub komunikatu emisji. Jeśli format adresu jest niepoprawny, można użyć metody [CNetAddressCtrl::D isplayerrortip](#displayerrortip) , aby wyświetlić okno komunikatu z poradą, które wskazuje graficznie punkt tekstowy kontroli adresu sieciowego i wyświetla wstępnie zdefiniowany komunikat o błędzie.

`CNetAddressCtrl`Klasa pochodzi od klasy [CEdit](../../mfc/reference/cedit-class.md) . W związku z tym Kontrola adresów sieciowych zapewnia dostęp do wszystkich komunikatów kontroli systemu Windows.

Na poniższej ilustracji przedstawiono okno dialogowe zawierające kontrolę adresu sieciowego. Pole tekstowe (1) dla kontrolki adres sieciowy zawiera nieprawidłowy adres sieciowy. Komunikat porady (2) jest wyświetlany, jeśli adres sieciowy jest nieprawidłowy.

![Okno dialogowe z kontrolą adresu sieciowego i poradą.](../../mfc/reference/media/cnetaddctrl.png "Okno dialogowe z kontrolą adresu sieciowego i poradą.")

## <a name="example"></a>Przykład

Poniższy przykład kodu jest częścią okna dialogowego, która sprawdza poprawność adresu sieciowego. Programy obsługi zdarzeń dla trzech przycisków radiowych określają, że adres sieciowy może być jednym z trzech typów adresów. Użytkownik wprowadza adres w polu tekstowym kontrolki sieci, a następnie naciska przycisk, aby sprawdzić poprawność adresu. Jeśli adres jest prawidłowy, zostanie wyświetlony komunikat o powodzeniu. w przeciwnym razie zostanie wyświetlony wstępnie zdefiniowany komunikat o błędzie porady.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład kodu z pliku nagłówkowego okna dialogowego definiuje zmienne [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) i [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) , które są wymagane przez metodę [CNetAddressCtrl:: GetAddress](#getaddress) .

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

Ta klasa jest obsługiwana w systemie Windows Vista i nowszych.

Dodatkowe wymagania dotyczące tej klasy zostały opisane w temacie [wymagania dotyczące kompilacji dla wspólnych formantów systemu Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

## <a name="cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a> CNetAddressCtrl:: CNetAddressCtrl

Konstruuje `CNetAddressCtrl` obiekt.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Uwagi

Użyj metody [CNetAddressCtrl:: Create](#create) lub [CNetAddressCtrl:: CreateEx](#createex) , aby utworzyć kontrolkę sieci i dołączyć ją do `CNetAddressCtrl` obiektu.

## <a name="cnetaddressctrlcreate"></a><a name="create"></a> CNetAddressCtrl:: Create

Tworzy kontrolę adresów sieciowych z określonymi stylami i dołącza je do bieżącego `CNetAddressCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*\
podczas Bitowa kombinacja stylów do zastosowania do kontrolki. Aby uzyskać więcej informacji, zobacz [Edytowanie stylów](../../mfc/reference/styles-used-by-mfc.md#edit-styles).

*cinania*\
podczas Odwołanie do struktury [Rect](/windows/win32/api/windef/ns-windef-rect) , która zawiera położenie i rozmiar kontrolki.

*pParentWnd*\
podczas Wskaźnik o wartości innej niż null do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który jest oknem nadrzędnym formantu.

*nID*\
podczas Identyfikator kontrolki.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

## <a name="cnetaddressctrlcreateex"></a><a name="createex"></a> CNetAddressCtrl:: CreateEx

Tworzy kontrolę adresów sieciowych z określonymi stylami rozszerzonymi i dołącza je do bieżącego `CNetAddressCtrl` obiektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*\
podczas Bitowa kombinacja (lub) rozszerzonych stylów do zastosowania do kontrolki. Aby uzyskać więcej informacji, zobacz parametr *dwExStyle* funkcji [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .

*dwStyle*\
podczas Kombinacja bitowa (lub) stylów do zastosowania do kontrolki. Aby uzyskać więcej informacji, zobacz [Edytowanie stylów](../../mfc/reference/styles-used-by-mfc.md#edit-styles).

*cinania*\
podczas Odwołanie do struktury [Rect](/windows/win32/api/windef/ns-windef-rect) , która zawiera położenie i rozmiar kontrolki.

*pParentWnd*\
podczas Wskaźnik o wartości innej niż null do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który jest oknem nadrzędnym formantu.

*nID*\
podczas Identyfikator kontrolki.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

## <a name="cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a> CNetAddressCtrl::D isplayErrorTip

Wyświetla komunikat o błędzie w etykietce dymka, która jest skojarzona z bieżącym formantem adresu sieciowego.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Wartość zwracana

Wartość `S_OK` , jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

Użyj metody [CNetAddressCtrl:: SetAllowType](#setallowtype) , aby określić typy adresów, które mogą być obsługiwane przez bieżącą kontrolę adresu sieciowego. Użyj metody [CNetAddressCtrl:: GetAddress](#getaddress) , aby sprawdzić poprawność i przeanalizować adres sieciowy wprowadzony przez użytkownika. Użyj metody [CNetAddressCtrl::D isplayerrortip](#displayerrortip) , aby wyświetlić poradę komunikatu o błędzie, jeśli metoda [CNetAddressCtrl:: GetAddress](#getaddress) nie powiedzie się.

Ten komunikat wywołuje [NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) makro, które jest opisane w Windows SDK. To makro wysyła `NCM_DISPLAYERRORTIP` komunikat.

## <a name="cnetaddressctrlgetaddress"></a><a name="getaddress"></a> CNetAddressCtrl:: GetAddress

Pobiera zweryfikowaną i przeanalizowana reprezentację adresu sieciowego skojarzonego z bieżącą kontrolą adresu sieciowego.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parametry

*pAddress*<br/>
[in. out] Wskaźnik do struktury [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) .  Przed wywołaniem metody GetAddress Ustaw element członkowski *pAddrInfo* tej struktury na adres struktury [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) .

### <a name="return-value"></a>Wartość zwracana

Wartość S_OK, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie kod błędu COM. Aby uzyskać więcej informacji o możliwych kodach błędów, zobacz sekcję wartość zwracana w makrze [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) .

### <a name="remarks"></a>Uwagi

Jeśli ta metoda zakończy się pomyślnie, struktura [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) zawiera dodatkowe informacje o adresie sieciowym.

Użyj metody [CNetAddressCtrl:: SetAllowType](#setallowtype) , aby określić typy adresów, które może obsługiwać bieżąca Kontrola adresów sieciowych. Użyj metody [CNetAddressCtrl:: GetAddress](#getaddress) , aby sprawdzić poprawność i przeanalizować adres sieciowy wprowadzony przez użytkownika. Użyj metody [CNetAddressCtrl::D isplayerrortip](#displayerrortip) , aby wyświetlić poradę komunikatu o błędzie, jeśli metoda [CNetAddressCtrl:: GetAddress](#getaddress) nie powiedzie się.

Ta metoda wywołuje [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) makro, które jest opisane w Windows SDK. To makro wysyła komunikat NCM_GETADDRESS.

## <a name="cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a> CNetAddressCtrl:: getallowtype

Pobiera typ adresu sieciowego, który może być obsługiwany przez bieżącą kontrolę adresu sieciowego.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Wartość zwracana

Kombinacja bitowa (lub) flag, która określa typy adresów, które może obsługiwać kontrola adresów sieciowych. Aby uzyskać więcej informacji, zobacz [NET_STRING](/windows/win32/shell/net-string).

### <a name="remarks"></a>Uwagi

Ten komunikat wywołuje [NetAddr_GetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) makro, które jest opisane w Windows SDK. To makro wysyła komunikat NCM_GETALLOWTYPE.

## <a name="cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a> CNetAddressCtrl:: SetAllowType

Ustawia typ adresu sieciowego, który może być obsługiwany przez bieżącą kontrolę adresu sieciowego.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parametry

*dwAddrMask*\
podczas Kombinacja bitowa (lub) flag, która określa typy adresów, które może obsługiwać kontrola adresów sieciowych. Aby uzyskać więcej informacji, zobacz [NET_STRING](/windows/win32/shell/net-string).

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie kod błędu COM.

### <a name="remarks"></a>Uwagi

Użyj metody [CNetAddressCtrl:: SetAllowType](#setallowtype) , aby określić typy adresów, które mogą być obsługiwane przez bieżącą kontrolę adresu sieciowego. Użyj metody [CNetAddressCtrl:: GetAddress](#getaddress) , aby sprawdzić poprawność i przeanalizować adres sieciowy wprowadzony przez użytkownika. Użyj metody [CNetAddressCtrl::D isplayerrortip](#displayerrortip) , aby wyświetlić poradę komunikatu o błędzie, jeśli metoda [CNetAddressCtrl:: GetAddress](#getaddress) nie powiedzie się.

Ten komunikat wywołuje [NetAddr_SetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) makro, które jest opisane w Windows SDK. To makro wysyła komunikat NCM_SETALLOWTYPE.

## <a name="see-also"></a>Zobacz też

[Klasa CNetAddressCtrl](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)
