---
title: 1.2 definicje terminów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8563bb757ad8d30f1639f017769bfd6c4084efa0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688599"
---
# <a name="12-definition-of-terms"></a>1.2 Definicje terminów
Poniższe terminy są używane w tym dokumencie:  
  
 ograniczenie  
 Punkt synchronizacji, który musi zostać osiągnięta przez wszystkie wątki w zespole.  Każdy wątek oczekuje, aż wszystkie wątki w zespole odbierane w tym momencie. Brak jawnego bariery identyfikowane przez dyrektywy i niejawne bariery utworzone przez implementację.  
  
 konstrukcja  
 Konstrukcję jest oświadczenie. Składa się z dyrektywą i kolejne strukturalnego bloku. Należy pamiętać, że niektóre dyrektywy nie są częścią konstrukcji. (Zobacz *OpenMP — dyrektywa* w [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)).  
  
 Dyrektywy  
 C lub C++ **#pragma** następuje **omp** identyfikator, tekst i znakiem nowego wiersza. Dyrektywa określa zachowanie programu.  
  
 zakres dynamiczny  
 Wszystkie instrukcje w *leksykalne zakres*, oraz żadnej instrukcji wewnątrz funkcji, która jest wykonywana w wyniku wykonania instrukcji w zakresie leksykalne. Zakres dynamiczny jest również nazywany *region*.  
  
 zakres leksykalne  
 Instrukcje lexically zawartych w *strukturalnego bloku*.  
  
 głównym wątku  
 Wątek, który tworzy zespół podczas *równoległego regionu* została wprowadzona.  
  
 równoległego regionu  
 Instrukcje, które należy powiązać konstrukcję parallel OpenMP i mogą być wykonywane przez wiele wątków.  
  
 private  
 W nazwach zmiennych prywatnych, blok pamięci, która jest unikatowa dla wątku odniesienia. Należy pamiętać, że istnieje kilka sposobów, aby określić, czy zmienna jest prywatny: definicję w ramach równoległego regionu **threadprivate** dyrektywy **prywatnej**, **firstprivate**, **lastprivate**, lub **redukcji** klauzulę lub użyj zmiennej jako **dla**zmienna sterująca pętli w **dla** pętli bezpośrednio po **dla** lub **równoległe w** dyrektywy.  
  
 region  
 Zakres dynamiczny.  
  
 region szeregowe  
 Instrukcje wykonywane tylko przez *głównego wątku* poza zakres dynamiczny żadnego *równoległego regionu*.  
  
 serializacji  
 Do wykonania konstrukcję równolegle z zespołem wątków składające się z tylko jednego wątku (czyli głównego wątku dla tej konstrukcji równoległe), serial kolejności wykonywania instrukcji strukturalnego bloku (takie same kolejność tak, jakby nie były bloku części równoległe konstrukcji) i nie wpływa na wartość zwrócona przez **omp_in_parallel()** (oprócz skutków żadnego zagnieżdżone równoległe konstrukcje).  
  
 udostępnione  
 Udostępniona zmienna nazwy pojedynczy blok pamięci masowej. Wszystkie wątki w zespole, które uzyskują dostęp do tej zmiennej będą uzyskiwać dostęp do tego bloku jednego magazynu.  
  
 strukturalnego bloku  
 Strukturalnego bloku jest pojedynczy wpis, oraz jednego zakończenia instrukcji (pojedynczy lub złożony). Oświadczenia wynosi strukturalnego bloku skok do lub z tej instrukcji (tym wywołaniu **longjmp**(3 C) lub korzystanie z **throw**, ale wywołanie **zakończyć** jest dozwolona). Instrukcja złożona jest strukturalnego bloku, jeśli jego wykonywania zawsze zaczyna się od otwarcia **{** i zawsze kończy się na zamknięcie **}**. Instrukcja wyrażeń, wybór instrukcji, instrukcji iteracji lub **spróbuj** blok jest strukturalnego bloku uzyskane odpowiedniej instrukcji złożonej, umieszczając je w **{** i **}** byłoby strukturalnego bloku. Skok oświadczenie, instrukcja labeled lub instrukcji deklaracji nie jest strukturalnego bloku.  
  
 Zespołu  
 Jeden lub więcej wątków współpracujących podczas wykonywania konstrukcji.  
  
 wątek  
 Jednostka wykonywania o serial przepływu sterowania, zestaw zmiennych prywatnych i dostęp do udostępnionych zmiennych.  
  
 zmienna  
 Identyfikator, opcjonalnie kwalifikowana przez nazwy przestrzeni nazw, nazwę obiektu.