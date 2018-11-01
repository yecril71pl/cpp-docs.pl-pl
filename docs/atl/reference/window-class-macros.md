---
title: Makra klasy okna
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 75a6a769770c9de8b26c08fae852197cdb99248e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503158"
---
# <a name="window-class-macros"></a>Makra klasy okna

Te makra definiują narzędzia klasy okna.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Pozwala określić nazwę nowej klasy okna.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Pozwala określić nazwę nowej klasy okna i otaczającej klasy procedurę okna, którego będzie używać nowej klasy.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Pozwala określić nazwę istniejącej klasy okna, na którym będzie opierać się nową klasę okna.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Umożliwia określanie parametrów klasy.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="declare_wnd_class"></a>  DECLARE_WND_CLASS

Pozwala określić nazwę nowej klasy okna. Umieść tego makra w kontrolkę ActiveX biblioteki ATL klasy kontrolki.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
[in] Nazwa nowej klasy okna. Jeśli ma wartość NULL, ATL wygeneruje nazwę klasy okna.

### <a name="remarks"></a>Uwagi

Jeśli używasz opcji /permissive-compiler następnie DECLARE_WND_CLASS spowoduje błąd kompilatora; Zamiast tego użyj DECLARE_WND_CLASS2.

DECLARE_WND_CLASS pozwala określić nazwę klasę okna, o których informacje, które będą zarządzane przez [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS definiuje nową klasę okna, implementując następującą funkcję statyczne:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS określa następujące style dla nowego okna:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS określa również kolor tła okna domyślne. Użyj [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) makra, aby podać własne style i kolor tła.

[CWindowImpl](cwindowimpl-class.md) używa makro DECLARE_WND_CLASS można utworzyć okna, w oparciu o nowe klasy okna. Aby zmienić to zachowanie, użyj [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) makro, albo podać własną implementację [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) funkcji.

Aby uzyskać więcej informacji na temat korzystania z systemu windows w ATL, zobacz artykuł [klas okien ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2

(Visual Studio 2017) Podobny do DECLARE_WND_CLASS, ale z dodatkowym parametrem, który pozwala uniknąć błędów zależna nazwa podczas kompilowania za pomocą /permissive-option.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
[in] Nazwa nowej klasy okna. Jeśli ma wartość NULL, ATL wygeneruje nazwę klasy okna.

*EnclosingClass*<br/>
[in] Nazwa klasy okna, który zawiera nową klasę okna. Nie może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Jeśli używasz /permissive-option następnie DECLARE_WND_CLASS spowoduje błąd kompilacji, ponieważ zawiera nazwę zależnego. DECLARE_WND_CLASS2 wymaga jawnie nazwę klasy, że to makro jest używane w i nie powoduje błąd w obszarze /permissive-flag.
W przeciwnym razie to makro jest taka sama jak [DECLARE_WND_CLASS](#declare_wnd_class).

##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS

Umożliwia określanie parametrów klasy. Umieść tego makra w kontrolkę ActiveX biblioteki ATL klasy kontrolki.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
[in] Nazwa okna klasy tego superklasie będzie *OrigWndClassName*. Jeśli ma wartość NULL, ATL wygeneruje nazwę klasy okna.

*OrigWndClassName*<br/>
[in] Nazwa istniejącej klasy okna.

### <a name="remarks"></a>Uwagi

Tego makra pozwala określić nazwę klasy okna, w której będzie superklasie istniejącej klasy okna. [CWndClassInfo](cwndclassinfo-class.md) zarządza informacjami superklasy.

DECLARE_WND_SUPERCLASS implementuje statyczne następującą funkcję:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Domyślnie [CWindowImpl](cwindowimpl-class.md) używa [DECLARE_WND_CLASS](#declare_wnd_class) makra można utworzyć okna oparte na nową klasę okna. Określając makro DECLARE_WND_SUPERCLASS w `CWindowImpl`-klasy, klasy okna będzie zależeć od istniejącej klasy, ale będzie używać Twojej procedurę okna. Ta metoda jest wywoływana superclassing.

Oprócz za pomocą makra DECLARE_WND_CLASS i DECLARE_WND_SUPERCLASS, można zastąpić [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) funkcji z Twojej własnej implementacji.

Aby uzyskać więcej informacji na temat korzystania z systemu windows w ATL, zobacz artykuł [klas okien ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX

Pozwala określić nazwę istniejącej klasy okna, na którym będzie opierać się nową klasę okna. Umieść tego makra w kontrolkę ActiveX biblioteki ATL klasy kontrolki.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parametry

*WndClassName*<br/>
[in] Nazwa nowej klasy okna. Jeśli ma wartość NULL, ATL wygeneruje nazwę klasy okna.

*Styl*<br/>
[in] Styl okna.

*tło /*<br/>
[in] Kolor tła okna.

### <a name="remarks"></a>Uwagi

To makro służy do określania parametrów klasy nowe klasy okna, o których informacje, które będą zarządzane przez [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX definiuje nową klasę okna, implementując następującą funkcję statyczne:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Jeśli chcesz korzystać z domyślnych stylów i kolor tła, użyj [DECLARE_WND_CLASS](#declare_wnd_class) makra. Aby uzyskać więcej informacji na temat korzystania z systemu windows w ATL, zobacz artykuł [klas okien ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Zobacz też

[Makra](atl-macros.md)

