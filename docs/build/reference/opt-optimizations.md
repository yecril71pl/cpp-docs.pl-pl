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
ms.openlocfilehash: fb59b861bc46c93a3f5fa1b6c6b8d1b73ddefc66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320249"
---
# <a name="opt-optimizations"></a>/OPT (Optymalizacje)

Kontroluje optymalizacje, które LINK wykonuje podczas kompilacji.

## <a name="syntax"></a>Składnia

> **/ OPT:**{**REF** | **NOREF**}<br/>
> **/ OPT:**{**ICF**[**=**_iteracji_] | **NOICF**}<br/>
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Argumenty

**REF** &AMP;#124; **NOREF**

**/ OPT: REF** eliminuje funkcje i dane, które nigdy nie są wywoływane; **/OPT:NOREF** utrzymuje funkcje i dane, które nigdy nie są wywoływane.

/ OPT: REF jest włączone, LINK Usuwa nieużywane spakowane funkcje i dane, znane jako *Comdat*. Ta optymalizacja jest znana jako eliminacja przechodnia (lub tranzytywna) COMDAT. **/OPT: REF** opcji również wyłącza łączenie przyrostowe.

Funkcje śródwierszowe i funkcji składowej zdefiniowanej w obrębie deklaracji klasy są zawsze Comdat. Wszystkie funkcje w pliku obiektu są wykonywane w Comdat, gdy jest kompilowany przy użyciu [/Gy](gy-enable-function-level-linking.md) opcji. Aby umieścić **const** dane w Comdat, należy zadeklarować ją za pomocą `__declspec(selectany)`. Aby uzyskać informacje dotyczące sposobu określania danych do usunięcia lub zwijanie, zobacz [selectany](../../cpp/selectany.md).

Domyślnie **/OPT: REF** został włączony przez konsolidator, chyba że **/OPT:NOREF** lub [/DEBUG](debug-generate-debug-info.md) jest określony. Aby zastąpić to ustawienie domyślne i zachować COMDATs bez odwołań w programie, określ **/OPT:NOREF**. Możesz użyć [/INCLUDE](include-force-symbol-references.md) opcję, aby zastąpić usunięcie określonego symbolu.

Jeśli [/DEBUG](debug-generate-debug-info.md) jest określony, wartość domyślna dla **/OPT** jest **NOREF**, a wszystkie funkcje są zachowywane w obrazie. Aby zastąpić to ustawienie domyślne i zoptymalizować kompilację debugowania, określ **/OPT: REF**. Można zmniejszyć rozmiar plik wykonywalny i mogą być przydatne optymalizacji, nawet w przypadku debugowania kompilacji. Firma Microsoft zaleca również określenie **noicf** zachować identyczne funkcje podczas debugowania kompilacji. Dzięki temu można łatwiej odczytywać ślady stosu i ustawiać punkty przerwania w funkcjach, które w przeciwnym razie byłyby składane razem.

**ICF**\[**=**_iterations_] &#124; **NOICF**

Użyj **ICF**\[**=**_iteracji_] Aby wykonać identyczne składanie COMDAT. Zbędne dane COMDAT mogą być usunięte z danych wyjściowych konsolidatora. Opcjonalny *iteracji* parametr określa, ile razy przenosić symbole dla duplikatów. Domyślna liczba iteracji wynosi 1. Dodatkowe iteracje mogą zlokalizować więcej duplikatów, które zostaną odkryte przez składanie w poprzedniej iteracji.

Domyślnie **/OPT: ICF** został włączony przez konsolidator, chyba że **noicf** lub [/DEBUG](debug-generate-debug-info.md) jest określony. Aby zastąpić to ustawienie domyślne i uniemożliwić Comdat jest składanych w programie, określ **noicf**.

Do kompilacji debugowanej, należy jawnie określić **/OPT: ICF** aby umożliwić składanie COMDAT. Jednak ponieważ **/OPT: ICF** może scalić identyczne dane lub funkcje, może zmienić nazwy funkcji, które pojawiają się w śladach stosu. Może także spowodować, że można ustawić punktów przerwania w pewnych funkcjach lub zbadanie niektórych danych w debugerze i przejście do nieoczekiwanych funkcji po użytkownik pojedynczy krok przeglądania kodu. Zachowania kodu są identyczne, ale prezentacji debuger może być bardzo mylące. W związku z tym, nie zaleca się używanie **/OPT: ICF** w przypadku debugowania kompilacji, chyba że korzyści wynikające z mniejszego kodu przewyższają niedogodności.

