---
title: Paski dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed0e773dda8a1a31a028a0b6c5e349b2e3655982
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401501"
---
# <a name="dialog-bars"></a>Paski dialogowe

Pasek dialogowy jest pasek narzędzi, rodzajem z [pasek sterowania](../mfc/control-bars.md) , mogą zawierać dowolny rodzaj kontrolki. Ponieważ ma ona charakterystykę niemodalnego okna dialogowego, [CDialogBar](../mfc/reference/cdialogbar-class.md) obiekt zapewnia bardziej zaawansowanych narzędzi.

Istnieje kilka podstawowych różnic między paska narzędzi i `CDialogBar` obiektu. A `CDialogBar` obiekt zostanie utworzony z szablonu okna dialogowego zasobu, który można utworzyć za pomocą edytora okien dialogowych Visual C++ i które mogą zawierać dowolny rodzaj kontrolki Windows. Użytkownik może z kontrolki karty do kontroli. I możesz określić style wyrównania wyrównać paska dialogowego z dowolnej części nadrzędnej ramki okna, a nawet pozostawić na miejscu, jeśli element nadrzędny jest rozmiar. Na poniższej ilustracji przedstawiono paska dialogowego z wielu kontrolek.

![Pasek dialogowy VC](../mfc/media/vc378t1.gif "vc378t1") paska dialogowego

Pod innymi względami pracę `CDialogBar` obiekt jest tak jak w przypadku niemodalnego okna dialogowego. Edytor okien dialogowych umożliwia projektowanie i tworzenie zasobu okna dialogowego.

Jest jedną z zalet programu paski dialogowe, mogą zawierać formanty innych niż przycisków.

Mimo że jest to normalne do wyprowadzenia własne klasy okien dialogowych z `CDialog`, nie zazwyczaj pochodną klasy dla paska dialogowego. Paski dialogowe są rozszerzenia do głównego okna i komunikaty paska dialogowego powiadamianie kontrolki, takie jak **BN_CLICKED** lub **EN_CHANGE**, będą wysyłane do nadrzędnego okna dialogowego paska głównego okna.

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Próbki](../visual-cpp-samples.md)

