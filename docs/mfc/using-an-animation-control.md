---
title: Używanie formantu animacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecde11ddb55992032b2a8b052e2897a384293bc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-animation-control"></a>Używanie formantu animacji
Typowy sposób formantu animacji jest zgodny ze wzorcem poniżej:  
  
-   Formant nie zostanie utworzony. Jeśli formant jest określona w szablonie — okno dialogowe, tworzenie odbywa się automatycznie po utworzeniu okna dialogowego. (Powinien mieć [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) element członkowski w klasy okien dialogowych umożliwiająca formantu animacji.) Alternatywnie można użyć [Utwórz](../mfc/reference/canimatectrl-class.md#create) funkcji członkowskiej można utworzyć formantu jako okna podrzędnego każdego okna.  
  
-   Ładowanie klip AVI do formantu animacji, wywołując [Otwórz](../mfc/reference/canimatectrl-class.md#open) funkcję elementu członkowskiego. W przypadku formantu animacji w oknie dialogowym, dobrym miejscem, w tym celu jest klasy okien dialogowych [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji.  
  
-   Odtwarzania przez wywołanie metody [odtwarzanie](../mfc/reference/canimatectrl-class.md#play) funkcję elementu członkowskiego. W przypadku formantu animacji w oknie dialogowym, dobrym miejscem, w tym celu jest klasy okien dialogowych **OnInitDialog** funkcji. Wywoływanie **odtwarzanie** nie jest konieczne, jeśli ma formantu animacji `ACS_AUTOPLAY` styl zestawu.  
  
-   Jeśli chcesz wyświetlić części klipu lub go odtworzyć klatka, użyj `Seek` funkcję elementu członkowskiego. Aby zatrzymać klip odtwarzany, użyj `Stop` funkcję elementu członkowskiego.  
  
-   Jeśli nie ma do zniszczenia kontrolki od razu, usunąć klip z pamięci przez wywołanie metody **Zamknij** funkcję elementu członkowskiego.  
  
-   W przypadku formantu animacji w oknie dialogowym go i `CAnimateCtrl` obiektu zostaną automatycznie usunięte. Jeśli nie, musisz upewnij się, że oba formantu i `CAnimateCtrl` obiektu prawidłowo zostaną zniszczone. Likwidowanie formantu automatycznie zamyka klip AVI.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

