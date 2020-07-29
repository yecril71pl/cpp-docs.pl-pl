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
ms.openlocfilehash: 874c4b974348d1bef8c8c3837f46c1c27d6d304b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215195"
---
# <a name="opt-optimizations"></a>/OPT (Optymalizacje)

Kontroluje optymalizacje, które LINK wykonuje podczas kompilacji.

## <a name="syntax"></a>Składnia

> **/OPT:**{**ref**  |  **NOREF**} \
> **/OPT:**{**ICF**[ **=** _iteracje_] | **NOICF**} \
> **/OPT:**{**LBR**  |  **NOLBR**}

## <a name="arguments"></a>Argumenty

**NOREF** **ref** &#124;

**/OPT: ref** eliminuje funkcje i dane, które nigdy nie są przywoływane; **/OPT: NOREF** utrzymuje funkcje i dane, które nigdy nie są przywoływane.

Gdy/OPT: REF jest włączona, LINK usuwa spakowane funkcje i dane, znane jako *COMDAT*. Ta optymalizacja jest znana jako eliminacja przechodnia (lub tranzytywna) COMDAT. Opcja **/OPT: ref** wyłącza również łączenie przyrostowe.

Wbudowane funkcje i funkcje członkowskie zdefiniowane wewnątrz deklaracji klasy są zawsze COMDAT. Wszystkie funkcje w pliku obiektu są wprowadzane do COMDAT, jeśli są kompilowane przy użyciu opcji [/Gy](gy-enable-function-level-linking.md) . Aby umieścić **`const`** dane w COMDAT, należy je zadeklarować za pomocą `__declspec(selectany)` . Aby uzyskać informacje na temat sposobu określania danych do usunięcia lub złożenia, zobacz [selectany](../../cpp/selectany.md).

Domyślnie **/OPT: ref** jest włączany przez konsolidator, chyba że określono **/OPT: NOREF** lub [/Debug](debug-generate-debug-info.md) . Aby zastąpić to ustawienie domyślne i zachować COMDAT bez odwołań w programie, należy określić **/OPT: NOREF**. Można użyć opcji [/include](include-force-symbol-references.md) , aby zastąpić usunięcie określonego symbolu.

Jeśli jest określona opcja [/Debug](debug-generate-debug-info.md) , wartością domyślną dla **/opt** jest **NOREF**, a wszystkie funkcje są zachowywane w obrazie. Aby zastąpić to ustawienie domyślne i zoptymalizować kompilację debugowania, należy określić **/OPT: ref**. Może to zmniejszyć rozmiar pliku wykonywalnego i może być przydatna Optymalizacja nawet w kompilacjach debugowania. Zalecamy również określenie **/OPT: NOICF** , aby zachować identyczne funkcje w kompilacjach debugowania. Dzięki temu można łatwiej odczytywać ślady stosu i ustawiać punkty przerwania w funkcjach, które w przeciwnym razie byłyby składane razem.

**Zapora ICF** \[ **=** _iteracje_] &#124; **NOICF**

Użyj iteracji usługi **ICF** \[ **=** _iterations_], aby wykonać identyczne składanie COMDAT. Zbędne dane COMDAT mogą być usunięte z danych wyjściowych konsolidatora. Opcjonalne parametry *iteracji* określają, ile razy mają być przenoszone symbole dla duplikatów. Domyślna liczba iteracji wynosi 1. Dodatkowe iteracje mogą zlokalizować więcej duplikatów, które zostaną odkryte przez składanie w poprzedniej iteracji.

Domyślnie **/OPT: Zapora ICF** jest włączana przez konsolidator, chyba że określono **/OPT: NOICF** lub [/Debug](debug-generate-debug-info.md) . Aby zastąpić to ustawienie domyślne i zapobiec składaniu COMDAT w programie, należy określić **/OPT: NOICF**.

W kompilacji debugowania należy jawnie określić **/OPT: ICF** , aby umożliwić składanie COMDAT. Jednak ponieważ **/OPT: ICF** może scalać identyczne dane lub funkcje, może zmienić nazwy funkcji, które pojawiają się w śladach stosu. Może również uniemożliwić ustawienie punktów przerwania w niektórych funkcjach lub przeanalizować niektóre dane w debugerze i może przejść do nieoczekiwanych funkcji podczas wykonywania pojedynczych kroków w kodzie. Zachowanie kodu jest identyczne, ale Prezentacja debugera może być bardzo myląca. W związku z tym nie zaleca się używania **/OPT: ICF** w kompilacjach debugowania, chyba że zalety mniejszego kodu przekraczają te wady.

