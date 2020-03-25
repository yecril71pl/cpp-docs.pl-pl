---
title: Ostrzeżenie LNK4105 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 655a6dfde77984cd0c941ec0d8abb0c4d099c80f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183296"
---
# <a name="linker-tools-warning-lnk4105"></a>Ostrzeżenie LNK4105 narzędzi konsolidatora

nie określono argumentu z opcją "Option"; Ignorowanie opcji

To ostrzeżenie występuje tylko wtedy, gdy opcja [/LIBPATH](../../build/reference/libpath-additional-libpath.md) jest ustawiona. Jeśli dla tej opcji nie określono katalogu, konsolidator zignoruje opcję i wygeneruje ten komunikat ostrzegawczy.

Jeśli nie musisz przesłonić istniejących ustawień biblioteki środowiskowej, Usuń opcję/LIBPATH z wiersza polecenia konsolidatora. Jeśli chcesz użyć alternatywnej ścieżki wyszukiwania dla bibliotek, określ alternatywną ścieżkę po opcji/LIBPATH.

## <a name="example"></a>Przykład

```
link /libpath:c:\filepath\lib bar.obj
```

nakazuje konsolidatorowi wyszukanie wymaganych bibliotek w `c:\filepath\lib` przed wyszukiwaniem w lokalizacjach domyślnych.
