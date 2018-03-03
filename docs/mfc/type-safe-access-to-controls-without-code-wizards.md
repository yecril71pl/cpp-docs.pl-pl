---
title: "Bezpieczny dostęp do formantów bez użycia kreatorów kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c5a4adce63851620326add61857433b32e1fad5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu
Pierwszym sposobem tworzenia bezpieczny dostęp do formantów używa wbudowanej funkcji członkowskich można rzutować typu zwracanego klasy `CWnd`w `GetDlgItem` funkcji członkowskiej do odpowiedniego typu formantu C++, jak w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 Ta funkcja członkowska można użyć do kontroli dostępu w sposób bezpieczny kod podobny do następującego:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczny dostęp do formantów w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu](../mfc/type-safe-access-to-controls-with-code-wizards.md)

