---
title: -GT (Obsługa włókien magazynu wątków lokalnych) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
dev_langs:
- C++
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eeec9ddce36777fc6fcb15b30a864f1c04a7b09b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700844"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (Obsługa bezpieczeństwa włókien magazynu wątków lokalnych)

Obsługuje bezpieczeństwo włókien dla danych przydzielonych przy użyciu statycznego magazynu wątków lokalnych, oznacza to, że dane przydzielonymi `__declspec(thread)`.

## <a name="syntax"></a>Składnia

```
/GT
```

## <a name="remarks"></a>Uwagi

Dane są deklarowane przy użyciu `__declspec(thread)` jest przywoływane za pośrednictwem tablicy lokalny magazyn wątków (TLS). Tablica TLS to tablicę adresów, które system przechowuje dla każdego wątku. Każdy adres w tej tablicy zawiera lokalizację magazynu wątków lokalnych danych.

Fiber jest obiektem uproszczone, który składa się ze stosu i kontekst rejestru i mogą być planowane w różnych wątkach. Fiber można uruchamiać na żadnym z wątków. Ponieważ włókna mogą uzyskać wymieniane i ponownie uruchomić później w innym wątku, adres tablicy TLS nie musi być buforowane lub optymalizowane jako wspólnych podwyrażeń przez wywołanie funkcji (zobacz [/Og (optymalizacje globalne)](../../build/reference/og-global-optimizations.md) opcja dla szczegółowe informacje). **/GT** zapobiega takich optymalizacji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **optymalizacji** stronę właściwości.

1. Modyfikowanie **Włącz optymalizacje bezpieczne dla włókna** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)