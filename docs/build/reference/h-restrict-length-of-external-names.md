---
title: -H (Ograniczaj długość nazw zewnętrznych) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /h
dev_langs:
- C++
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d178fcd62c39c65d9f4f8958fde3b178a074671
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895321"
---
# <a name="h-restrict-length-of-external-names"></a>/H (Ograniczaj długość nazw zewnętrznych)

Przestarzałe. Ogranicza długość nazw zewnętrznych.

## <a name="syntax"></a>Składnia

> **/ H**<em>numer</em>

## <a name="arguments"></a>Argumenty

*Numer*  
Określa maksymalną długość nazw zewnętrznych dozwolone w programie.

## <a name="remarks"></a>Uwagi

Domyślnie długość nazw zewnętrznych (publicznych) to 2047 znaków. Ta zasada obowiązuje dla programów C i C++. Za pomocą **/h** można jedynie zmniejszyć maksymalną długość identyfikatorów, powinna ona być. Odstęp między **/h** i *numer* jest opcjonalne.

Jeśli program zawiera nazwy zewnętrzne, które są dłuższe niż *numer*, dodatkowe znaki są ignorowane. Jeśli kompilujesz program bez **/h** i jeśli identyfikator zawiera więcej niż 2047 znaków, kompilator wygeneruje [krytyczny C1064 błąd](../../error-messages/compiler-errors-1/fatal-error-c1064.md).

Limit długości obejmuje wszystkie utworzone przez kompilator wiodącego podkreślenia (**\_**) lub znak (**\@**). Następujące znaki są częścią identyfikatora i znaczące lokalizacji.

- Kompilator sam doda wiodącego podkreślenia (**\_**) do nazw zmodyfikowane przez `__cdecl` (ustawienie domyślne) i `__stdcall` Konwencje wywoływania oraz wiodący znak (**\@** ) do nazw zmodyfikowane przez `__fastcall` konwencji wywoływania.

- Kompilator dołącza informacje o rozmiarze argument nazwy zmodyfikowane przez `__fastcall` i `__stdcall` Konwencje wywoływania i dodaje informacje o typie do nazwy języka C++.

Może się okazać **/h** przydatne:

- Podczas tworzenia programów mieszane pod względem językowym lub przenośnym.

- Kiedy używasz narzędzia, które nakładają ograniczenia dotyczące długość identyfikatorów zewnętrznych.

- Jeśli chcesz ograniczyć ilość miejsca używanego przez symbole w kompilacji debugowania.

W poniższym przykładzie pokazano jak przy użyciu **/h** faktycznie może powodować błędy, jeśli identyfikator długości są ograniczone zbyt dużo:

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

Należy zachować ostrożność przy użyciu **/h** opcji z powodu kompilatora wstępnie zdefiniowane identyfikatory. Jeśli długość maksymalna identyfikator jest za mała, niektórych wstępnie zdefiniowane identyfikatory będzie wywołania funkcji nierozwiązane, a także niektóre biblioteki. Na przykład jeśli `printf` funkcja jest używana opcja **/H5** jest określona w czasie kompilacji, symbol **_prin** zostanie utworzony, aby można było odwoływać się do `printf`, i to nie zostanie znaleziony w bibliotece.

Korzystanie z **/h** jest niezgodny z [/GL (Optymalizacja Całoprogramowa)](../../build/reference/gl-whole-program-optimization.md).

**/H** opcja jest przestarzały, ponieważ Visual Studio 2005; maksymalna długość granicach zostały zwiększone i **/h** nie jest już potrzebny. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

2. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

3. Wpisz opcję kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)