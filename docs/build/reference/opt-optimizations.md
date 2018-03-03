---
title: -OPT (optymalizacje) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86427dbf1ac6c3404daa36d2e02786aa80ed6453
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="opt-optimizations"></a>/OPT (Optymalizacje)
Kontroluje optymalizacje, które LINK wykonuje podczas kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/OPT:{REF | NOREF}  
/OPT:{ICF[=iterations] | NOICF}  
/OPT:{LBR | NOLBR}  
```  
  
## <a name="arguments"></a>Argumenty  
 **REF** &#124; **NOREF**  
 **/OPT:REF** eliminuje funkcji i danych, który nie istnieje odwołanie; **/OPT: noref** przechowuje funkcji i danych, który nie istnieje odwołanie.  
  
 Gdy /OFT:REF jest włączone, LINK usuwa opakowane funkcje i dane, do których nie ma odniesień. Obiekt zawiera spakowanych funkcji i danych (Comdat), jeśli został skompilowany przy użyciu [/Gy](../../build/reference/gy-enable-function-level-linking.md) opcji. Ta optymalizacja jest znana jako eliminacja przechodnia (lub tranzytywna) COMDAT. Domyślnie **/OPT:REF** jest włączona w kompilacjach bez debugowania. Aby zastąpić to ustawienie domyślne i przechowywać nieużywane Comdat w programie, należy określić **/OPT: noref**. Można użyć [/INCLUDE](../../build/reference/include-force-symbol-references.md) opcji powoduje usunięcie określony symbol.  
  
 Gdy **/OPT:REF** włączono jawnie lub domyślnie ograniczone **/OPT: ICF** jest włączona który tylko złożeń funkcje identyczne. Jeśli chcesz **/OPT:REF** , ale nie **/OPT: ICF**, należy określić **/OPT:REF, NOICF** lub **noicf**.  
  
 Jeśli [/DEBUG](../../build/reference/debug-generate-debug-info.md) jest określony, wartością domyślną **/OPT** jest **NOREF**, i wszystkie funkcje zostaną zachowane w obrazie. Aby zastąpić to ustawienie domyślne i zoptymalizować kompilacji debugowania, określ **/OPT:REF**. Ponieważ **/OPT:REF** oznacza **/OPT: ICF**, zaleca się, że można również określić **noicf** zachować identyczne funkcji w kompilacjach debugowania. Dzięki temu można łatwiej odczytywać ślady stosu i ustawiać punkty przerwania w funkcjach, które w przeciwnym razie byłyby składane razem. **/OPT:REF** opcja powoduje wyłączenie konsolidowania przyrostowego.  
  
 Należy jawnie oznaczyć `const` dane jako COMDAT; użyj [__declspec(selectany)](../../cpp/selectany.md).  
  
 Określanie **/OPT: ICF** nie obsługuje **/OPT:REF** opcji.  
  
 **ICF [=** `iterations` **] &#124; NOICF**   
 Użyj **/OPT: ICF [=**`iterations`**]** przeprowadzić identycznych sekcji comdat. Zbędne dane COMDAT mogą być usunięte z danych wyjściowych konsolidatora. Opcjonalny `iterations` parametr określa liczbę razy, aby przechodzić między nimi symbole duplikatów. Domyślna liczba iteracji wynosi dwa. Dodatkowe iteracje mogą zlokalizować więcej duplikatów, które zostaną odkryte przez składanie w poprzedniej iteracji.  
  
 Konsolidator zachowuje się inaczej po **/OPT:REF** określono — i **ICF** jest włączona domyślnie — niż podczas **/OPT:REF, Zapora połączenia internetowego** został jawnie określony. Formę **ICF** z włączoną funkcją **/OPT:REF** samodzielnie nie fold danych tylko do odczytu — dotyczy to również .rdata, .pdata i .xdata. W związku z tym złożone są mniej funkcji, gdy obrazy są tworzone dla [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] ponieważ funkcje w tych modułach zależą więcej danych tylko do odczytu — na przykład .pdata i .xdata. Aby uzyskać pełne **ICF** składania zachowanie, jawnie określ **/OPT: ICF**.  
  
 Funkcje należy umieścić w Comdat, należy użyć **/Gy** — opcja kompilatora; można umieścić `const` danych, należy zadeklarować go `__declspec(selectany)`. Aby uzyskać informacje o sposobie określania danych dla składania, zobacz [selectany](../../cpp/selectany.md).  
  
 Domyślnie **ICF** jest włączone, jeśli **REF** znajduje się na. Aby zastąpić to ustawienie domyślne, jeśli **REF** jest określony, użyj **NOICF**. Gdy **/OPT:REF** nie została określona w kompilacji debugowania, należy jawnie określić **/OPT: ICF** umożliwiające zwijaniu sekcji COMDAT. Jednak ponieważ **/OPT: ICF** scalić identyczne dane lub funkcji, można zmienić nazwy funkcji, które są widoczne w śladów stosu. Może również uniemożliwić ustawienie punktów przerwania w pewnych funkcjach lub zbadanie niektórych danych w debugerze, a także przenieść cię do nieoczekiwanych funkcji podczas przechodzenia przez kod w jednym kroku. W związku z tym nie zaleca się używanie **/OPT: ICF** podczas debugowania kompilacje, chyba że niedogodności przeważają korzyści wynikające z mniejszym kodu.  
  
> [!NOTE]
>  Ponieważ **/OPT: ICF** może spowodować, że ten sam adres ma być przypisane do różnych funkcji lub elementy członkowskie danych tylko do odczytu (`const` zmienne skompilowana przy użyciu **/Gy**), mogą być dzielone program, który jest zależny od unikatowe adresy dla funkcji lub elementy członkowskie danych tylko do odczytu. Aby uzyskać więcej informacji, zobacz [/Gy (Włącz funkcję łączenia na poziomie)](../../build/reference/gy-enable-function-level-linking.md).  
  
 **LBR** &#124; **NOLBR**  
 **/OPT:LBR** i **/OPT:NOLBR** opcje są stosowane tylko do plików binarnych ARM. Ponieważ pewne instrukcje gałęzi procesora ARM mają ograniczony zasięg, jeśli konsolidator wykryje skok do adresu spoza zakresu, zastępuje adres docelowy instrukcji gałęzi adresem kodu „wyspy”, który zawiera instrukcję gałęzi, która odnosi się do faktycznego adresu docelowego. Można użyć **/OPT:LBR** w celu zoptymalizowania wykrywania instrukcje gałęzi long i rozmieszczenie Wyspy pośredniego kod aby zminimalizować łącznego rozmiaru kodu. **/OPT:NOLBR** informuje konsolidator, aby wygenerować kod Wyspy instrukcje gałęzi long jako zostaną napotkane, bez optymalizacji.  
  
 Domyślnie **/OPT:LBR** opcja została ustawiona podczas konsolidowania przyrostowego nie jest włączona. -Incremental łącza, ale nie optymalizacje long gałęzi, określić **/OPT:NOLBR**. **/OPT:LBR** opcja powoduje wyłączenie konsolidowania przyrostowego.  
  
## <a name="remarks"></a>Uwagi  
 Optymalizacje ogólnie zmniejszają rozmiar obrazu i zwiększają szybkość programu kosztem zwiększonego czasu łączenia.  
  
 Można użyć [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) opcję, aby zobaczyć funkcje, które zostały usunięte przez **/OPT:REF** i funkcje, które są składane przez **/OPT: ICF**.  
  
### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję OPT:ICF lub OPT:REF konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku po lewej stronie rozwiń **właściwości konfiguracji**, **konsolidatora**, **optymalizacji**.  
  
3.  Zmodyfikuj jedną z tych właściwości:  
  
    -   **Włącz zwijaniu sekcji COMDAT**  
  
    -   **Odwołania**  
  
### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić opcję konsolidatora OPT:LBR w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Wybierz opcję w **dodatkowe opcje**:  
  
     `/opt:lbr`  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)