---
title: Klasa CWndClassInfo
ms.date: 11/04/2016
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
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: c1b516f6e92f98d660f7757870a3e634dcef4518
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835509"
---
# <a name="cwndclassinfo-class"></a>Klasa CWndClassInfo

Ta klasa udostępnia metody rejestrowania informacji dla klasy okna.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CWndClassInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|[Zarejestruj](#register)|Rejestruje klasę okna.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|[m_atom](#m_atom)|Unikatowy identyfikator klasy zarejestrowanego okna.|
|[m_bSystemCursor](#m_bsystemcursor)|Określa, czy zasób kursora odwołuje się do kursora systemowego, czy do kursora zawartego w zasobie modułu.|
|[m_lpszCursorID](#m_lpszcursorid)|Określa nazwę zasobu kursora.|
|[m_lpszOrigName](#m_lpszorigname)|Zawiera nazwę istniejącej klasy okna.|
|[m_szAutoName](#m_szautoname)|Przechowuje nazwę klasy okna wygenerowaną przez ATL.|
|[m_wc](#m_wc)|Utrzymuje informacje o klasie okna w `WNDCLASSEX` strukturze.|
|[pWndProc](#pwndproc)|Wskazuje procedurę okna istniejącej klasy Window.|

## <a name="remarks"></a>Uwagi

`CWndClassInfo` zarządza informacjami o klasie okna. Zwykle używasz `CWndClassInfo` jednego z trzech makr, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX lub DECLARE_WND_SUPERCLASS, zgodnie z opisem w poniższej tabeli:

|Makro|Opis|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` rejestruje informacje o nowej klasie okna.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` rejestruje informacje o nowej klasie okna, łącznie z parametrami klasy.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` rejestruje informacje o klasie okna, która jest oparta na istniejącej klasie, ale używa innej procedury okna. Ta technika jest nazywana nadklasą.|

Domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md) zawiera `DECLARE_WND_CLASS` makro do utworzenia okna opartego na nowej klasie okna. DECLARE_WND_CLASS zapewnia domyślne style i kolor tła kontrolki. Jeśli chcesz samodzielnie określić styl i kolor tła, Utwórz klasę z `CWindowImpl` i dołącz DECLARE_WND_CLASS_EX makro w definicji klasy.

Jeśli chcesz utworzyć okno oparte na istniejącej klasie okna, Utwórz klasę z `CWindowImpl` i uwzględnij DECLARE_WND_SUPERCLASS makro w definicji klasy. Na przykład:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Aby uzyskać więcej informacji na temat klas okien, zobacz [klasy okien](/windows/win32/winmsg/window-classes) w Windows SDK.

Aby uzyskać więcej informacji na temat korzystania z systemu Windows w ATL, zobacz [klasy okien ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a> CWndClassInfo:: m_atom

Zawiera unikatowy identyfikator dla zarejestrowanej klasy okna.

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a> CWndClassInfo:: m_bSystemCursor

W przypadku wartości TRUE zasób kursora systemowego zostanie załadowany po zarejestrowaniu klasy okna.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Uwagi

W przeciwnym razie zasób kursora zawarty w module zostanie załadowany.

`CWndClassInfo` używa `m_bSystemCursor` tylko wtedy, gdy określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (wartość domyślna w [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub makro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) . W tym przypadku `m_bSystemCursor` jest inicjowane na wartość true. Aby uzyskać więcej informacji, zobacz Omówienie [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a> CWndClassInfo:: m_lpszCursorID

Określa nazwę zasobu kursora lub identyfikator zasobu w wyrazie o niskim porządku i zero w wyrazie o wysokiej kolejności.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Uwagi

Gdy Klasa okna jest zarejestrowana, dojście do kursora identyfikowane przez `m_lpszCursorID` jest pobierane i przechowywane przez [m_wc](#m_wc).

`CWndClassInfo` używa `m_lpszCursorID` tylko wtedy, gdy określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (wartość domyślna w [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub makro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) . W tym przypadku `m_lpszCursorID` jest zainicjowany do IDC_ARROW. Aby uzyskać więcej informacji, zobacz Omówienie [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a> CWndClassInfo:: m_lpszOrigName

Zawiera nazwę istniejącej klasy okna.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Uwagi

`CWndClassInfo` używane `m_lpszOrigName` tylko wtedy, gdy w definicji klasy dołączysz makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . W takim przypadku `CWndClassInfo` rejestruje klasę okna na podstawie klasy o nazwie `m_lpszOrigName` . Aby uzyskać więcej informacji, zobacz Omówienie [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a> CWndClassInfo:: m_szAutoName

Przechowuje nazwę klasy okna.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Uwagi

`CWndClassInfo`używa `m_szAutoName` tylko wtedy, gdy dla parametru DECLARE_WND_CLASS jest przenoszona wartość null `WndClassName` , [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) lub [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ATL będzie konstruować nazwę, gdy zarejestrowano klasę Window.

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a> CWndClassInfo:: m_wc

Utrzymuje informacje o klasie okna w strukturze [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw) .

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Uwagi

Jeśli określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (wartość domyślna w [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub makro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) , `m_wc` zawiera informacje o nowej klasie okna.

Jeśli określono makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) , `m_wc` zawiera informacje o superklasie — klasie okna, która jest oparta na istniejącej klasie, ale używa innej procedury okna. [m_lpszOrigName](#m_lpszorigname) i [pWndProc](#pwndproc) zapisać odpowiednio nazwę i procedurę okna istniejącej klasy okna.

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a> CWndClassInfo::p WndProc

Wskazuje procedurę okna istniejącej klasy Window.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Uwagi

`CWndClassInfo` używane `pWndProc` tylko wtedy, gdy w definicji klasy dołączysz makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . W takim przypadku `CWndClassInfo` rejestruje klasę okna, która jest oparta na istniejącej klasie, ale używa innej procedury okna. Procedura okna istniejącej klasy okna jest zapisywana w `pWndProc` . Aby uzyskać więcej informacji, zobacz Omówienie [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

## <a name="cwndclassinforegister"></a><a name="register"></a> CWndClassInfo:: register

Wywoływane przez [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create) , aby zarejestrować klasę Window, jeśli nie została jeszcze zarejestrowana.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parametry

*pProc*<br/>
określoną Określa pierwotną procedurę okna istniejącej klasy okna.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, Atom, który jednoznacznie identyfikuje zarejestrowanej klasy okna. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (wartość domyślna w [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) lub makro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) , `Register` rejestruje nową klasę okna. W tym przypadku parametr *pProc* nie jest używany.

Jeśli określono [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro, rejestruje klasę klasy `Register` window, która jest oparta na istniejącej klasie, ale używa innej procedury okna. Procedura okna istniejącej klasy okna jest zwracana w *pProc*.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
