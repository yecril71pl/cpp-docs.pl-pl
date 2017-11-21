---
title: "Wymagania formantów standardowych systemu Windows Vista dotyczące kompilacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6f6dabd14ddb95f1b4c2b49389c27f61a69970f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Wymagania kontrolek standardowych systemu Windows Vista dotyczące kompilacji
Biblioteka Microsoft Foundation Class (MFC) obsługuje formanty standardowe systemu Windows w wersji 6.1. Formanty standardowe są uwzględnione w [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] i biblioteki wchodzi w skład [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]. Biblioteka zawiera nowych metod, które podnoszą istniejących klas i nowe klasy i metody, które obsługują [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] formantów standardowych. Podczas tworzenia aplikacji, należy wykonać wymagania dotyczące kompilacji i migracji, które zostały opisane w poniższych sekcjach.  
  
## <a name="compilation-requirements"></a>Wymagania dotyczące kompilacji  
  
### <a name="supported-versions"></a>Obsługiwane wersje  
 Niektóre nowe klasy i metody obsługują tylko [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] lub nowszym, podczas gdy inne metody również obsługiwać starszych systemów operacyjnych. Zanotuj w `Requirements` każdego tematu Metoda określa, kiedy minimalny wymagany system operacyjny jest [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)].  
  
 Nawet jeśli komputer nie jest uruchamiane [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)], można utworzyć aplikację MFC, która będzie uruchamiany na [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] Jeśli masz pliki nagłówków wersji 6.1 MFC na tym komputerze. Jednak typowe formantów, które zostały zaprojektowane specjalnie z myślą o [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] działać tylko w tym systemie i są ignorowane przez starszych systemów operacyjnych.  
  
### <a name="supported-character-sets"></a>Obsługiwanych zestawów znaków  
 Nowe formanty wspólne systemu Windows obsługuje tylko zestaw znaków Unicode i nie zestawu znaków ANSI. W przypadku tworzenia aplikacji w wierszu polecenia, użyj obu Definiuj następujące (/ D) opcji kompilatora, aby określić Unicode jako podstawowy zestaw znaków:  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 W przypadku tworzenia aplikacji w programie Visual Studio zintegrowane środowisko programistyczne (IDE), określ **zestaw znaków Unicode** opcji **zestaw znaków** właściwości w **ogólne**  węzła właściwości projektu.  
  
 Wersja ANSI kilka metod MFC są przestarzałe, począwszy od formantów standardowych systemu Windows w wersji 6.1. Aby uzyskać więcej informacji, zobacz [przestarzałe interfejsy API ANSI](../mfc/deprecated-ansi-apis.md).  
  
## <a name="migration-requirements"></a>Wymagania dotyczące migracji  
 Jeśli używasz środowiska IDE programu Visual Studio do tworzenia nowej aplikacji MFC, która używa formanty standardowe systemu Windows w wersji 6.1 IDE automatycznie deklaruje odpowiednie manifestu. Jednak jeśli migracji istniejącej aplikacji MFC z wcześniejszej wersji programu Visual Studio, którego chcesz użyć nowe formanty wspólne IDE nie automatycznie zapewnia manifestu informacje dotyczące uaktualnienia wersji aplikacji. Zamiast tego należy ręcznie Wstaw następujący kod źródłowy w pliku stdafx.h:  
  
```  
#ifdef UNICODE  
#if defined _M_IX86  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_IA64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_X64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#else  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#endif  
#endif  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)   
 [Diagram hierarchii](../mfc/hierarchy-chart.md)   
 [Przestarzałe interfejsy API ANSI](../mfc/deprecated-ansi-apis.md)

