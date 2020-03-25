---
title: Błąd D8027 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: 42341507dfc2d3da02639dd28ab1265783452388
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196888"
---
# <a name="command-line-error-d8027"></a>Błąd D8027 wiersza polecenia

nie można wykonać elementu "Component"

Kompilator nie może uruchomić danego składnika kompilatora lub konsolidatora.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Za mało pamięci, aby załadować składnik. Jeśli NMAKE wywołał kompilator, uruchom kompilator spoza pliku reguł programu make.

1. Bieżący system operacyjny nie może uruchomić składnika. Upewnij się, że ścieżka wskazuje pliki wykonywalne odpowiednie dla danego systemu operacyjnego.

1. Składnik został uszkodzony. Skopiuj składnik z dysków dystrybucji przy użyciu programu instalacyjnego.

1. Opcja została określona nieprawidłowo. Na przykład:

    ```
    cl /B1 file1.c
    ```
