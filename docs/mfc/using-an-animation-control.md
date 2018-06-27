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
ms.openlocfilehash: 0d6b6b07040fbece5fae24fb2ca6be8985695eb0
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950540"
---
# <a name="using-an-animation-control"></a>Używanie formantu animacji
Typowy sposób formantu animacji jest zgodny ze wzorcem poniżej:  
  
-   Formant nie zostanie utworzony. Jeśli formant jest określona w szablonie — okno dialogowe, tworzenie odbywa się automatycznie po utworzeniu okna dialogowego. (Powinien mieć [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) element członkowski w klasy okien dialogowych umożliwiająca formantu animacji.) Alternatywnie można użyć [Utwórz](../mfc/reference/canimatectrl-class.md#create) funkcji członkowskiej można utworzyć formantu jako okna podrzędnego każdego okna.  
  
-   Ładowanie klip AVI do formantu animacji, wywołując [Otwórz](../mfc/reference/canimatectrl-class.md#open) funkcję elementu członkowskiego. W przypadku formantu animacji w oknie dialogowym, dobrym miejscem, w tym celu jest klasy okien dialogowych [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji.  
  
-   Odtwarzania przez wywołanie metody [odtwarzanie](../mfc/reference/canimatectrl-class.md#play) funkcję elementu członkowskiego. W przypadku formantu animacji w oknie dialogowym, dobrym miejscem, w tym celu jest klasy okien dialogowych `OnInitDialog` funkcji. Wywoływanie `Play` nie jest konieczne, jeśli zestaw stylów ACS_AUTOPLAY formantu animacji.  
  
-   Jeśli chcesz wyświetlić części klipu lub go odtworzyć klatka, użyj `Seek` funkcję elementu członkowskiego. Aby zatrzymać klip odtwarzany, użyj `Stop` funkcję elementu członkowskiego.  
  
-   Jeśli nie ma do zniszczenia kontrolki od razu, usunąć klip z pamięci przez wywołanie metody `Close` funkcję elementu członkowskiego.  
  
-   W przypadku formantu animacji w oknie dialogowym go i `CAnimateCtrl` obiektu zostaną automatycznie usunięte. Jeśli nie, musisz upewnij się, że oba formantu i `CAnimateCtrl` obiektu prawidłowo zostaną zniszczone. Likwidowanie formantu automatycznie zamyka klip AVI.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

