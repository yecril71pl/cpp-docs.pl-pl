---
title: Klasa CIPAddressCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67c775f314cc70da1b662ca9b9c5f0a2e68eb2bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cipaddressctrl-class"></a>Klasa CIPAddressCtrl
Udostępnia funkcje formant adresu IP systemu Windows.  
  
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
|[CIPAddressCtrl::Create](#create)|Tworzy kontrolkę adresów IP i dołącza go do `CIPAddressCtrl` obiektu.|  
|[CIPAddressCtrl::CreateEx](#createex)|Tworzy kontrolkę adresu IP w określonym stylu rozszerzonej systemu Windows i dołącza go do `CIPAddressCtrl` obiektu.|  
|[CIPAddressCtrl::GetAddress](#getaddress)|Pobiera wartości adresów dla wszystkich pól cztery w formant adresu IP.|  
|[CIPAddressCtrl::IsBlank](#isblank)|Określa, czy wszystkie pola w formancie adresów IP są puste.|  
|[CIPAddressCtrl::SetAddress](#setaddress)|Ustawia wartości adresów dla wszystkich pól cztery w formant adresu IP.|  
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Ustawia fokus klawiatury określonego pola w formant adresu IP.|  
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Ustawia zakres w określonym polu w formancie adresu IP.|  
  
## <a name="remarks"></a>Uwagi  
 Formant adresu IP, podobny do formantu edycyjnego formantu umożliwia wprowadzanie i manipulowania numeryczny adres w formacie protokołu internetowego (IP).  
  
 Ten formant (i w związku z tym `CIPAddressCtrl` klasy) jest dostępna tylko dla programów, w obszarze Microsoft Internet Explorer w wersji 4.0 lub nowszy. Będą one również dostępne w przyszłych wersjach systemu Windows i Windows NT.  
  
 Aby uzyskać więcej ogólnych informacji na temat kontroli adresu IP, zobacz [formanty adresów IP](http://msdn.microsoft.com/library/windows/desktop/bb761372) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl  
 Tworzy `CIPAddressCtrl` obiektu.  
  
```  
CIPAddressCtrl();
```  
  
##  <a name="clearaddress"></a>CIPAddressCtrl::ClearAddress  
 Czyści zawartość formant adresu IP.  
  
```  
void ClearAddress();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_CLEARADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761377), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="create"></a>CIPAddressCtrl::Create  
 Tworzy kontrolkę adresów IP i dołącza go do `CIPAddressCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Styl formantu adresu IP. Zastosowanie Style okna. Należy uwzględnić **ws_child —** stylów formantu musi być oknem podrzędnym. Zobacz [właściwości CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) w zestawie SDK systemu Windows lista style systemu windows.  
  
 `rect`  
 Odwołanie do rozmiar i położenie formant adresu IP. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.  
  
 `pParentWnd`  
 Wskaźnik do okna nadrzędnego formant adresu IP. Nie może być **wartości NULL.**  
  
 `nID`  
 Identyfikator formantu adresu IP.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CIPAddressCtrl` obiektu w dwóch krokach.  
  
1.  Wywołanie konstruktora, który tworzy `CIPAddressCtrl` obiektu.  
  
2.  Wywołanie **Utwórz**, co powoduje formant adresu IP.  
  
 Jeśli chcesz style rozszerzonej systemu windows za pomocą formantu wywołanie [CreateEx](#createex) zamiast **Utwórz**.  
  
##  <a name="createex"></a>CIPAddressCtrl::CreateEx  
 Wywołanie tej funkcji można utworzyć formantu (okno podrzędne) i skojarz ją z `CIPAddressCtrl` obiektu.  
  
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
 Styl formantu adresu IP. Zastosowanie Style okna. Należy uwzględnić **ws_child —** stylów formantu musi być oknem podrzędnym. Zobacz [właściwości CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) w zestawie SDK systemu Windows lista style systemu windows.  
  
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
  
##  <a name="getaddress"></a>CIPAddressCtrl::GetAddress  
 Pobiera wartości adresów dla wszystkich pól cztery w formant adresu IP.  
  
```  
int GetAddress(
    BYTE& nField0,  
    BYTE& nField1,  
    BYTE& nField2,  
    BYTE& nField3);  
  
int GetAddress(DWORD& dwAddress);
```  
  
### <a name="parameters"></a>Parametry  
 `nField0`  
 Odwołanie do wartości pola 0 z spakowana adresu IP.  
  
 `nField1`  
 Odwołanie do wartości pola 1 z spakowana adresu IP.  
  
 `nField2`  
 Odwołanie do wartości pola 2 z spakowana adresu IP.  
  
 `nField3`  
 Odwołanie do wartości pola 3 z spakowana adresu IP.  
  
 `dwAddress`  
 Odwołanie do adresu `DWORD` wartość, która otrzymuje adres IP. Zobacz **uwagi** dla tabeli, która przedstawia sposób `dwAddress` jest wypełnione.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba pól niepustych formant adresu IP.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378), zgodnie z opisem w zestawie Windows SDK. W pierwszym prototypu powyżej liczby w polach od 0 do 3 formantu, przeczytaj od lewej do prawej odpowiednio, wypełnić cztery parametry. W drugim prototyp powyżej `dwAddress` jest wypełniana w następujący sposób.  
  
|Pole|Usługa BITS zawierający wartość pola|  
|-----------|-------------------------------------|  
|0|24 do 31|  
|1|16 do 23|  
|2|8 do 15|  
|3|od 0 do 7|  
  
##  <a name="isblank"></a>CIPAddressCtrl::IsBlank  
 Określa, czy wszystkie pola w formancie adresów IP są puste.  
  
```  
BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wszystkie pola formant adresu IP są puste; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_ISBLANK](http://msdn.microsoft.com/library/windows/desktop/bb761379), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setaddress"></a>CIPAddressCtrl::SetAddress  
 Ustawia wartości adresów dla wszystkich pól cztery w formant adresu IP.  
  
```  
void SetAddress(
    BYTE nField0,  
    BYTE nField1,  
    BYTE nField2,  
    BYTE nField3);  
  
void SetAddress(DWORD dwAddress);
```  
  
### <a name="parameters"></a>Parametry  
 `nField0`  
 Wartość pola 0 z spakowana adresu IP.  
  
 `nField1`  
 Wartość pola 1 z spakowana adresu IP.  
  
 `nField2`  
 Wartość pola 2 z spakowana adresu IP.  
  
 `nField3`  
 Wartość pola 3 z spakowana adresu IP.  
  
 `dwAddress`  
 A `DWORD` wartości, która zawiera nowego adresu IP. Zobacz **uwagi** dla tabeli, która przedstawia sposób `DWORD` wprowadzono wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380), zgodnie z opisem w zestawie Windows SDK. W pierwszym prototypu powyżej liczby w polach od 0 do 3 formantu, przeczytaj od lewej do prawej odpowiednio, wypełnić cztery parametry. W drugim prototyp powyżej `dwAddress` jest wypełniana w następujący sposób.  
  
|Pole|Usługa BITS zawierający wartość pola|  
|-----------|-------------------------------------|  
|0|24 do 31|  
|1|16 do 23|  
|2|8 do 15|  
|3|od 0 do 7|  
  
##  <a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus  
 Ustawia fokus klawiatury określonego pola w formant adresu IP.  
  
```  
void SetFieldFocus(WORD nField);
```  
  
### <a name="parameters"></a>Parametry  
 `nField`  
 Indeks pola liczony od zera, do którego można ustawić fokusu. Jeśli ta wartość jest większa niż liczba pól, fokus jest ustawiony na pierwsze pole puste. Jeśli wszystkie pola są niepustą, fokus jest ustawiony pierwsze pole.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_SETFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb761381), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange  
 Ustawia zakres w określonym polu w formancie adresu IP.  
  
```  
void SetFieldRange(
    int nField,  
    BYTE nLower,  
    BYTE nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 `nField`  
 Indeks pola liczony od zera, do którego zostanie zastosowana zakresu.  
  
 `nLower`  
 Odwołanie do liczby całkowitej odbieranie dolny limit określonego pola w tym formancie adresu IP.  
  
 `nUpper`  
 Odwołanie do liczby całkowitej odbieranie górnego limitu określonego pola w tym formancie adresu IP.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [IPM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761382), zgodnie z opisem w zestawie Windows SDK. Użyj tych dwóch parametrów `nLower` i `nUpper`, aby wskazać dolna i górna granicami pola, zamiast *wRange* parametrem komunikat Win32.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



