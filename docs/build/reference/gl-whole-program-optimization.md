---
title: -GL (optymalizacja całego programu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97561a63a21550cc06f29a95f6ddf05687758b83
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723661"
---
# <a name="gl-whole-program-optimization"></a>/GL (Optymalizacja całego programu)

Włącza optymalizację całego programu.

## <a name="syntax"></a>Składnia

```
/GL[-]
```

## <a name="remarks"></a>Uwagi

Optymalizacja całego programu umożliwia kompilatorowi wykonanie optymalizacje z informacjami na wszystkich modułach w programie. Bez optymalizacji całego programu optymalizacje są wykonywane na podstawie modułu (compiland —).

Optymalizacja całego programu jest domyślnie wyłączona i musi być jawnie włączone. Jednak użytkownik może również jawnie wyłączyć za pomocą **/GL-**.

Informacje dotyczące wszystkich modułów kompilator wykonywać następujące czynności:

- Optymalizuj korzystanie z rejestrów w granicach funkcji.

- Czy lepiej sobie radzą śledzenia zmiany danych globalnych, dzięki czemu zmniejszenie liczby obciążeń i magazynów.

- Czy lepiej sobie radzą śledzenia wyłuskania możliwe zbiór elementów zmodyfikowana przez wskaźnik, zmniejszenie liczby obciążeń i magazynów.

- Wbudowanej funkcji w module, nawet wtedy, gdy funkcja jest zdefiniowana w innym module.

pliki .obj utworzone z **/GL** nie będą dostępne do tych narzędzi konsolidatora jako [EDITBIN](../../build/reference/editbin-reference.md) i [DUMPBIN](../../build/reference/dumpbin-reference.md).

Jeśli kompilujesz program jest połączony z **/GL** i [/c](../../build/reference/c-compile-without-linking.md), opcję/LTCG — opcja konsolidatora należy używać do tworzenia pliku wyjściowego.

[/ Zi](../../build/reference/z7-zi-zi-debug-information-format.md) nie można używać z **/GL**

Format plików utworzone z **/GL** w bieżącej wersji mogą nie być odczytywane w kolejnych wersjach Visual C++. Nie powinien wysłać plik .lib, składająca się z plików .obj, które zostały utworzone z **/GL** , chyba że chcesz wysłać kopii pliku .lib dla wszystkich wersji programu Visual C++ można oczekiwać od użytkowników, do użycia, teraz i w przyszłości.

pliki .obj utworzone z **/GL** i prekompilowane pliki nagłówka nie należy używać do tworzenia pliku .lib, chyba że zostanie połączony plik .lib na tym samym komputerze, który **/GL** pliku .obj. Informacje z pliku .obj prekompilowany plik nagłówkowy będzie potrzebna w czasie połączenia.

Aby uzyskać więcej informacji na ograniczenia optymalizacja całego programu i udostępniono optymalizacje, zobacz [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  **/GL** również sprawia, że Optymalizacja z przewodnikiem dostępne; zobacz opcję/LTCG.  Podczas kompilowania dla profilowana Optymalizacja i jeśli chcesz, aby funkcja porządkowania z Twojej optymalizacje profilowe z przewodnikiem, należy skompilować z [/Gy](../../build/reference/gy-enable-function-level-linking.md) lub opcję kompilatora, która oznacza /Gy.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Zobacz [opcję/LTCG (Generowanie kodu Link-time)](../../build/reference/ltcg-link-time-code-generation.md) instrukcje dotyczące sposobu określania **/GL** w środowisku programistycznym.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)