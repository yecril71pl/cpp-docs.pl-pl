---
title: /fp (Określenie zachowania zmiennoprzecinkowego)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: 8b948edba3244eb22089b2ef5b4c8131736e1fb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452575"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Określenie zachowania zmiennoprzecinkowego)

Określa zachowanie liczb zmiennopozycyjnych w pliku kodu źródłowego.

## <a name="syntax"></a>Składnia

> **/ FP:**[**dokładne** | **z wyjątkiem**[**-**] | **szybkie** | **strict**]

### <a name="arguments"></a>Argumenty

#### <a name="precise"></a>dokładny

Wartość domyślna **/FP** jest **/FP: precise**.

**/FP: precise** flagi zwiększa spójność testów zmiennopozycyjnych na równość i nierówność, wyłączając optymalizacje, które mogą zmienić dokładność wykonywania obliczeń zmiennopozycyjnych. (Zachowanie określonej dokładności jest wymagane, aby uzyskać pełną zgodność z ANSI). Domyślnie w kodzie x86 architektury, że użycie x87 Koprocesor instrukcje, kompilator używa Koprocesor użytkownika 80-bitowych rejestrów do przechowywania wyników pośrednich obliczeń zmiennopozycyjnych. Zwiększa to szybkość działania programu i zmniejsza jego rozmiar. Ponieważ jednak obliczanie obejmuje typy danych zmiennopozycyjnych, które są reprezentowane w pamięci przez mniej niż 80 bitów, dołączanie dodatkowych bitów precyzji (80 bitów pomniejszone o liczbę bitów w mniejszym typie zmiennopozycyjnym) w trakcie długich obliczeń może wygenerować niespójne wyniki.

Za pomocą **/FP: precise** na x86 procesorów, kompilator wykonuje Zaokrąglanie dla zmiennych typu `float` z dokładnością odpowiednią dla przydziałów i rzutowania i gdy parametry są przekazywane do funkcji. To zaokrąglanie gwarantuje, że dane nie zachowują żadnego znaczenia większego od pojemności ich typu. Program skompilowany z **/FP: precise** może być wolniejszy i większy niż skompilowany bez **/FP: precise**. **/ FP: precise** wyłącza funkcje wewnętrzne; standardowej biblioteki wykonawczej procedury są używane zamiast tego. Aby uzyskać więcej informacji, zobacz [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md).

Następujące zachowanie zmiennopozycyjne jest włączone za pomocą **/FP: precise**:

- Skracanie — czyli stosowanie złożonej operacji, w której wykonuje się tylko jedno zaokrąglenie w punkcie końcowym, aby zastąpić wiele operacji.

- Optymalizacje wyrażeń, które są nieprawidłowe dla specjalnych wartości (NaN, +nieskończoność, -nieskończoność, +0, -0), nie są dozwolone. Optymalizacje x-x = > 0 x * 0 = > 0 x-0 = > x, x + 0 = > x i 0-x = > - x są nieprawidłowe z różnych powodów. (Zobacz norma IEEE 754 i C99).

- Kompilator poprawnie przetwarza porównania obejmujące NaN. Na przykład x! = x, które daje w wyniku **true** Jeśli `x` jest NaN i uporządkowane porównania używające NaN zgłosić wyjątek.

- Obliczanie wyrażenia następuje po C99 FLT_EVAL_METHOD=2, z następującym wyjątkiem: gdy programuje się dla architektury procesorów x86, ponieważ FPU jest ustawiony na 53-bitową precyzję, uznaje się to za precyzję long-double.

- Mnożenie przez dokładnie 1.0 jest przekształcane na zastosowanie innego mnożnika. x * y\*1.0 jest przekształcane na x\*y. Podobnie, x\*1.0\*y jest przekształcana na x\*y.

- Dzielenie przez dokładnie 1.0 jest przekształcane na zastosowanie dzielnej. x * x przekształceniu y/1.0\*y. Podobnie, x / 1.0\*y jest przekształcana na x\*y.

Za pomocą **/FP: precise** podczas [fenv_access](../../preprocessor/fenv-access.md) znajduje się na wyłącza optymalizacje, takie jak ocen w czasie kompilacji wyrażeń liczb zmiennopozycyjnych. Na przykład, jeśli używasz [_control87 —, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) do zmiany trybu zaokrąglania, a kompilator wykonuje obliczenie zmiennopozycyjne, określony tryb zaokrąglania nie obowiązuje chyba że `fenv_access`ma wartość ON.

**/ FP: precise** zastępuje **/Op** — opcja kompilatora.

#### <a name="fast"></a>Szybka

