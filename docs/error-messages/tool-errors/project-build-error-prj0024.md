---
title: Błąd PRJ0024 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb539a5f1ee5f1aa5f9d828d93fa6d0dc8690c22
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215601"
---
# <a name="project-build-error-prj0024"></a>Błąd PRJ0024 kompilacji projektu

> Ścieżka Unikodowa '*ścieżki*"nie mogą być przekonwertowana na stronę kodową ANSI użytkownika.

*ścieżka* to oryginalna wersja Unicode ciąg ścieżki. Ten błąd może wystąpić w przypadkach, gdy ścieżka Unikodowa, niemożliwymi bezpośrednio do ANSI dla bieżącej strony kodowej systemu.

Ten błąd może wystąpić, jeśli pracujesz z projektem, który został opracowany w systemie przy użyciu strony kodowej, który nie znajduje się na tym komputerze.

Rozwiązanie dotyczące tego błędu jest zaktualizować ścieżkę, aby użyć tekstu ANSI lub Zainstaluj stronę kodową na swoim komputerze i jest ustawiony jako domyślny system.