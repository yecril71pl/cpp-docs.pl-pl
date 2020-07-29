---
title: /Gd, /Gr, /Gv, /Gz (Konwencja wywoływania)
ms.date: 09/05/2018
f1_keywords:
- /Gr
- /Gv
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
ms.openlocfilehash: e1617b7c158e9705a6211310fa7873f667a62ba5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234370"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Konwencja wywoływania)

Te opcje określają kolejność, w której argumenty funkcji są wypychane na stosie, niezależnie od tego, czy funkcja wywołująca lub wywoływana funkcja usuwa argumenty ze stosu na końcu wywołania, oraz Konwencję Name-dekorowania nazwy, której kompilator używa do identyfikowania poszczególnych funkcji.

## <a name="syntax"></a>Składnia

> **`/Gd`**\
> **`/Gr`**\
> **`/Gv`**\
> **`/Gz`**

## <a name="remarks"></a>Uwagi

**`/Gd`** ustawienie domyślne Określa [__cdecl](../../cpp/cdecl.md) konwencji wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych C++ i funkcji oznaczonych [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)lub [__vectorcall](../../cpp/vectorcall.md).

**`/Gr`** Określa **`__fastcall`** konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka C++, funkcji o nazwie `main` i funkcji, które są oznaczone **`__cdecl`** , **`__stdcall`** lub **`__vectorcall`** . Wszystkie **`__fastcall`** funkcje muszą mieć prototypy. Ta konwencja wywołania jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i jest ignorowana przez kompilatory, które obsługują inne architektury.

**`/Gz`** Określa **`__stdcall`** konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka C++, funkcji o nazwie `main` i funkcji, które są oznaczone **`__cdecl`** , **`__fastcall`** lub **`__vectorcall`** . Wszystkie **`__stdcall`** funkcje muszą mieć prototypy. Ta konwencja wywołania jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i jest ignorowana przez kompilatory, które obsługują inne architektury.

**`/Gv`** Określa **`__vectorcall`** konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka C++, funkcji o nazwie `main` , funkcji z `vararg` listą argumentów zmiennych lub funkcji, które są oznaczone atrybutem powodującym konflikt **`__cdecl`** , **`__stdcall`** lub **`__fastcall`** . Ta konwencja wywołania jest dostępna tylko w architekturze x86 i x64, które obsługują/arch: SSE2 i nowsze, i są ignorowane przez kompilatory, które są przeznaczone dla architektury ARM.

Funkcje, które przyjmują zmienną liczbę argumentów, muszą być oznaczone **`__cdecl`** .

**`/Gd`**, **`/Gr`** **`/Gv`** i **`/Gz`** nie są zgodne z [`/clr:safe`](clr-common-language-runtime-compilation.md) lub **/CLR: Pure**. **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017 lub nowszym.

> [!NOTE]
> Domyślnie dla procesorów x86 są używane funkcje członkowskie języka C++ [`__thiscall`](../../cpp/thiscall.md) .

Dla wszystkich procesorów funkcja członkowska, która jest jawnie oznaczona jako **`__cdecl`** , **`__fastcall`** , **`__vectorcall`** lub **`__stdcall`** używa określonej konwencji wywoływania, jeśli nie jest ignorowana w tej architekturze. Funkcja członkowska, która przyjmuje zmienną liczbę argumentów, zawsze używa **`__cdecl`** konwencji wywoływania.

Te opcje kompilatora nie mają wpływu na dekorację nazw metod i funkcji języka C++. O ile nie zadeklarowano jako `extern "C"` , metody i funkcje C++ używają innego schematu Name-dekorowania nazwy. Aby uzyskać więcej informacji, zobacz [nazwy dekoracyjne](decorated-names.md).

Aby uzyskać więcej informacji na temat konwencji wywoływania, zobacz [konwencje wywoływania](../../cpp/calling-conventions.md).

## <a name="__cdecl-specifics"></a>__cdecl szczegóły

W przypadku procesorów x86 wszystkie argumenty funkcji są przesyłane na stosie od prawej do lewej. W przypadku architektur ARM i x64 niektóre argumenty są przesyłane przez rejestr, a pozostałe są przesyłane na stosie od prawej do lewej. Procedura wywołująca wyciąga argumenty ze stosu.

Dla języka C **`__cdecl`** konwencja nazewnictwa używa nazwy funkcji poprzedzonej znakiem podkreślenia ( `_` ); nie jest przeprowadzane tłumaczenie wielkości liter. O ile nie zadeklarowano jako `extern "C"` , funkcje języka C++ używają innego schematu Name-dekorowania nazwy. Aby uzyskać więcej informacji, zobacz [nazwy dekoracyjne](decorated-names.md).

## <a name="__fastcall-specifics"></a>__fastcall szczegóły

Niektóre **`__fastcall`** argumenty funkcji są przekazywane w rejestrach (dla procesorów x86, ECX i EDX), a pozostałe są wypychane na stosie od prawej do lewej. Wywołana procedura powoduje przeprowadzenie tych argumentów ze stosu przed zwróceniem. Zazwyczaj **/gr** zmniejsza czas wykonywania.

> [!NOTE]
> Należy zachować ostrożność w przypadku użycia **`__fastcall`** konwencji wywoływania dla dowolnej funkcji, która jest zapisywana w wbudowanym języku asemblera. Użycie rejestrów może powodować konflikt z użyciem kompilatora.

Dla języka C **`__fastcall`** konwencja nazewnictwa używa nazwy funkcji poprzedzonej znakiem ( **\@** ), po której następuje rozmiar argumentów funkcji w bajtach. Nie jest wykonywane żadne tłumaczenie wielkości liter. Kompilator używa tego szablonu do konwencji nazewnictwa:

`@function_name@number`

Używając **`__fastcall`** konwencji nazewnictwa, należy użyć standardowych plików dołączanych. W przeciwnym razie otrzymasz nierozwiązane odwołania zewnętrzne.

## <a name="__stdcall-specifics"></a>__stdcall szczegóły

**`__stdcall`** Argumenty funkcji są wypychane na stosie od prawej do lewej, a wywoływana funkcja pop te argumenty ze stosu przed zwróceniem.

Dla języka C **`__stdcall`** konwencja nazewnictwa używa nazwy funkcji poprzedzonej znakiem podkreślenia ( **\_** ), po której następuje znak ( **\@** ) i rozmiar argumentów funkcji w bajtach. Nie jest wykonywane żadne tłumaczenie wielkości liter. Kompilator używa tego szablonu do konwencji nazewnictwa:

`_functionname@number`

## <a name="__vectorcall-specifics"></a>__vectorcall szczegóły

**`__vectorcall`** Argumenty całkowite funkcji są przenoszone przez wartość, przy użyciu do dwóch (w przypadku wersji x86) lub czterech (na poziomie x64) rejestrów liczb całkowitych oraz do sześciu XMM rejestrów dla wartości zmiennoprzecinkowych i wektorowych, a pozostałe są przesyłane na stosie od prawej do lewej. Wywołana funkcja czyści stos przed zwróceniem. Wartości typu Vector i zmiennoprzecinkowego są zwracane w XMM0.

Dla języka C **`__vectorcall`** konwencja nazewnictwa używa nazwy funkcji, a po niej dwa znaki ( **\@\@** ) i rozmiar argumentów funkcji w bajtach. Nie jest wykonywane żadne tłumaczenie wielkości liter. Kompilator używa tego szablonu do konwencji nazewnictwa:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości zaawansowane **C/C++**  >  **Advanced** .

1. Zmodyfikuj właściwość **konwencji wywoływania** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora MSVC](compiler-options.md)
- [Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
