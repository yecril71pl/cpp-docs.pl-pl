---
title: "Chotkeyctrl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9bf8168525c89188e27f2982255647b454a22c7d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chotkeyctrl-class"></a>Chotkeyctrl — klasa
Udostępnia funkcje systemu Windows wspólnej formantu klawisza dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CHotKeyCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Konstruuje `CHotKeyCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHotKeyCtrl::Create](#create)|Tworzy formantu klawisza dostępu i dołącza go do `CHotKeyCtrl` obiektu.|  
|[CHotKeyCtrl::CreateEx](#createex)|Tworzy formantu klawisza dostępu przy użyciu określonego stylów rozszerzonej systemu Windows i dołącza go do `CHotKeyCtrl` obiektu.|  
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Pobiera wirtualnego klucza flagi kodu i modyfikator klucza dostępu z formantu klawisza dostępu.|  
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Pobiera nazwę klucza, w zestawie znaków lokalnych przypisane do klawisza dostępu.|  
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Pobiera nazwę klucza, w zestawie znaków lokalnych przypisane do określonej wirtualnej kod klucza.|  
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Określa kombinację klawiszy dostępu dla formantu klawisza dostępu.|  
|[CHotKeyCtrl::SetRules](#setrules)|Określa nieprawidłowy kombinacji i kombinacja modyfikatora domyślnego dla formantu klawisza dostępu.|  
  
## <a name="remarks"></a>Uwagi  
 "Formantu klawisza dostępu" jest typu window, który umożliwia użytkownikowi utworzenie klawisza dostępu. "Klawisz skrótu" jest kombinacja klawiszy, które użytkownik może nacisnąć szybko wykonania akcji. (Na przykład użytkownik może utworzyć klawisza dostępu, który aktywuje danego okna i aktualizuje na początku porządek osi). Formantu klawisza dostępu Wyświetla opcje użytkownika oraz zapewnia, że użytkownik wybierze prawidłową kombinację klawiszy.  
  
 Ten formant (i w związku z tym `CHotKeyCtrl` klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Gdy użytkownik wybierze kombinację klawiszy, aplikacja może pobrać kombinację klawiszy z formantu i użyj **WM_SETHOTKEY** wiadomości, aby skonfigurować klawisza dostępu w systemie. Przy każdym naciśnięciu klawisza dostępu, z dowolną część systemu, okna określony w **WM_SETHOTKEY** odbiera komunikat `WM_SYSCOMMAND` Określanie komunikatu **SC_HOTKEY**. Ten komunikat zostanie aktywowany okna, który odbiera on. Klawisz dostępu pozostaje ważny aż do aplikacji, która wywołuje **WM_SETHOTKEY** kończy pracę.  
  
 Ten mechanizm różni się od gorących klucza pomocy technicznej, która jest zależna od **WM_HOTKEY** komunikat i systemu Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309) i [UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327) funkcji.  
  
 Aby uzyskać więcej informacji na temat używania `CHotKeyCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHotKeyCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl  
 Konstruuje `CHotKeyCtrl` obiektu.  
  
```  
CHotKeyCtrl();
```  
  