> [!NOTE]
> Ponieważ **/OPT: ICF** może spowodować, że ten sam adres, który ma być przypisane do różnych funkcji lub elementów członkowskich danych tylko do odczytu (czyli **const** zmiennych, gdy kompilowany przy użyciu **/Gy**), może przerwać program, który zależy od unikatowych adresów dla funkcji lub elementów członkowskich danych tylko do odczytu. Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie poziomie funkcji)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

**/OPT:LBR** i **nolbr** opcje dotyczą tylko plików binarnych ARM. Ponieważ pewne instrukcje gałęzi procesora ARM mają ograniczony zasięg, jeśli konsolidator wykryje skok do adresu spoza zakresu, zastępuje adres docelowy instrukcji gałęzi adresem kodu „wyspy”, który zawiera instrukcję gałęzi, która odnosi się do faktycznego adresu docelowego. Możesz użyć **/OPT:LBR** Aby zoptymalizować wykrywanie instrukcji długich gałęzi i położenie pośrednich Wysp kodu do zminimalizowania całkowitego rozmiaru kodu. **Nolbr** powoduje, że konsolidator generuje Wyspy kodu dla instrukcji długich gałęzi po ich napotkaniu, bez optymalizacji.

Domyślnie **/OPT:LBR** opcja jest ustawiona, gdy łączenie przyrostowe nie jest włączone. Jeśli chcesz nieprzyrostowego łącza, ale nie chcesz długich optymalizacji rozgałęzień, określ **nolbr**. **/OPT:LBR** opcji wyłącza łączenie przyrostowe.

## <a name="remarks"></a>Uwagi

W przypadku użycia, w wierszu polecenia, konsolidator wartość domyślna to **LBR/OPT: REF, ICF,**. Jeśli **/DEBUG** jest określony, wartością domyślną jest **NOLBR /OPT:NOREF, NOICF,**.

**/OPT** optymalizacje ogólnie zmniejszają rozmiar obrazu i zwiększają szybkość programu. Te ulepszenia mogą być istotne w przypadku większych programów, dlatego są one włączone domyślnie dla sprzedaży detalicznej.

Optymalizacji konsolidatora zająć dodatkowy czas na początku, ale zoptymalizowanego kodu również pozwala zaoszczędzić czas, kiedy konsolidator relokacje mniej można naprawić i tworzy mniejsze finalnego obrazu i zaoszczędzić jeszcze więcej czas, kiedy ma mniej informacji debugowania, aby przetworzyć i zapisać w pliku PDB. Kiedy Optymalizacja jest włączona, dzięki temu może skrócić czas łącza, zgodnie z niewielkim kosztem dodatkowej analizy mogą być zrównoważone przez czas, który oszczędności w konsolidatorze przesuwa się nad mniejsze pliki binarne.

**/OPT** argumenty można określić razem, oddzielonych przecinkami. Na przykład, zamiast z **/OPT: REF noicf**, można określić **/OPT: REF, NOICF**.

Możesz użyć [/VERBOSE](verbose-print-progress-messages.md) opcję konsolidatora, aby zobaczyć funkcje, które są usuwane przez **/OPT: REF** i funkcje, które są składane przez **/OPT: ICF**.

**/OPT** argumentów jest często skonfigurowane dla projektów utworzonych za pomocą **nowy projekt** okna dialogowego w programie Visual Studio IDE i zwykle mają różne wartości do debugowania i zwalniania konfiguracji. Jeśli wartość nie jest ustawiona dla tych opcji konsolidatora w projekcie, możesz uzyskać wartości domyślne projektu, które mogą być inne niż wartości domyślne używane przez konsolidator, w wierszu polecenia.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję OPT:ICF lub OPT:REF konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** stronę właściwości.

1. Zmodyfikuj jedną z tych właściwości:

   - **Włącz zwijanie COMDAT**

   - **Odwołania**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora OPT:LBR w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje**:

   `/opt:lbr` lub `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> właściwości.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
