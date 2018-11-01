---
title: Błąd PRJ0024 kompilacji projektu
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: 645b898bdffcc6d7b397c25eb3c41cea25cb361f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589647"
---
# <a name="project-build-error-prj0024"></a>Błąd PRJ0024 kompilacji projektu

> Ścieżka Unikodowa '*ścieżki*"nie mogą być przekonwertowana na stronę kodową ANSI użytkownika.

*ścieżka* to oryginalna wersja Unicode ciąg ścieżki. Ten błąd może wystąpić w przypadkach, gdy ścieżka Unikodowa, niemożliwymi bezpośrednio do ANSI dla bieżącej strony kodowej systemu.

Ten błąd może wystąpić, jeśli pracujesz z projektem, który został opracowany w systemie przy użyciu strony kodowej, który nie znajduje się na tym komputerze.

Rozwiązanie dotyczące tego błędu jest zaktualizować ścieżkę, aby użyć tekstu ANSI lub Zainstaluj stronę kodową na swoim komputerze i jest ustawiony jako domyślny system.