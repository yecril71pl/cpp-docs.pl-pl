---
title: "Wydajność bibliotek wielowątkowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 240b2baf8f3d59465b7b8313197086fec4c13285
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multithreaded-libraries-performance"></a>Wydajność bibliotek wielowątkowych
Jednowątkowe CRT nie jest już dostępny. W tym temacie omówiono sposób uzyskać maksymalną wydajność bibliotek wielowątkowych.  
  
## <a name="maximizing-performance"></a>Maksymalizacja wydajności  
 Wydajność bibliotek wielowątkowych została ulepszona i znajduje się w pobliżu wydajność bibliotek wyeliminowana teraz pojedynczym wątku. Dla tych sytuacji, gdy nawet wyższej wydajności jest wymagana, istnieje kilka nowych funkcji.  
  
-   Blokowanie niezależne strumienia umożliwia zablokowanie strumienia, a następnie użyj [_nolock — funkcje](../c-runtime-library/nolock-functions.md) który bezpośredni dostęp strumienia. Dzięki temu można podciągnięta poza krytyczne pętle wykorzystania blokady.  
  
-   Ustawienia regionalne dla każdego wątku zmniejsza koszty dostępu ustawień regionalnych dla scenariuszy wielowątkowe (zobacz [_configthreadlocale —](../c-runtime-library/reference/configthreadlocale.md)).  
  
-   Funkcje zależne od ustawień regionalnych (o nazwach końcówką _l) pobierać ustawienia regionalne jako parametru, usuwanie znacznej koszt (na przykład [printf, _printf_l —, wprintf, _wprintf_l —](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).  
  
-   Optymalizacja pod kątem typowych strony kodowe zmniejszyć koszt wiele operacji krótki.  
  
-   Definiowanie [_crt_disable_perfcrit_locks —](../c-runtime-library/crt-disable-perfcrit-locks.md) wymusza wszystkie operacje We/Wy założono modelu jednowątkowe We/Wy i używania formularzy _nolock — funkcje. Dzięki temu wysokiej I/E — na podstawie jednowątkowe aplikacji, aby uzyskać lepszą wydajność.  
  
-   Narażenia dojścia sterty CRT umożliwia włączenie sterty fragmentacji niski (LFH) systemu Windows, stosu CRT, co może znacznie poprawić wydajność w scenariuszach wysokiej skalowanych.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)