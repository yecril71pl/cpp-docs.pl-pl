---
title: -fp (określenie zachowania zmiennoprzecinkowego) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
dev_langs:
- C++
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 520a6e2d675c55e47a0424ab93c6a76d521f2358
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2018
ms.locfileid: "34422696"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Określenie zachowania zmiennoprzecinkowego)

Określa zachowanie liczb zmiennopozycyjnych w pliku kodu źródłowego.

## <a name="syntax"></a>Składnia

> **/ FP:**[**dokładne** | **z wyjątkiem**[**-**] | **fast** | **strict**]

### <a name="arguments"></a>Argumenty

#### <a name="precise"></a>dokładne

Wartość domyślna **/FP** jest **/FP: precise**.

**/FP: precise** flagi zwiększa spójność testów zmiennoprzecinkowych na równość i nierówność wyłączając funkcje optymalizacji, które można zmienić dokładności obliczeń zmiennoprzecinkowych. (Zachowanie określonej dokładności jest wymagane, aby uzyskać pełną zgodność z ANSI). Domyślnie w kodzie x86 architektury, że instrukcji Koprocesor stosowania x87, kompilator używa Koprocesor na 80-bitowa rejestrów dla pośrednich wyników obliczeń zmiennoprzecinkowych. Zwiększa to szybkość działania programu i zmniejsza jego rozmiar. Ponieważ jednak obliczanie obejmuje typy danych zmiennopozycyjnych, które są reprezentowane w pamięci przez mniej niż 80 bitów, dołączanie dodatkowych bitów precyzji (80 bitów pomniejszone o liczbę bitów w mniejszym typie zmiennopozycyjnym) w trakcie długich obliczeń może wygenerować niespójne wyniki.

Z **/FP: dokładne** na x86 procesorów, kompilator wykonuje zaokrąglania na zmiennych typu `float` poprawne precyzji przydziałów i rzutowania, gdy parametry są przekazywane do funkcji. To zaokrąglanie gwarantuje, że dane nie zachowują żadnego znaczenia większego od pojemności ich typu. Program skompilowane z **/FP: dokładne** może być wolniejsze i większa niż jeden skompilowany bez **/FP: dokładne**. **/ FP: precise** wyłącza funkcje wewnętrzne; standardowej biblioteki wykonawczej procedury są używane zamiast tego. Aby uzyskać więcej informacji, zobacz [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md).

Następujące zachowania zmiennoprzecinkowego jest włączone w **/FP: precise**:

- Skracanie — czyli stosowanie złożonej operacji, w której wykonuje się tylko jedno zaokrąglenie w punkcie końcowym, aby zastąpić wiele operacji.

- Optymalizacje wyrażeń, które są nieprawidłowe dla specjalnych wartości (NaN, +nieskończoność, -nieskończoność, +0, -0), nie są dozwolone. Optymalizacje x-x = > 0, x * 0 = > 0, x-0 = > x, x + 0 = > x i 0 x = > - x z różnych powodów, są nieprawidłowe. (Zobacz norma IEEE 754 i C99).

- Kompilator poprawnie przetwarza porównania obejmujące NaN. Na przykład x! = x daje w wyniku **true** Jeśli `x` jest wartością typu NaN i zgłosić wyjątek, uporządkowanej porównania obejmujące NaN.

- Obliczanie wyrażenia następuje po C99 FLT_EVAL_METHOD=2, z następującym wyjątkiem: gdy programuje się dla architektury procesorów x86, ponieważ FPU jest ustawiony na 53-bitową precyzję, uznaje się to za precyzję long-double.

- Mnożenie przez dokładnie 1.0 jest przekształcane na zastosowanie innego mnożnika. x * y\*1.0 jest przekształcana na x\*y. Podobnie x\*1.0\*y jest przekształcana na x\*y.

- Dzielenie przez dokładnie 1.0 jest przekształcane na zastosowanie dzielnej. x * y/1.0 jest przekształcana na x\*y. Podobnie x / 1.0\*y jest przekształcana na x\*y.

Przy użyciu **/FP: precise** podczas [fenv_access](../../preprocessor/fenv-access.md) znajduje się na wyłącza optymalizacje, takie jak obliczanie kompilacji wyrażeń zmiennoprzecinkowych. Na przykład, jeśli używasz [_control87 —, _controlfp —, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) zmianę trybu zaokrąglania i kompilator wykonuje obliczeń zmiennoprzecinkowych, zostanie określony tryb zaokrąglania nie jest włączona chyba że `fenv_access`ma wartość ON.

**/ FP: precise** zastępuje **/Op** — opcja kompilatora.

#### <a name="fast"></a>Szybkie

