---
title: Błąd czasu wykonania języka C R6002
ms.date: 11/04/2016
f1_keywords:
- R6002
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
ms.openlocfilehash: b2e617b6f7841f1aa7e6fd2f6962c0e117fab6c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197421"
---
# <a name="c-runtime-error-r6002"></a>Błąd czasu wykonania języka C R6002

Obsługa zmiennoprzecinkowa nie została załadowana

Wymagana biblioteka zmiennoprzecinkowa nie została połączona.

> [!NOTE]
> Jeśli ten komunikat o błędzie wystąpi podczas uruchamiania aplikacji, aplikacja została zamknięta, ponieważ ma problem wewnętrzny. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane usterką w kodzie aplikacji lub przez próbę uruchomienia aplikacji, która nie została skompilowana dla określonego procesora komputera.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby naprawić lub ponownie zainstalować program.
> - Sprawdź, **Windows Update** w **Panelu sterowania** aktualizacje oprogramowania.
> - Sprawdź dostępność zaktualizowanej wersji aplikacji. Jeśli problem będzie nadal występował, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd może wystąpić w aplikacji, gdy biblioteka zmiennoprzecinkowa nie została połączona. Sprawdź jedną z następujących przyczyn:

- Ciąg formatu dla funkcji `printf_s` lub `scanf_s` zawiera specyfikację formatu zmiennoprzecinkowego, a program nie zawierał żadnych wartości zmiennoprzecinkowych ani zmiennych. Aby rozwiązać ten problem, użyj argumentu zmiennoprzecinkowego, aby odpowiadał specyfikacji formatu zmiennoprzecinkowego, lub w innym miejscu w programie wykonać przypisanie zmiennoprzecinkowe. Powoduje to załadowanie obsługi zmiennoprzecinkowej.

- Kompilator minimalizuje rozmiar programu przez załadowanie obsługi zmiennoprzecinkowej tylko wtedy, gdy jest to konieczne. Kompilator nie może wykryć operacji zmiennoprzecinkowych lub specyfikacji formatu zmiennoprzecinkowego w ciągach formatu, dlatego nie ładuje niezbędnych procedur zmiennoprzecinkowych. Aby rozwiązać ten problem, należy użyć specyfikacji formatu zmiennoprzecinkowego i podać argument zmiennoprzecinkowy lub w innym miejscu w programie wykonać przypisanie zmiennoprzecinkowe. Powoduje to załadowanie obsługi zmiennoprzecinkowej.

- W programie w języku mieszanym biblioteka C została określona przed biblioteką Pascal, gdy program został połączony. Połącz ponownie i Określ bibliotekę C jako ostatnią.
