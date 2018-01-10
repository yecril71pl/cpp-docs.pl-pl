---
title: "Komunikaty o błędach ML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.errors.ml
dev_langs: C++
helpviewer_keywords: MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fa5933c9c676b76ebe342ffa848e7b40926da08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ml-error-messages"></a>Komunikaty o błędach ML
Komunikaty o błędach wygenerowanych przez składniki MASM dzielą się na trzy kategorie:  
  
-   **Błędy krytyczne.** Oznaczają one poważny problem, który uniemożliwia wykonanie jej normalny proces narzędzie.  
  
-   **Błędy niekrytyczne.** Narzędzie może zakończenia procesu. Jeśli tak, jego wynik nie jest może być jednego z nich.  
  
-   **Ostrzeżenia.** Te komunikaty wskazują warunki, które mogą uniemożliwić uzyskiwania żądanych wyników.  
  
 Wszystkie komunikaty o błędach mieć następującą formę:  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 gdzie:  
  
 `Utility`  
 Program, który wysłał komunikat o błędzie.  
  
 *Nazwa pliku*  
 Plik, który zawiera warunek generowanie błędu.  
  
 *Wiersz*  
 Wiersz przybliżoną, gdy istnieje warunek błędu.  
  
 *Error_type*  
 Krytyczny błąd, błąd lub ostrzeżenie.  
  
 *Kod*  
 Unikatowy 5 - lub 6-cyfrowy kod błędu.  
  
 `Message_text`  
 Krótko- i ogólny opis warunku błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft Macro Assembler — dokumentacja](../../assembler/masm/microsoft-macro-assembler-reference.md)