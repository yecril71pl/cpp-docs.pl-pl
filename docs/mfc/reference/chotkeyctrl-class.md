---
title: Klasa CHotKeyCtrl
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: 758fb78fbd4e25a0e2fb8cea300c5371ece04fb4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366885"
---
# <a name="chotkeyctrl-class"></a>Klasa CHotKeyCtrl

Udostępnia funkcje systemu Windows wspólny klawisz skrótu kontroli.

## <a name="syntax"></a>Składnia

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Konstruuje `CHotKeyCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHotKeyCtrl::Utwórz](#create)|Tworzy kontrolkę klawisza skrótu `CHotKeyCtrl` i dołącza go do obiektu.|
|[CHotKeyCtrl::CreateEx](#createex)|Tworzy kontrolkę klawisza skrótu z określonymi stylami rozszerzonymi systemu Windows i dołącza go do `CHotKeyCtrl` obiektu.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Pobiera kod klucza wirtualnego i flagi modyfikatora skrótu z kontrolki klawisza skrótu.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Pobiera nazwę klucza w lokalnym zestawie znaków przypisaną do klucza skrótu.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Pobiera nazwę klucza w lokalnym zestawie znaków przypisaną do określonego kodu klucza wirtualnego.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Ustawia kombinację klawiszy skrótu dla kontroli klawiszy skrótu.|
|[CHotKeyCtrl::SetRules](#setrules)|Definiuje nieprawidłowe kombinacje i domyślną kombinację modyfikatora dla formantu klawisza skrótu.|

## <a name="remarks"></a>Uwagi

"Kontrolka klawiszy skrótu" to okno, które umożliwia użytkownikowi utworzenie skrótu klawiszowego. "Klawisz skrótu" to kombinacja klawiszy, którą użytkownik może nacisnąć, aby szybko wykonać akcję. (Na przykład użytkownik może utworzyć klawisz skrótu, który aktywuje dane okno i przenosi go na górę zamówienia Z.) Kontrolka klawiszy skrótu wyświetla wybór użytkownika i zapewnia, że użytkownik wybierze prawidłową kombinację klawiszy.

Ten formant (i `CHotKeyCtrl` dlatego klasa) jest dostępny tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersji 3.51 lub nowszych.

Gdy użytkownik wybierze kombinację klawiszy, aplikacja może pobrać określoną kombinację klawiszy z formantu i użyć komunikatu WM_SETHOTKEY, aby skonfigurować klawisz skrótu w systemie. Za każdym razem, gdy użytkownik naciśnie klawisz skrótu, z dowolnej części systemu, okno określone w WM_SETHOTKEY wiadomości odbiera komunikat WM_SYSCOMMAND określający SC_HOTKEY. Ten komunikat aktywuje okno, które go odbiera. Klawisz skrótu pozostaje prawidłowy, dopóki aplikacja, która nazywa WM_SETHOTKEY kończy pracę.

Ten mechanizm różni się od obsługi klucza skrótu, który zależy od komunikatu WM_HOTKEY i funkcji [Windows RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) i [UnregisterHotKey.](/windows/win32/api/winuser/nf-winuser-unregisterhotkey)

Aby uzyskać więcej `CHotKeyCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl

Konstruuje `CHotKeyCtrl` obiekt.

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a>CHotKeyCtrl::Utwórz

Tworzy kontrolkę klawisza skrótu `CHotKeyCtrl` i dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu klawisza skrótu. Zastosuj dowolną kombinację stylów sterowania. Aby uzyskać więcej [informacji, zobacz Typowe style sterowania](/windows/win32/Controls/common-control-styles) w programie Windows SDK.

*Rect*<br/>
Określa rozmiar i położenie formantu klawisza skrótu. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT](/windows/win32/api/windef/ns-windef-rect).

*pParentWnd*<br/>
Określa okno nadrzędne formantu klawisza skrótu, zwykle [CDialog](../../mfc/reference/cdialog-class.md). Nie może być null.

