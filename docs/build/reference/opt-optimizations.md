---
title: / OPT (optymalizacje) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc9f7f66b9bd0ee2c0da65d17eac33e1cbc8c316
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463108"
---
# <a name="opt-optimizations"></a>/OPT (Optymalizacje)

Kontroluje optymalizacje, które LINK wykonuje podczas kompilacji.

## <a name="syntax"></a>Składnia

> **/ OPT:**{**REF** | **NOREF**}<br/>
> **/ OPT:**{**ICF**[**=**_iteracji_] | **NOICF**}<br/>
> **/ OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Argumenty

**REF** &AMP;#124; **NOREF**

**/OPT:REF** eliminuje funkcji i danych, który nie istnieje odwołanie; **/OPT: noref** przechowuje funkcji i danych, który nie istnieje odwołanie.

Po włączeniu /OPT:REF łącze usuwa nieużywane spakowanych funkcji i danych, nazywane *Comdat*. Ta optymalizacja jest znana jako eliminacja przechodnia (lub tranzytywna) COMDAT. **/OPT:REF** opcji wyłącza, konsolidowania przyrostowego.

Funkcje wbudowane i funkcje elementu członkowskiego zdefiniowane wewnątrz deklaracji klasy są zawsze Comdat. Jeśli ma być kompilowana przy użyciu wszystkich funkcji w pliku obiektu zostały wprowadzone do Comdat [/Gy](../../build/reference/gy-enable-function-level-linking.md) opcji. Aby umieścić **const** dane w Comdat, należy zadeklarować go za pomocą `__declspec(selectany)`. Aby uzyskać informacje o sposobie określania danych dotyczących usuwania lub składania, zobacz [selectany](../../cpp/selectany.md).

Domyślnie **/OPT:REF** jest włączana przez konsolidator, chyba że **/OPT: noref** lub [/DEBUG](../../build/reference/debug-generate-debug-info.md) jest określona. Aby zastąpić to ustawienie domyślne i przechowywać nieużywane Comdat w programie, należy określić **/OPT: noref**. Można użyć [/INCLUDE](../../build/reference/include-force-symbol-references.md) opcji powoduje usunięcie określony symbol.

Jeśli [/DEBUG](../../build/reference/debug-generate-debug-info.md) jest określony, wartością domyślną **/OPT** jest **NOREF**, i wszystkie funkcje zostaną zachowane w obrazie. Aby zastąpić to ustawienie domyślne i zoptymalizować kompilację debugowania, określ **/OPT:REF**. Można zmniejszyć rozmiar pliku wykonywalnego i mogą być przydatne optymalizacji nawet w przypadku debugowania kompilacji. Zaleca się, że można również określić **noicf** zachować identyczne kompilacje funkcji podczas debugowania. Dzięki temu można łatwiej odczytywać ślady stosu i ustawiać punkty przerwania w funkcjach, które w przeciwnym razie byłyby składane razem.

**ICF**\[**=**_iteracji_] &#124; **NOICF**

Użyj **ICF**\[**=**_iteracji_] do wykonania identycznych sekcji comdat. Zbędne dane COMDAT mogą być usunięte z danych wyjściowych konsolidatora. Opcjonalny *iteracji* parametr określa liczbę razy, aby przechodzić między nimi symbole duplikatów. Domyślna liczba iteracji jest 1. Dodatkowe iteracje mogą zlokalizować więcej duplikatów, które zostaną odkryte przez składanie w poprzedniej iteracji.

Domyślnie **/OPT: ICF** jest włączana przez konsolidator, chyba że **noicf** lub [/DEBUG](../../build/reference/debug-generate-debug-info.md) jest określona. Aby zastąpić to ustawienie domyślne i uniemożliwić Comdat jest złożone w programie, należy określić **noicf**.

Kompilacji debugowanej, należy jawnie określić **/OPT: ICF** umożliwiające zwijaniu sekcji COMDAT. Jednak ponieważ **/OPT: ICF** scalić identyczne dane lub funkcji, można zmienić nazwy funkcji, które są widoczne w śladów stosu. Może również spowodować, że można ustawić punktów przerwania w niektórych funkcji, lub do zbadania niektóre dane w debugerze i można przejść do funkcji nieoczekiwany po możesz pojedynczy krok za pomocą kodu. Zachowanie kodu jest taki sam, ale prezentacji debuger może być bardzo trudne. W związku z tym nie zaleca się używanie **/OPT: ICF** podczas debugowania kompilacje, chyba że niedogodności przeważają korzyści wynikające z mniejszym kodu.

