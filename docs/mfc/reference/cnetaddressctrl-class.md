---
title: Klasa CNetAddressCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a433d723e15d910674c129b1e62ca82c1de4bb0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cnetaddressctrl-class"></a>Klasa CNetAddressCtrl
`CNetAddressCtrl` Klasa reprezentuje kontroli adres sieci, które służy do danych wejściowych i sprawdzania poprawności w formacie IPv4, IPv6 i adresów o nazwie DNS.  
  
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
|[CNetAddressCtrl::Create](#create)|Tworzy kontrolkę adres sieci przy użyciu określonego stylów i dołącza go do bieżącej `CNetAddressCtrl` obiektu.|  
|[CNetAddressCtrl::CreateEx](#createex)|Tworzy kontrolkę adres sieci z określonym rozszerzone style i dołącza go do bieżącej `CNetAddressCtrl` obiektu.|  
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Wyświetla etykieta dymka błąd, gdy użytkownik wprowadzi adresu sieciowego nieobsługiwany w bieżącym formantem adresu sieciowego.|  
|[CNetAddressCtrl::GetAddress](#getaddress)|Pobiera zweryfikowane i przeanalizowana reprezentacja adresu sieciowego, skojarzone z bieżącym formantem adresu sieciowego.|  
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Pobiera typ adresu sieciowego, obsługujące bieżącym formantem adresu sieciowego.|  
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Ustawia typ adresu sieciowego, obsługujące bieżącym formantem adresu sieciowego.|  
  
## <a name="remarks"></a>Uwagi  
 Formant adresu sieciowego sprawdza, czy format adresu, który użytkownik wprowadza jest poprawna. Formant nie faktycznie nawiązać adresu sieciowego. [CNetAddressCtrl::SetAllowType](#setallowtype) metody określa co najmniej jeden typ adresu który [CNetAddressCtrl::GetAddress](#getaddress) metody można przeanalizować i sprawdź. Adres może być w formie IPv4, IPv6 lub nazwanym adres serwera, sieci, hosta lub docelowej komunikat emisji. Jeśli format adresie jest niepoprawny, możesz użyć [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodę w celu wyświetlenia pola wiadomości Porada graficznie wskazuje pole tekstowe z formantem adresu sieciowego i wyświetla wstępnie zdefiniowanej komunikat o błędzie.  
  
 `CNetAddressCtrl` Jest pochodną klasy [CEdit](../../mfc/reference/cedit-class.md) klasy. W rezultacie kontroli adres sieci zapewnia dostęp do wszystkich komunikatów formant edycji systemu Windows.  
  
 Na poniższym rysunku przedstawiono okno dialogowe, które zawiera formant adresu sieciowego. Tekst pola (1) dla formantu adres sieci zawiera nieprawidłowy adres sieciowy. Zostanie wyświetlony komunikat Porada (2), jeśli adres sieciowy jest nieprawidłowy.  
  
 ![Okno dialogowe z formantem adresu sieciowego i poradą. ] (../../mfc/reference/media/cnetaddctrl.png "cnetaddctrl")  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod jest częścią okna dialogowego, które sprawdza poprawność adresu sieciowego. Programy obsługi zdarzeń dla trzech przycisków radiowych określić adresu sieciowego może być jednym z trzech typów adresu. Użytkownik wprowadza adres w polu tekstowym kontroli sieci, a następnie naciśnie przycisk, aby zweryfikować adres. Jeśli adres jest nieprawidłowy, zostanie wyświetlony komunikat z potwierdzeniem; w przeciwnym razie zostanie wyświetlony komunikat błędu Porada wstępnie zdefiniowane.  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu z pliku nagłówka okna dialogowego definiuje [NC_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345) i [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) zmiennych, które są wymagane przez [CNetAddressCtrl::GetAddress](#getaddress)metody.  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CNetAddressCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
 Ta klasa jest obsługiwana w [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] i nowszych.  
  
 Dodatkowe wymagania dotyczące tej klasy są opisane w [kompilacji wymagania dla formantów systemu Windows Vista wspólnej](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
##  <a name="cnetaddressctrl"></a>CNetAddressCtrl::CNetAddressCtrl  
 Konstruuje `CNetAddressCtrl` obiektu.  
  
```  
CNetAddressCtrl();
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CNetAddressCtrl::Create](#create) lub [CNetAddressCtrl::CreateEx](#createex) metody tworzenia kontroli sieci i dołączenie go do `CNetAddressCtrl` obiektu.  
  
##  <a name="create"></a>CNetAddressCtrl::Create  
 Tworzy kontrolkę adres sieci przy użyciu określonego stylów i dołącza go do bieżącej `CNetAddressCtrl` obiektu.  
  
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
|[in]`dwStyle`|Bitowe połączenie style, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [edytować style](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|  
|[in]`rect`|Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która zawiera położenie i rozmiar formantu.|  
|[in]`pParentWnd`|Wskaźnik inną niż null do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki.|  
|[in]`nID`|Identyfikator formantu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
##  <a name="createex"></a>CNetAddressCtrl::CreateEx  
 Tworzy kontrolkę adres sieci z określonym rozszerzone style i dołącza go do bieżącej `CNetAddressCtrl` obiektu.  
  
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
|[in]`dwExStyle`|Bitowe połączenie (lub) rozszerzone style, które mają być zastosowane do formantu. Aby uzyskać więcej informacji, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkcji.|  
|[in]`dwStyle`|Bitowe połączenie (lub) style, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [edytować style](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|  
|[in]`rect`|Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która zawiera położenie i rozmiar formantu.|  
|[in]`pParentWnd`|Wskaźnik inną niż null do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki.|  
|[in]`nID`|Identyfikator formantu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
##  <a name="displayerrortip"></a>CNetAddressCtrl::DisplayErrorTip  
 Wyświetla komunikat o błędzie w dymku, która jest skojarzona z bieżącym formantem adresu sieciowego.  
  
```  
HRESULT DisplayErrorTip();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość `S_OK` Jeśli ta metoda jest pomyślnie; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metodę, aby określić typy adresów, obsługiwane w bieżącym formantem adresu sieciowego. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody weryfikacji i przeanalizować adresu sieciowego, wprowadzonych przez użytkownika. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodę w celu wyświetlenia poradę komunikat błędu, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda zakończy się niepowodzeniem.  
  
 Ten komunikat, wywołuje [NetAddr_DisplayErrorTip](http://msdn.microsoft.com/library/windows/desktop/bb774314) makra, który jest opisany w zestawie SDK systemu Windows. Tym makro wysyła `NCM_DISPLAYERRORTIP` wiadomości.  
  
##  <a name="getaddress"></a>CNetAddressCtrl::GetAddress  
 Pobiera zweryfikowane i przeanalizowana reprezentacja adresu sieciowego, który jest skojarzony z bieżącym formantem adresu sieciowego.  
  
```  
HRESULT GetAddress(PNC_ADDRESS pAddress) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[w, out]`pAddress`|Wskaźnik do [NC_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345) struktury.  Ustaw `pAddrInfo` członkiem tej struktury z adresem [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) struktury przed wywołaniem metody GetAddress.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość `S_OK` Jeśli ta metoda jest pomyślnie; w przeciwnym razie kod błędu COM. Aby uzyskać więcej informacji o kodach błędów możliwe, zobacz sekcję zwrócić wartość [NetAddr_GetAddress](http://msdn.microsoft.com/library/windows/desktop/bb774316) makra.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda zakończy się pomyślnie, [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) struktura zawiera dodatkowe informacje dotyczące adresu sieciowego.  
  
 Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metodę, aby określić typy adresów może obsługiwać bieżącym formantem adresu sieciowego. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody weryfikacji i przeanalizować adresu sieciowego, wprowadzonych przez użytkownika. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodę w celu wyświetlenia poradę komunikat błędu, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda zakończy się niepowodzeniem.  
  
 Ta metoda wywołuje [NetAddr_GetAddress](http://msdn.microsoft.com/library/windows/desktop/bb774316) makra, który jest opisany w zestawie SDK systemu Windows. Tym makro wysyła `NCM_GETADDRESS` wiadomości.  
  
##  <a name="getallowtype"></a>CNetAddressCtrl::GetAllowType  
 Pobiera typ adresu sieciowego, obsługujące bieżącym formantem adresu sieciowego.  
  
```  
DWORD GetAllowType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bitowe połączenie (lub) flagi określająca typy adresów kontroli adres sieci może obsługiwać. Aby uzyskać więcej informacji, zobacz [NET_STRING](http://msdn.microsoft.com/library/windows/desktop/bb762586).  
  
### <a name="remarks"></a>Uwagi  
 Ten komunikat, wywołuje [NetAddr_GetAllowType](http://msdn.microsoft.com/library/windows/desktop/bb774318) makra, który jest opisany w zestawie SDK systemu Windows. Tym makro wysyła `NCM_GETALLOWTYPE` wiadomości.  
  
##  <a name="setallowtype"></a>CNetAddressCtrl::SetAllowType  
 Ustawia typ adresu sieciowego, obsługujące bieżącym formantem adresu sieciowego.  
  
```  
HRESULT SetAllowType(DWORD dwAddrMask);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`dwAddrMask`|Bitowe połączenie (lub) flagi określająca typy adresów kontroli adres sieci może obsługiwać. Aby uzyskać więcej informacji, zobacz [NET_STRING](http://msdn.microsoft.com/library/windows/desktop/bb762586).|  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie kod błędu COM.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CNetAddressCtrl::SetAllowType](#setallowtype) metodę, aby określić typy adresów, obsługiwane w bieżącym formantem adresu sieciowego. Użyj [CNetAddressCtrl::GetAddress](#getaddress) metody weryfikacji i przeanalizować adresu sieciowego, wprowadzonych przez użytkownika. Użyj [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) metodę w celu wyświetlenia poradę komunikat błędu, jeśli [CNetAddressCtrl::GetAddress](#getaddress) metoda zakończy się niepowodzeniem.  
  
 Ten komunikat, wywołuje [NetAddr_SetAllowType](http://msdn.microsoft.com/library/windows/desktop/bb774320) makra, który jest opisany w zestawie SDK systemu Windows. Tym makro wysyła `NCM_SETALLOWTYPE` wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CNetAddressCtrl](../../mfc/reference/cnetaddressctrl-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)