*Nid*<br/>
Określa identyfikator formantu klawisza skrótu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CHotKeyCtrl` obiektu w dwóch krokach. Najpierw wywołaj konstruktora, a następnie wywołaj `Create`, co `CHotKeyCtrl` tworzy kontrolka klawisza skrótu i dołącza go do obiektu.

Jeśli chcesz używać rozszerzonych stylów okien z formantem, zadzwoń [do CreateEx](#createex) zamiast `Create`.

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a>CHotKeyCtrl::CreateEx

Wywołanie tej funkcji, aby utworzyć formant (okno `CHotKeyCtrl` podrzędne) i skojarzyć go z obiektem.

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
Określa styl formantu klawisza skrótu. Zastosuj dowolną kombinację stylów sterowania. Aby uzyskać więcej informacji, zobacz [Typowe style sterowania](/windows/win32/Controls/common-control-styles) w panelu Windows SDK.

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

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a>CHotKeyCtrl::GetHotKey

Pobiera kod klucza wirtualnego i flagi modyfikatora skrótu klawiaturowego z kontrolki klawiszy skrótu.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
[na zewnątrz] Wirtualny kod klawisza skrótu klawiaturowego. Aby uzyskać listę standardowych kodów kluczy wirtualnych, zobacz Winuser.h.

*wModifiers*<br/>
[na zewnątrz] Bitowa kombinacja (OR) flag wskazujących klawisze modyfikujące w skrótu klawiaturowym.

Flagi modyfikatora są następujące:

|Flaga|Odpowiedni klucz|
|----------|-----------------------|
|HOTKEYF_ALT|ALT — Klawisz|
|HOTKEYF_CONTROL|Klawisz CTRL|
|HOTKEYF_EXT|Klucz rozszerzony|
|HOTKEYF_SHIFT|Klawisz SHIFT|

### <a name="return-value"></a>Wartość zwracana

W pierwszej przeciążone metody DWORD, który zawiera kod klucza wirtualnego i flagi modyfikatora. Bajt niskiego rzędu słowa niskiego rzędu zawiera kod klucza wirtualnego, bajt wysokiego rzędu słowa niskiego rzędu zawiera flagi modyfikatora, a słowo wysokiego rzędu wynosi zero.

### <a name="remarks"></a>Uwagi

Kod klucza wirtualnego i klawisze modyfikatora razem definiują skrót klawiaturowy.

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać zlokalizowane nazwę klucza skrótu.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Wartość zwracana

Zlokalizowana nazwa aktualnie wybranego klucza skrótu. Jeśli nie ma zaznaczonego `GetHotKeyName` skrótu klawiszowego, zwraca pusty ciąg.

### <a name="remarks"></a>Uwagi

Nazwa zwracana przez tę funkcję elementu członkowskiego pochodzi od sterownika klawiatury. Nielokalizowany sterownik klawiatury można zainstalować w zlokalizowanej wersji systemu Windows i odwrotnie.

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a>CHotKeyCtrl::GetKeyName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać zlokalizowaną nazwę klucza przypisanego do określonego kodu klucza wirtualnego.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Parametry

*Vk*<br/>
Kod klucza wirtualnego.

*f Rozszerzony*<br/>
Jeśli kod klucza wirtualnego jest kluczem rozszerzonym, prawda; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Zlokalizowana nazwa klucza określona przez parametr *vk.* Jeśli klucz nie ma zamapowanej nazwy, `GetKeyName` zwraca pusty ciąg.

### <a name="remarks"></a>Uwagi

Nazwa klawisza zwracana przez tę funkcję pochodzi ze sterownika klawiatury, dzięki czemu można zainstalować niezlokalizowany sterownik klawiatury w zlokalizowanej wersji systemu Windows i odwrotnie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a>CHotKeyCtrl::SetHotKey

Ustawia skrót klawiaturowy dla kontrolki klawiszy skrótu.

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
[w] Wirtualny kod klawisza skrótu klawiaturowego. Aby uzyskać listę standardowych kodów kluczy wirtualnych, zobacz Winuser.h.

*wModifiers*<br/>
[w] Bitowa kombinacja (OR) flag wskazujących klawisze modyfikujące w skrótu klawiaturowym.

Flagi modyfikatora są następujące:

|Flaga|Odpowiedni klucz|
|----------|-----------------------|
|HOTKEYF_ALT|ALT — Klawisz|
|HOTKEYF_CONTROL|Klawisz CTRL|
|HOTKEYF_EXT|Klucz rozszerzony|
|HOTKEYF_SHIFT|Klawisz SHIFT|

### <a name="remarks"></a>Uwagi

Kod klucza wirtualnego i klawisze modyfikatora razem definiują skrót klawiaturowy.

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a>CHotKeyCtrl::SetRules

Wywołanie tej funkcji, aby zdefiniować nieprawidłowe kombinacje i domyślną kombinację modyfikatora dla formantu klawisza skrótu.

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wInvalidComb*<br/>
Tablica flag określająca nieprawidłowe kombinacje klawiszy. Może to być kombinacja następujących wartości:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL+ALT

- HKCOMB_NONE niezmodyfikowane klucze

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT+ALT

- HKCOMB_SC SHIFT+CTRL

- HKCOMB_SCA SHIFT+CTRL+ALT

*wModifiers*<br/>
Tablica flag określająca kombinację klawiszy, która ma być używana, gdy użytkownik wprowadzi nieprawidłową kombinację. Aby uzyskać więcej informacji na temat flag modyfikatora, zobacz [GetHotKey](#gethotkey).

### <a name="remarks"></a>Uwagi

Gdy użytkownik wprowadzi nieprawidłową kombinację klawiszy, zgodnie z definicją flag określonych w *wInvalidComb,* system używa operatora OR do łączenia klawiszy wprowadzonych przez użytkownika z flagami określonymi w *wModifiers*. Wynikowa kombinacja klawiszy jest konwertowana na ciąg, a następnie wyświetlana w formancie klawisza skrótu.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
