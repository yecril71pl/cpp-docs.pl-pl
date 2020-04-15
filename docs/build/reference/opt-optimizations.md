---
title: /OPT (Optymalizacje)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: b25db4d6c260c3c6751de293aa2a82df8aa05e7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336224"
---
# <a name="opt-optimizations"></a>/OPT (Optymalizacje)

Kontroluje optymalizacje, które LINK wykonuje podczas kompilacji.

## <a name="syntax"></a>Składnia

> **/OPT:**{**REF** | **NOREF**}<br/>
> **/OPT:**{**ICF**[**=**_iteracje_] | **NOICF**}<br/>
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Argumenty

**REF** &#124; **NOREF**

**/OPT:REF** eliminuje funkcje i dane, które nigdy nie są przywoły, o których mowa; **/OPT:NOREF** przechowuje funkcje i dane, które nigdy nie są przywoływane.

Gdy opcja /OPT:REF jest włączona, funkcja LINK usuwa nieodłączone spakowane funkcje i dane, znane jako *COMDATs*. Ta optymalizacja jest znana jako eliminacja przechodnia (lub tranzytywna) COMDAT. Opcja **/OPT:REF** wyłącza również łączenie przyrostowe.

Wbudowane funkcje i funkcje członkowskie zdefiniowane wewnątrz deklaracji klasy są zawsze COMDATs. Wszystkie funkcje w pliku obiektu są wykonane w COMDATs, jeśli jest skompilowany przy użyciu [/Gy](gy-enable-function-level-linking.md) opcji. Aby umieścić **const** danych w COMDATs, `__declspec(selectany)`należy zadeklarować go za pomocą . Aby uzyskać informacje na temat określania danych do usunięcia lub złożenia, zobacz [selectany](../../cpp/selectany.md).

Domyślnie **/OPT:REF** jest włączona przez konsolidator, chyba że **podano wartość /OPT:NOREF** lub [/DEBUG.](debug-generate-debug-info.md) Aby zastąpić tę wartość domyślną i zachować w programie nieodnosione identyfikatory COMDATs, należy określić **/OPT:NOREF**. Można użyć opcji [/INCLUDE,](include-force-symbol-references.md) aby zastąpić usunięcie określonego symbolu.

Jeśli [/DEBUG](debug-generate-debug-info.md) jest określony, domyślnie **dla /OPT** jest **NOREF**, a wszystkie funkcje są zachowywane na obrazie. Aby zastąpić tę wartość domyślną i zoptymalizować kompilację debugowania, określ **/OPT:REF**. Może to zmniejszyć rozmiar pliku wykonywalnego i może być użyteczną optymalizacją nawet w kompilacjach debugowania. Zaleca się również określenie **/OPT:NOICF** zachować identyczne funkcje w kompilacjach debugowania. Dzięki temu można łatwiej odczytywać ślady stosu i ustawiać punkty przerwania w funkcjach, które w przeciwnym razie byłyby składane razem.

**Iteracje ICF**\[**=**_iterations_] &#124; **NOICF**

Użyj_iteracji_ **ICF**\[**=**], aby wykonać identyczne składanie COMDAT. Zbędne dane COMDAT mogą być usunięte z danych wyjściowych konsolidatora. Parametr *opcjonalnych iteracji* określa liczbę razy, kiedy symbole mają być przenoszone przez symbole duplikatów. Domyślna liczba iteracji to 1. Dodatkowe iteracje mogą zlokalizować więcej duplikatów, które zostaną odkryte przez składanie w poprzedniej iteracji.

Domyślnie **/OPT:ICF** jest włączona przez konsolidator, chyba że **podano wartość /OPT:NOICF** lub [/DEBUG.](debug-generate-debug-info.md) Aby zastąpić tę wartość domyślną i zapobiec składaniu comdatów w programie, określ **/OPT:NOICF**.

W kompilacji debugowania należy jawnie określić **/OPT:ICF,** aby włączyć składanie COMDAT. Jednak ponieważ **/OPT:ICF** można scalić identyczne dane lub funkcje, można zmienić nazwy funkcji, które pojawiają się w ślady stosu. Może również uniemożliwić ustawienie punktów przerwania w niektórych funkcji lub zbadać niektóre dane w debugerze i może zabrać Cię do nieoczekiwanych funkcji, gdy jednoetapowy kod. Zachowanie kodu jest identyczne, ale prezentacja debugera może być bardzo mylące. W związku z tym nie zaleca się używać **/OPT:ICF** w debugowania kompilacji, chyba że korzyści mniejszego kodu przewyższają te wady.

