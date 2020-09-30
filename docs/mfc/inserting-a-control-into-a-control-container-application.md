---
title: 'Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: e8426fd7a420ef06650930e547d06c78cc094975
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503105"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek

Aby można było uzyskać dostęp do kontrolki ActiveX z aplikacji kontenera kontrolek ActiveX, należy dodać formant ActiveX do aplikacji kontenera za pomocą okna dialogowego [Wstawianie kontrolki ActiveX](../windows/adding-editing-or-deleting-controls.md) .

Aby dodać kontrolkę ActiveX do projektu kontenera kontrolek ActiveX, zobacz [Wyświetlanie i Dodawanie kontrolek ActiveX do okna dialogowego](../windows/adding-editing-or-deleting-controls.md).

Po dodaniu kontrolki należy dodać zmienną członkowską (typ kontrolki ActiveX) do klasy okna dialogowego. Aby uzyskać więcej informacji na temat tej procedury, zobacz [Dodawanie zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md).

Po dodaniu zmiennej składowej Klasa, nazywana klasą otoki, jest automatycznie generowana i dodawana do projektu. Ta klasa jest używana jako interfejs między kontenerem formantów i osadzonym formantem.

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](activex-control-containers.md)
