---
title: Komunikaty o błędach ML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fbc2ae6388ad11a411850d03de421d2f6820fc03
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057100"
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
  
 *wiersz*  
 Wiersz przybliżoną, gdy istnieje warunek błędu.  
  
 *Error_type*  
 Krytyczny błąd, błąd lub ostrzeżenie.  
  
 *Kod*  
 Unikatowy 5 - lub 6-cyfrowy kod błędu.  
  
 `Message_text`  
 Krótko- i ogólny opis warunku błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft Macro Assembler — dokumentacja](../../assembler/masm/microsoft-macro-assembler-reference.md)