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
ms.openlocfilehash: 71e3b1a9fde84f96696d26c891ab6688f246d575
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363314"
---
# <a name="cnetaddressctrl-class"></a>Klasa CNetAddressCtrl

Klasa `CNetAddressCtrl` reprezentuje kontrolę adresu sieciowego, której można użyć do wprowadzania i sprawdzania poprawności formatu adresów IPv4, IPv6 i nazwanych adresów DNS.

## <a name="syntax"></a>Składnia

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Konstruuje `CNetAddressCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNetAddressCtrl::Tworzenie](#create)|Tworzy kontrolkę adresu sieciowego z określonymi `CNetAddressCtrl` stylami i dołącza ją do bieżącego obiektu.|
|[CNetAddressCtrl::CreateEx](#createex)|Tworzy kontrolkę adresu sieciowego z określonymi rozszerzonymi stylami i dołącza ją do bieżącego `CNetAddressCtrl` obiektu.|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Wyświetla wskazówkię dymka błędu, gdy użytkownik wprowadzi nieobsługinięty adres sieciowy w bieżącym formancie adresu sieciowego.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Pobiera zweryfikowaną i przeanalizowaną reprezentację adresu sieciowego skojarzonego z bieżącą kontrolą adresu sieciowego.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Pobiera typ adresu sieciowego, który może obsługiwać bieżący formant adresu sieciowego.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Ustawia typ adresu sieciowego, który może obsługiwać bieżący formant adresu sieciowego.|

## <a name="remarks"></a>Uwagi

Formant adresu sieciowego sprawdza, czy format adresu, który użytkownik wprowadza, jest poprawny. Formant faktycznie nie łączy się z adresem sieciowym. [CNetAddressCtrl::SetAllowType](#setallowtype) metoda określa jeden lub więcej typów adresów, które [CNetAddressCtrl Metoda](#getaddress) może przeanalizować i zweryfikować. Adres może mieć postać adresu IPv4, IPv6 lub nazwanego adresu dla serwera, sieci, hosta lub miejsca docelowego wiadomości emisji. Jeśli format adresu jest nieprawidłowy, można użyć metody [CNetAddressCtrl::DisplayErrorTip,](#displayerrortip) aby wyświetlić okno komunikatu infotip, które graficznie wskazuje pole tekstowe formantu adresu sieciowego i wyświetla wstępnie zdefiniowany komunikat o błędzie.

Klasa `CNetAddressCtrl` jest pochodną [CEdit](../../mfc/reference/cedit-class.md) klasy. W związku z tym kontrola adresu sieciowego zapewnia dostęp do wszystkich komunikatów sterujących edycji systemu Windows.

Poniższy rysunek przedstawia okno dialogowe zawierające kontrolkę adresu sieciowego. Pole tekstowe (1) formantu adresu sieciowego zawiera nieprawidłowy adres sieciowy. Komunikat infotip (2) jest wyświetlany, jeśli adres sieciowy jest nieprawidłowy.

![Okno dialogowe z kontrolą adresu sieciowego i informacjami.](../../mfc/reference/media/cnetaddctrl.png "Okno dialogowe z kontrolą adresu sieciowego i informacjami.")

## <a name="example"></a>Przykład

Poniższy przykład kodu jest częścią okna dialogowego, które sprawdza poprawność adresu sieciowego. Programy obsługi zdarzeń dla trzech przycisków radiowych określają, że adres sieciowy może być jednym z trzech typów adresów. Użytkownik wprowadza adres w polu tekstowym formantu sieci, a następnie naciska przycisk, aby sprawdzić poprawność adresu. Jeśli adres jest prawidłowy, wyświetlany jest komunikat o powodach; w przeciwnym razie zostanie wyświetlony wstępnie zdefiniowany komunikat o błędzie infotip.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład kodu z pliku nagłówka okna dialogowego definiuje [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) i [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) zmiennych, które są wymagane przez [CNetAddressCtrl::GetAddress](#getaddress) metody.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cedit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

Ta klasa jest obsługiwana w systemie Windows Vista i nowszych.

Dodatkowe wymagania dla tej klasy są opisane w [wymagania dotyczące kompilacji dla wspólnych formantów systemu Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

## <a name="cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a>CNetAddressCtrl::CNetAddressCtrl

Konstruuje `CNetAddressCtrl` obiekt.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Uwagi

Użyj [CNetAddressCtrl::Create](#create) lub [CNetAddressCtrl::CreateEx](#createex) metody, aby utworzyć formant sieci i dołączyć go do `CNetAddressCtrl` obiektu.

## <a name="cnetaddressctrlcreate"></a><a name="create"></a>CNetAddressCtrl::Tworzenie

Tworzy kontrolkę adresu sieciowego z określonymi `CNetAddressCtrl` stylami i dołącza ją do bieżącego obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Dwstyle*|[w] Bitowa kombinacja stylów, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [Edytowanie stylów](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[w] Odwołanie do [struktury RECT,](/previous-versions/dd162897\(v=vs.85\)) która zawiera położenie i rozmiar formantu.|
|*pParentWnd*|[w] Wskaźnik inny niż null do [obiektu CWnd,](../../mfc/reference/cwnd-class.md) który jest nadrzędnym oknem formantu.|
|*Nid*|[w] Identyfikator formantu.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

## <a name="cnetaddressctrlcreateex"></a><a name="createex"></a>CNetAddressCtrl::CreateEx

Tworzy kontrolkę adresu sieciowego z określonymi rozszerzonymi stylami i dołącza ją do bieżącego `CNetAddressCtrl` obiektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Dwexstyle*|[w] Kombinacja bitowa (OR) stylów rozszerzonych, które mają być zastosowane do formantu. Aby uzyskać więcej informacji, zobacz parametr *dwExStyle* funkcji [CreateWindowEx.](/windows/win32/api/winuser/nf-winuser-createwindowexw)|
|*Dwstyle*|[w] Bitowe połączenie (OR) stylów, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [Edytowanie stylów](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[w] Odwołanie do [struktury RECT,](/previous-versions/dd162897\(v=vs.85\)) która zawiera położenie i rozmiar formantu.|
|*pParentWnd*|[w] Wskaźnik inny niż null do [obiektu CWnd,](../../mfc/reference/cwnd-class.md) który jest nadrzędnym oknem formantu.|
|*Nid*|[w] Identyfikator formantu.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

## <a name="cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a>CNetAddressCtrl::DisplayErrorTip

Wyświetla komunikat o błędzie w końcówce dymka skojarzonej z bieżącą kontrolą adresu sieciowego.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, `S_OK` jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metody, aby określić typy adresów, które bieżącego formantu adres sieci może obsługiwać. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody do sprawdzania poprawności i analizowania adresu sieciowego, który użytkownik wprowadza. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metody wyświetlania informacji komunikat o błędzie, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda nie powiedzie się.

Ten komunikat wywołuje [makro NetAddr_DisplayErrorTip,](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) które jest opisane w sdk systemu Windows. To makro `NCM_DISPLAYERRORTIP` wysyła wiadomość.

## <a name="cnetaddressctrlgetaddress"></a><a name="getaddress"></a>CNetAddressCtrl::GetAddress

Pobiera zweryfikowaną i przeanalizowaną reprezentację adresu sieciowego skojarzonego z bieżącą kontrolą adresu sieciowego.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parametry

*pAddress (adres pAddress)*<br/>
[w, na zewnątrz] Wskaźnik do [struktury NC_ADDRESS.](/windows/win32/api/shellapi/ns-shellapi-nc_address)  Ustaw element członkowski *pAddrInfo* tej struktury na adres [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) struktury przed wywołaniem GetAddress metody.

### <a name="return-value"></a>Wartość zwracana

Wartość S_OK, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie kod błędu COM. Aby uzyskać więcej informacji na temat możliwych kodów błędów, zobacz sekcję Wartość zwrotu [makra NetAddr_GetAddress.](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress)

### <a name="remarks"></a>Uwagi

Jeśli ta metoda zakończy się pomyślnie, [struktura NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) zawiera dodatkowe informacje o adresie sieciowym.

Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metody, aby określić typy adresów bieżącego formantu adres sieci może obsługiwać. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody do sprawdzania poprawności i analizowania adresu sieciowego, który użytkownik wprowadza. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metody wyświetlania informacji komunikat o błędzie, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda nie powiedzie się.

Ta metoda wywołuje [makro NetAddr_GetAddress,](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) które jest opisane w sdk systemu Windows. To makro wysyła komunikat NCM_GETADDRESS.

## <a name="cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a>CNetAddressCtrl::GetAllowType

Pobiera typ adresu sieciowego, który może obsługiwać bieżący formant adresu sieciowego.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Wartość zwracana

Bitowe połączenie (OR) flag, który określa typy adresów kontroli adresu sieciowego może obsługiwać. Aby uzyskać więcej informacji, zobacz [NET_STRING](/windows/win32/shell/net-string).

### <a name="remarks"></a>Uwagi

Ten komunikat wywołuje [makro NetAddr_GetAllowType,](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) które jest opisane w sdk systemu Windows. To makro wysyła komunikat NCM_GETALLOWTYPE.

## <a name="cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a>CNetAddressCtrl::SetAllowType

Ustawia typ adresu sieciowego, który może obsługiwać bieżący formant adresu sieciowego.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwAddrMask*|[w] Bitowe połączenie (OR) flag, który określa typy adresów kontroli adresu sieciowego może obsługiwać. Aby uzyskać więcej informacji, zobacz [NET_STRING](/windows/win32/shell/net-string).|

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie kod błędu COM.

### <a name="remarks"></a>Uwagi

Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metody, aby określić typy adresów, które bieżącego formantu adres sieci może obsługiwać. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody do sprawdzania poprawności i analizowania adresu sieciowego, który użytkownik wprowadza. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metody wyświetlania informacji komunikat o błędzie, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda nie powiedzie się.

Ten komunikat wywołuje [makro NetAddr_SetAllowType,](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) które jest opisane w sdk systemu Windows. To makro wysyła komunikat NCM_SETALLOWTYPE.

## <a name="see-also"></a>Zobacz też

[CNetAddressTrl Klasa](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)
