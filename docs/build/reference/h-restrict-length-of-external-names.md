---
title: /H (Ograniczaj długość nazw zewnętrznych)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: 9a8976700cfb0f333c2715c573aa2d239e2a8e3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218991"
---
# <a name="h-restrict-length-of-external-names"></a>/H (Ograniczaj długość nazw zewnętrznych)

Przestarzałe. Ogranicza długość nazw zewnętrznych.

## <a name="syntax"></a>Składnia

> **/H**<em>Numer</em> /h

## <a name="arguments"></a>Argumenty

*liczba*<br/>
Określa maksymalną długość nazw zewnętrznych dozwolonych w programie.

## <a name="remarks"></a>Uwagi

Domyślnie długość nazw zewnętrznych (publicznych) to 2 047 znaków. Dotyczy to programów C i C++. Użycie polecenia **/h** może zmniejszyć maksymalną dozwoloną długość identyfikatorów, a nie zwiększyć. Spacja między argumentami **/h** i *Number* jest opcjonalna.

Jeśli program zawiera nazwy zewnętrzne dłuższe niż *Liczba*, dodatkowe znaki są ignorowane. Jeśli kompilujesz program bez **/h** i jeśli identyfikator zawiera więcej niż 2 047 znaków, kompilator generuje [błąd krytyczny C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).

Limit długości obejmuje dowolny utworzony przez kompilator znak podkreślenia ( **\_** ) lub znak ( **\@** ). Te znaki są częścią identyfikatora i mają znaczącą lokalizację.

- Kompilator dodaje wiodący znak podkreślenia ( **\_** ) do nazw modyfikowanych przez **`__cdecl`** (domyślne) i **`__stdcall`** konwencje wywoływania oraz znak wiodący przy znaku ( **\@** ) do nazw modyfikowanych przez **`__fastcall`** konwencję wywoływania.

- Kompilator dołącza informacje o rozmiarze argumentu do nazw modyfikowanych przez **`__fastcall`** **`__stdcall`** konwencje wywoływania i dodaje informacje o typie do nazw C++.

Może się okazać **przydatne:**

- Podczas tworzenia programów w języku mieszanym lub przenośnym.

- W przypadku korzystania z narzędzi, które nakładają limity dla długości identyfikatorów zewnętrznych.

- Jeśli chcesz ograniczyć ilość miejsca używaną przez symbole w kompilacji debugowania.

W poniższym przykładzie pokazano, jak za pomocą polecenia **/h** można faktycznie wprowadzać błędy, jeśli długość identyfikatora jest zbyt duża:

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

Należy również zachować ostrożność w przypadku używania opcji **/h** z powodu wstępnie zdefiniowanych identyfikatorów kompilatora. Jeśli maksymalna długość identyfikatora jest za mała, niektóre wstępnie zdefiniowane identyfikatory będą nierozwiązane, a także określone wywołania funkcji biblioteki. Na przykład jeśli `printf` Funkcja jest używana i opcja **/H5** jest określona w czasie kompilacji, symbol **_prin** zostanie utworzony w celu odwołania `printf` , a nie zostanie znaleziony w bibliotece.

Użycie **/h** jest niezgodne z [/GL (Optymalizacja całego programu)](gl-whole-program-optimization.md).

Opcja **/h** jest przestarzała od programu Visual Studio 2005; Zwiększono limity maksymalnej długości, a **/h** nie jest już potrzebne. Aby zapoznać się z listą przestarzałych opcji kompilatora, zobacz Opcje kompilatora **przestarzałe i usunięte** w [opcjach kompilatora wymienionych według kategorii](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Wprowadź opcję kompilatora w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