> [!NOTE]
> Ponieważ **/OPT: ICF** może spowodować, że ten sam adres zostanie przypisany do różnych funkcji lub elementów członkowskich danych tylko do odczytu (czyli **`const`** zmienne po skompilowaniu za pomocą **/Gy**), może przerwać program, który zależy od unikatowych adresów dla funkcji lub elementów członkowskich danych tylko do odczytu. Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie na poziomie funkcji)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

Opcje **/OPT: LBR** i **/OPT: NOLBR** dotyczą tylko plików binarnych ARM. Ponieważ pewne instrukcje gałęzi procesora ARM mają ograniczony zakres, jeśli konsolidator wykryje przeskoczenie do adresu spoza zakresu, zastępuje adres docelowy instrukcji gałęzi adresem o adresie "Wyspa", który zawiera instrukcję gałęzi, która jest przeznaczona dla rzeczywistej lokalizacji docelowej. Można użyć **/OPT: LBR** , aby zoptymalizować wykrywanie instrukcji długich gałęzi i rozmieszczenia pośrednich wysp kodu w celu zminimalizowania ogólnego rozmiaru kodu. **/OPT: NOLBR** nakazuje konsolidatorowi generowanie wysp kodu dla długich instrukcji gałęzi w miarę ich napotkania, bez optymalizacji.

Domyślnie opcja **/OPT: LBR** jest ustawiana, gdy łączenie przyrostowe nie jest włączone. Jeśli chcesz utworzyć łącze nieprzyrostowe, ale nie długotrwałe optymalizacje gałęzi, określ **/OPT: NOLBR**. Opcja **/OPT: LBR** wyłącza łączenie przyrostowe.

## <a name="remarks"></a>Uwagi

W przypadku użycia w wierszu polecenia, konsolidator domyślnie ustawia **/OPT: REF, ICF, LBR**. Jeśli jest określona opcja **/Debug** , wartość domyślna to **/OPT: NOREF, NOICF, NOLBR**.

Optymalizacje **/opt** zazwyczaj zmniejszają rozmiar obrazu i zwiększają szybkość działania programu. Te ulepszenia mogą być istotne w większych programach, dlatego są one domyślnie włączone dla kompilacji detalicznych.

Optymalizacja konsolidatora zajmuje dodatkowy czas na początku, ale zoptymalizowany kod również zapisuje czas, gdy konsolidator ma mniejszą relokację w celu usunięcia i utworzenia mniejszego obrazu końcowego i zapisuje jeszcze więcej czasu, gdy ma mniej informacji debugowania do przetwarzania i zapisywania w pliku PDB. Gdy Optymalizacja jest włączona, może skutkować szybszym czasem łączenia, ponieważ niewielki dodatkowy koszt analizy może być wyższy niż przesunięty przez oszczędność czasu w konsolidatorze w przypadku mniejszych plików binarnych.

Argumenty **/opt** można określić razem, rozdzielając je przecinkami. Na przykład zamiast **/OPT: ref/OPT: NOICF**, można określić **/OPT: REF, NOICF**.

Aby zobaczyć funkcje, które są usuwane przez **/OPT: ref** i funkcje, które są składane przez **/OPT: ICF**, można użyć opcji [/verbose](verbose-print-progress-messages.md) konsolidatora.

Argumenty **/opt** są często ustawiane dla projektów utworzonych przy użyciu okna dialogowego **Nowy projekt** w środowisku IDE programu Visual Studio i zazwyczaj mają różne wartości dla konfiguracji debugowania i wydań. Jeśli nie ustawiono żadnej wartości dla tych opcji konsolidatora w projekcie, możesz uzyskać wartości domyślne projektu, które mogą się różnić od wartości domyślnych używanych przez konsolidator w wierszu polecenia.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję OPT:ICF lub OPT:REF konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  **Linker**  >  stronę właściwości**optymalizacji** konsolidatora właściwości konfiguracji.

1. Zmodyfikuj jedną z tych właściwości:

   - **Włącz zwijanie COMDAT**

   - **Dokumentacja**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora OPT:LBR w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja właściwości**  >  **Linker**  >  **wiersza polecenia** konsolidatora.

1. Wprowadź opcję w opcjach **dodatkowych**:

   `/opt:lbr` lub `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> właściwości.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja konsolidatora MSVC](linking.md)
- [MSVC Opcje konsolidatora](linker-options.md)
