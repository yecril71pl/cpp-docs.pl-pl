---
title: Drukowanie w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: f275078fbef9026363305bb714da3a2af333c91f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619819"
---
# <a name="printing-in-rich-edit-controls"></a>Drukowanie w formantach edycji wzbogaconej

Możesz powiedzieć formant edycji wzbogaconej ([CRichEditCtrl](reference/cricheditctrl-class.md)) w celu renderowania danych wyjściowych dla określonego urządzenia, na przykład drukarki. Można również określić urządzenie wyjściowe, dla którego jest formatowany tekst kontrolki edycji wzbogaconej.

Aby sformatować część zawartości kontrolki edycji wzbogaconej dla określonego urządzenia, można użyć funkcji składowej [FormatRange](reference/cricheditctrl-class.md#formatrange) . Struktura [FormatRange](/windows/win32/api/richedit/ns-richedit-formatrange) używana z tą funkcją określa zakres tekstu do sformatowania oraz kontekstu urządzenia (DC) dla urządzenia docelowego.

Po sformatowaniu tekstu dla urządzenia wyjściowego można wysłać dane wyjściowe do urządzenia za pomocą funkcji składowej [DisplayBand](reference/cricheditctrl-class.md#displayband) . Wielokrotnie korzystając z `FormatRange` i `DisplayBand` , aplikacja, która drukuje zawartość kontrolki edycji wzbogaconej, może zaimplementować pasmo. (Pasma to podział danych wyjściowych na mniejsze części do celów drukowania).

Można użyć funkcji elementu członkowskiego [SetTargetDevice](reference/cricheditctrl-class.md#settargetdevice) , aby określić urządzenie docelowe, dla którego jest formatowany tekst kontrolki edycji wzbogaconej. Ta funkcja jest przydatna w przypadku ustawienia WYSIWYG (co jest widoczne) formatowania, w którym aplikacja umieszcza tekst przy użyciu domyślnych metryk czcionki drukarki zamiast ekranu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](using-cricheditctrl.md)<br/>
[Formanty](controls-mfc.md)
