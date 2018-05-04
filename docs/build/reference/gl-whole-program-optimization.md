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
ms.openlocfilehash: ce972b6e7254ad7454f8e8799283588f0fdd5270
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="gl-whole-program-optimization"></a>/GL (Optymalizacja całego programu)
Włącza optymalizację całego programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/GL[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 Optymalizacja całego programu umożliwia kompilatorowi przeprowadzić optymalizacji informacje dla wszystkich modułów w programie. Bez optymalizacji całego programu optymalizacje są wykonywane na poszczególnych modułu (compiland).  
  
 Optymalizacja całego programu jest domyślnie wyłączona i musi być jawnie włączone. Jednak użytkownik może również jawnie wyłączyć z **/GL-**.  
  
 Informacje o wszystkich modułów kompilator może:  
  
-   Optymalizuj użycie rejestrów poza granicami funkcji.  
  
-   Czy lepiej zadania śledzenia zmiany danych globalnych, dzięki czemu zmniejszenie liczby obciążenia sieci i magazynów.  
  
-   Czy lepiej zadania śledzenia wyłuskania zestaw możliwych elementy zmodyfikowane przez wskaźnik, zmniejszenie liczby obciążenia sieci i magazynów.  
  
-   Wbudowanej funkcji w module nawet wtedy, gdy funkcja jest zdefiniowana w innym module.  
  
 pliki .obj utworzonej z **/GL** nie będą dostępne do takich narzędzi konsolidatora jako [polecenia EDITBIN](../../build/reference/editbin-reference.md) i [DUMPBIN](../../build/reference/dumpbin-reference.md).  
  
 Jeśli kompilacja programu z **/GL** i [/c](../../build/reference/c-compile-without-linking.md), należy użyć opcję/LTCG — opcja konsolidatora można utworzyć pliku wyjściowego.  
  
 [/ Zi](../../build/reference/z7-zi-zi-debug-information-format.md) nie można używać z **/GL**  
  
 Format plików utworzony z **/GL** w bieżącej wersji może nie być odczytywane w kolejnych wersjach programu Visual C++. Nie powinien dostarczać pliku lib złożoną z plików .obj, które zostały utworzone z **/GL** , chyba że chcesz wysłać kopii pliku lib dla wszystkich wersji programu Visual C++ spodziewasz się użytkowników, aby używali obecnie i w przyszłości.  
  
 pliki .obj utworzonej z **/GL** i prekompilowane pliki nagłówka nie należy używać do tworzenia pliku .lib, chyba że plików lib zostaną połączone na tym samym komputerze, wytworzonego **/GL** pliku obj. Informacje z pliku obj. prekompilowany plik nagłówka będą potrzebne w czasie łącza.  
  
 Aby uzyskać więcej informacji na ograniczenia optymalizacja całego programu i dostępne z optymalizacji, zobacz [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  **/GL** również sprawia, że profil z przewodnikiem optymalizacji dostępne; zobacz opcję/LTCG.  W przypadku kompilowania kodu dla profilowanej optymalizacji i jeśli funkcja porządkowania z Twojej optymalizacje profilowe z przewodnikiem, należy skompilować z [/Gy](../../build/reference/gy-enable-function-level-linking.md) lub opcję kompilatora, która oznacza /Gy.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Zobacz [opcję/LTCG (Generowanie kodu w czasie Link)](../../build/reference/ltcg-link-time-code-generation.md) informacji dotyczących sposobu określania **/GL** w środowisku programistycznym.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)