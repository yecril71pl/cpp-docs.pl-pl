---
title: Lokalizacja przenoszenia definicji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44211105429e33c136999a7877ac6ee42af29f17
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33327843"
---
# <a name="move-definition-location"></a>Lokalizacja przenoszenia definicji
**Co:** pozwala natychmiast przesunąć definicji funkcji do odpowiedniego pliku nagłówka.

**Kiedy:** ma funkcję, która ma zostać przeniesiona do pliku nagłówka.  

**Dlaczego:** można ręcznie przenieść funkcji, ale ta funkcja zostanie przesunięty w jego automatycznie, tworzenie pliku nagłówka, jeśli jest to wymagane.

**Jak:**

1. Umieść kursor tekstu lub mysz za pośrednictwem funkcji, dla którego ma zostać przeniesiona.

   ![Wyróżniony kod](images/movedefinition_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **lokalizacja przenoszenia definicji** z menu kontekstowego.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **lokalizacja przenoszenia definicji** z menu kontekstowego.

1. Funkcja zostaną przeniesione do odpowiedniego pliku nagłówka zostaną wyświetlone w menu podręczne okno podglądu.  Jeśli plik nagłówka nie istnieje, jej zostanie również utworzona i umieszczane w projekcie.

   ![Tworzenia deklaracji / definicji wyniku](images/movedefinition_result.png)