> [!NOTE]
> Ponieważ **/OPT:ICF** może spowodować, że ten sam adres ma być przypisany do różnych funkcji lub elementów członkowskich danych tylko do odczytu (czyli zmiennych **const** podczas kompilowania przy użyciu **/Gy),** może spowodować przerwanie programu, który zależy od unikatowych adresów dla funkcji lub tylko do odczytu elementów członkowskich danych. Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie na poziomie funkcji)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

Opcje **/OPT:LBR** i **/OPT:NOLBR** mają zastosowanie tylko do plików binarnych ARM. Ponieważ niektóre instrukcje gałęzi procesora ARM mają ograniczony zakres, jeśli konsolidator wykryje skok do adresu poza zakresem, zastępuje adres docelowy instrukcji gałęzi adresem kodem "wyspa", który zawiera instrukcję gałęzi, która jest przeznaczona dla rzeczywistego miejsca docelowego. Można użyć **/OPT:LBR,** aby zoptymalizować wykrywanie długich instrukcji gałęzi i rozmieszczenie wysp kodu pośredniego, aby zminimalizować ogólny rozmiar kodu. **/OPT:NOLBR** instruuje konsolidatora do generowania wysp kodu dla długich instrukcji gałęzi, jak są one napotkane, bez optymalizacji.

Domyślnie opcja **/OPT:LBR** jest ustawiana, gdy łączenie przyrostowe nie jest włączone. Jeśli chcesz łącze niewymiotne, ale nie długie optymalizacje gałęzi, określ **/OPT:NOLBR**. Opcja **/OPT:LBR** wyłącza łączenie przyrostowe.

## <a name="remarks"></a>Uwagi

Gdy jest używany w wierszu polecenia, konsolidator domyślnie **ma wartość /OPT:REF,ICF,LBR**. Jeśli **/DEBUG** jest określony, wartość domyślna to **/OPT:NOREF,NOICF,NOLBR**.

Optymalizacje **/OPT** zazwyczaj zmniejszają rozmiar obrazu i zwiększają szybkość programu. Te ulepszenia mogą być znaczne w większych programach, dlatego są domyślnie włączone dla kompilacji detalicznych.

Optymalizacja konsolidatora zajmuje dodatkowy czas z góry, ale zoptymalizowany kod oszczędza również czas, gdy konsolidator ma mniej relokacji, aby naprawić i tworzy mniejszy obraz końcowy, i oszczędza jeszcze więcej czasu, gdy ma mniej informacji debugowania do przetwarzania i zapisu w PDB. Gdy optymalizacja jest włączona, może to spowodować krótszy czas łącza ogólnej, jak mały dodatkowy koszt w analizie może być więcej niż kompensowane przez oszczędność czasu w konsolidator przechodzi przez mniejsze pliki binarne.

Argumenty **/OPT** mogą być określone razem, oddzielone przecinkami. Na przykład zamiast **/OPT:REF /OPT:NOICF**można określić **/OPT:REF,NOICF**.

Za pomocą konsolidatora [/VERBOSE](verbose-print-progress-messages.md) można wyświetlić funkcje, które są usuwane przez **/OPT:REF,** oraz funkcje, które są składane przez **/OPT:ICF**.

Argumenty **/OPT** są często ustawiane dla projektów utworzonych przy użyciu okna dialogowego **Nowy projekt** w programie Visual Studio IDE i zwykle mają różne wartości dla konfiguracji debugowania i wydania. Jeśli nie ustawiono żadnej wartości dla tych opcji konsolidatora w projekcie, można uzyskać domyślne wartości projektu, które mogą różnić się od wartości domyślnych używanych przez konsolidator w wierszu polecenia.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję OPT:ICF lub OPT:REF konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Wybierz stronę właściwości > **Optymalizacja**  > **konsolidatora**właściwości właściwości **konfiguracji.**

1. Zmodyfikuj jedną z tych właściwości:

   - **Włącz zwijanie COMDAT**

   - **Dokumentacja**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora OPT:LBR w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Wybierz stronę właściwości**wiersza polecenia wiersza**  > **konsolidatora** >  **właściwości konfiguracji.**

1. Wprowadź opcję w opcji **Dodatkowe opcje:**

   `/opt:lbr` lub `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> i właściwości.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
