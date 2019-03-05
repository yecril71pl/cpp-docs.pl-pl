---
title: 'Instrukcje: Używanie odsyłacza mapy komunikatów'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
ms.openlocfilehash: 9467dce943da8c5fb447dcd3c83d044218fa183d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326104"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Instrukcje: Używanie odsyłacza mapy komunikatów

We wpisach etykietą \<memberFxn >, napisać własną funkcję członkowską pochodnej [CWnd](../../mfc/reference/cwnd-class.md) klasy. Nadaj funkcji dowolną nazwę, jaką chcesz. Inne funkcje, takie jak `OnActivate`, funkcji składowej klasy `CWnd`. Jeśli wywołany, przekazują komunikat, który ma `DefWindowProc` funkcji Windows. Przetwarzanie komunikatów powiadomień w Windows, Zastąp odpowiednie `CWnd` funkcja w klasie pochodnej. Funkcja powinna wywołać zastąpiona funkcja w klasie bazowej umożliwiające klasy bazowej, a Windows odpowiedzieć na wiadomość.

We wszystkich przypadkach należy umieścić prototypu funkcji w `CWnd`-klasy pochodnej, nagłówek i kod wpisu mapy wiadomości, jak pokazano.

Są używane następujące terminy:

|Termin|Definicja|
|----------|----------------|
|identyfikator|Identyfikator elementu menu zdefiniowanych przez użytkownika (wm_command — komunikaty) lub identyfikator formantu (komunikaty powiadomień okna podrzędnego).|
|"message" i "wNotifyCode"|Windows komunikatu identyfikatorów, zgodnie z definicją w systemie WINDOWS. H.|
|nMessageVariable|Nazwa zmiennej, która zawiera wartość zwrotną z elementu `RegisterWindowMessage` funkcji Windows.|

## <a name="see-also"></a>Zobacz także

[Mapy komunikatów](../../mfc/reference/message-maps-mfc.md)
