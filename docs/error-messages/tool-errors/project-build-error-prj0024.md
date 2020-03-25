---
title: Błąd PRJ0024 kompilacji projektu
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: bcfdcce54618acca0e22daa54e95083cf3ee9d50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192617"
---
# <a name="project-build-error-prj0024"></a>Błąd PRJ0024 kompilacji projektu

> Nie można przetłumaczyć ścieżki Unicode "*Path*" na stronę kodową ANSI użytkownika.

*ścieżka* to oryginalna wersja Unicode ciągu ścieżki. Ten błąd może wystąpić w przypadkach, gdy istnieje ścieżka Unicode, której nie można bezpośrednio przetłumaczyć na ANSI na bieżącą stronę kodową systemu.

Ten błąd może wystąpić, jeśli pracujesz z projektem, który został opracowany w systemie przy użyciu strony kodowej, która nie znajduje się na komputerze.

Rozwiązaniem tego błędu jest zaktualizowanie ścieżki w celu użycia tekstu ANSI lub zainstalowanie strony kodowej na komputerze i ustawienie jej jako wartości domyślnej systemu.
