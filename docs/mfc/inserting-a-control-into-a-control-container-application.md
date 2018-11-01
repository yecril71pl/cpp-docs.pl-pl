---
title: 'Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: 2ca503119df955e8b76f6f8c131421f3e2d85652
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541378"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek

Zanim z aplikacji kontenera kontrolek ActiveX, uzyskujesz dostęp do formantu ActiveX, należy dodać formant ActiveX do aplikacji kontenera przy użyciu [Wstawianie formantu ActiveX](../windows/insert-activex-control-dialog-box.md) okno dialogowe.

Aby dodać formant ActiveX do projektu kontener formantu ActiveX, zobacz [wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Po dodaniu kontrolki, należy dodać zmienną członkowską (o typie formantu ActiveX) do klasy okno dialogowe. Aby uzyskać więcej informacji na temat tej procedury, zobacz [dodawania zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md).

Po dodaniu zmiennej składowej klasy, określane jako klasę otoki jest automatycznie generowane i dodawane do projektu. Ta klasa jest używana jako interfejs między kontener formantu i osadzonego formantu.

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

