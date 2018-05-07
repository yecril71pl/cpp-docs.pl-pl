---
title: Wyodrębnij funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fc4d48c972bca9352f326085574e4cf4df83aea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="extract-function"></a>Wyodrębnij — funkcja
**Co:** pozwala włączyć do odrębnej funkcji fragment kodu.

**Kiedy:** masz fragment kodu istniejących w niektórych funkcji, który musi być wywoływana z inną funkcję.  

**Dlaczego:** użytkownik może kopiowanie/wklejanie kodu, ale który może doprowadzić do duplikacji.  Lepszym rozwiązaniem jest Refaktoryzuj ten fragment do jego własnej funkcji, która może być za darmo wywoływany przez innych funkcji.

**Jak:**

1. Wyróżnij kodu, który zostanie wyodrębniony:

   ![Wyróżniony kod](images/extractfunction_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + M**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **wyodrębnić funkcji (eksperymentalne)** z menu kontekstowego.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > wyodrębnić funkcji (funkcja eksperymentalna)**.
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **wyodrębnić funkcji (eksperymentalne)** z menu kontekstowego.
     * Kliknij przycisk ![żarówka](images/bulb.png) ikonę, która pojawia się w lewym marginesie i wybierz **wyodrębnić funkcji (eksperymentalne)** z menu kontekstowego.

1. W **wyodrębnić funkcji/metodzie (eksperymentalne)** , wprowadź nazwę nowej funkcji, gdzie należy wybrać kod do umieszczenia, a kliknij **OK** przycisku.  

   ![Wyodrębnij funkcja — funkcja](images/extractfunction_dialog.png)

1. Zostanie utworzona nowa funkcja w przypadku, gdy wybrano prototypu funkcji w odpowiedni plik nagłówka i oryginalny kod zostanie zmieniona do wywołania tej funkcji.

   ![Wyodrębnij wyniku — funkcja](images/extractfunction_result.png)