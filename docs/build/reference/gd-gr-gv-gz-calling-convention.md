---
title: /Gd, /Gr, /Gv, /Gz (Konwencja wywoływania)
ms.date: 09/05/2018
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
ms.openlocfilehash: 7c4f7e6edb020f5c8d2abf80f14df33e18a915c5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817468"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Konwencja wywoływania)

Te opcje określają kolejność, która funkcja argumenty są wypychane na stos, czy wywołujący funkcję lub wywołana funkcja usuwa argumenty ze stosu na końcu wywołania i Konwencję dekorowania nazwy, której kompilator używa do identyfikowania poszczególne funkcje.

## <a name="syntax"></a>Składnia

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**<br/>

## <a name="remarks"></a>Uwagi

**/GD —**, domyślne ustawienie określa [__cdecl](../../cpp/cdecl.md) konwencja wywołania dla wszystkich funkcji z wyjątkiem składowych języka C++, funkcji i funkcji, które są oznaczone [__stdcall](../../cpp/stdcall.md), [__ Fastcall](../../cpp/fastcall.md), lub [__vectorcall](../../cpp/vectorcall.md).

**GR** Określa `__fastcall` Konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka C++, funkcji o nazwie `main`i funkcje, które są oznaczone `__cdecl`, `__stdcall`, lub `__vectorcall`. Wszystkie `__fastcall` funkcje muszą mieć prototypy. Ta konwencja wywołania jest dostępna tylko w kompilatorach, których platformą docelową x86 i jest ignorowana przez kompilatory, których celem są inne architektury.

**/GZ** Określa `__stdcall` Konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka C++, funkcji o nazwie `main`i funkcje, które są oznaczone `__cdecl`, `__fastcall`, lub `__vectorcall`. Wszystkie `__stdcall` funkcje muszą mieć prototypy. Ta konwencja wywołania jest dostępna tylko w kompilatorach, których platformą docelową x86 i jest ignorowana przez kompilatory, których celem są inne architektury.

**GV** Określa `__vectorcall` Konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka C++, nazwanych głównymi, funkcje z `vararg` listy argumentów zmiennych lub funkcji, które są oznaczone jako sprzeczne `__cdecl`, `__stdcall`, lub `__fastcall` atrybutu. Ta konwencja wywołania jest dostępna tylko na architekturach x86 i x64, które obsługują SSE2 i wyższych i jest ignorowana przez kompilatory, przeznaczonych dla architektury ARM.

Funkcje, które przyjmują zmienną liczbę argumentów, które muszą być oznaczone `__cdecl`.

**/GD —**, **GR**, **GV** i **GZ** nie są zgodne z [/CLR: Safe](clr-common-language-runtime-compilation.md) lub   **/CLR: pure**. **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

> [!NOTE]
> Domyślnie x86 procesorów, funkcji składowych języka C++ użyj [__thiscall](../../cpp/thiscall.md).

Dla wszystkich procesorów funkcja członkowska, która jest jawnie oznaczona jako `__cdecl`, `__fastcall`, `__vectorcall`, lub `__stdcall` używa określonej konwencji wywoływania, jeśli nie jest ona ignorowana na danej architekturze. Funkcja elementu członkowskiego, która przyjmuje zmienną liczbę argumentów, zawsze używa `__cdecl` konwencji wywoływania.

Te opcje kompilatora nie mają wpływu na dekorację nazwy metod języka C++ i funkcji. O ile nie jest zadeklarowany jako `extern "C"`, metody i funkcje C++ używają innego schematu dekorowania nazwy. Aby uzyskać więcej informacji, zobacz [nazwy dekorowane](decorated-names.md).

Aby uzyskać więcej informacji dotyczących konwencji wywoływania, zobacz [Konwencje wywoływania](../../cpp/calling-conventions.md).

## <a name="cdecl-specifics"></a>Charakterystyka __cdecl

Na x86 procesorów, wszystkie argumenty funkcji są przekazywane na stosie od prawej do lewej. Na ARM i x64 architektury, niektóre argumenty są przekazywane przez rejestr, a pozostałe są przekazywane na stosie od prawej do lewej. Wywołanie procedury pobiera argumenty ze stosu.

Dla języka C `__cdecl` nazewnictwa Konwencji używa nazwy funkcji poprzedzonej podkreśleniem ( `_` ); Translacja wielkości liter nie jest wykonywane. O ile nie jest zadeklarowany jako `extern "C"`, funkcje C++ używają innego schematu dekorowania nazwy. Aby uzyskać więcej informacji, zobacz [nazwy dekorowane](decorated-names.md).

## <a name="fastcall-specifics"></a>Charakterystyka __fastcall

Niektóre `__fastcall` argumenty funkcji są przekazywane w rejestrach (dla x86 procesorów, ECX i EDX), a pozostałe są wypychane na stosie od prawej do lewej. Wywołana procedura wyciąga te argumenty ze stosu przed jego zwracaniem. Zazwyczaj **GR** zmniejsza czas wykonania.

> [!NOTE]
> Należy zachować ostrożność, korzystając z `__fastcall` konwencja wywołania dla dowolnej funkcji, która jest napisana w języku zestawu. Korzystanie z rejestrów może powodować konflikt przy użyciu kompilatora.

Dla języka C `__fastcall` nazewnictwa Konwencji używa nazwy funkcji poprzedzone znakiem (**\@**) następuje rozmiar argumentów funkcji w bajtach. Translacja wielkości liter nie jest wykonywane. Kompilator używa tego szablonu do konwencji nazewnictwa:

`@function_name@number`

Kiedy używasz `__fastcall` konwencji nazewnictwa, użyj standardowych plików dołączeń. W przeciwnym wypadku otrzymasz nierozpoznawane odwołania zewnętrzne.

## <a name="stdcall-specifics"></a>Charakterystyka __stdcall

A `__stdcall` argumenty funkcji są wypychane na stosie od prawej do lewej i wywołana funkcja wyciąga te argumenty ze stosu przed jego zwracaniem.

Dla języka C `__stdcall` nazewnictwa Konwencji używa nazwy funkcji poprzedzonej podkreśleniem (**\_**) i następuje znak (**\@**) i rozmiar — funkcja argumenty w bajtach. Translacja wielkości liter nie jest wykonywane. Kompilator używa tego szablonu do konwencji nazewnictwa:

`_functionname@number`

## <a name="vectorcall-specifics"></a>Charakterystyka __vectorcall

A `__vectorcall` funkcji liczby całkowitej argumenty są przekazywane przez wartość, przy użyciu maksymalnie dwóch (na x86) lub czterech (na x64) liczby całkowitej rejestrów całkowitoliczbowych i maksymalnie sześciu rejestrów XMM dla zmiennoprzecinkowych i wartości wektorowych, a pozostałe są przekazywane na stosie od prawej do lewej. Wywołana funkcja czyści stos, przed jego zwracaniem. Wektor i zmiennoprzecinkowej wartości zwracane są zwracane w XMM0.

Dla języka C `__vectorcall` konwencji nazewnictwa używa nazwy funkcji, a następnie dwoma znakami (**\@\@**) oraz rozmiar argumentów funkcji w bajtach. Translacja wielkości liter nie jest wykonywane. Kompilator używa tego szablonu do konwencji nazewnictwa:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **C/C++** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **konwencji wywoływania** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Zobacz także

- [MSVC Compiler Options](compiler-options.md)
- [Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
