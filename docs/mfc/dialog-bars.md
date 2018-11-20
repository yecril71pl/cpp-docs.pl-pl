---
title: Paski dialogowe
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: 800cc208df7299cf440508c2705b0b0ddb9ae665
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175356"
---
# <a name="dialog-bars"></a>Paski dialogowe

Pasek dialogowy jest pasek narzędzi, rodzajem z [pasek sterowania](../mfc/control-bars.md) , mogą zawierać dowolny rodzaj kontrolki. Ponieważ ma ona charakterystykę niemodalnego okna dialogowego, [CDialogBar](../mfc/reference/cdialogbar-class.md) obiekt zapewnia bardziej zaawansowanych narzędzi.

Istnieje kilka podstawowych różnic między paska narzędzi i `CDialogBar` obiektu. A `CDialogBar` obiekt zostanie utworzony z szablonu okna dialogowego zasobu, który można utworzyć za pomocą edytora okien dialogowych Visual C++ i które mogą zawierać dowolny rodzaj kontrolki Windows. Użytkownik może z kontrolki karty do kontroli. I możesz określić style wyrównania wyrównać paska dialogowego z dowolnej części nadrzędnej ramki okna, a nawet pozostawić na miejscu, jeśli element nadrzędny jest rozmiar. Na poniższej ilustracji przedstawiono paska dialogowego z wielu kontrolek.

![Pasek dialogowy VC](../mfc/media/vc378t1.gif "Pasek dialogowy VC") <br/>
Paska dialogowego

Pod innymi względami pracę `CDialogBar` obiekt jest tak jak w przypadku niemodalnego okna dialogowego. Edytor okien dialogowych umożliwia projektowanie i tworzenie zasobu okna dialogowego.

Jest jedną z zalet programu paski dialogowe, mogą zawierać formanty innych niż przycisków.

Mimo że jest to normalne do wyprowadzenia własne klasy okien dialogowych z `CDialog`, nie zazwyczaj pochodną klasy dla paska dialogowego. Paski dialogowe są rozszerzenia do głównego okna i komunikaty paska dialogowego powiadamianie kontrolki, takie jak **BN_CLICKED** lub **EN_CHANGE**, będą wysyłane do nadrzędnego okna dialogowego paska głównego okna.

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Próbki](../visual-cpp-samples.md)

