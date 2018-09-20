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
ms.openlocfilehash: 3da9684d0218c631cbd745475d48f1cf23addde5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404569"
---
# <a name="using-an-animation-control"></a>Używanie formantu animacji

Typowy kontrolki animacji jest zgodny ze wzorcem poniżej:

- Formant zostanie utworzony. Kontrolka została określona w szablonu okna dialogowego, tworzenie przebiega automatycznie podczas tworzenia okna dialogowego. (Powinien mieć [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) elementu członkowskiego w swojej klasie okna dialogowego, która odnosi się do kontrolki animacji.) Alternatywnie, można użyć [Utwórz](../mfc/reference/canimatectrl-class.md#create) funkcja elementu członkowskiego, aby utworzyć formant jako okna podrzędnego każdego okna.

- Ładowanie klip AVI do formantu animacji, wywołując [Otwórz](../mfc/reference/canimatectrl-class.md#open) funkcja elementu członkowskiego. W przypadku formantu animacji w oknie dialogowym, dobrym miejscem, w tym celu trwa klasy okien dialogowych [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji.

- Odtwórz klip, wywołując [Odtwórz](../mfc/reference/canimatectrl-class.md#play) funkcja elementu członkowskiego. W przypadku formantu animacji w oknie dialogowym, dobrym miejscem, w tym celu trwa klasy okien dialogowych `OnInitDialog` funkcji. Wywoływanie `Play` nie jest konieczne, jeśli zestaw stylów ACS_AUTOPLAY kontrolki animacji.

- Jeśli chcesz wyświetlić części klipu lub odtworzyć go klatka po klatce, użyj `Seek` funkcja elementu członkowskiego. Aby zatrzymać klip odtwarzany, użyj `Stop` funkcja elementu członkowskiego.

- Jeśli nie ma do zniszczenia kontrolki, następnie od razu, Usuń klip z pamięci przez wywołanie metody `Close` funkcja elementu członkowskiego.

- Jeśli kontrolki animacji znajduje się w oknie dialogowym go i `CAnimateCtrl` obiekt jest niszczony automatycznie. Jeśli nie, musisz upewnij się, że obie kontrolki i `CAnimateCtrl` obiektu są poprawnie niszczone. Likwidowanie kontrolki automatycznie zamyka klip AVI.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

