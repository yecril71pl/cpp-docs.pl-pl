---
title: /GL (Optymalizacja całego programu)
ms.date: 11/04/2016
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 6251209dac74a504bb0635f0c544c39935090a42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292136"
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

pliki .obj utworzone z **/GL** nie będą dostępne do tych narzędzi konsolidatora jako [EDITBIN](editbin-reference.md) i [DUMPBIN](dumpbin-reference.md).

Jeśli kompilujesz program jest połączony z **/GL** i [/c](c-compile-without-linking.md), opcję/LTCG — opcja konsolidatora należy używać do tworzenia pliku wyjściowego.

[/ Zi](z7-zi-zi-debug-information-format.md) nie można używać z **/GL**

Format plików utworzone z **/GL** w bieżącej wersji mogą nie być odczytywane w kolejnych wersjach Visual C++. Nie powinien wysłać plik .lib, składająca się z plików .obj, które zostały utworzone z **/GL** , chyba że chcesz wysłać kopii pliku .lib dla wszystkich wersji programu Visual C++ można oczekiwać od użytkowników, do użycia, teraz i w przyszłości.

pliki .obj utworzone z **/GL** i prekompilowane pliki nagłówka nie należy używać do tworzenia pliku .lib, chyba że zostanie połączony plik .lib na tym samym komputerze, który **/GL** pliku .obj. Informacje z pliku .obj prekompilowany plik nagłówkowy będzie potrzebna w czasie połączenia.

Aby uzyskać więcej informacji na ograniczenia optymalizacja całego programu i udostępniono optymalizacje, zobacz [opcję/LTCG](ltcg-link-time-code-generation.md).  **/GL** również sprawia, że Optymalizacja z przewodnikiem dostępne; zobacz opcję/LTCG.  Podczas kompilowania dla profilowana Optymalizacja i jeśli chcesz, aby funkcja porządkowania z Twojej optymalizacje profilowe z przewodnikiem, należy skompilować z [/Gy](gy-enable-function-level-linking.md) lub opcję kompilatora, która oznacza /Gy.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Zobacz [opcję/LTCG (Generowanie kodu Link-time)](ltcg-link-time-code-generation.md) instrukcje dotyczące sposobu określania **/GL** w środowisku programistycznym.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
