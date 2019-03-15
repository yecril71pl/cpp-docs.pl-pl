---
title: /GA (Optymalizuj dla aplikacji systemu Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
ms.openlocfilehash: a5eb6a10f3c4833ecc3e9d9c8451894788ebd938
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817387"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
