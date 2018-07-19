---
title: Klasa CHotKeyCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8151b69b92566f45766c4ffa25d40bb5f077c606
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337261"
---
# <a name="chotkeyctrl-class"></a>Klasa CHotKeyCtrl
Oferuje funkcje Windows formantu typowego klawisza dostępu.  
  
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
|[CHotKeyCtrl::Create](#create)|Tworzy formantu klawisza dostępu i dołącza je do `CHotKeyCtrl` obiektu.|  
|[CHotKeyCtrl::CreateEx](#createex)|Tworzy formantu klawisza dostępu przy użyciu określonego stylów rozszerzonej Windows i dołącza je do `CHotKeyCtrl` obiektu.|  
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Pobiera wirtualnego kodu i modyfikator flagi kluczy z klawisza dostępu z formantu klawisza dostępu.|  
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Pobiera nazwę klucza, w zestawie znaków lokalnych przypisane do klawisza dostępu.|  
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Pobiera nazwę klucza, w zestawie znaków lokalnych przypisane do określonej wirtualnej kod klawisza.|  
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Ustawia gorąca kombinację klawiszy dla formantu klawisza dostępu.|  
|[CHotKeyCtrl::SetRules](#setrules)|Definiuje nieprawidłowe kombinacje i kombinacji modyfikator domyślny dla formantu klawisza dostępu.|  
  
## <a name="remarks"></a>Uwagi  
 "Formantu klawisza dostępu" jest oknem, który umożliwia użytkownikowi utworzenie klawisza dostępu. "Klawisz skrótu" jest kombinacji klawiszy, który użytkownik może nacisnąć szybko wykonać akcję. (Na przykład użytkownik może utworzyć aktywuje danego okno i udostępnia go do góry porządek klawisza dostępu). Formantu klawisza dostępu Wyświetla opcje użytkownika i gwarantuje, że użytkownik wybierze prawidłową kombinację klawiszy.  
  
 Ta kontrolka (i w związku z tym `CHotKeyCtrl` klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Po użytkownik wybierze kombinację klawiszy, aplikacja może pobrać określonej kombinacji klawiszy z formantu i komunikat WM_SETHOTKEY umożliwia ustawianie klawisza dostępu w systemie. Zawsze, gdy użytkownik naciśnie klawisz skrótu, z dowolnej części systemu, okna określony w komunikacie WM_SETHOTKEY odbiera komunikat WM_SYSCOMMAND, określając SC_HOTKEY. Ten komunikat uaktywnia okna, które otrzymuje go. Klawisz skrótu pozostanie ważny aż do aplikacji, która umożliwia zamknięcie WM_SETHOTKEY wywołana.  
  
 Ten mechanizm różni się od gorąca obsługę kluczy, która jest zależna od komunikat WM_HOTKEY i Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309) i [UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327) funkcji.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CHotKeyCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [korzystanie z CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHotKeyCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="chotkeyctrl"></a>  CHotKeyCtrl::CHotKeyCtrl  
 Konstruuje `CHotKeyCtrl` obiektu.  
  
```  
CHotKeyCtrl();
```  
  
##  <a name="create"></a>  CHotKeyCtrl::Create  
 Tworzy formantu klawisza dostępu i dołącza je do `CHotKeyCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa styl formantu klawisza dostępu firmy. Zastosuj dowolną kombinację style kontrolki. Zobacz [najczęściej używane style kontrolki](http://msdn.microsoft.com/library/windows/desktop/bb775498) w zestawie Windows SDK, aby uzyskać więcej informacji.  
  
 *Rect*  
 Określa rozmiar i położenie formantu klawisza dostępu firmy. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [struktura RECT](../../mfc/reference/rect-structure1.md).  
  
 *pParentWnd*  
 Określa formantu klawisza dostępu przez okno nadrzędne, zwykle [CDialog](../../mfc/reference/cdialog-class.md). Nie może być równa NULL.  
  
 *nID*  
 Określa identyfikator formantu klawisza dostępu firmy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli inicjowanie się powiodła. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CHotKeyCtrl` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołać `Create`, który tworzy formantu klawisza dostępu i dołącza go do `CHotKeyCtrl` obiektu.  
  
 Style rozszerzone systemu windows za pomocą formantu należy wywołać [CreateEx](#createex) zamiast `Create`.  
  
##  <a name="createex"></a>  CHotKeyCtrl::CreateEx  
 Wywołaj tę funkcję, aby utworzyć kontrolkę (okno podrzędne) i powiąż ją z `CHotKeyCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 *dwStyle*  
 Określa styl formantu klawisza dostępu firmy. Zastosuj dowolną kombinację style kontrolki. Aby uzyskać więcej informacji, zobacz [najczęściej używane style kontrolki](http://msdn.microsoft.com/library/windows/desktop/bb775498) w zestawie Windows SDK.  
  
 *Rect*  
 Odwołanie do [Prostokąt](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.  
  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *nID*  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="gethotkey"></a>  CHotKeyCtrl::GetHotKey  
 Pobiera wirtualnego kodu i modyfikator flagi kluczy skrótu klawiatury z formantu klawisza dostępu.  
  
```  
DWORD GetHotKey() const;  
  
void GetHotKey(
    WORD& wVirtualKeyCode,  
    WORD& wModifiers) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] *wVirtualKeyCode*  
 Wirtualne kod klawisza skrótu klawiaturowego. Aby uzyskać listę standardowa wirtualnej kody klawiszy Zobacz Winuser.h.  
  
 [out] *wModifiers*  
 Bitowa kombinacja (lub) flagi wskazujące klawisze modyfikujące w skrótów klawiaturowych.  
  
 Dostępne są następujące flagi modyfikatora:  
  
|Flaga|Odpowiedni klucz|  
|----------|-----------------------|  
|HOTKEYF_ALT|ALT — Klawisz|  
|HOTKEYF_CONTROL|Klawisz CTRL|  
|HOTKEYF_EXT|Rozszerzone klucza|  
|HOTKEYF_SHIFT|Klawisz SHIFT|  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym przeciążonej metody, DWORD, zawierającej wirtualny klucza kodu i modyfikator flagi. Mniej znaczący bajt, wyraz niskiego rzędu zawiera wirtualny kod klawisza, bajt wyższego rzędu word niskiego rzędu zawiera flagi modyfikatora i word wyższego rzędu jest równa zero.  
  
### <a name="remarks"></a>Uwagi  
 Kod klawisza wirtualnego i klawisze modyfikujące, które razem definiują skrót klawiaturowy.  
  
##  <a name="gethotkeyname"></a>  CHotKeyCtrl::GetHotKeyName  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać zlokalizowana nazwa klawisza dostępu.  
  
```  
CString GetHotKeyName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zlokalizowana nazwa aktualnie wybranego klucza dostępu. Jeśli wybrany klucz dostępu, nie istnieje `GetHotKeyName` zwraca pusty ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa która to funkcja elementu członkowskiego zwraca pochodzi z sterownik klawiatury. Można zainstalować sterownik niezlokalizowana klawiatury w zlokalizowanej wersji systemu Windows i na odwrót.  
  
##  <a name="getkeyname"></a>  CHotKeyCtrl::GetKeyName  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać zlokalizowana nazwa klucza przypisane do określonej wirtualnej kod klawisza.  
  
```  
static CString GetKeyName(
    UINT vk,  
    BOOL fExtended);
```  
  
### <a name="parameters"></a>Parametry  
 *vk*  
 Kod klawisza wirtualnego.  
  
 *fExtended*  
 Jeśli kod klawisza wirtualnego jest rozszerzonej klucz, wartość PRAWDA; w przeciwnym razie wartość FALSE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zlokalizowana nazwa klucza określonym przez *vk* parametru. Jeśli klucz nie ma zamapowany nazwy, `GetKeyName` zwraca pusty ciąg.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa klucza, którego funkcja zwraca wartość pochodzi z sterownik klawiatury, dzięki czemu można zainstalować sterownik niezlokalizowana klawiatury w zlokalizowanej wersji systemu Windows i na odwrót.  
  
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
 [in] *wVirtualKeyCode*  
 Wirtualne kod klawisza skrótu klawiaturowego. Aby uzyskać listę standardowa wirtualnej kody klawiszy Zobacz Winuser.h.  
  
 [in] *wModifiers*  
 Bitowa kombinacja (lub) flagi wskazujące klawisze modyfikujące w skrótów klawiaturowych.  
  
 Dostępne są następujące flagi modyfikatora:  
  
|Flaga|Odpowiedni klucz|  
|----------|-----------------------|  
|HOTKEYF_ALT|ALT — Klawisz|  
|HOTKEYF_CONTROL|Klawisz CTRL|  
|HOTKEYF_EXT|Rozszerzone klucza|  
|HOTKEYF_SHIFT|Klawisz SHIFT|  
  
### <a name="remarks"></a>Uwagi  
 Kod klawisza wirtualnego i klawisze modyfikujące, które razem definiują skrót klawiaturowy.  
  
##  <a name="setrules"></a>  CHotKeyCtrl::SetRules  
 Wywołaj tę funkcję, aby zdefiniować nieprawidłowe kombinacje i kombinacji modyfikator domyślny dla formantu klawisza dostępu.  
  
```  
void SetRules(
    WORD wInvalidComb,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>Parametry  
 *wInvalidComb*  
 Tablica flagi, który określa nieprawidłowy kombinacje klawiszy. Może być kombinacją następujących wartości:  
  
- HKCOMB_A ALT  
  
- HKCOMB_C CTRL  
  
- HKCOMB_CA KLAWISZE CTRL + ALT  
  
- Niezmodyfikowane HKCOMB_NONE kluczy  
  
- HKCOMB_S SHIFT  
  
- HKCOMB_SA SHIFT + ALT  
  
- HKCOMB_SC SHIFT + CTRL  
  
- HKCOMB_SCA SHIFT + KLAWISZE CTRL + ALT  
  
 *wModifiers*  
 Tablica flagi, która określa kombinację klawiszy do użycia, gdy użytkownik wprowadzi nieprawidłowe połączenie. Aby uzyskać więcej informacji na temat flagi modyfikatora, zobacz [GetHotKey](#gethotkey).  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik wprowadza Nieprawidłowa kombinacja klawiszy, zgodnie z definicją flag określonych we *wInvalidComb*, wówczas system używa operatora OR połączyć klucze wprowadzonej przez użytkownika za pomocą flag określonych we *wModifiers*. Wynikowy kombinacja klawiszy jest konwertowana na ciąg, a następnie wyświetlane w formantu klawisza dostępu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