##  <a name="create"></a>CHotKeyCtrl::Create  
 Tworzy formantu klawisza dostępu i dołącza go do `CHotKeyCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl formantu klawisza dostępu firmy. Zastosuj dowolną kombinację stylów formantu. Zobacz [najczęściej używane style formantu](http://msdn.microsoft.com/library/windows/desktop/bb775498) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
 `rect`  
 Określa rozmiar i położenie gorących sterujący klucza. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [struktura RECT](../../mfc/reference/rect-structure1.md).  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki klucza dostępu, zwykle [cdialog —](../../mfc/reference/cdialog-class.md). Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu klawisza dostępu firmy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CHotKeyCtrl` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać **Utwórz**, która tworzy formantu klawisza dostępu i dołącza go do `CHotKeyCtrl` obiektu.  
  
 Jeśli chcesz style rozszerzonej systemu windows za pomocą formantu wywołanie [CreateEx](#createex) zamiast **Utwórz**.  
  
##  <a name="createex"></a>CHotKeyCtrl::CreateEx  
 Wywołanie tej funkcji można utworzyć formantu (okno podrzędne) i skojarz ją z `CHotKeyCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Określa styl rozszerzony formantu tworzona. Aby uzyskać listę rozszerzone style systemu Windows, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 `dwStyle`  
 Określa styl formantu klawisza dostępu firmy. Zastosuj dowolną kombinację stylów formantu. Aby uzyskać więcej informacji, zobacz [najczęściej używane style formantu](http://msdn.microsoft.com/library/windows/desktop/bb775498) w zestawie Windows SDK.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujące rozmiar i położenie okna, które ma zostać utworzony w współrzędne klienta `pParentWnd`.  
  
 `pParentWnd`  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 `nID`  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="gethotkey"></a>CHotKeyCtrl::GetHotKey  
 Pobiera wirtualnego klucza flagi kodu i modyfikator skrótu klawiatury z formantu klawisza dostępu.  
  
```  
DWORD GetHotKey() const;  
  
void GetHotKey(
    WORD& wVirtualKeyCode,  
    WORD& wModifiers) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`wVirtualKeyCode`  
 Kod klucza wirtualnego skrót klawiaturowy. Listę standardowych wirtualnego kodów klucza Zobacz Winuser.h.  
  
 [out]`wModifiers`  
 Bitowe połączenie (lub) flag, które wskazują klawisze modyfikujące w skrót klawiaturowy.  
  
 Modyfikator flagi są następujące:  
  
|Flaga|Odpowiedni klucz|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|ALT — Klawisz|  
|`HOTKEYF_CONTROL`|Klawisz CTRL|  
|`HOTKEYF_EXT`|Rozszerzone klucza|  
|`HOTKEYF_SHIFT`|Klawisz SHIFT|  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym przeciążonej metody, `DWORD` zawierający wirtualnego klucza flagi kodu i modyfikator. Mniej znaczącego bajtu Word znaczącymi bitami zawiera wirtualnego kod klucza, byte znaczących Word znaczącymi bitami zawiera flagi modyfikator i word znaczących wynosi zero.  
  
### <a name="remarks"></a>Uwagi  
 Kod klucza wirtualnego i jednocześnie klawisze modyfikujące definiują skrót klawiaturowy.  
  
##  <a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName  
 Wywołanie tej funkcji Członkowskich uzyskanie zlokalizowana nazwa klawisza dostępu.  
  
```  
CString GetHotKeyName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zlokalizowana nazwa aktualnie wybranego klucza dostępu. Jeśli wybrany klucz dostępu, nie istnieje `GetHotKeyName` zwraca pusty ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa, która zwraca funkcji członkowskiej pochodzi z sterownik klawiatury. Można zainstalować sterownik klawiatury nie zlokalizowane w zlokalizowanej wersji systemu Windows i na odwrót.  
  
##  <a name="getkeyname"></a>CHotKeyCtrl::GetKeyName  
 Wywołanie tej funkcji Członkowskich zlokalizowanej nazwy klucza przypisane do określonej wirtualnej kod klucza.  
  
```  
static CString GetKeyName(
    UINT vk,  
    BOOL fExtended);
```  
  
### <a name="parameters"></a>Parametry  
 `vk`  
 Wirtualne kod klucza.  
  
 *fExtended*  
 W przypadku wirtualnego kod klucza rozszerzonego klucza **TRUE**; w przeciwnym razie **FALSE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zlokalizowana nazwa określony przez klucz `vk` parametru. Jeśli klucz nie ma mapowanych nazwy, `GetKeyName` zwraca pusty ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa klucza, który ta funkcja zwraca wartość pochodzi z sterownik klawiatury, aby móc zainstalować sterownik klawiatury nie zlokalizowane w zlokalizowanej wersji systemu Windows i na odwrót.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]  
  
##  <a name="sethotkey"></a>CHotKeyCtrl::SetHotKey  
 Ustawia skrót klawiaturowy dla formantu klawisza dostępu.  
  
```  
void SetHotKey(
    WORD wVirtualKeyCode,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`wVirtualKeyCode`  
 Kod klucza wirtualnego skrót klawiaturowy. Listę standardowych wirtualnego kodów klucza Zobacz Winuser.h.  
  
 [in]`wModifiers`  
 Bitowe połączenie (lub) flag, które wskazują klawisze modyfikujące w skrót klawiaturowy.  
  
 Modyfikator flagi są następujące:  
  
|Flaga|Odpowiedni klucz|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|ALT — Klawisz|  
|`HOTKEYF_CONTROL`|Klawisz CTRL|  
|`HOTKEYF_EXT`|Rozszerzone klucza|  
|`HOTKEYF_SHIFT`|Klawisz SHIFT|  
  
### <a name="remarks"></a>Uwagi  
 Kod klucza wirtualnego i jednocześnie klawisze modyfikujące definiują skrót klawiaturowy.  
  
##  <a name="setrules"></a>CHotKeyCtrl::SetRules  
 Wywołanie tej funkcji, aby zdefiniować kombinacje nieprawidłowy i kombinacja modyfikatora domyślnego dla formantu klawisza dostępu.  
  
```  
void SetRules(
    WORD wInvalidComb,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>Parametry  
 `wInvalidComb`  
 Tablica flag, który określa nieprawidłowy kombinacje klawiszy. Może być kombinacją następujących wartości:  
  
- `HKCOMB_A`ALT  
  
- `HKCOMB_C`CTRL  
  
- `HKCOMB_CA`CTRL + ALT  
  
- `HKCOMB_NONE`Klucze zostały zmodyfikowane  
  
- `HKCOMB_S`SHIFT  
  
- `HKCOMB_SA`SHIFT + ALT  
  
- `HKCOMB_SC`SHIFT + CTRL  
  
- `HKCOMB_SCA`SHIFT + CTRL + ALT  
  
 `wModifiers`  
 Tablica flag, która określa kombinację klawiszy do użycia, kiedy użytkownik wprowadzi nieprawidłowe połączenie. Aby uzyskać więcej informacji o flagach modyfikator, zobacz [GetHotKey](#gethotkey).  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik wprowadza nieprawidłową kombinację klucza, zgodnie z definicją flag określonych we `wInvalidComb`, system używa operatora OR połączyć klucze wprowadzony przez użytkownika z flag określonych we `wModifiers`. Wynikowa kombinacji klawiszy jest konwertowana na ciąg znaków, a następnie wyświetlane w formantu klawisza dostępu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)



