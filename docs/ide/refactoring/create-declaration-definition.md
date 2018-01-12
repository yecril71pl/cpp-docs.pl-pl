---
title: Tworzenia deklaracji / definicji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 889c8acf5e0ef0ed6a7ac90088a6188658d49d75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="create-declaration--definition"></a>Tworzenia deklaracji / definicji
**Co:** pozwala natychmiast wygenerować deklaracji lub definicji funkcji.

**Kiedy:** ma funkcję, która wymaga delcaration, lub na odwrót.  

**Dlaczego:** można ręcznie utworzyć deklaracji/definicji, ale to zostanie ona utworzona automatycznie, tworzenie pliku nagłówka/kodu, jeśli jest to wymagane.

**Jak:**

1. Umieść kursor tekstu lub mysz za pośrednictwem funkcji, dla której chcesz utworzyć deklaracji lub definicji.

   ![Wyróżniony kod](images/createdefinition_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **tworzenia deklaracji / definicji** z menu kontekstowego.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **tworzenia deklaracji / definicji** z menu kontekstowego.

1. Funkcja deklaracja/definicja zostanie utworzona w pliku źródłowego lub nagłówek, który pojawi się w oknie podręcznym podglądu.  Jeśli plik źródłowy lub nagłówka nie istnieje, jej zostanie również utworzona i umieszczane w projekcie.

   ![Tworzenia deklaracji / definicji wyniku](images/createdefinition_result.png)
