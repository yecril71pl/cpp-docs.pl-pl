---
title: Makra klasy okna
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 18c0912c506bc52421b18d36346204b557c0fc5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325733"
---
# <a name="window-class-macros"></a>Makra klasy okna

Te makra definiują narzędzia klasy okna.

|||
|-|-|
|[Declare_wnd_class](#declare_wnd_class)|Umożliwia określenie nazwy nowej klasy okna.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Umożliwia określenie nazwy nowej klasy okna i otaczającej klasy, której procedura okna będzie używana nowa klasa.|
|[Declare_wnd_superclass](#declare_wnd_superclass)|Umożliwia określenie nazwy istniejącej klasy okna, na której będzie oparta nowa klasa okna.|
|[Declare_wnd_class_ex](#declare_wnd_class_ex)|Umożliwia określenie parametrów klasy.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a>Declare_wnd_class

Umożliwia określenie nazwy nowej klasy okna. Umieść to makro w klasie kontrolnej formantu ACTIVEX ATL.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parametry

*Nazwa WNDClass*<br/>
[w] Nazwa nowej klasy okna. Jeśli null, ATL wygeneruje nazwę klasy okna.

### <a name="remarks"></a>Uwagi

Jeśli używasz /permissive- kompilatora opcji, a następnie DECLARE_WND_CLASS spowoduje błąd kompilatora; zamiast tego użyj DECLARE_WND_CLASS2.

DECLARE_WND_CLASS umożliwia określenie nazwy nowej klasy okna, której informacje będą zarządzane przez [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS definiuje nową klasę okna, implementując następującą funkcję statyczną:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS określa następujące style dla nowego okna:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS określa również domyślny kolor tła okna. Użyj [makra DECLARE_WND_CLASS_EX,](#declare_wnd_class_ex) aby zapewnić własne style i kolor tła.

[CWindowImpl](cwindowimpl-class.md) używa makra DECLARE_WND_CLASS do utworzenia okna na podstawie nowej klasy okna. Aby zastąpić to zachowanie, należy użyć [makra DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) lub podać własną implementację funkcji [GetWndClassInfo.](cwindowimpl-class.md#getwndclassinfo)

Aby uzyskać więcej informacji na temat korzystania z okien w atl, zobacz artykuł [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

(Visual Studio 2017) Podobne do DECLARE_WND_CLASS, ale z dodatkowym parametrem, który pozwala uniknąć błędu nazwy zależnej podczas kompilowania z /permissive- opcja.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parametry

*Nazwa WNDClass*<br/>
[w] Nazwa nowej klasy okna. Jeśli null, ATL wygeneruje nazwę klasy okna.

*Klasa enclosing*<br/>
[w] Nazwa klasy okna, która otacza nową klasę okna. Nie może być null.

### <a name="remarks"></a>Uwagi

Jeśli używasz /permissive- opcja, a następnie DECLARE_WND_CLASS spowoduje błąd kompilacji, ponieważ zawiera nazwę zależną. DECLARE_WND_CLASS2 wymaga jawnie nazwy klasy, w której jest używane to makro i nie powoduje błędu pod /permissive- flaga.
W przeciwnym razie to makro jest identyczne [z DECLARE_WND_CLASS](#declare_wnd_class).

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a>Declare_wnd_superclass

Umożliwia określenie parametrów klasy. Umieść to makro w klasie kontrolnej formantu ACTIVEX ATL.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parametry

*Nazwa WNDClass*<br/>
[w] Nazwa klasy okna, która będzie superclass *OrigWndClassName*. Jeśli null, ATL wygeneruje nazwę klasy okna.

*OrigWndClassName (Nazwa klasy OrigWnd)*<br/>
[w] Nazwa istniejącej klasy okna.

### <a name="remarks"></a>Uwagi

To makro umożliwia określenie nazwy klasy okna, która będzie superklasy istniejącej klasy okna. [CWndClassInfo](cwndclassinfo-class.md) zarządza informacjami o nadklasie.

DECLARE_WND_SUPERCLASS implementuje następującą funkcję statyczną:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Domyślnie [CWindowImpl](cwindowimpl-class.md) używa makra [DECLARE_WND_CLASS](#declare_wnd_class) do utworzenia okna na podstawie nowej klasy okna. Określając makro DECLARE_WND_SUPERCLASS w klasie pochodnej `CWindowImpl`okna, klasa okna będzie oparta na istniejącej klasie, ale użyje procedury okna. Ta technika nazywana jest superklasing.

Oprócz używania makr DECLARE_WND_CLASS i DECLARE_WND_SUPERCLASS można zastąpić funkcję [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) własną implementacją.

Aby uzyskać więcej informacji na temat korzystania z okien w atl, zobacz artykuł [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a>Declare_wnd_class_ex

Umożliwia określenie nazwy istniejącej klasy okna, na której będzie oparta nowa klasa okna. Umieść to makro w klasie kontrolnej formantu ACTIVEX ATL.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parametry

*Nazwa WNDClass*<br/>
[w] Nazwa nowej klasy okna. Jeśli null, ATL wygeneruje nazwę klasy okna.

* — styl*<br/>
[w] Styl okna.

*bkgnd ( bkgnd )*<br/>
[w] Kolor tła okna.

### <a name="remarks"></a>Uwagi

To makro umożliwia określenie parametrów klasy nowej klasy okna, której informacje będą zarządzane przez [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX definiuje nową klasę okna, implementując następującą funkcję statyczną:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Jeśli chcesz użyć stylów domyślnych i koloru tła, użyj [makra DECLARE_WND_CLASS.](#declare_wnd_class) Aby uzyskać więcej informacji na temat korzystania z okien w atl, zobacz artykuł [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Zobacz też

[Makra](atl-macros.md)
