---
title: -GA (Optymalizuj dla aplikacji Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
dev_langs:
- C++
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ef8aaf1e2b3f1dd75f7ca2669aaf09f3d121a98
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710063"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (Optymalizuj dla aplikacji systemu Windows)

Wyniki w kodzie bardziej wydajne dla pliku .exe do uzyskiwania dostępu do zmiennych lokalny magazyn wątków (TLS).

## <a name="syntax"></a>Składnia

```
/GA
```

## <a name="remarks"></a>Uwagi

**/GA** szybkość dostępu do danych zadeklarowane za pomocą [__declspec(thread)](../../cpp/declspec.md) w programie systemu Windows. Gdy ta opcja jest ustawiona, [__tls_index](/windows/desktop/ProcThread/thread-local-storage) — makro jest domyślnie przyjmuje wartość 0.

Za pomocą **/GA** dla biblioteki DLL może spowodować wygenerowanie złego kodu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)