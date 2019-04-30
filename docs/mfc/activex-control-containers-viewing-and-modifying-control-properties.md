---
title: 'Kontenery kontrolek ActiveX: Wyświetlanie i modyfikowanie właściwości kontrolki'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: 0a03acfd880bcf63017eec9796315b98e5d5f4d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394887"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Kontenery kontrolek ActiveX: Wyświetlanie i modyfikowanie właściwości kontrolki

Po wstawieniu kontrolki ActiveX do projektu jest przydatny do wyświetlania i zmieniania właściwości jest obsługiwana przez kontrolkę ActiveX. W tym artykule omówiono sposób używania edytora zasobów Visual C++, aby to zrobić.

Jeśli Twojej aplikacji kontenera kontrolek ActiveX używa formantów osadzone, należy można wyświetlać i modyfikować właściwości formantu znajduje się w edytorze zasobów. Edytor zasobów umożliwia również do ustawiania wartości właściwości w czasie projektowania. Edytor zasobów następnie automatycznie zapisuje te wartości w pliku zasobów projektu. Dowolne wystąpienie kontrolki będzie miał jego właściwości inicjowana na te wartości.

W tej procedurze założono, że wstawiono formant do projektu. Aby uzyskać informacje, zobacz [kontenery kontrolek ActiveX: Wstawianie kontrolki do aplikacji kontenera kontrolek](../mfc/inserting-a-control-into-a-control-container-application.md).

Pierwszym krokiem podczas przeglądania właściwości formantu jest dodaje wystąpienie formantu do projektu szablonu okna dialogowego.

### <a name="to-view-the-properties-of-a-control"></a>Aby wyświetlić właściwości formantu

1. Otwórz w widoku zasobu **okna dialogowego** folderu.

1. Otwórz szablon okno główne okno dialogowe.

1. Wstaw kontrolkę ActiveX za pomocą **Wstawianie formantu ActiveX** okno dialogowe. Aby uzyskać więcej informacji, zobacz [wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. Zaznacz formant ActiveX w oknie dialogowym.

1. W oknie dialogowym właściwości kliknij **właściwości** przycisku.

Użyj **właściwości** okno dialogowe, aby zmodyfikować i jego natychmiastowe testowanie nowych właściwości.

## <a name="see-also"></a>Zobacz także

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
