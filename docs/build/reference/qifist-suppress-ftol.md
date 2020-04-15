---
title: /QIfist (Pomijanie _ftol)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 5d6e12a1003ea125b0da4bfef580d8096e97553a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336100"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist (Pomijanie _ftol)

Przestarzałe. Pomija wywołanie funkcji `_ftol` pomocnika, gdy wymagana jest konwersja z typu zmiennoprzecinkowego do typu integralnego.

## <a name="syntax"></a>Składnia

```
/QIfist
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> **/QIfist** jest dostępny tylko w kompilatorze docelowym x86; ta opcja kompilatora nie jest dostępna w kompilatorach docelowych x64 lubARM.

Oprócz konwersji z typu zmiennoprzecinkowego `_ftol` na typ integralny, funkcja zapewnia, że tryb zaokrąglania jednostki zmiennoprzecinowej (FPU) jest skierowany do zera (obcinanie), ustawiając bity 10 i 11 wyrazu sterującego. Gwarantuje to, że konwersja z typu zmiennoprzecinkowego na typ integralny odbywa się zgodnie z opisem standardu ANSI C (ułamkowa część liczby jest odrzucana). W przypadku korzystania **z /QIfist**gwarancja ta nie ma już zastosowania. Tryb zaokrąglania będzie jednym z czterech, jak udokumentowano w podręcznikach referencyjnych firmy Intel:

- Zaokrąglić w kierunku najbliższego (parzystej liczby, jeśli jest w równej odległości)

- Zaokrąglić w kierunku ujemnej nieskończoności

- Zaokrąglić w kierunku dodatniej nieskończoności

- Zaokrąglić w kierunku zera

Można użyć [funkcji _control87, \__controlfp, _control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C run-time, aby zmodyfikować zachowanie zaokrąglania FPU. Domyślnym trybem zaokrąglania FPU jest "Zaokrąglanie w kierunku najbliższego". Za pomocą **/QIfist** może poprawić wydajność aplikacji, ale nie bez ryzyka. Należy dokładnie przetestować części kodu, które są wrażliwe na tryby zaokrąglania przed poleganiem na kod zbudowany z **/QIfist** w środowiskach produkcyjnych.

[/arch (x86)](arch-x86.md) i **/QIfist** nie mogą być używane na tym samym compiland.

> [!NOTE]
> **/QIfist** nie jest domyślnie obowiązywać, ponieważ bity zaokrąglania mają również wpływ na zmiennoprzecinkowy do zaokrąglania zmiennoprzecinkowego (co występuje po każdym obliczeniu), więc po ustawieniu flag dla zaokrąglania w stylu C (w kierunku zera) obliczenia zmiennoprzecinkowy mogą być różne. **/QIfist** nie należy używać, jeśli kod zależy od oczekiwanego zachowania obcinania ułamkowej części liczby zmiennoprzecinowej. Jeśli nie masz pewności, nie używaj **/QIfist**.

**/QIfist** Opcja jest przestarzałe począwszy od programu Visual Studio 2005. Kompilator dokonał znaczących ulepszeń w float do int szybkość konwersji. Aby uzyskać listę przestarzałych opcji kompilatora, zobacz **Przestarzałe i usunięte opcje kompilatora** w [opcjach kompilatora wymienionych według kategorii](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Kliknij folder **C/C++.**

1. Kliknij stronę właściwości **Wiersz polecenia.**

1. Wpisz opcję kompilatora w polu **Opcje dodatkowe.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[/Q Opcje (Operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
