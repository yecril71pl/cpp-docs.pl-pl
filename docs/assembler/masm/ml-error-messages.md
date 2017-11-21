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
ms.openlocfilehash: 8ba8cafde365ceb31af144ac40af1daa1e1f90b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Microsoft Macro Assembler — odwołanie](../../assembler/masm/microsoft-macro-assembler-reference.md)