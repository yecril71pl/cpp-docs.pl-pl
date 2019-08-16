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
ms.openlocfilehash: 9818c32a7779d646ca5a9485a1331dfa393408ba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506151"
---
# <a name="chotkeyctrl-class"></a>Klasa CHotKeyCtrl

Oferuje funkcje formantu typowego klawisza dostępu systemu Windows.

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
|[CHotKeyCtrl:: Create](#create)|Tworzy formant klawisza dostępu i dołącza go do `CHotKeyCtrl` obiektu.|
|[CHotKeyCtrl::CreateEx](#createex)|Tworzy formant klawisza dostępu o określonych stylach rozszerzonych systemu Windows i dołącza go do `CHotKeyCtrl` obiektu.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Pobiera kod klucza wirtualnego i flagi modyfikatora klawisza skrótu z formantu klawisza dostępu.|
|[CHotKeyCtrl:: GetHotKeyName](#gethotkeyname)|Pobiera nazwę klucza w lokalnym zestawie znaków przypisanym do klawisza skrótu.|
|[CHotKeyCtrl:: getnazwaklucza](#getkeyname)|Pobiera nazwę klucza w lokalnym zestawie znaków przypisany do określonego kodu klucza wirtualnego.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Ustawia kombinację klawisza skrótu dla formantu klawisza dostępu.|
|[CHotKeyCtrl::SetRules](#setrules)|Definiuje nieprawidłowe kombinacje i domyślną kombinację modyfikatorów dla formantu klawisza dostępu.|

## <a name="remarks"></a>Uwagi

"Kontrolka klawisza dostępu" jest oknem, które umożliwia użytkownikowi tworzenie klawisza skrótu. "Klawisz dostępu" jest kombinacją klawiszy, którą użytkownik może nacisnąć, aby szybko wykonać akcję. (Na przykład użytkownik może utworzyć klawisz dostępu, który aktywuje danego okna i umieszcza go w górnej części porządku Z.) Kontrolka klawisza gorąca wyświetla opcje użytkownika i zapewnia, że użytkownik wybiera prawidłową kombinację klawiszy.

Ten formant (i w związku `CHotKeyCtrl` z tym Klasa) jest dostępny tylko dla programów uruchomionych w systemach Windows 95/98 i Windows NT w wersji 3,51 lub nowszej.

Gdy użytkownik wybierze kombinację klawiszy, aplikacja może pobrać określoną kombinację klawiszy z kontrolki i użyć komunikatu WM_SETHOTKEY do skonfigurowania klawisza skrótu w systemie. Za każdym razem, gdy użytkownik naciśnie klawisz gorąca, z dowolnej części systemu, okno określone w komunikacie WM_SETHOTKEY otrzymuje komunikat WM_SYSCOMMAND określający SC_HOTKEY. Ten komunikat aktywuje okno, które je odbiera. Klawisz dostępu pozostaje ważny do momentu, aż aplikacja, która wywołała WM_SETHOTKEY.

Ten mechanizm różni się od obsługi klucza gorącego, który zależy od komunikatu WM_HOTKEY oraz funkcji Windows [funkcję RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) i [UnregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) .

Aby uzyskać więcej informacji na `CHotKeyCtrl`temat korzystania z programu, zobacz [kontrolki](../../mfc/controls-mfc.md) i [Używanie CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="chotkeyctrl"></a>CHotKeyCtrl:: CHotKeyCtrl

Konstruuje `CHotKeyCtrl` obiekt.

```
CHotKeyCtrl();
```

##  <a name="create"></a>CHotKeyCtrl:: Create

Tworzy formant klawisza dostępu i dołącza go do `CHotKeyCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl formantu klawisza dostępu. Zastosuj dowolną kombinację stylów kontrolek. Aby uzyskać więcej informacji, zobacz [typowe style formantów](/windows/win32/Controls/common-control-styles) w Windows SDK.

*cinania*<br/>
Określa rozmiar i położenie kontrolki klawisza skrótu. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [Struktura](/windows/win32/api/windef/ns-windef-rect).

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki klawisza aktywnego, zazwyczaj [CDialog](../../mfc/reference/cdialog-class.md). Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki klawisza skrótu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CHotKeyCtrl` Obiekt jest konstruowany w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`, który tworzy formant klawisza dostępu i dołącza go `CHotKeyCtrl` do obiektu.

Jeśli chcesz użyć rozszerzonych stylów systemu Windows z kontrolką, wywołaj [CreateEx](#createex) zamiast `Create`.

##  <a name="createex"></a>CHotKeyCtrl:: CreateEx

Wywołaj tę funkcję, aby utworzyć kontrolkę (okno podrzędne) i skojarzyć ją z `CHotKeyCtrl` obiektem.

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
Określa styl formantu klawisza dostępu. Zastosuj dowolną kombinację stylów kontrolek. Aby uzyskać więcej informacji, zobacz [typowe style formantów](/windows/win32/Controls/common-control-styles) w Windows SDK.

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

##  <a name="gethotkey"></a>CHotKeyCtrl:: GetHotKey

Pobiera kod klucza wirtualnego i flagi modyfikatora skrótu klawiaturowego z formantu klawisza dostępu.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
określoną Kod klucza wirtualnego skrótu klawiaturowego. Aby uzyskać listę standardowych kodów kluczy wirtualnych, zobacz Winuser. h.

*wModifiers*<br/>
określoną Kombinacja bitowa (lub) flag wskazujących klawisze modyfikujące skrótu klawiaturowego.

Flagi modyfikatora są następujące:

|Flaga|Odpowiedni klucz|
|----------|-----------------------|
|HOTKEYF_ALT|ALT — Klawisz|
|HOTKEYF_CONTROL|Klawisz CTRL|
|HOTKEYF_EXT|Klucz rozszerzony|
|HOTKEYF_SHIFT|Klawisz SHIFT|

### <a name="return-value"></a>Wartość zwracana

W pierwszej przeciążonej metodzie DWORD, która zawiera kod klucza wirtualnego i flagi modyfikatora. Niewielka część wyrazu z niskim priorytetem zawiera kod klucza wirtualnego, czyli bajt o wysokim poziomie kolejności, zawierający flagi modyfikatora, a wyraz o wysokiej kolejności jest równy zero.

### <a name="remarks"></a>Uwagi

Kod klucza wirtualnego i klawisze modyfikujące wspólnie definiują skrót klawiaturowy.

##  <a name="gethotkeyname"></a>CHotKeyCtrl:: GetHotKeyName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać zlokalizowaną nazwę klawisza skrótu.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Wartość zwracana

Zlokalizowana nazwa aktualnie wybranego klawisza skrótu. Jeśli nie wybrano żadnego klawisza dostępu `GetHotKeyName` , zwraca pusty ciąg.

### <a name="remarks"></a>Uwagi

Nazwa zwracana przez tę funkcję elementu członkowskiego pochodzi ze sterownika klawiatury. Można zainstalować Niezlokalizowany sterownik klawiatury w zlokalizowanej wersji systemu Windows i na odwrót.

##  <a name="getkeyname"></a>CHotKeyCtrl:: getnazwaklucza

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać zlokalizowaną nazwę klucza przypisanego do określonego kodu klucza wirtualnego.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Parametry

*vk*<br/>
Kod klucza wirtualnego.

*fExtended*<br/>
Jeśli kod klucza wirtualnego jest kluczem rozszerzonym, prawda; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Zlokalizowana nazwa klucza określona przez parametr *VK* . Jeśli klucz nie ma zmapowanej nazwy, `GetKeyName` zwraca pusty ciąg.

### <a name="remarks"></a>Uwagi

Nazwa klucza, którą ta funkcja zwraca, pochodzi ze sterownika klawiatury, aby można było zainstalować Niezlokalizowany sterownik klawiatury w zlokalizowanej wersji systemu Windows i odwrotnie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>  CHotKeyCtrl::SetHotKey

Ustawia skrót klawiaturowy dla formantu klawisza dostępu.

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
podczas Kod klucza wirtualnego skrótu klawiaturowego. Aby uzyskać listę standardowych kodów kluczy wirtualnych, zobacz Winuser. h.

*wModifiers*<br/>
podczas Kombinacja bitowa (lub) flag wskazujących klawisze modyfikujące skrótu klawiaturowego.

Flagi modyfikatora są następujące:

|Flaga|Odpowiedni klucz|
|----------|-----------------------|
|HOTKEYF_ALT|ALT — Klawisz|
|HOTKEYF_CONTROL|Klawisz CTRL|
|HOTKEYF_EXT|Klucz rozszerzony|
|HOTKEYF_SHIFT|Klawisz SHIFT|

### <a name="remarks"></a>Uwagi

Kod klucza wirtualnego i klawisze modyfikujące wspólnie definiują skrót klawiaturowy.

##  <a name="setrules"></a>CHotKeyCtrl:: SetRules

Wywołaj tę funkcję, aby zdefiniować nieprawidłowe kombinacje i domyślną kombinację modyfikatora dla kontrolki klawisza skrótu.

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wInvalidComb*<br/>
Tablica flag, które określają nieprawidłowe kombinacje klawiszy. Może być kombinacją następujących wartości:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE niezmodyfikowanych kluczy

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT+ALT

- HKCOMB_SC SHIFT + CTRL

- HKCOMB_SCA SHIFT + CTRL + ALT

*wModifiers*<br/>
Tablica flag, która określa kombinację klawiszy, która ma zostać użyta, gdy użytkownik wprowadzi nieprawidłową kombinację. Aby uzyskać więcej informacji na temat flag modyfikatorów [](#gethotkey), zobacz GetHotKey.

### <a name="remarks"></a>Uwagi

Gdy użytkownik wprowadza nieprawidłową kombinację klawiszy zdefiniowaną przez flagi określone w *wInvalidComb*, system używa operatora OR, aby połączyć klucze wprowadzone przez użytkownika z flagami określonymi w *wModifiers*. Wynikająca kombinacja klawiszy jest konwertowana na ciąg, a następnie wyświetlana w kontrolce klawisza skrótu.

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
