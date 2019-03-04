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
ms.openlocfilehash: 51198b44346785369771f63b80164c1a131f6950
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279692"
---
# <a name="cnetaddressctrl-class"></a>Klasa CNetAddressCtrl

`CNetAddressCtrl` Klasa reprezentuje formant adresu sieciowego, który służy do wprowadzania i sprawdzania poprawności formatu IPv4, IPv6 i nazwanych adresów DNS.

## <a name="syntax"></a>Składnia

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Konstruuje `CNetAddressCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNetAddressCtrl::Create](#create)|Tworzy formant adresu sieciowego przy użyciu określonego stylów i dołącza go do bieżącego `CNetAddressCtrl` obiektu.|
|[CNetAddressCtrl::CreateEx](#createex)|Tworzy formant adresu sieciowego przy użyciu określonego style rozszerzone i dołącza go do bieżącego `CNetAddressCtrl` obiektu.|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Wyświetla dymku błąd, gdy użytkownik wprowadzi adres sieciowy nieobsługiwane w bieżącej formant adresu sieciowego.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Pobiera reprezentację adres sieciowy skojarzony z bieżącym formant adresu sieciowego zweryfikowane i przeanalizowane.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Pobiera typ adresu sieciowego, który może obsługiwać bieżące formant adresu sieciowego.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Ustawia typ adresu sieciowego, który może obsługiwać bieżące formant adresu sieciowego.|

## <a name="remarks"></a>Uwagi

Formant adresu sieciowego sprawdza, czy format adresu, wprowadzanych przez użytkownika jest poprawna. Kontrolka nie faktycznie połączyć się z adresu sieciowego. [CNetAddressCtrl::SetAllowType](#setallowtype) metody określa co najmniej jeden typ adresu, [CNetAddressCtrl::GetAddress](#getaddress) metoda można przeanalizować i sprawdzić. Adres może być w formie IPv4, IPv6 lub nazwane adres serwera, sieci, hosta lub docelowej komunikat emisji. Jeśli format adresu jest niepoprawny, możesz użyć [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodę, aby wyświetlić okno komunikatu porady, które graficznie wskazuje formant adresu sieciowego, w polu tekstowym i wyświetla wstępnie zdefiniowanej komunikat o błędzie.

`CNetAddressCtrl` Klasa pochodzi od [CEdit](../../mfc/reference/cedit-class.md) klasy. W związku z tym formant adresu sieciowego zapewnia dostęp do wszystkich komunikatów sterujących edycji Windows.

Poniższa ilustracja przedstawia okno dialogowe, który zawiera formant adresu sieciowego. Tekst pola (1) dla formant adresu sieciowego zawiera nieprawidłowy adres sieciowy. Zostanie wyświetlony komunikat Porada (2), jeśli adres sieciowy jest nieprawidłowy.

![Okno dialogowe z formant adresu sieciowego i porady. ](../../mfc/reference/media/cnetaddctrl.png "Okna dialogowego z formantem adresu sieciowego i porady.")

## <a name="example"></a>Przykład

Poniższy przykład kodu jest częścią okno dialogowe, które sprawdza poprawność adresu sieciowego. Programy obsługi zdarzeń dla trzech przycisków radiowych Określ adres sieciowy może być jednym z trzech typów adresu. Użytkownik wprowadzi adres w polu tekstowym kontroli sieci, a następnie naciska przycisk, aby zweryfikować adresu. Jeśli adres jest prawidłowy, jest wyświetlany komunikat o powodzeniu; w przeciwnym razie jest wyświetlany komunikat o błędzie Porada wstępnie zdefiniowane.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład kodu z okna dialogowego pliku nagłówka definiuje [NC_ADDRESS](/windows/desktop/api/shellapi/ns-shellapi-tagnc_address) i [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) zmiennych, które są wymagane przez [CNetAddressCtrl::GetAddress](#getaddress)metody.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

Ta klasa jest obsługiwana w Windows Vista i nowszych wersjach.

Dodatkowe wymagania dla tej klasy są opisane w [tworzenie wymagania dla Windows Vista wspólnych formantów](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="cnetaddressctrl"></a>  CNetAddressCtrl::CNetAddressCtrl

Konstruuje `CNetAddressCtrl` obiektu.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Uwagi

Użyj [CNetAddressCtrl::Create](#create) lub [CNetAddressCtrl::CreateEx](#createex) metodę, aby utworzyć formant sieci i dołącz je do `CNetAddressCtrl` obiektu.

##  <a name="create"></a>  CNetAddressCtrl::Create

Tworzy formant adresu sieciowego przy użyciu określonego stylów i dołącza go do bieżącego `CNetAddressCtrl` obiektu.

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
|*dwStyle*|[in] Bitowa kombinacja style, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [Edytuj style](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[in] Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która zawiera położenie i rozmiar kontrolki.|
|*pParentWnd*|[in] Wskaźnik zerowy [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki.|
|*nID*|[in] Identyfikator kontrolki.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="createex"></a>  CNetAddressCtrl::CreateEx

Tworzy formant adresu sieciowego przy użyciu określonego style rozszerzone i dołącza go do bieżącego `CNetAddressCtrl` obiektu.

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
|*dwExStyle*|[in] Bitowa kombinacja (lub) rozszerzone style, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz *dwExStyle* parametru [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) funkcji.|
|*dwStyle*|[in] Bitowa kombinacja (lub) style, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [Edytuj style](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[in] Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która zawiera położenie i rozmiar kontrolki.|
|*pParentWnd*|[in] Wskaźnik zerowy [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki.|
|*nID*|[in] Identyfikator kontrolki.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="displayerrortip"></a>  CNetAddressCtrl::DisplayErrorTip

Wyświetla komunikat o błędzie w dymku, który jest skojarzony z bieżącym formant adresu sieciowego.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Wartość zwracana

Wartość `S_OK` Jeśli ta metoda jest powiodła się; w przeciwnym razie, kod błędu.

### <a name="remarks"></a>Uwagi

Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metodę, aby określić typy adresów, które może obsługiwać bieżące formant adresu sieciowego. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody sprawdzania poprawności i przeanalizować adresu sieciowego, wprowadzonych przez użytkownika. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodę w celu wyświetlenia poradę komunikat o błędzie, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda zakończy się niepowodzeniem.

Ten komunikat, wywołuje [NetAddr_DisplayErrorTip](/windows/desktop/api/shellapi/nf-shellapi-netaddr_displayerrortip) makro, który jest opisany w zestawie Windows SDK. Wysyła tego makra `NCM_DISPLAYERRORTIP` wiadomości.

##  <a name="getaddress"></a>  CNetAddressCtrl::GetAddress

Pobiera reprezentację adresu sieciowego, który jest skojarzony z bieżącym formant adresu sieciowego zweryfikowane i przeanalizowane.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parametry

*pAddress*<br/>
[out w] Wskaźnik do [NC_ADDRESS](/windows/desktop/api/shellapi/ns-shellapi-tagnc_address) struktury.  Ustaw *pAddrInfo* członkiem tej struktury adres [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) struktury przed wywołaniem getaddress — metoda.

### <a name="return-value"></a>Wartość zwracana

Wartość S_OK, jeśli ta metoda się powiedzie; w przeciwnym razie kod błędu modelu COM. Aby uzyskać więcej informacji na temat możliwych kodów błędów, zobacz sekcję zwracają wartość [NetAddr_GetAddress](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getaddress) makra.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda zakończy się pomyślnie, [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) struktura zawiera dodatkowe informacje na temat adresu sieciowego.

Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metodę, aby określić typy adresów może obsługiwać bieżące formant adresu sieciowego. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody sprawdzania poprawności i przeanalizować adresu sieciowego, wprowadzonych przez użytkownika. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodę w celu wyświetlenia poradę komunikat o błędzie, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda zakończy się niepowodzeniem.

Ta metoda wywołuje [NetAddr_GetAddress](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getaddress) makro, który jest opisany w zestawie Windows SDK. Makra wysyła komunikat NCM_GETADDRESS.

##  <a name="getallowtype"></a>  CNetAddressCtrl::GetAllowType

Pobiera typ adresu sieciowego, który może obsługiwać bieżące formant adresu sieciowego.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Wartość zwracana

Bitowa kombinacja (lub) flagami określający typy adresów może obsługiwać formant adresu sieciowego. Aby uzyskać więcej informacji, zobacz [NET_STRING](https://msdn.microsoft.com/library/windows/desktop/bb762586).

### <a name="remarks"></a>Uwagi

Ten komunikat, wywołuje [NetAddr_GetAllowType](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getallowtype) makro, który jest opisany w zestawie Windows SDK. Makra wysyła komunikat NCM_GETALLOWTYPE.

##  <a name="setallowtype"></a>  CNetAddressCtrl::SetAllowType

Ustawia typ adresu sieciowego, który może obsługiwać bieżące formant adresu sieciowego.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*dwAddrMask*|[in] Bitowa kombinacja (lub) flagami określający typy adresów może obsługiwać formant adresu sieciowego. Aby uzyskać więcej informacji, zobacz [NET_STRING](https://msdn.microsoft.com/library/windows/desktop/bb762586).|

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli ta metoda się powiedzie; w przeciwnym razie kod błędu modelu COM.

### <a name="remarks"></a>Uwagi

Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metodę, aby określić typy adresów, które może obsługiwać bieżące formant adresu sieciowego. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody sprawdzania poprawności i przeanalizować adresu sieciowego, wprowadzonych przez użytkownika. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodę w celu wyświetlenia poradę komunikat o błędzie, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda zakończy się niepowodzeniem.

Ten komunikat, wywołuje [NetAddr_SetAllowType](/windows/desktop/api/shellapi/nf-shellapi-netaddr_setallowtype) makro, który jest opisany w zestawie Windows SDK. Makra wysyła komunikat NCM_SETALLOWTYPE.

## <a name="see-also"></a>Zobacz także

[Klasa CNetAddressCtrl](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)
