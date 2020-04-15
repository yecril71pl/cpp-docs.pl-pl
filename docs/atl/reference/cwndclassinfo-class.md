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
ms.openlocfilehash: 01706bf61c3b977c28998325ece68724cfbc7452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330334"
---
# <a name="cwndclassinfo-class"></a>Klasa CWndClassInfo

Ta klasa zawiera metody rejestrowania informacji dla klasy okna.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CWndClassInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|[Zarejestruj](#register)|Rejestruje klasę okna.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_atom](#m_atom)|Jednoznacznie identyfikuje klasę zarejestrowanego okna.|
|[m_bSystemCursor](#m_bsystemcursor)|Określa, czy zasób kursora odwołuje się do kursora systemowego, czy do kursora zawartego w zasobie modułu.|
|[m_lpszCursorID](#m_lpszcursorid)|Określa nazwę zasobu kursora.|
|[m_lpszOrigName](#m_lpszorigname)|Zawiera nazwę istniejącej klasy okna.|
|[m_szAutoName](#m_szautoname)|Przechowuje nazwę wygenerowaną przez ATL klasy okna.|
|[m_wc](#m_wc)|Przechowuje informacje o `WNDCLASSEX` klasie okna w strukturze.|
|[pWndProc (proces pWndProc)](#pwndproc)|Wskazuje na procedurę okna istniejącej klasy okna.|

## <a name="remarks"></a>Uwagi

`CWndClassInfo`zarządza informacjami klasy okna. Zazwyczaj używa `CWndClassInfo` się za pośrednictwem jednego z trzech makr, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX lub DECLARE_WND_SUPERCLASS, zgodnie z opisem w poniższej tabeli:

|Makro|Opis|
|-----------|-----------------|
|[Declare_wnd_class](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`rejestruje informacje dla nowej klasy okna.|
|[Declare_wnd_class_ex](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`rejestruje informacje dla nowej klasy okna, w tym parametry klasy.|
|[Declare_wnd_superclass](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`rejestruje informacje dla klasy okna, która jest oparta na istniejącej klasie, ale używa innej procedury okna. Ta technika nazywana jest superklasing.|

Domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md) zawiera `DECLARE_WND_CLASS` makro, aby utworzyć okno na podstawie nowej klasy okna. DECLARE_WND_CLASS zapewnia domyślne style i kolor tła dla formantu. Jeśli chcesz samodzielnie określić styl i kolor tła, wyjdź z `CWindowImpl` klasy i uwzględnij makro DECLARE_WND_CLASS_EX w definicji klasy.

Jeśli chcesz utworzyć okno na podstawie istniejącej klasy okna, `CWindowImpl` należy wyprowadzić klasę z i uwzględnić makro DECLARE_WND_SUPERCLASS w definicji klasy. Przykład:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Aby uzyskać więcej informacji na temat klas okien, zobacz [klasy okien](/windows/win32/winmsg/window-classes) w windows SDK.

Aby uzyskać więcej informacji na temat korzystania z okien w atl, zobacz artykuł [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a>CWndClassInfo::m_atom

Zawiera unikatowy identyfikator dla klasy zarejestrowanego okna.

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor

Jeśli TRUE, zasób kursora systemowego zostanie załadowany po zarejestrowaniu klasy okna.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Uwagi

W przeciwnym razie zasób kursora zawarty w module zostanie załadowany.

`CWndClassInfo`jest `m_bSystemCursor` używany tylko wtedy, gdy [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (wartość domyślna w [CWindowImpl)](../../atl/reference/cwindowimpl-class.md)lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makra jest określony. W takim `m_bSystemCursor` przypadku jest inicjowany do TRUE. Aby uzyskać więcej informacji, zobacz [omówienie CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID

Określa nazwę zasobu kursora lub identyfikator zasobu w słowie niskiego rzędu i zero w słowie wysokiego rzędu.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Uwagi

Po zarejestrowaniu klasy okna dojście do kursora `m_lpszCursorID` zidentyfikowanego przez jest pobierane i przechowywane przez [m_wc](#m_wc).

`CWndClassInfo`jest `m_lpszCursorID` używany tylko wtedy, gdy [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (wartość domyślna w [CWindowImpl)](../../atl/reference/cwindowimpl-class.md)lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makra jest określony. W takim `m_lpszCursorID` przypadku jest inicjowany do IDC_ARROW. Aby uzyskać więcej informacji, zobacz [omówienie CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName

Zawiera nazwę istniejącej klasy okna.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Uwagi

`CWndClassInfo`jest `m_lpszOrigName` używany tylko wtedy, gdy makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) jest uwzględniane w definicji klasy. W takim `CWndClassInfo` przypadku rejestruje klasę okna na podstawie `m_lpszOrigName`klasy nazwanej przez . Aby uzyskać więcej informacji, zobacz [omówienie CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a>CWndClassInfo::m_szAutoName

Przechowuje nazwę klasy okna.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Uwagi

`CWndClassInfo``m_szAutoName` używa tylko wtedy, gdy `WndClassName` wartość NULL jest przekazywana dla parametru [do DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) lub [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL skonstruuje nazwę, gdy klasa okna jest zarejestrowana.

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a>CWndClassInfo::m_wc

Przechowuje informacje o klasie okna w strukturze [WNDCLASSEX.](/windows/win32/api/winuser/ns-winuser-wndclassexw)

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Uwagi

Jeśli określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (domyślnie w [CWindowImpl)](../../atl/reference/cwindowimpl-class.md)lub [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makra, `m_wc` zawiera informacje o nowej klasy okna.

Jeśli określono [makro DECLARE_WND_SUPERCLASS,](window-class-macros.md#declare_wnd_superclass) `m_wc` zawiera informacje o nadklasie — klasa okna, która jest oparta na istniejącej klasy, ale używa innej procedury okna. [m_lpszOrigName](#m_lpszorigname) i [pWndProc](#pwndproc) zapisać istniejącą klasę okna nazwę i procedury okna, odpowiednio.

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo::pWndProc

Wskazuje na procedurę okna istniejącej klasy okna.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Uwagi

`CWndClassInfo`jest `pWndProc` używany tylko wtedy, gdy makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) jest uwzględniane w definicji klasy. W takim `CWndClassInfo` przypadku rejestruje klasę okna, która jest oparta na istniejącej klasy, ale używa innej procedury okna. Procedura okna istniejącej klasy okna `pWndProc`jest zapisywana w pliku . Aby uzyskać więcej informacji, zobacz [omówienie CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinforegister"></a><a name="register"></a>CWndClassInfo::Zarejestruj się

Wywoływane przez [CWindowImpl::Create,](../../atl/reference/cwindowimpl-class.md#create) aby zarejestrować klasę okna, jeśli nie została jeszcze zarejestrowana.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parametry

*pProc (pProc)*<br/>
[na zewnątrz] Określa oryginalną procedurę okna istniejącej klasy okna.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, atom, który jednoznacznie identyfikuje klasę okna jest zarejestrowany. W przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli określono [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (domyślnie w [CWindowImpl)](../../atl/reference/cwindowimpl-class.md)lub [makro DECLARE_WND_CLASS_EX,](window-class-macros.md#declare_wnd_class_ex) `Register` rejestruje nową klasę okna. W takim przypadku parametr *pProc* nie jest używany.

Jeśli określono [makro DECLARE_WND_SUPERCLASS,](window-class-macros.md#declare_wnd_superclass) `Register` rejestruje nadklasę — klasę okna, która jest oparta na istniejącej klasie, ale używa innej procedury okna. Procedura okna istniejącej klasy okna jest zwracana w *pProc*.

## <a name="see-also"></a>Zobacz też

[Klasa CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
