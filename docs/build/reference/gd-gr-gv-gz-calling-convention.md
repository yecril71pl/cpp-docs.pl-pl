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
ms.openlocfilehash: 73fce079a98a3f4afaa35f8b8c6630fc8a9b4ca4
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825529"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Konwencja wywoływania)

Te opcje określają kolejność, w której argumenty funkcji są wypychane na stosie, niezależnie od tego, czy funkcja wywołująca lub wywoływana funkcja usuwa argumenty ze stosu na końcu wywołania, oraz Konwencję Name-dekorowania nazwy, której kompilator używa do identyfikowania poszczególnych funkcji.

## <a name="syntax"></a>Składnia

> **/GD**\
> **/Gr**\
> **/GV**\
> **/GZ**

## <a name="remarks"></a>Uwagi

**/GD**, ustawienie domyślne określa konwencję wywoływania [__cdecl](../../cpp/cdecl.md) dla wszystkich funkcji, z wyjątkiem funkcji składowych C++ i funkcji oznaczonych [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)lub [__vectorcall](../../cpp/vectorcall.md).

**/Gr** określa `__fastcall` konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka `main`C++, funkcji o nazwie i `__cdecl`funkcji `__stdcall`, które `__vectorcall`są oznaczone, lub. Wszystkie `__fastcall` funkcje muszą mieć prototypy. Ta konwencja wywołania jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i jest ignorowana przez kompilatory, które obsługują inne architektury.

**/GZ** określa `__stdcall` konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka `main`C++, funkcji o nazwie i `__cdecl`funkcji `__fastcall`, które `__vectorcall`są oznaczone, lub. Wszystkie `__stdcall` funkcje muszą mieć prototypy. Ta konwencja wywołania jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i jest ignorowana przez kompilatory, które obsługują inne architektury.

**/GV** określa Konwencję `__vectorcall` wywoływania dla wszystkich funkcji, z wyjątkiem funkcji składowych języka `main`C++, funkcji o `vararg` nazwie, funkcji z listą argumentów zmiennych lub funkcji, które są `__cdecl`oznaczone `__stdcall`atrybutem `__fastcall` powodującym konflikt, lub. Ta konwencja wywołania jest dostępna tylko w architekturze x86 i x64, które obsługują/arch: SSE2 i nowsze, i są ignorowane przez kompilatory, które są przeznaczone dla architektury ARM.

Funkcje, które przyjmują zmienną liczbę argumentów, muszą być `__cdecl`oznaczone.

**/GD**, **/gr**, **/GV** i **/GZ** nie są zgodne z [/CLR: Safe](clr-common-language-runtime-compilation.md) lub **/CLR: Pure**. **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017 lub nowszym.

> [!NOTE]
> Domyślnie dla procesorów x86 funkcje członkowskie języka C++ używają [__thiscall](../../cpp/thiscall.md).

Dla wszystkich procesorów funkcja członkowska, która jest jawnie oznaczona jako `__cdecl`, `__fastcall`, `__vectorcall`lub `__stdcall` używa określonej konwencji wywoływania, jeśli nie jest ignorowana w tej architekturze. Funkcja członkowska, która przyjmuje zmienną liczbę argumentów, zawsze używa konwencji `__cdecl` wywoływania.

Te opcje kompilatora nie mają wpływu na dekorację nazw metod i funkcji języka C++. O ile nie `extern "C"`zadeklarowano jako, metody i funkcje C++ używają innego schematu Name-dekorowania nazwy. Aby uzyskać więcej informacji, zobacz [nazwy dekoracyjne](decorated-names.md).

Aby uzyskać więcej informacji na temat konwencji wywoływania, zobacz [konwencje wywoływania](../../cpp/calling-conventions.md).

## <a name="__cdecl-specifics"></a>__cdecl szczegóły

W przypadku procesorów x86 wszystkie argumenty funkcji są przesyłane na stosie od prawej do lewej. W przypadku architektur ARM i x64 niektóre argumenty są przesyłane przez rejestr, a pozostałe są przesyłane na stosie od prawej do lewej. Procedura wywołująca wyciąga argumenty ze stosu.

Dla języka C konwencja `__cdecl` nazewnictwa używa nazwy funkcji poprzedzonej znakiem podkreślenia ( `_` ); nie jest wykonywane żadne tłumaczenie wielkości liter. O ile nie `extern "C"`zadeklarowano jako, funkcje języka C++ używają innego schematu Name-dekorowania nazwy. Aby uzyskać więcej informacji, zobacz [nazwy dekoracyjne](decorated-names.md).

## <a name="__fastcall-specifics"></a>__fastcall szczegóły

Niektóre argumenty `__fastcall` funkcji są przekazywane w rejestrach (dla procesorów x86, ECX i EDX), a pozostałe są wypychane na stosie od prawej do lewej. Wywołana procedura powoduje przeprowadzenie tych argumentów ze stosu przed zwróceniem. Zazwyczaj **/gr** zmniejsza czas wykonywania.

> [!NOTE]
> Należy zachować ostrożność w przypadku `__fastcall` użycia konwencji wywoływania dla dowolnej funkcji, która jest zapisywana w wbudowanym języku asemblera. Użycie rejestrów może powodować konflikt z użyciem kompilatora.

Dla języka C konwencja `__fastcall` nazewnictwa używa nazwy funkcji poprzedzonej znakiem (**\@**), po której następuje rozmiar argumentów funkcji w bajtach. Nie jest wykonywane żadne tłumaczenie wielkości liter. Kompilator używa tego szablonu do konwencji nazewnictwa:

`@function_name@number`

Używając Konwencji `__fastcall` nazewnictwa, należy użyć standardowych plików dołączanych. W przeciwnym razie otrzymasz nierozwiązane odwołania zewnętrzne.

## <a name="__stdcall-specifics"></a>__stdcall szczegóły

Argumenty `__stdcall` funkcji są wypychane na stosie od prawej do lewej, a wywoływana funkcja pop te argumenty ze stosu przed zwróceniem.

Dla języka C konwencja `__stdcall` nazewnictwa używa nazwy funkcji poprzedzonej znakiem podkreślenia (**\_**), po której następuje znak (**\@**) i rozmiar argumentów funkcji w bajtach. Nie jest wykonywane żadne tłumaczenie wielkości liter. Kompilator używa tego szablonu do konwencji nazewnictwa:

`_functionname@number`

## <a name="__vectorcall-specifics"></a>__vectorcall szczegóły

Argumenty `__vectorcall` całkowite funkcji są przenoszone przez wartość, przy użyciu do dwóch (w przypadku wersji x86) lub czterech (na poziomie x64) rejestrów liczb całkowitych oraz do sześciu XMM rejestrów dla wartości zmiennoprzecinkowych i wektorowych, a pozostałe są przesyłane na stosie od prawej do lewej. Wywołana funkcja czyści stos przed zwróceniem. Wartości typu Vector i zmiennoprzecinkowego są zwracane w XMM0.

Dla języka C konwencja `__vectorcall` nazewnictwa używa nazwy funkcji, a po niej dwa znaki (**\@**) i rozmiar argumentów funkcji w bajtach. Nie jest wykonywane żadne tłumaczenie wielkości liter. Kompilator używa tego szablonu do konwencji nazewnictwa:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości**Zaawansowane** **C/C++** > .

1. Zmodyfikuj właściwość **konwencji wywoływania** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora MSVC](compiler-options.md)
- [Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
