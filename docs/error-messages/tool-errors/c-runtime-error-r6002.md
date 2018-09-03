---
title: C błąd w czasie wykonywania R6002 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50a970ecea4fdd7d397c09672b0548be947cab1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298567"
---
# <a name="c-runtime-error-r6002"></a>C R6002 błąd w czasie wykonywania
Obsługa liczb zmiennoprzecinkowych nie załadowany  
  
 Niezbędne biblioteki liczb zmiennoprzecinkowych nie został połączony.  
  
> [!NOTE]
>  Jeśli wystąpią ten komunikat o błędzie podczas uruchamiania aplikacji aplikacji został wyłączony, ponieważ ma ona wystąpił problem wewnętrzny. Istnieje kilka możliwych przyczyn tego błędu, ale często spowodowane przez usterką w kodzie aplikacji lub przy próbie uruchomienia aplikacji, który nie został utworzony dla procesora komputera.  
>   
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:  
>   
>  -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony **Panelu sterowania** do naprawy lub ponownej instalacji programu.  
> -   Sprawdź **usługi Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.  
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.  
  
 **Informacje dla programistów**  
  
 Ten błąd może wystąpić w aplikacji, gdy biblioteka liczb zmiennoprzecinkowych nie został połączony. Sprawdź, czy jeden z tych przyczyn:  
  
-   Ciąg formatu w celu `printf_s` lub `scanf_s` funkcja zawiera specyfikację formatu liczb zmiennoprzecinkowych i program nie zawiera żadnych wartości zmiennoprzecinkowych lub zmienne. Aby rozwiązać ten problem, umożliwia zgodne ze specyfikacją formatu liczb zmiennoprzecinkowych argumentu zmiennoprzecinkowego lub wykonać przypisania liczb zmiennoprzecinkowych w innym miejscu w programie. Powoduje to, że Obsługa liczb zmiennoprzecinkowych do załadowania.  
  
-   Kompilator minimalizuje rozmiar programu ładując Obsługa liczb zmiennoprzecinkowych tylko wtedy, gdy jest to konieczne. Kompilator nie może wykryć operacji zmiennoprzecinkowych lub specyfikacji formatu liczb zmiennoprzecinkowych w ciągach formatu, więc nie zostanie załadowany niezbędne procedury liczb zmiennoprzecinkowych. Aby rozwiązać ten problem, użyj specyfikacji formatu liczb zmiennoprzecinkowych i podać argument zmiennoprzecinkowy lub wykonać przypisania liczb zmiennoprzecinkowych w innym miejscu w programie. Powoduje to, że Obsługa liczb zmiennoprzecinkowych do załadowania.  
  
-   W programie dla wielu języków biblioteki C przed biblioteki FORTRAN podczas określono program był połączony. Połącz ponownie, a następnie określ biblioteki C ostatnio.