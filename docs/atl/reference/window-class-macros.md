---
title: Makra klasy okna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
dev_langs:
- C++
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0490eedb412e43f2ae99c4034648880be5f32a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="window-class-macros"></a>Makra klasy okna
Te makra zdefiniuj okna narzędzia klasy.  
  
|||  
|-|-|  
|[DECLARE_WND_CLASS](#declare_wnd_class)|Służy do określania nazwy nowej klasy okna.| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Umożliwia określenie nazwy nową klasę okna i otaczającą klasę procedurę okna, którego będzie używać nowej klasy.| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Służy do określenia nazwy istniejącej klasy okna, na którym będzie opierać się nową klasę okna.|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Umożliwia określenie parametrów klasy.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
   
##  <a name="declare_wnd_class"></a>  DECLARE_WND_CLASS  
 Służy do określania nazwy nowej klasy okna. Umieść to makro formantu ATL ActiveX klasy formantu.  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>Parametry  
 `WndClassName`  
 [in] Nazwa nowej klasy okna. Jeśli **NULL**, ATL wygeneruje nazwę klasy okna.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli używasz opcji /permissive-compiler, następnie DECLARE_WND_CLASS spowoduje błąd kompilatora; Zamiast tego użyj DECLARE_WND_CLASS2.
 
 DECLARE_WND_CLASS pozwala określić nazwę nowej klasy okna, którego informacje będą zarządzane przez [CWndClassInfo](cwndclassinfo-class.md). `DECLARE_WND_CLASS` Określa nową klasę okna zaimplementowanie następujące statycznej funkcji:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 `DECLARE_WND_CLASS` Określa style następujące nowe okno:  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 `DECLARE_WND_CLASS` Określa również kolor tła w oknie domyślnej. Użyj [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) makra, aby zapewnić własnych stylów i kolor tła.  
  
 [CWindowImpl](cwindowimpl-class.md) używa `DECLARE_WND_CLASS` makro można utworzyć okna oparte na nową klasę okna. Aby zmienić to zachowanie, użyj [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) makra, lub Podaj własny implementacja [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) funkcji.  

  
 Aby uzyskać więcej informacji o korzystaniu z systemu windows w ATL, zobacz artykuł [klas okien ALT](../../atl/atl-window-classes.md).  

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2  
 (Visual Studio 2017) Podobny do DECLARE_WND_CLASS, ale z dodatkowym parametrem, która pozwala uniknąć błędów zależna nazwa podczas kompilowania przy użyciu /permissive-option.
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>Parametry  
 `WndClassName`  
 [in] Nazwa nowej klasy okna. Jeśli **NULL**, ATL wygeneruje nazwę klasy okna. 

 `EnclosingClass`  
 [in] Nazwa klasy okna, która obejmuje nową klasę okna. Nie może być **NULL**.  
  
### <a name="remarks"></a>Uwagi 
Jeśli używasz /permissive-option, następnie DECLARE_WND_CLASS spowoduje błąd kompilacji, ponieważ zawiera ona zależna nazwa. DECLARE_WND_CLASS2 wymaga jawnie nazwy klasy, że to makro jest używane w i nie powoduje błąd w obszarze /permissive-flag.
W przeciwnym razie to makro jest taki sam jak [DECLARE_WND_CLASS](#declare_wnd_class).
   
##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS  
 Umożliwia określenie parametrów klasy. Umieść to makro formantu ATL ActiveX klasy formantu.  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>Parametry  
 `WndClassName`  
 [in] Nazwa okna klasy tej superklasie będzie `OrigWndClassName`. Jeśli **NULL**, ATL wygeneruje nazwę klasy okna.  
  
 `OrigWndClassName`  
 [in] Nazwa istniejącej klasy okna.  
  
### <a name="remarks"></a>Uwagi  
 To makro można określić nazwę klasy okna zostanie superklasie istniejącej klasy okna. [CWndClassInfo](cwndclassinfo-class.md) zarządza informacjami superklasy.  
  
 `DECLARE_WND_SUPERCLASS` implementuje następujące statycznej funkcji:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 Domyślnie [CWindowImpl](cwindowimpl-class.md) używa [DECLARE_WND_CLASS](#declare_wnd_class) makro można utworzyć okna oparte na nową klasę okna. Określając `DECLARE_WND_SUPERCLASS` makra w `CWindowImpl`-klasy, klasy okna będą oparte na istniejącej klasy, ale będzie używać sieci procedurę okna. Ta metoda jest wywoływana tworzenie nadklas.  
  
 Oprócz funkcji `DECLARE_WND_CLASS` i `DECLARE_WND_SUPERCLASS` makra, można zastąpić [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) funkcji z własną implementację.  

  
 Aby uzyskać więcej informacji o korzystaniu z systemu windows w ATL, zobacz artykuł [klas okien ALT](../../atl/atl-window-classes.md).  
  
##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX  
 Służy do określenia nazwy istniejącej klasy okna, na którym będzie opierać się nową klasę okna. Umieść to makro formantu ATL ActiveX klasy formantu.  
  
```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```  
  
### <a name="parameters"></a>Parametry  
 `WndClassName`  
 [in] Nazwa nowej klasy okna. Jeśli **NULL**, ATL wygeneruje nazwę klasy okna.  
  
 `style`  
 [in] Styl okna.  
  
 *tło /*  
 [in] Kolor tła okna.  
  
### <a name="remarks"></a>Uwagi  
 To makro umożliwia określenie parametrów klasy nową klasę okna, którego informacje będą zarządzane przez [CWndClassInfo](cwndclassinfo-class.md). `DECLARE_WND_CLASS_EX` Określa nową klasę okna zaimplementowanie następujące statycznej funkcji:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 Jeśli chcesz użyć domyślnych stylów i kolor tła, użyj [DECLARE_WND_CLASS](#declare_wnd_class) makra. Aby uzyskać więcej informacji o korzystaniu z systemu windows w ATL, zobacz artykuł [klas okien ALT](../../atl/atl-window-classes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](atl-macros.md)









