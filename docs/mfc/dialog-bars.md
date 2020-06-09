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
ms.openlocfilehash: 052e0b8a085c052f73d3c6540521f57fdfbb9c51
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624899"
---
# <a name="dialog-bars"></a>Paski dialogowe

Pasek okna dialogowego jest paskiem narzędzi, czyli rodzajem [paska sterowania](control-bars.md) , który może zawierać dowolny rodzaj kontrolki. Ponieważ ma właściwości niemodalnego okna dialogowego, obiekt [CDialogBar](reference/cdialogbar-class.md) zapewnia bardziej wydajny pasek narzędzi.

Istnieje kilka najważniejszych różnic między paskiem narzędzi a `CDialogBar` obiektem. `CDialogBar`Obiekt jest tworzony na podstawie zasobu szablonu okna dialogowego, który można utworzyć za pomocą edytora okna dialogowego Visual C++, który może zawierać dowolny rodzaj formantu systemu Windows. Użytkownik może z kontrolki kontrolować. Można również określić styl wyrównania, aby wyrównać pasek okna dialogowego do dowolnej części okna ramki nadrzędnej, lub nawet pozostawić go w miejscu, jeśli rozmiar elementu nadrzędnego zostanie zmieniony. Na poniższej ilustracji przedstawiono pasek dialogowe z różnymi kontrolkami.

![Pasek dialogowe VC](../mfc/media/vc378t1.gif "Pasek dialogowe VC") <br/>
Pasek okna dialogowego

W innych aspektach praca z `CDialogBar` obiektem jest taka, jak praca z niemodalnym oknem dialogowym. Użyj edytora okien dialogowych, aby zaprojektować i utworzyć zasób okna dialogowego.

Jedną z zalet pasków dialogowych jest to, że mogą one zawierać formanty inne niż przyciski.

Chociaż jest to normalne, aby utworzyć własne klasy okien dialogowych z programu `CDialog` , nie można zazwyczaj utworzyć własnej klasy dla paska dialogowego. Paskiem okien dialogowych są rozszerzenia do okna głównego i wszystkie kontrolki paska dialogowe — komunikaty powiadomień, takie jak **BN_CLICKED** lub **EN_CHANGE**, zostaną wysłane do obiektu nadrzędnego paska dialogowego, okna głównego.

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)<br/>
[Przykład](../overview/visual-cpp-samples.md)
