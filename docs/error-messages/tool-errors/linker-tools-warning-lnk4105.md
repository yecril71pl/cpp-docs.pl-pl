---
title: Ostrzeżenie LNK4105 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4411421741cf8bf7c714a6322d58bd177e7e7270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024986"
---
# <a name="linker-tools-warning-lnk4105"></a>Ostrzeżenie LNK4105 narzędzi konsolidatora

Brak argumentu określony za pomocą opcji "opcji"; Zignorowano opcję

Ostrzeżenie to pojawia się tylko po [/libpath —](../../build/reference/libpath-additional-libpath.md) ustawiono opcję. Jeśli nie określono katalogu przy użyciu tej opcji, konsolidator ignoruje opcję i generuje ten komunikat ostrzegawczy.

Jeśli jest konieczne zastąpienie istniejących ustawień biblioteki środowiska, należy usunąć/libpath — opcja z wiersza polecenia konsolidatora. Jeśli chcesz użyć ścieżki alternatywnej wyszukiwania dla bibliotek, należy określić ścieżkę alternatywną, zgodnie z opcją/libpath —.

## <a name="example"></a>Przykład

```
link /libpath:c:\filepath\lib bar.obj
```

będzie kierować konsolidator, aby wyszukać wymaganych bibliotek w `c:\filepath\lib` przed wyszukiwaniem w lokalizacji domyślnej.