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
ms.openlocfilehash: a3bdf26435fdfeea2196b9ef281d656805f51bf2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694995"
---
# <a name="c2-rules"></a>C.2 Reguły
Notacja została opisana w sekcji 6.1 C standard. Ten dodatek gramatyka zawiera rozszerzenia do gramatyki języka podstawowego dla dyrektywy OpenMP C i C++.  
  
 **/\* w języku C++ (ISO/IEC 14882:1998) \*/**  
  
 *seq — instrukcja*:  
  
 *— Instrukcja*  
  
 *OpenMP — dyrektywa*  
  
 *Instrukcja seq — instrukcja*  
  
 *seq — instrukcja openmp — dyrektywa*  
  
 **/\* w C90 (ISO/IEC 9899:1990) \*/**  
  
 *Lista instrukcji*:  
  
 *— Instrukcja*  
  
 *OpenMP — dyrektywa*  
  
 *Instrukcja listy — instrukcja*  
  
 *Lista instrukcji openmp — dyrektywa*  
  
 **/\* w C99 (ISO/IEC 9899:1999) \*/**  
  
 *element bloku*:  
  
 *Deklaracja*  
  
 *— Instrukcja*  
  
 *OpenMP — dyrektywa*  
  
 *Instrukcja*:  
  
 **/\* Standardowa — instrukcje \*/**  
  
 *konstrukcja OpenMP*  
  
 *OpenMP — konstrukcja*:  
  
 *konstrukcja równoległe*  
  
 *dla konstrukcji*  
  
 *konstrukcja sekcji*  
  
 *konstrukcja pojedynczej*  
  
 *równoległe dla konstrukcji*  
  
 *równoległe sekcje — konstrukcja*  
  
 *wzorzec construc*  
  
 *konstrukcja krytyczna*  
  
 *konstrukcja niepodzielna*  
  
 *konstrukcja uporządkowana*  
  
 *dyrektywy OpenMP*:  
  
 *bariera — dyrektywa*  
  
 *dyrektywa opróżniania*  
  
 *Blok strukturę*:  
  
 *— Instrukcja*  
  
 *konstrukcja równoległe*:  
  
 *Blok strukturę równoległe — dyrektywa*  
  
 *dyrektywa równoległe*:  
  
 **# pragma omp parallel***równoległe klauzuli*optseq *nowy wiersz*   
  
 *równoległe klauzuli*:  
  
 *Klauzula unikatowy równoległe*  
  
 *Klauzula danych*  
  
 *Klauzula unikatowy równoległe*:  
  
 **Jeśli (** *wyrażenie* **)**  
  
 **num_threads (** *wyrażenie* **)**  
  
 *dla konstrukcji*:  
  
 *instrukcji iteracji dla dyrektywy*  
  
 *dla dyrektywy*:  
  
 **omp pragma # dla** *klauzuli for*optseq *nowy wiersz*  
  
 *klauzuli for*:  
  
 *Unikatowy dla klauzuli*  
  
 *Klauzula danych*  
  
 **nowait**  
  
 *Unikatowy dla klauzuli*:  
  
 **uporządkowane**  
  
 **Harmonogram (** *rodzaj harmonogramu* **)**  
  
 **Harmonogram (** *rodzaj harmonogramu* **,** *wyrażenie* **)**  
  
 *rodzaj harmonogramu*:  
  
 **static**  
  
 **dynamic**  
  
 **Przewodnik**  
  
 **Środowisko uruchomieniowe**  
  
 *konstrukcja sekcji*:  
  
 *sekcja zakresie sekcje — dyrektywa*  
  
 *dyrektywa sekcje*:  
  
 **sekcje omp pragma #** *klauzuli sekcje*optseq *nowy wiersz*  
  
 *Klauzula sekcje*:  
  
 *Klauzula danych*  
  
 **nowait**  
  
 *zakres sekcji*:  
  
 *{sekcji sekwencji}*  
  
 *sekcja sekwencji*:  
  
 *dyrektywę sekcji*opt *strukturalnego bloku*  
  
 *sekcja sekwencji dyrektywę sekcji strukturę bloku*  
  
 *dyrektywę sekcji*:  
  
 **# pragma omp sekcji** *nowy wiersz*  
  
 *konstrukcja jednym*:  
  
 *Blok strukturę jednym — dyrektywa*  
  
 *dyrektywa jednym*:  
  
 **# pragma omp pojedynczego** *pojedynczej klauzuli*optseq *nowy wiersz*  
  
 *Klauzula jednym*:  
  
 *Klauzula danych*  
  
 **nowait**  
  
 *równoległe dla konstrukcji*:  
  
 *równoległe dla dyrektywy iteracji — instrukcja*  
  
 *równoległe dla dyrektywy*:  
  
 **# pragma omp parallel dla** *klauzuli for parallel*optseq *nowy wiersz*  
  
 *równoległe dla klauzuli*:  
  
 *Klauzula unikatowy równoległe*  
  
 *Unikatowy dla klauzuli*  
  
 *Klauzula danych*  
  
 *równoległe sekcje — konstrukcja*:  
  
 *równoległe sekcje dyrektywa sekcji scope*  
  
 *równoległe sekcje dyrektywa*:  
  
 **# pragma omp parallel sekcje** *równoległe sekcje klauzuli*optseq *nowy wiersz*  
  
 *równoległe sekcje klauzuli*:  
  
 *Klauzula unikatowy równoległe*  
  
 *Klauzula danych*  
  
 *konstrukcja wzorca*:  
  
 *dyrektywy Master strukturę bloku*  
  
 *dyrektywa wzorca*:  
  
 **wzorzec omp pragma #** *nowy wiersz*  
  
 *konstrukcja krytyczna*:  
  
 *krytyczne dyrektywy strukturę — blok*  
  
 *krytyczne dyrektywy*:  
  
 **krytyczne omp pragma #** *frazy region*opt *nowy wiersz*  
  
 *region frazy*:  
  
 *(identyfikator)*  
  
 *dyrektywa bariery*:  
  
 **bariera omp pragma #** *nowy wiersz*  
  
 *konstrukcja niepodzielna*:  
  
 *Instrukcja wyrażeń Atomic — dyrektywa*  
  
 *dyrektywa Atomic*:  
  
 **# pragma omp niepodzielny** *nowy wiersz*  
  
 *dyrektywa opróżniania*:  
  
 **# pragma omp opróżniania** *vars opróżniania*opt *nowy wiersz*  
  
 *Flush vars*:  
  
 *(zmiennej listy)*  
  
 *konstrukcja uporządkowana*:  
  
 *dyrektywa uporządkowane strukturę — blok*  
  
 *dyrektywa uporządkowane*:  
  
 **uporządkowane # pragma omp** *nowy wiersz*  
  
 *Deklaracja*:  
  
 **/\* deklaracje standardowe \*/**  
  
 *threadprivate — dyrektywa*  
  
 *dyrektywa threadprivate*:  
  
 **# pragma omp threadprivate (** *zmiennej listy***)** *nowy wiersz*   
  
 *Klauzula danych*:  
  
 **prywatne (** *zmiennej listy* **)**  
  
 **copyprivate (***zmiennej listy***)**   
  
 **firstprivate (***zmiennej listy***)**   
  
 **lastprivate (** *zmiennej listy***)**   
  
 **udostępnione (** *zmiennej listy* **)**  
  
 **domyślne (wspólna)**  
  
 **Domyślnie (Brak)**  
  
 **redukcja (***operatorem redukcji***:***zmiennej listy***)**   
  
 **copyin (***zmiennej listy***)**   
  
 *operatorem redukcji*:  
  
 *Jeden z*:  **+  \* -& ^ &#124; & &&#124;&#124;**  
  
 **/\* w języku C \*/**  
  
 *Zmienna listy*:  
  
 *Identyfikator*  
  
 *Zmienna listy* **,** *identyfikator*  
  
 **/\* w języku C++ \*/**  
  
 *Zmienna listy*:  
  
 *Identyfikator wyrażenia*  
  
 *Zmienna listy* **,** *identyfikator wyrażenia*