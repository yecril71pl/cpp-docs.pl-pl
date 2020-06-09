---
title: 'Kontenery formantów ActiveX: wyświetlanie i modyfikowanie właściwości formantu'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: b0ca43f59cf70dea1348f22a08cfb4e89b45c3dd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617358"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Kontenery formantów ActiveX: wyświetlanie i modyfikowanie właściwości formantu

Po wstawieniu kontrolki ActiveX do projektu warto wyświetlić i zmienić właściwości obsługiwane przez kontrolkę ActiveX. W tym artykule omówiono sposób używania Edytora zasobów Visual C++ w tym celu.

Jeśli aplikacja kontenera kontrolki ActiveX używa formantów osadzonych, można wyświetlać i modyfikować właściwości kontrolki w edytorze zasobów. Można również użyć edytora zasobów do ustawiania wartości właściwości w czasie projektowania. Następnie Edytor zasobów automatycznie zapisuje te wartości w pliku zasobów projektu. Wszystkie wystąpienia kontrolki zostaną następnie zainicjowane do tych wartości właściwości.

W tej procedurze przyjęto założenie, że wstawiono kontrolkę do projektu. Aby uzyskać więcej informacji, zobacz [kontenery kontrolek ActiveX: Wstawianie kontrolki do aplikacji kontenera kontrolek](inserting-a-control-into-a-control-container-application.md).

Pierwszym krokiem wyświetlania właściwości kontrolki jest dodanie wystąpienia kontrolki do szablonu okna dialogowego projektu.

### <a name="to-view-the-properties-of-a-control"></a>Aby wyświetlić właściwości kontrolki

1. W Widok zasobów Otwórz folder **okna dialogowego** .

1. Otwórz główny szablon okna dialogowego.

1. Wstaw kontrolkę ActiveX przy użyciu okna dialogowego **Wstawianie kontrolki ActiveX** . Aby uzyskać więcej informacji, zobacz [Wyświetlanie i Dodawanie kontrolek ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. W oknie dialogowym Wybierz kontrolkę ActiveX.

1. W oknie **Właściwości** kliknij przycisk **Właściwości** .

Za pomocą okna dialogowego **Właściwości** można natychmiast modyfikować i testować nowe właściwości.

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](activex-control-containers.md)
