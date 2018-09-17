---
title: -QIfist (pomijanie _ftol) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /qifist
dev_langs:
- C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d7c4bacec9da22e8c8ba9fd6330637a1fb25893
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714743"
---
# <a name="qifist-suppress-ftol"></a>/QIfist (Pomijanie _ftol)

Przestarzałe. Pomija wywołanie funkcji pomocnika `_ftol` podczas konwersji z typu zmiennoprzecinkowego na typ całkowity jest wymagany.

## <a name="syntax"></a>Składnia

```
/QIfist
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  **/ QIfist** jest dostępna tylko w kompilatorze dla x86; ta opcja kompilatora nie jest dostępna w kompilatorach przeznaczonych dla x64 orARM.

Oprócz konwersji z typu zmiennoprzecinkowego na typ całkowity `_ftol` funkcja zapewnia trybu zaokrąglania jednostki zmiennoprzecinkowej (FPU) kierunku zera (obcięciu), ustawiając bity 10 i 11 słowa sterującego. Gwarantuje to, że konwersja z typu zmiennoprzecinkowego na typ całkowitoliczbowy odbywa się zgodnie z opisem w standardu ANSI C (odrzucone ułamkową część liczby). Korzystając z **/QIfist**, gwarancja nie ma już zastosowania. Trybu zaokrąglania będzie jedną z czterech, zgodnie z opisem w instrukcje Intel:

- Zaokrąglona do najbliższej (parzystą liczbą Jeśli jednakowo odległych)

- Zaokrąglij w kierunku minus nieskończoność

- Zaokrąglij w kierunku Plus nieskończoność

- Zaokrąglij w kierunku zera

Możesz użyć [_control87 —, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) funkcji C Run-Time, aby zmodyfikować zachowanie zaokrąglania FPU. Domyślny tryb FPU zaokrąglania jest "Round do najbliższego." Za pomocą **/QIfist** może poprawić wydajność aplikacji, ale nie bez ryzyka. Należy dokładnie przetestować fragmenty kodu, które są wrażliwe na trybów zaokrąglania, zanim opierająca się na kod skompilowany przy użyciu **/QIfist** w środowiskach produkcyjnych.

[/ arch (x86)](../../build/reference/arch-x86.md) i **/QIfist** nie można używać w tym samym compiland —.

> [!NOTE]
>  **/ QIfist** jest obowiązuje domyślnie ponieważ zaokrąglanie bits także wpływ zmiennoprzecinkowa do zmiennoprzecinkowych wskazuje zaokrąglania (która pojawia się po obliczeniu co), dzięki czemu podczas ustawiania flagi zaokrąglania stylu języka C (w kierunku zera) z liczby zmiennoprzecinkowej obliczenia może się różnić. **/ QIfist** nie powinny być używane, jeśli kod jest zależna od oczekiwanego zachowania obcinanie część ułamkową liczby zmiennoprzecinkowej. Jeśli wiesz, nie używaj **/QIfist**.

**/QIfist** opcja jest przestarzały, począwszy od programu Visual Studio 2005. Kompilator wprowadził istotne ulepszenia float szybkości konwersji int. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)