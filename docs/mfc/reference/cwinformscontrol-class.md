---
title: Klasa CWinFormsControl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d126c7e6ef77142f20a9dd9d7ed68c44ede5fc1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cwinformscontrol-class"></a>Klasa CWinFormsControl
Zapewnia podstawowe funkcje do hostowania kontrolki formularzy systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class TManagedControl>  
class CWinFormsControl : public CWnd  
```  
  
#### <a name="parameters"></a>Parametry  
 `TManagedControl`  
 Formant formularzy systemu Windows programu .NET Framework ma być wyświetlany w aplikacji MFC.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Tworzy obiekt otoki formantu formularzy systemu Windows MFC.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Tworzy kontrolkę formularzy systemu Windows w kontenerze MFC.|  
|[CWinFormsControl::GetControl](#getcontrol)|Pobiera wskaźnik do formantu formularzy systemu Windows.|  
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Pobiera dojścia do formantu formularzy systemu Windows.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|Zastępuje [CWinFormsControl::GetControl](#getcontrol) w wyrażeniach.|  
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|Rzutuje typu jako wskaźnik do formantu formularzy systemu Windows.|  
  
## <a name="remarks"></a>Uwagi  
 `CWinFormsControl` Klasa udostępnia podstawowe funkcje do hostowania kontrolki formularzy systemu Windows.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Kod MFC nie pamięci podręcznej uchwytów okien (zwykle przechowywany w `m_hWnd`). Niektóre właściwości formantów formularzy systemu Windows wymagają, aby podstawowej Win32 `Window` zniszczone i ponownie utworzone przy użyciu `DestroyWindow` i `CreateWindow`. Uchwyty implementacji MFC Windows Forms `Destroy` i `Create` zdarzenia formantów, aby zaktualizować `m_hWnd` elementu członkowskiego.  
  
> [!NOTE]
>  Integracja MFC Windows Forms działa wyłącznie w projektach, które łącze dynamicznie z MFC (w którym jest zdefiniowany AFXDLL).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h  
  
##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl  
 Tworzy kontrolkę formularzy systemu Windows w kontenerze MFC.  
  
```  
inline BOOL CreateManagedControl(
    System::Type^ pType,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID)  
inline BOOL CreateManagedControl(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID);

 
inline BOOL CreateManagedControl(
    DWORD dwStyle,  
    int nPlaceHolderID,  
    CWnd* pParentWnd);

 
inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID);
```  
  
### <a name="parameters"></a>Parametry  
 `pType`  
 Typ danych formantu, który ma zostać utworzony. Musi być [typu](https://msdn.microsoft.com/en-us/library/system.type) — typ danych.  
  
 `dwStyle`  
 Styl okna, aby zastosować do formantu. Określ kombinację [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles). Obecnie są obsługiwane tylko następujące style: ws_tabstop —, ws_visible — i ws_disabled — ws_group —.  
  
 `rect`  
 A [struktura RECT](../../mfc/reference/rect-structure1.md) definiuje współrzędne górnego lewego i prawego dolnego rogu formantu (najpierw przeciążenia tylko).  
  
 `nPlaceHolderID`  
 Uchwyt formantu posiadacz statycznych miejscu umieścić w edytorze zasobów. Nowo utworzony formantu formularzy systemu Windows zastępuje kontrolki statycznej, zakładając, że jego położenie porządek osi i style (drugi przeciążenia tylko).  
  
 `pParentWnd`  
 Wskaźnik do okna nadrzędnego.  
  
 `nID`  
 Identyfikatora zasobu do przypisania do nowo utworzonego formantu.  
  
 `pControl`  
 Wystąpienie formantu formularzy systemu Windows ma zostać skojarzony z [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) obiektu (tylko w przypadku przeciążenia czwarty).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość różną od zera. W przypadku niepowodzenia zwraca zero.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy wystąpienie formantu formularzy systemu Windows programu .NET Framework w kontenerze MFC.  
  
 Typ danych .NET Framework akceptuje pierwszy przeciążenia metody `pType` tak, aby MFC można utworzyć wystąpienia nowy obiekt tego typu. `pType` musi być [typu](https://msdn.microsoft.com/en-us/library/system.type) — typ danych.  
  
 Drugi przeciążenia metody tworzy formantu formularzy systemu Windows na podstawie `TManagedControl` parametru szablonu `CWinFormsControl` klasy. Rozmiar i położenie formantu jest oparta na `RECT` struktury przekazywany do metody. Tylko `dwStyle` ma znaczenie dla stylów.  
  
 Trzeci przeciążenia metody tworzy kontrolki formularza systemu Windows, który zastępuje statyczną kontrolkę niszczenie go przy założeniu, że jego położenie porządek osi i style. Kontrolki statycznej służy tylko jako symbolu zastępczego dla formantu formularzy systemu Windows. Podczas tworzenia kontrolki, to przeciążenie łączy style z `dwStyle` przy użyciu stylów zasobów kontrolki statycznej.  
  
 Czwarty przeciążenia metody umożliwia przekazywanie w formancie formularzy systemu Windows już wystąpień `pControl` który MFC będzie zawijany. Musi być tego samego typu co `TManagedControl` parametru szablonu `CWinFormsControl` klasy.  
  
 Zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) dla przykładów w formularzu systemu Windows kontrolki.  
  
##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl  
 Tworzy obiekt otoki formantu formularzy systemu Windows MFC.  
  
```  
CWinFormsControl();
```  
  
### <a name="remarks"></a>Uwagi  
 Formant formularzy systemu Windows zostanie uruchomiony po wywołaniu [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).  
  
##  <a name="getcontrol"></a>  CWinFormsControl::GetControl  
 Pobiera wskaźnik do formantu formularzy systemu Windows.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do formantu formularzy systemu Windows.  
  
### <a name="example"></a>Przykład  
  Zobacz [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).  
  
##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle  
 Pobiera dojścia do formantu formularzy systemu Windows.  
  
```  
inline HWND GetControlHandle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do formantu formularzy systemu Windows.  
  
### <a name="remarks"></a>Uwagi  
 `GetControlHandle` to metoda pomocnika, która zwraca uchwyt okna przechowywane w .NET Framework właściwości formantu. Wartość uchwyt okna jest kopiowany do [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) podczas wywołania [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).  
  
##  <a name="operator_-_gt"></a>  CWinFormsControl::operator-&gt;  
 Zastępuje [CWinFormsControl::GetControl](#getcontrol) w wyrażeniach.  
  
```  
inline TManagedControl^  operator->() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator oferuje wygodny składnię, która zastępuje `GetControl` w wyrażeniach.  
  
 Aby uzyskać więcej informacji na formularzach systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_tmanagedcontrol"></a>  CWinFormsControl::operator TManagedControl ^  
 Rzutuje typu jako wskaźnik do formantu formularzy systemu Windows.  
  
```  
inline operator TManagedControl^() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator przekazuje `CWinFormsControl<TManagedControl>` do funkcji, które akceptują wskaźnik do formantu formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)   
 [Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)
