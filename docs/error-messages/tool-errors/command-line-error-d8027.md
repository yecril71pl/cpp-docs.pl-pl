---
title: Błąd D8027 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: d3a7908ec9e7e37d83fd7b928cad2ef256313c40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214184"
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