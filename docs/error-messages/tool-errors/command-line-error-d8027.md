---
title: Błąd d8027 wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8234835d3bb0545c8a72bf35cfb55b2e18bc7da2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070382"
---
# <a name="command-line-error-d8027"></a>Błąd D8027 wiersza polecenia

Nie można wykonać operacji "component"

Kompilator nie można uruchomić składnika danego kompilatora lub konsolidatora.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Nie ma wystarczającej ilości pamięci, aby załadować składnika. Jeśli NMAKE wywołana kompilator, należy uruchomić kompilatora poza pliku reguł programu make.

1. Bieżący system operacyjny nie można uruchomić składnika. Upewnij się, że punkty ścieżki plików wykonywalnych odpowiednie dla używanego systemu operacyjnego.

1. Składnik jest uszkodzony. Ponownie skopiować składnika z dysków dystrybucyjnych, za pomocą programu INSTALACYJNEGO.

1. Opcja została określona niepoprawnie. Na przykład:

    ```
    cl /B1 file1.c
    ```