**Fast** opcja tworzy najszybszy kod w większości przypadków przez złagodzić zasady optymalizacji operacji zmiennopozycyjnych. Pozwala to kompilatorowi na optymalizację kodu zmiennopozycyjnego pod kątem szybkości, kosztem dokładności i poprawności. Gdy **Fast** jest określony, kompilator może niepoprawnie zaokrąglać w instrukcjach przypisania, rzutowaniach typu lub wywołaniach funkcji i może nie zaokrąglać wyrażeń pośrednich. Kompilator może zmienić kolejność operacji lub wykonywać przekształcenia algebraiczne — na przykład, według zasad łączności i rozdzielności — bez względu na ich wpływ na wyniki skończonej precyzji. Kompilator może zmienić operacje i operandy na te o pojedynczej precyzji, zamiast zachowywać reguły promocji typu C++. Optymalizacje zmniejszenia Floating point określonych są zawsze włączone ([fp_contract](../../preprocessor/fp-contract.md) ma wartość ON). Wyjątki zmiennoprzecinkowe i dostęp do środowiska FPU są wyłączone (**/FP: except-** jest implikowane i [fenv_access](../../preprocessor/fenv-access.md) jest WYŁĄCZONY).

**Fast** nie można używać z **/FP: strict** lub **/FP: precise**. Używana jest ostatnia opcja określona w wierszu polecenia. Określenie zarówno **Fast** i **/FP: except** generuje błąd kompilatora.

Określanie [/za, /Ze (Wyłącz rozszerzenia językowe)](../../build/reference/za-ze-disable-language-extensions.md) (zgodność z ANSI) i **Fast** może spowodować nieoczekiwane zachowanie. Na przykład, operacje zmiennopozycyjne o pojedynczej precyzji mogą nie zostać zaokrąglone do pojedynczej precyzji.

#### <a name="except"></a>Z wyjątkiem

**/FP: except** opcja umożliwia wiarygodny model wyjątków zmiennopozycyjnych. Wyjątki są zgłaszane natychmiast po ich wygenerowaniu. Domyślnie ta opcja jest wyłączona. Dołączanie znaku minusa do opcji (**/FP: except-**) jawnie wyłącza je.

#### <a name="strict"></a>ściśle

**/FP: strict** opcja umożliwia najbardziej restrykcyjny model zmiennopozycyjny. **/ FP: strict** powoduje, że [fp_contract](../../preprocessor/fp-contract.md) na OFF i [fenv_access](../../preprocessor/fenv-access.md) na on. **/ FP: except** jest implikowane i może być wyłączone przez jawne określenie **/FP: except-**. Gdy jest używane z **/FP: except —**, **/FP: strict** Wymusza ścisłą semantykę zmiennoprzecinkową, ale bez uwzględniania zdarzeń wyjątkowych.

## <a name="remarks"></a>Uwagi

Wiele **/FP** opcje mogą być określone w tej samej kompilacji.

Aby kontrolować zachowanie liczb zmiennopozycyjnych za pomocą funkcji, zobacz [float_control](../../preprocessor/float-control.md) pragmy. Ustawienie to zastępuje **/FP** ustawienie kompilatora. Zalecamy zapisywanie i przywracanie lokalnego zachowania liczb zmiennopozycyjnych jako dobrą praktykę programistyczną:

```cpp
#pragma float_control(precise, on, push)
// Code that uses /fp:precise mode
#pragma float_control(pop)
```

Większość optymalizacji zmiennopozycyjnych związanych z **/FP: strict**, **/FP: except** (i) i `fp_contract` pragma są zależne od maszyny. **/ FP: strict** i **/FP: except** nie są zgodne z **/CLR**.

**/ FP: precise** powinno dotyczyć większości wymagań zmiennopozycyjnych aplikacji. Możesz użyć **/FP: except** i **/FP: strict**, jednak może wystąpić spadek wydajności. Jeśli wydajność jest najważniejsza, rozważ użycie **Fast**.

**/ FP: strict**, **Fast**, i **/FP: precise** są trybami precyzji (dokładności). Tylko jeden może być wdrożony w tym samym czasie. Jeśli oba **/FP: strict** i **/FP: precise** są określone, kompilator używa tego, który ostatnio przetwarzane. Zarówno **/FP: strict** i **Fast** nie może być określony.

Aby uzyskać więcej informacji, zobacz [programu Microsoft Visual C++ Optymalizacja zmiennopozycyjna](floating-point-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** > **C/C++** > **generowania kodu** stronę właściwości.

1. Modyfikowanie **Model zmiennoprzecinkowy** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora](compiler-options.md)
- [Ustawianie opcji kompilatora](setting-compiler-options.md)
- [Optymalizacja zmiennopozycyjna Microsoft Visual C++](floating-point-optimization.md)