---
title: C. Gramatyka OpenMP C i C++
ms.date: 01/16/2019
ms.assetid: 97a878ce-1533-47f7-a134-66fcbff48524
ms.openlocfilehash: 85e18161079b49e83cc9fedb3184ee220c889e75
ms.sourcegitcommit: 2ebbf8093fadb9a1b78a4381439bcd5c01a89267
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397358"
---
# <a name="c-openmp-c-and-c-grammar"></a>C. Gramatyka OpenMP C i C++

[C.1 Notacja](#c1-notation)<br/>
[C.2 Reguły](#c2-rules)

## <a name="c1-notation"></a>C.1 Notacja

Reguły gramatyki składają się z nazwy dla inny niż końcowy, następuje dwukropek, następuje zastąpienie alternatywy w osobnych wierszach.

Termin składni wyrażenia<sub>zoptymalizowany pod kątem</sub> wskazuje, że termin jest opcjonalna w ramach wymiany.

Składni wyrażenia *termin*<sub>optseq</sub> jest odpowiednikiem *termin seq*<sub>zoptymalizowany pod kątem</sub> z następujące reguły dodatkowe:

*termin seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Termin*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termin seq* *termin*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*termin seq* `,` *termin* 

## <a name="c2-rules"></a>C.2 Reguły

Notacja zostało opisane w sekcji 6.1 c standard. Ten dodatek gramatyki przedstawia rozszerzenia gramatyki języka podstawowego dla dyrektyw OpenMP C i C++.

**/\* w języku C++ (ISO/IEC 14882:1998) \*/**

*statement-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja seq — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seq — instrukcja openmp — dyrektywa*

**/\* w C90 (ISO/IEC 9899:1990) \*/**

*Lista instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*listę instrukcji, instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista instrukcji openmp — dyrektywa*

**/\* w C99 (ISO/IEC 9899:1999) \*/**

*block-item*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*

**/\* Standardowa instrukcji \*/**

*Instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja OpenMP*

*konstrukcja OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja pojedynczego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-for-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ordered-construct*

*OpenMP — dyrektywa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*barrier-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dyrektywa Flush*

*blok ze strukturą*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*

*parallel-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą równoległych — dyrektywa*

*parallel-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel` *Klauzula równoległych*<sub>optseq</sub> *nowy wiersz*

*parallel-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*unique-parallel-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `if (` *Wyrażenie*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `num_threads (` *Wyrażenie*   `)`

*dla konstrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji iteracji dla dyrektywy*

*dla dyrektywy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp for` *klauzuli for*<sub>optseq</sub> *nowy wiersz*

*for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*unique-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `ordered`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *Typ harmonogramu*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *rodzaj harmonogramu* `,` *wyrażenia*    `)`

*rodzaj harmonogramu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `static`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `dynamic`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `guided`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `runtime`

*sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekcja zakresu sekcje — dyrektywa*

*dyrektywa sekcje*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp sections` *Klauzula sekcje*<sub>optseq</sub> *nowy wiersz*

*sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*zakres sekcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{sekcji sekwencja}*

*sekcja sekwencji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-directive*<sub>opt</sub> *structured-block*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-sequence section-directive structured-block*

*dyrektywy Section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp section` *nowy wiersz*

*konstrukcja pojedynczego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą pojedynczej dyrektywy*

*dyrektywa pojedynczego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp single` *pojedynczej klauzuli*<sub>optseq</sub> *nowy wiersz*

*pojedynczej klauzuli*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*parallel-for-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji iteracji równoległe dla dyrektywy*

*parallel-for-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel for` *klauzuli for równoległych*<sub>optseq</sub> *nowy wiersz*

*parallel-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*parallel-sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*powiązane sekcji równoległych sekcje — dyrektywa*

*parallel-sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel sections` *parallel-sections-clause*<sub>optseq</sub> *new-line*

*parallel-sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*master-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą Master dyrektywa*

*master-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp master` *nowy wiersz*

*konstrukcji krytycznej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą dyrektywy Critical*

*critical-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp critical` *region frazy*<sub>zoptymalizowany pod kątem</sub> *nowy wiersz*

*region frazy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(identyfikator)*

*barrier-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp barrier` *nowy wiersz*

*atomic-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja wyrażeń dyrektywy niepodzielnej*

*dyrektywy niepodzielnej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp atomic` *nowy wiersz*

*dyrektywa Flush*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp flush` *var opróżniania*<sub>zoptymalizowany pod kątem</sub> *nowy wiersz*

*var opróżniania*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(zmienna lista)*

*ordered-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą uporządkowane — dyrektywa*

*dyrektywa uporządkowane*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp ordered` *nowy wiersz*

**/\* Standardowa deklaracji \*/**

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate-directive*

*threadprivate-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp threadprivate (` *Lista zmiennej* `)` *nowy wiersz* 

*data-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `private (` *Lista zmiennych*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyprivate (`  *Lista zmiennych*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `firstprivate (`  *Lista zmiennych*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `lastprivate (` *Lista zmiennych*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `shared (` *Lista zmiennych*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( shared )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( none )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `reduction (`  *operatorem redukcji*`:`*liście zmiennych*     `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyin (`  *Lista zmiennych*    `)`

*operatorem redukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Jeden z:   `+ \* - & ^ | && ||`

**/\* w języku C \*/**

*Lista zmiennej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista zmiennej* `,` *identyfikator* 

**/\* w języku C++ \*/**

*Lista zmiennej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*id-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista zmiennej* `,` *identyfikator wyrażenia* 
