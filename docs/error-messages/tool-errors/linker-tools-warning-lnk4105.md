---
title: Ostrzeżenie LNK4105 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 880c8519a530f492d0c322575a1386af8a7d0187
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310932"
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