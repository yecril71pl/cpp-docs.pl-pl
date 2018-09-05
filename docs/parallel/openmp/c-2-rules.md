---
title: C.2 reguły | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb83b35a03608e272e9af67159b61e5dbf4e1ec6
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755024"
---
# <a name="c2-rules"></a>C.2 Reguły
Notacja zostało opisane w sekcji 6.1 c standard. Ten dodatek gramatyki przedstawia rozszerzenia gramatyki języka podstawowego dla dyrektyw OpenMP C i C++.

**/\* w języku C++ (ISO/IEC 14882:1998) \*/**

*seq — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP — dyrektywa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja seq — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seq — instrukcja openmp — dyrektywa*

**/\* w C90 (ISO/IEC 9899:1990) \*/**

*Lista instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP — dyrektywa*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*listę instrukcji, instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista instrukcji openmp — dyrektywa*

**/\* w C99 (ISO/IEC 9899:1999) \*/**

*blokowanie elementu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*OpenMP — dyrektywa*

**/\* Standardowa instrukcji \*/**

*Instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja OpenMP*

*konstrukcja OpenMP*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja równoległych*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dla konstrukcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja sekcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja pojedynczego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*równoległe dla konstrukcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*równoległe sekcje konstruktora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja Master*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcji krytycznej*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja niepodzielna*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*konstrukcja uporządkowane*

*OpenMP — dyrektywa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dyrektywa barrier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dyrektywa Flush*

*blok ze strukturą*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*

*konstrukcja równoległych*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą równoległych — dyrektywa*

*dyrektywa równoległych*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp pragma # równoległe** *klauzuli równoległych*<sub>optseq</sub> *nowy wiersz*

*Klauzula równoległych*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Klauzula unikatowy równoległych*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*klauzuli danych*

*unikatowe klauzuli równoległych*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Jeśli (** *wyrażenie* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**num_threads (** *wyrażenie* **)**

*dla konstrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji iteracji dla dyrektywy*

*dla dyrektywy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp pragma # dla** *klauzuli for*<sub>optseq</sub> *nowy wiersz*

*klauzuli for*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unikatowy dla klauzuli*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*klauzuli danych*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*Unikatowy dla klauzuli*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Uporządkowane**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Harmonogram (** *rodzaj harmonogramu* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Harmonogram (** *rodzaj harmonogramu* **,** *wyrażenie* **)**

*rodzaj harmonogramu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statyczne**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Dynamiczne**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**krok po kroku**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Środowisko uruchomieniowe**

*konstrukcja sekcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekcja zakresu sekcje — dyrektywa*

*dyrektywa sekcje*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sekcje omp pragma #** *klauzuli sekcje*<sub>optseq</sub> *nowy wiersz*

*Klauzula sekcje*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*klauzuli danych*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*zakres sekcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{sekcji sekwencja}*

*sekcja sekwencji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dyrektywy Section*<sub>zoptymalizowany pod kątem</sub> *strukturalnego bloku*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekcja sekwencji dyrektywy section ze strukturą bloku*

*dyrektywy Section*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pragma omp sekcji** *nowy wiersz*

*konstrukcja pojedynczego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą pojedynczej dyrektywy*

*dyrektywa pojedynczego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp pragma # pojedynczego** *pojedynczej klauzuli*<sub>optseq</sub> *nowy wiersz*

*pojedynczej klauzuli*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*klauzuli danych*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**NOWAIT**

*równoległe dla konstrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji iteracji równoległe dla dyrektywy*

*równoległe dla dyrektywy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp pragma # równoległe w** *klauzuli for równoległych*<sub>optseq</sub> *nowy wiersz*

*klauzuli for równoległych*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Klauzula unikatowy równoległych*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unikatowy dla klauzuli*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*klauzuli danych*

*równoległe sekcje konstruktora*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*powiązane sekcji równoległych sekcje — dyrektywa*

*równoległe sekcje dyrektywy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# sekcji równoległych omp pragma** *równoległych sekcje klauzuli*<sub>optseq</sub> *nowy wiersz*

*równoległe sekcje klauzuli*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Klauzula unikatowy równoległych*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*klauzuli danych*

*konstrukcja Master*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą Master dyrektywa*

*wzorzec dyrektywy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**wzorzec omp pragma #** *nowy wiersz*

*konstrukcji krytycznej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą dyrektywy Critical*

*dyrektywy Critical*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp pragma # krytyczne** *frazy region*<sub>zoptymalizowany pod kątem</sub> *nowy wiersz*

*region frazy*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(identyfikator)*

*dyrektywa barrier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp barierę** *nowy wiersz*

*konstrukcja Atomic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja wyrażeń dyrektywy niepodzielnej*

*dyrektywy niepodzielnej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp niepodzielny** *nowy wiersz*

*dyrektywa Flush*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**omp pragma # opróżniania** *var opróżniania*<sub>zoptymalizowany pod kątem</sub> *nowy wiersz*

*var opróżniania*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(zmienna lista)*

*konstrukcja uporządkowane*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*blok ze strukturą uporządkowane — dyrektywa*

*dyrektywa uporządkowane*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**uporządkowane # pragma omp** *nowy wiersz*

**/\* Standardowa deklaracji \*/**

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dyrektywa threadprivate*

*dyrektywa threadprivate*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp threadprivate (** *liście zmiennych***)** *nowy wiersz* 

*klauzuli danych*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**prywatne (** *liście zmiennych* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyprivate (***liście zmiennych***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**firstprivate (***liście zmiennych***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**lastprivate (** *liście zmiennych***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**udostępnione (** *liście zmiennych* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**domyślne (udostępnione)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Domyślnie (Brak)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**redukcja (***operatorem redukcji***:***liście zmiennych***)** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyin (***liście zmiennych***)** 

*operatorem redukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Jeden z:  **+  \* -& ^ &#124; & &&#124;&#124;**

**/\* w języku C \*/**

*Lista zmiennej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista zmiennej* **,** *identyfikator*

**/\* w języku C++ \*/**

*Lista zmiennej*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ID — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista zmiennej* **,** *identyfikator wyrażenia*