> [!NOTE]
> Ponieważ **/OPT: ICF** może spowodować, że ten sam adres ma być przypisane do różnych funkcji lub elementy członkowskie danych tylko do odczytu (to znaczy **const** zmiennych, gdy skompilowano przy użyciu **/Gy**), może spowodować nieprawidłowe program, który jest zależny od unikatowe adresy dla funkcji lub elementy członkowskie danych tylko do odczytu. Aby uzyskać więcej informacji, zobacz [/Gy (Włącz funkcję łączenia na poziomie)](../../build/reference/gy-enable-function-level-linking.md).

**LBR** &AMP;#124; **NOLBR**

**/OPT:LBR** i **/OPT:NOLBR** opcje są stosowane tylko do plików binarnych ARM. Ponieważ pewne instrukcje gałęzi procesora ARM mają ograniczony zasięg, jeśli konsolidator wykryje skok do adresu spoza zakresu, zastępuje adres docelowy instrukcji gałęzi adresem kodu „wyspy”, który zawiera instrukcję gałęzi, która odnosi się do faktycznego adresu docelowego. Można użyć **/OPT:LBR** w celu zoptymalizowania wykrywania instrukcje gałęzi long i rozmieszczenie Wyspy pośredniego kod aby zminimalizować łącznego rozmiaru kodu. **/OPT:NOLBR** informuje konsolidator, aby wygenerować kod Wyspy instrukcje gałęzi long jako zostaną napotkane, bez optymalizacji.

Domyślnie **/OPT:LBR** opcja została ustawiona podczas konsolidowania przyrostowego nie jest włączona. -Incremental łącza, ale nie optymalizacje long gałęzi, określić **/OPT:NOLBR**. **/OPT:LBR** opcja powoduje wyłączenie konsolidowania przyrostowego.

## <a name="remarks"></a>Uwagi

Gdy jest używany w wierszu polecenia, konsolidator domyślnie **LBR /OPT:REF, Zapora połączenia internetowego,**. Jeśli **/DEBUG** jest określony, wartością domyślną jest **NOLBR/OPT: noref NOICR,**.

**/OPT** optymalizacje zazwyczaj zmniejszyć rozmiar obrazu i zwiększyć szybkość programu. Te ulepszenia mogą być istotne w przypadku większych programów, dlatego są one włączone domyślnie dla kompilacji sprzedaży detalicznej.

Optymalizacja konsolidatora zająć dodatkowy czas na początku, ale zoptymalizowanego kodu pozwalają również zmniejszyć gdy konsolidator relokacje mniej można naprawić i tworzy mniejsze finalnego obrazu i zapisuje nawet dłużej, gdy posiada mniej informacji debugowania do przetwarzania i zapisać w pliku PDB. Gdy Optymalizacja jest włączona, może to skutkować skrócić czas łącza ogólny, jak małych dodatkowych kosztów analizę może być więcej niż przesunięcie czasu, który oszczędności w konsolidatorze przesuwa się nad mniejsze pliki binarne.

**/OPT** argumentów można określić razem, oddzielonych przecinkami. Na przykład zamiast z **/OPT:REF noicf**, można określić **/OPT:REF, NOICF**.

Można użyć [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) opcji konsolidatora, aby zobaczyć funkcje, które zostały usunięte przez **/OPT:REF** i funkcje, które są składane przez **/OPT: ICF**.

**/OPT** argumenty często są ustawione dla projektów utworzonych za pomocą **nowy projekt** okno dialogowe w programie Visual Studio IDE i zwykle mają różne wartości dla debugowania i konfiguracje wydania. Jeśli wartość nie jest ustawiona dla tych opcji konsolidatora w projekcie, mogą wystąpić wartości domyślnych projektu, które mogą się różnić od wartości domyślne używane przez narzędzie konsolidacji w wierszu polecenia.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję OPT:ICF lub OPT:REF konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** strony właściwości.

1. Zmodyfikuj jedną z tych właściwości:

   - **Włącz zwijaniu sekcji COMDAT**

   - **Odwołania**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora OPT:LBR w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. Wybierz opcję w **dodatkowe opcje**:

   `/opt:lbr` lub `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> właściwości.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
