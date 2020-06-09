---
title: Tworzenie zasobu okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
ms.openlocfilehash: efaef11cfdc036a201ced3357ca81b37a5dc29db
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619626"
---
# <a name="creating-the-dialog-resource"></a>Tworzenie zasobu okna dialogowego

Aby zaprojektować okno [dialogowe](dialog-boxes.md) i utworzyć zasób okna dialogowego, należy użyć [edytora okien dialogowych](../windows/dialog-editor.md). W edytorze okien dialogowych można:

- Dostosuj rozmiar i lokalizację, w której będzie wyświetlane okno dialogowe.

- Przeciągnij różne rodzaje kontrolek z palety formantów i upuść je w dowolnym miejscu w oknie dialogowym.

- Umieść kontrolki z przyciskami wyrównania na pasku narzędzi.

- Przetestuj okno dialogowe, symulując wygląd i zachowanie, które będzie miało w programie. W trybie testowym można manipulować kontrolkami okna dialogowego, wpisując tekst w polach tekstowych, klikając przyciski i tak dalej.

Po zakończeniu zasób szablonu okna dialogowego jest przechowywany w pliku skryptu zasobu aplikacji. W razie konieczności można edytować go później. Pełny opis sposobu tworzenia i edytowania zasobów okien dialogowych znajduje się w tematach dotyczących [edytora okien dialogowych](../windows/dialog-editor.md) . Ta technika służy również do tworzenia zasobów szablonu okna dialogowego dla klas [CFormView](reference/cformview-class.md) i [formularzy CRecordView](reference/crecordview-class.md) .

Gdy pojawi się okno dialogowe, należy utworzyć klasę okna dialogowego i zmapować jej komunikaty, jak opisano w temacie [Tworzenie klasy okien dialogowych za pomocą kreatorów kodu](creating-a-dialog-class-with-code-wizards.md).

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](dialog-boxes.md)<br/>
[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
