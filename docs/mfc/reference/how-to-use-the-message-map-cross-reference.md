---
title: 'Porady: używanie odsyłacza mapy komunikatów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fccdf620cbdaeffc7fb201e014edc4c7c1dddc83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434456"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Porady: używanie odsyłacza mapy komunikatów

We wpisach etykietą \<memberFxn >, napisać własną funkcję członkowską pochodnej [CWnd](../../mfc/reference/cwnd-class.md) klasy. Nadaj funkcji dowolną nazwę, jaką chcesz. Inne funkcje, takie jak `OnActivate`, funkcji składowej klasy `CWnd`. Jeśli wywołany, przekazują komunikat, który ma `DefWindowProc` funkcji Windows. Przetwarzanie komunikatów powiadomień w Windows, Zastąp odpowiednie `CWnd` funkcja w klasie pochodnej. Funkcja powinna wywołać zastąpiona funkcja w klasie bazowej umożliwiające klasy bazowej, a Windows odpowiedzieć na wiadomość.

We wszystkich przypadkach należy umieścić prototypu funkcji w `CWnd`-klasy pochodnej, nagłówek i kod wpisu mapy wiadomości, jak pokazano.

Są używane następujące terminy:

|Termin|Definicja|
|----------|----------------|
|identyfikator|Identyfikator elementu menu zdefiniowanych przez użytkownika (wm_command — komunikaty) lub identyfikator formantu (komunikaty powiadomień okna podrzędnego).|
|"message" i "wNotifyCode"|Windows komunikatu identyfikatorów, zgodnie z definicją w systemie WINDOWS. H.|
|nMessageVariable|Nazwa zmiennej, która zawiera wartość zwrotną z elementu `RegisterWindowMessage` funkcji Windows.|

## <a name="see-also"></a>Zobacz też

[Mapy komunikatów](../../mfc/reference/message-maps-mfc.md)

