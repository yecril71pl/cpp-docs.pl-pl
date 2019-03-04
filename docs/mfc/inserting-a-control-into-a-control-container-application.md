---
title: 'Kontenery kontrolek ActiveX: Wstawianie kontrolki do aplikacji kontenera kontrolek'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: 5f2b964d337ee882bff8acd904ad2fcf64879f88
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283634"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Kontenery kontrolek ActiveX: Wstawianie kontrolki do aplikacji kontenera kontrolek

Zanim z aplikacji kontenera kontrolek ActiveX, uzyskujesz dostęp do formantu ActiveX, należy dodać formant ActiveX do aplikacji kontenera przy użyciu [Wstawianie formantu ActiveX](../windows/insert-activex-control-dialog-box.md) okno dialogowe.

Aby dodać formant ActiveX do projektu kontener formantu ActiveX, zobacz [wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Po dodaniu kontrolki, należy dodać zmienną członkowską (o typie formantu ActiveX) do klasy okno dialogowe. Aby uzyskać więcej informacji na temat tej procedury, zobacz [dodawania zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md).

Po dodaniu zmiennej składowej klasy, określane jako klasę otoki jest automatycznie generowane i dodawane do projektu. Ta klasa jest używana jako interfejs między kontener formantu i osadzonego formantu.

## <a name="see-also"></a>Zobacz także

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
