---
title: Klasa CWndClassInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
dev_langs: C++
helpviewer_keywords: CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b07f6b12914e18f3f83abedf59742a8b7c7867b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cwndclassinfo-class"></a>Klasa CWndClassInfo
Ta klasa dostarcza metody do rejestrowania informacji o klasy okna.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CWndClassInfo
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|[Rejestr](#register)|Rejestruje klasę okna.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_atom](#m_atom)|Identyfikuje klasę okna w zarejestrowany.|  
|[m_bSystemCursor](#m_bsystemcursor)|Określa, czy zasobu kursora odnosi się do kursora systemu lub zawarte w module zasobu kursora.|  
|[m_lpszCursorID](#m_lpszcursorid)|Określa nazwę zasobu kursora.|  
|[m_lpszOrigName](#m_lpszorigname)|Zawiera nazwę istniejącej klasy okna.|  
|[m_szAutoName](#m_szautoname)|Zostały wygenerowane ATL Nazwa klasy okna.|  
|[m_wc](#m_wc)|Przechowuje informacje o klasie okna w **WNDCLASSEX** struktury.|  
|[pWndProc](#pwndproc)|Wskazuje procedurę okna istniejącej klasy okna.|  
  
## <a name="remarks"></a>Uwagi  
 `CWndClassInfo`zarządza informacjami klasy okna. Zazwyczaj używają `CWndClassInfo` za pomocą jednego z trzech makra `DECLARE_WND_CLASS`, `DECLARE_WND_CLASS_EX`, lub `DECLARE_WND_SUPERCLASS`, zgodnie z opisem w poniższej tabeli:  
  
|Makra|Opis|  
|-----------|-----------------|  
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`rejestruje informacje dla nowej klasy okna.|  
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`rejestruje informacje dla nowej klasy okna tym parametrów klasy.|  
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`rejestruje informacje dla klasy okna jest oparta na istniejącej klasy, która korzysta z innego okna procedury. Ta metoda jest wywoływana tworzenie nadklas.|  
  
 Domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md) obejmuje `DECLARE_WND_CLASS` makro można utworzyć okna oparte na nową klasę okna. DECLARE_WND_CLASS zawiera domyślne style i kolor tła formantu. Jeśli chcesz określić styl i kolor tła samodzielnie, pochodzi z klasy `CWindowImpl` i obejmują `DECLARE_WND_CLASS_EX` makra w definicji klasy.  
  
 Jeśli chcesz utworzyć okna, w oparciu o istniejące klasy okna, pochodzi z klasy `CWindowImpl` i obejmują `DECLARE_WND_SUPERCLASS` makra w definicji klasy. Na przykład:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]  
  
 Aby uzyskać więcej informacji na temat klasy okien, zobacz [klasy okien](http://msdn.microsoft.com/library/windows/desktop/ms632596) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji o korzystaniu z systemu windows w ATL, zobacz artykuł [klas okien ALT](../../atl/atl-window-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="m_atom"></a>CWndClassInfo::m_atom  
 Zawiera unikatowy identyfikator klasy okna zarejestrowany.  
  
```
ATOM m_atom;
```  
  
##  <a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor  
 Jeśli **TRUE**, zasobu kursora systemu zostanie załadowany po zarejestrowaniu klasy okna.  
  
```
BOOL m_bSystemCursor;
```  
  
### <a name="remarks"></a>Uwagi  
 W przeciwnym razie zostanie załadowany zasobu kursora zawarte w module.  
  
 `CWndClassInfo`używa `m_bSystemCursor` tylko wtedy, gdy [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro jest określona. W takim przypadku `m_bSystemCursor` jest ustawiana na **TRUE**. Aby uzyskać więcej informacji, zobacz [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) omówienie.  
  
##  <a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID  
 Określa nazwy zasobu kursora lub identyfikator zasobu w programie word znaczącymi bitami i zero w programie word znaczących.  
  
```
LPCTSTR m_lpszCursorID;
```  
  
### <a name="remarks"></a>Uwagi  
 Po zarejestrowaniu klasy okna, dojście do kursora identyfikowane przez `m_lpszCursorID` jest pobierany i przechowywane przez [m_wc](#m_wc).  
  
 `CWndClassInfo`używa `m_lpszCursorID` tylko wtedy, gdy [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro jest określona. W takim przypadku `m_lpszCursorID` jest ustawiana na **IDC_ARROW**. Aby uzyskać więcej informacji, zobacz [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) omówienie.  
  
##  <a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName  
 Zawiera nazwę istniejącej klasy okna.  
  
```
LPCTSTR m_lpszOrigName;
```  
  
### <a name="remarks"></a>Uwagi  
 `CWndClassInfo`używa `m_lpszOrigName` tylko Jeśli dołączysz [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra w definicji klasy. W takim przypadku `CWndClassInfo` rejestruje klasę okna w oparciu o nazwie klasy `m_lpszOrigName`. Aby uzyskać więcej informacji, zobacz [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) omówienie.  
  
##  <a name="m_szautoname"></a>CWndClassInfo::m_szAutoName  
 Przechowuje nazwę klasy okna.  
  
```
TCHAR m_szAutoName[13];
```  
  
### <a name="remarks"></a>Uwagi  
 `CWndClassInfo`używa `m_szAutoName` tylko wtedy, gdy **NULL** została przekazana `WndClassName` parametr [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) lub [ DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL utworzy nazwę po zarejestrowaniu klasy okna.  
  
##  <a name="m_wc"></a>CWndClassInfo::m_wc  
 Przechowuje informacje o klasie okna w [WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577) struktury.  
  
```
WNDCLASSEX m_wc;
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makra `m_wc` zawiera informacje o nowe klasy okna.  
  
 Jeśli określono [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra `m_wc` zawiera informacje o superklasie — jest oparta na istniejącej klasy, która korzysta z innego okna procedury klasy okna. [m_lpszOrigName](#m_lpszorigname) i [pWndProc](#pwndproc) odpowiednio Zapisz nazwę istniejącej klasy okna i procedurę okna.  
  
##  <a name="pwndproc"></a>CWndClassInfo::pWndProc  
 Wskazuje procedurę okna istniejącej klasy okna.  
  
```
WNDPROC pWndProc;
```  
  
### <a name="remarks"></a>Uwagi  
 `CWndClassInfo`używa `pWndProc` tylko Jeśli dołączysz [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra w definicji klasy. W takim przypadku `CWndClassInfo` rejestruje klasę okna, jest oparta na istniejącej klasy, która korzysta z innego okna procedury. Procedurę okna istniejącej klasy okna jest zapisywany w `pWndProc`. Aby uzyskać więcej informacji, zobacz [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) omówienie.  
  
##  <a name="register"></a>CWndClassInfo::Register  
 Wywoływane przez [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create) można zarejestrować klasy okna, jeśli nie została jeszcze zarejestrowana.  
  
```
ATOM Register(WNDPROC* pProc);
```  
  
### <a name="parameters"></a>Parametry  
 `pProc`  
 [out] Określa oryginalną procedurę okna istniejącej klasy okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia atom który unikatowo identyfikuje klasy okna jest zarejestrowany. W przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makra `Register` rejestruje nową klasę okna. W takim przypadku `pProc` parametr nie jest używany.  
  
 Jeśli określono [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra `Register` rejestruje superklasą — jest oparta na istniejącej klasy, która korzysta z innego okna procedury klasy okna. Procedurę okna istniejącej klasy okna jest zwracany w `pProc`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)