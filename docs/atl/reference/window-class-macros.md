---
title: Makra klasy okna
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: ca19eba1632ef3754b704c82ad5a872160ae0c91
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834469"
---
# <a name="window-class-macros"></a>Makra klasy okna

Te makra definiują narzędzia klasy okna.

|Nazwa|Opis|
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Umożliwia określenie nazwy nowej klasy okna.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Umożliwia określenie nazwy nowej klasy okna i otaczającej klasy, której będzie używać nowa klasa.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Umożliwia określenie nazwy istniejącej klasy okna, na której będzie oparta Nowa Klasa okna.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Umożliwia określenie parametrów klasy.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a> DECLARE_WND_CLASS

Umożliwia określenie nazwy nowej klasy okna. Umieść to makro w klasie kontrolki kontrolki ActiveX ATL.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
podczas Nazwa nowej klasy okna. Jeśli wartość jest równa NULL, ATL wygeneruje nazwę klasy okna.

### <a name="remarks"></a>Uwagi

Jeśli używasz opcji kompilatora/permissive-, DECLARE_WND_CLASS spowoduje błąd kompilatora; Zamiast tego użyj DECLARE_WND_CLASS2.

DECLARE_WND_CLASS pozwala określić nazwę nowej klasy okna, której informacje będą zarządzane przez [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS definiuje nową klasę okna przez implementację następującej funkcji statycznej:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS określa następujące style dla nowego okna:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS określa również kolor tła okna domyślnego. Użyj makra [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) , aby podać własne style i kolor tła.

[CWindowImpl](cwindowimpl-class.md) używa makra DECLARE_WND_CLASS do utworzenia okna opartego na nowej klasie okna. Aby zastąpić to zachowanie, użyj makra [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) lub podaj własną implementację funkcji [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) .

Aby uzyskać więcej informacji na temat korzystania z systemu Windows w ATL, zobacz [klasy okien ATL](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a> DECLARE_WND_CLASS2

(Visual Studio 2017) Podobnie jak DECLARE_WND_CLASS, ale z dodatkowym parametrem, który pozwala uniknąć błędu nazwy zależnej podczas kompilowania z opcją/permissive-.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
podczas Nazwa nowej klasy okna. Jeśli wartość jest równa NULL, ATL wygeneruje nazwę klasy okna.

*EnclosingClass*<br/>
podczas Nazwa klasy okna, która obejmuje nową klasę okna. Nie może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Jeśli używasz opcji/permissive-, DECLARE_WND_CLASS spowoduje błąd kompilacji, ponieważ zawiera nazwę zależną. DECLARE_WND_CLASS2 wymaga jawnej nazwy klasy, w której jest używane to makro, i nie powoduje błędu pod flagą/permissive-.
W przeciwnym razie to makro jest takie samo jak [DECLARE_WND_CLASS](#declare_wnd_class).

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a> DECLARE_WND_SUPERCLASS

Umożliwia określenie parametrów klasy. Umieść to makro w klasie kontrolki kontrolki ActiveX ATL.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
podczas Nazwa klasy okna, która będzie klasą *OrigWndClassName*. Jeśli wartość jest równa NULL, ATL wygeneruje nazwę klasy okna.

*OrigWndClassName*<br/>
podczas Nazwa istniejącej klasy okna.

### <a name="remarks"></a>Uwagi

To makro umożliwia określenie nazwy klasy okna, która będzie klasą istniejącej klasy okien. [CWndClassInfo](cwndclassinfo-class.md) zarządza informacjami klasy superklasy.

DECLARE_WND_SUPERCLASS implementuje następującą funkcję statyczną:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Domyślnie [CWindowImpl](cwindowimpl-class.md) używa makra [DECLARE_WND_CLASS](#declare_wnd_class) , aby utworzyć okno na podstawie nowej klasy okna. Określając DECLARE_WND_SUPERCLASS makro w `CWindowImpl` klasie pochodnej, Klasa Window będzie oparta na istniejącej klasie, ale użyje procedury okna. Ta technika jest nazywana nadklasą.

Oprócz używania DECLARE_WND_CLASS i DECLARE_WND_SUPERCLASS makra można zastąpić funkcję [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) własną implementacją.

Aby uzyskać więcej informacji na temat korzystania z systemu Windows w ATL, zobacz [klasy okien ATL](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a> DECLARE_WND_CLASS_EX

Umożliwia określenie nazwy istniejącej klasy okna, na której będzie oparta Nowa Klasa okna. Umieść to makro w klasie kontrolki kontrolki ActiveX ATL.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
podczas Nazwa nowej klasy okna. Jeśli wartość jest równa NULL, ATL wygeneruje nazwę klasy okna.

*styl*<br/>
podczas Styl okna.

*Pędzel*<br/>
podczas Kolor tła okna.

### <a name="remarks"></a>Uwagi

To makro umożliwia określenie parametrów klasy nowej klasy okna, których informacje będą zarządzane przez [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX definiuje nową klasę okna przez implementację następującej funkcji statycznej:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Jeśli chcesz użyć domyślnych stylów i koloru tła, użyj makra [DECLARE_WND_CLASS](#declare_wnd_class) . Aby uzyskać więcej informacji na temat korzystania z systemu Windows w ATL, zobacz [klasy okien ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Zobacz też

[Makra](atl-macros.md)
