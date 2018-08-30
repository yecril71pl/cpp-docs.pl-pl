---
title: Klasa CWndClassInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11f61e89ab888b678bf54f65b999c0fd4394dbea
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201665"
---
# <a name="cwndclassinfo-class"></a>Klasa CWndClassInfo
Ta klasa dostarcza metody do rejestrowania informacji dla klasy okna.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CWndClassInfo
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|[Zarejestruj się](#register)|Rejestruje klasę okna.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_atom](#m_atom)|Jednoznacznie identyfikuje klasę okna zarejestrowane.|  
|[m_bSystemCursor](#m_bsystemcursor)|Określa, czy zasobu kursora odnosi się do kursora systemu lub kursora zawarte w zasobie modułu.|  
|[m_lpszCursorID](#m_lpszcursorid)|Określa nazwę zasobu kursora.|  
|[m_lpszOrigName](#m_lpszorigname)|Zawiera nazwę istniejącej klasy okna.|  
|[m_szAutoName](#m_szautoname)|Przechowuje generowane ATL musi mieć nazwę klasy okna.|  
|[m_wc](#m_wc)|Przechowuje informacje o klasie okna w `WNDCLASSEX` struktury.|  
|[pWndProc](#pwndproc)|Wskazuje procedurę okna istniejącej klasy okna.|  
  
## <a name="remarks"></a>Uwagi  
 `CWndClassInfo` zarządza informacjami klasy okna. Zazwyczaj używa się `CWndClassInfo` za pomocą jednego z trzech makra, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX lub DECLARE_WND_SUPERCLASS, zgodnie z opisem w poniższej tabeli:  
  
|Macro|Opis|  
|-----------|-----------------|  
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` rejestruje informacje o nowe klasy okna.|  
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` rejestruje informacje o nową klasę okna, w tym parametrów klasy.|  
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` rejestruje informacje dotyczące klasy okna, która opiera się na istniejącej klasy, ale używa procedury innego okna. Ta metoda jest wywoływana superclassing.|  
  
 Domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md) obejmuje `DECLARE_WND_CLASS` makra można utworzyć okna oparte na nową klasę okna. DECLARE_WND_CLASS zawiera domyślne style i kolor tła kontrolki. Jeśli chcesz określić styl i kolor tła, samodzielnie pochodzi z klasy `CWindowImpl` i zawierać makra DECLARE_WND_CLASS_EX w definicji klasy.  
  
 Jeśli chcesz utworzyć okno, w oparciu o istniejące klasy okna pochodzi z klasy `CWindowImpl` i zawierać makra DECLARE_WND_SUPERCLASS w definicji klasy. Na przykład:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]  
  
 Aby uzyskać więcej informacji na temat klas okien, zobacz [klas okien](https://msdn.microsoft.com/library/windows/desktop/ms632596) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat korzystania z systemu windows w ATL, zobacz artykuł [klas okien ATL](../../atl/atl-window-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="m_atom"></a>  CWndClassInfo::m_atom  
 Zawiera unikatowy identyfikator klasy okna zarejestrowane.  
  
```
ATOM m_atom;
```  
  
##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor  
 W przypadku opcji TRUE zasobu kursora systemu zostanie załadowany po zarejestrowaniu klasy okna.  
  
```
BOOL m_bSystemCursor;
```  
  
### <a name="remarks"></a>Uwagi  
 W przeciwnym razie zostanie załadowany zasobu kursora zawarte w module.  
  
 `CWndClassInfo` używa `m_bSystemCursor` tylko wtedy, gdy [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (ustawienie domyślne w [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) — makro jest określony. W tym przypadku `m_bSystemCursor` jest ustawiana na wartość TRUE. Aby uzyskać więcej informacji, zobacz [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Przegląd.  
  
##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID  
 Określa nazwę zasobu kursora lub identyfikator zasobu w word niskiego rzędu i zera w programie word wyższego rzędu.  
  
```
LPCTSTR m_lpszCursorID;
```  
  
### <a name="remarks"></a>Uwagi  
 Po zarejestrowaniu klasy okna, dojścia do kursora identyfikowane przez `m_lpszCursorID` są pobierane i przechowywane przez [m_wc](#m_wc).  
  
 `CWndClassInfo` używa `m_lpszCursorID` tylko wtedy, gdy [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (ustawienie domyślne w [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) — makro jest określony. W tym przypadku `m_lpszCursorID` jest inicjowany do IDC_ARROW. Aby uzyskać więcej informacji, zobacz [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Przegląd.  
  
##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName  
 Zawiera nazwę istniejącej klasy okna.  
  
```
LPCTSTR m_lpszOrigName;
```  
  
### <a name="remarks"></a>Uwagi  
 `CWndClassInfo` używa `m_lpszOrigName` tylko Jeśli dołączysz [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra w definicji klasy. W tym przypadku `CWndClassInfo` rejestruje klasę okna na podstawie klasy o nazwie określonej przez `m_lpszOrigName`. Aby uzyskać więcej informacji, zobacz [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Przegląd.  
  
##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName  
 Przechowuje nazwę klasy okna.  
  
```
TCHAR m_szAutoName[13];
```  
  
### <a name="remarks"></a>Uwagi  
 `CWndClassInfo` używa `m_szAutoName` tylko wtedy, gdy wartość NULL jest przekazywana `WndClassName` parametr [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) lub [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . ATL będzie konstruowania nazwę, po zarejestrowaniu klasy okna.  
  
##  <a name="m_wc"></a>  CWndClassInfo::m_wc  
 Przechowuje informacje klasy okna w [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577) struktury.  
  
```
WNDCLASSEX m_wc;
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (ustawienie domyślne w [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makra `m_wc` zawiera informacje o nowe klasy okna.  
  
 Jeśli określono [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra `m_wc` zawiera informacje o superklasie — klasy okna, która opiera się na istniejącej klasy, ale używa procedury innego okna. [m_lpszOrigName](#m_lpszorigname) i [pWndProc](#pwndproc) odpowiednio Zapisz nazwę istniejącej klasy okna i procedurę okna.  
  
##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc  
 Wskazuje procedurę okna istniejącej klasy okna.  
  
```
WNDPROC pWndProc;
```  
  
### <a name="remarks"></a>Uwagi  
 `CWndClassInfo` używa `pWndProc` tylko Jeśli dołączysz [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra w definicji klasy. W tym przypadku `CWndClassInfo` rejestruje klasę okna, która opiera się na istniejącej klasy, ale używa procedury innego okna. Istniejące klasy okna procedurę okna jest zapisywany w `pWndProc`. Aby uzyskać więcej informacji, zobacz [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Przegląd.  
  
##  <a name="register"></a>  CWndClassInfo::Register  
 Wywoływane przez [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create) zarejestrować klasy okna, jeśli nie została jeszcze zarejestrowana.  
  
```
ATOM Register(WNDPROC* pProc);
```  
  
### <a name="parameters"></a>Parametry  
 *pProc*  
 [out] Określa, oryginalnym procedurę okna w istniejącej klasy okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, atom, który jednoznacznie identyfikuje klasę okna, jest zarejestrowany. W przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (ustawienie domyślne w [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makra `Register` rejestruje nowe klasy okna. W tym przypadku *pProc* parametr nie jest używany.  
  
 Jeśli określono [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra `Register` rejestruje superklasą — klasy okna, która opiera się na istniejącej klasy, ale używa procedury innego okna. Istniejące klasy okna procedurę okna jest zwracany w *pProc*.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)