**Fast** opcja tworzy najszybszy kod w większości przypadków przez mniejsze zasady Optymalizacja operacji zmiennoprzecinkowej. Pozwala to kompilatorowi na optymalizację kodu zmiennopozycyjnego pod kątem szybkości, kosztem dokładności i poprawności. Gdy **Fast** jest określony, kompilator nie może poprawnie zaokrąglona w instrukcji przypisania, typecasts, lub wywołania funkcji i nie może wykonać zaokrąglania pośredniego wyrażeń. Kompilator może zmienić kolejność operacji lub wykonywać przekształcenia algebraiczne — na przykład, według zasad łączności i rozdzielności — bez względu na ich wpływ na wyniki skończonej precyzji. Kompilator może zmienić operacje i operandy na te o pojedynczej precyzji, zamiast zachowywać reguły promocji typu C++. Zmniejszenie Floating point dotyczące optymalizacji są zawsze włączone ([fp_contract](../../preprocessor/fp-contract.md) ma wartość ON). Wyjątki zmiennoprzecinkowe i dostęp do środowiska FPU są wyłączone (**/FP: except-** technicznego i [fenv_access](../../preprocessor/fenv-access.md) ma wartość OFF).

**Fast** nie można używać z **/FP: strict** lub **/FP: precise**. Używana jest ostatnia opcja określona w wierszu polecenia. Określenie zarówno **Fast** i **/FP: except** generuje błąd kompilatora.

Określanie [/Za, /Ze (Wyłącz rozszerzenia językowe)](../../build/reference/za-ze-disable-language-extensions.md) (zgodność ANSI) i **Fast** może spowodować nieoczekiwane zachowanie. Na przykład, operacje zmiennopozycyjne o pojedynczej precyzji mogą nie zostać zaokrąglone do pojedynczej precyzji.

#### <a name="except"></a>Z wyjątkiem

**/FP: except** opcja umożliwia modelu niezawodnej zmiennoprzecinkowych wyjątków. Wyjątki są zgłaszane natychmiast po ich wygenerowaniu. Domyślnie ta opcja jest wyłączona. Dołączanie znakiem minus opcji (**/FP: except-**) jawnie wyłącza je.

#### <a name="strict"></a>ściśle

**/FP: strict** opcja umożliwia najbardziej rygorystyczne model zmiennoprzecinkowy. **/ FP: strict** powoduje, że [fp_contract](../../preprocessor/fp-contract.md) wyłącza i [fenv_access](../../preprocessor/fenv-access.md) się ON. **/ FP: except** jest domniemane i może być wyłączone przez jawne określenie **/FP: except-**. W przypadku użycia z **/FP: except-**, **/FP: strict** Wymusza ścisłą semantykę zmiennoprzecinkową, ale bez przestrzegania zdarzeń wyjątkowych.

## <a name="remarks"></a>Uwagi

Wiele **/FP** opcje można określić w tej samej kompilacji.

Aby kontrolować zachowania zmiennoprzecinkowego przez funkcję, zobacz [float_control](../../preprocessor/float-control.md) pragma. Przesłania **/FP** Ustawienia kompilatora. Zalecamy zapisywanie i przywracanie lokalnego zachowania liczb zmiennopozycyjnych jako dobrą praktykę programistyczną:

```cpp
#pragma float_control(precise, on, push)
// Code that uses /fp:precise mode
#pragma float_control(pop)
```

Większość zmiennoprzecinkowe optymalizacje związane z **/FP: strict**, **/FP: z wyjątkiem** (i jego odpowiedniego pragmy) i `fp_contract` pragma są zależne od maszyny. **/ FP: strict** i **/FP: except** nie są zgodne z **/CLR**.

**/ FP: precise** należy spełnić większość wymagań zmiennoprzecinkowe aplikacji. Można użyć **/FP: except** i **/FP: strict**, ale niektóre spadek wydajności. Jeśli najważniejszych wydajności, należy rozważyć, czy ma być używany **Fast**.

**/ FP: strict**, **Fast**, i **/FP: precise** tryby precision (poprawności). Tylko jeden może być wdrożony w tym samym czasie. Jeśli oba **/FP: strict** i **/FP: dokładne** są określone, kompilator używa ten, który przetwarza ostatnio. Zarówno **/FP: strict** i **Fast** nie może zostać określony.

Aby uzyskać więcej informacji, zobacz [Microsoft Visual C++ Floating-Point optymalizacji](floating-point-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń węzeł **właściwości konfiguracji** > **C/C++** > **generowania kodu** strony właściwości.

1. Modyfikowanie **zmiennoprzecinkową modelu punktu** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora](compiler-options.md)
- [Ustawianie opcji kompilatora](setting-compiler-options.md)
- [Microsoft Visual C++ zmiennoprzecinkową punktu optymalizacji](floating-point-optimization.md)