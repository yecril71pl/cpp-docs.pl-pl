---
title: "Zarządzanie oknami podrzędnymi MDI | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MDICLIENT
dev_langs: C++
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1489fa4ec75b94c9daad7216a28599c6ef67e5a5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="managing-mdi-child-windows"></a>Zarządzanie oknami podrzędnymi MDI
MDI ramki głównej z systemem windows (po jednym dla każdego aplikacji) zawiera okno podrzędne specjalne **MDICLIENT** okna. **MDICLIENT** okna zarządza obszaru klienckiego głównego okna ramowego i okien podrzędnych z kolei ma: okna dokumentów, pochodną `CMDIChildWnd`. Ponieważ okna dokumentów okien ramowych, same (okien podrzędnych MDI), mogą również mieć własne elementy podrzędne. We wszystkich tych przypadkach okno nadrzędne zarządza jego okien podrzędnych i przekazuje niektóre polecenia do nich.  
  
 W oknie ramowym MDI zarządza okno ramowe **MDICLIENT** okna położenia go w połączeniu z paskami sterowania. **MDICLIENT** okno z kolei zarządza wszystkich podrzędnych okien ramowych MDI. Na poniższej ilustracji przedstawiono relacje między ramki okna MDI, jego **MDICLIENT** okna, a jego podrzędnych okien ramowych dokumentu.  
  
 ![Okno podrzędne w oknie ramowym MDI](../mfc/media/vc37gb1.gif "vc37gb1")  
Okna ramowe MDI i elementy podrzędne  
  
 Ramki okna MDI działa także w połączeniu z bieżącego okna podrzędnego MDI, jeśli istnieje. Okno ramowe MDI deleguje komunikaty poleceń do podrzędnego MDI przed ponowną próbą obsługi samej siebie.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)  
  
-   [Style okna ramowego](../mfc/frame-window-styles-cpp.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

