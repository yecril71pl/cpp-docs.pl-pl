---
title: Zarządzanie oknami podrzędnymi MDI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MDICLIENT
dev_langs:
- C++
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58ddef11e56da760bbecaa47f03dfa6c57dfa3ed
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929484"
---
# <a name="managing-mdi-child-windows"></a>Zarządzanie oknami podrzędnymi MDI
MDI ramki głównej z systemem windows (po jednym dla każdego aplikacji) zawiera okno MDICLIENT okna podrzędnego specjalnych. Okno MDICLIENT zarządza obszaru klienckiego głównego okna ramowego i okien podrzędnych z kolei ma: okna dokumentów, pochodną `CMDIChildWnd`. Ponieważ okna dokumentów okien ramowych, same (okien podrzędnych MDI), mogą również mieć własne elementy podrzędne. We wszystkich tych przypadkach okno nadrzędne zarządza jego okien podrzędnych i przekazuje niektóre polecenia do nich.  
  
 W oknie ramowym MDI okno ramowe zarządza okno MDICLIENT położenia go w połączeniu z paskami sterowania. Okno MDICLIENT z kolei zarządza wszystkich podrzędnych okien ramowych MDI. Na poniższej ilustracji przedstawiono relację między MDI ramkę okna, okno MDICLIENT i jego podrzędnych okien ramowych dokumentu.  
  
 ![Okno podrzędne w oknie ramowym MDI](../mfc/media/vc37gb1.gif "vc37gb1")  
Okna ramowe MDI i elementy podrzędne  
  
 Ramki okna MDI działa także w połączeniu z bieżącego okna podrzędnego MDI, jeśli istnieje. Okno ramowe MDI deleguje komunikaty poleceń do podrzędnego MDI przed ponowną próbą obsługi samej siebie.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)  
  
-   [Style okna ramowego](../mfc/frame-window-styles-cpp.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

