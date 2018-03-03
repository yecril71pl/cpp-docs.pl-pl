---
title: Automatyczna Paralelizacja i Wektoryzacja | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b458dbe06bd69817c659c3bfec1d1ab7a216d1f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Automatyczna paralelizacja i wektoryzacja
Automatyczny Paralelizator i Wektoryzowania automatycznego są przeznaczone do zapewnienia wzrost wydajności automatyczne pętle w kodzie.  
  
## <a name="auto-parallelizer"></a>Automatyczny Paralelizator  
 [/Qpar](../build/reference/qpar-auto-parallelizer.md) przełącznik kompilator umożliwia *automatyczna paralelizacja* pętli w kodzie. Po określeniu tej flagi bez zmiany istniejącego kodu kompilator oblicza kod, aby znaleźć pętli, które mogą korzystać z paralelizacja. Ponieważ może odnaleźć pętli, które nie wykonują większość pracy i w związku z tym nie będzie korzystać z paralelizacja i ponieważ każdy niepotrzebnych paralelizacja może stanowić zagrożenie duplikowanie puli wątków, dodatkowe synchronizacji lub inne przetwarzania, które mogą one spowolnić wydajność zamiast ulepszeń, kompilator jest zachowawcze w pętli, które go parallelizes zaznaczenie. Rozważmy na przykład poniższy przykład, w którym górna granica pętli nie jest znany w czasie kompilacji:  
  
```cpp  
void loop_test(int u) {  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 Ponieważ `u` może być mała wartość, kompilator nie będzie automatycznie parallelize pętlę. Jednak nadal może być ona zarządzana przetwarzaniem, ponieważ wiadomo, że `u` będzie zawsze duże. Aby włączyć automatyczna paralelizacja, określ [#pragma loop(hint_parallel(n))](../preprocessor/loop.md), gdzie `n` jest to liczba wątków, aby parallelize między. W poniższym przykładzie kompilator będzie podejmować próby parallelize pętli między 8 wątków.  
  
```cpp  
void loop_test(int u) {  
#pragma loop(hint_parallel(8))  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 Jak w przypadku wszystkich [dyrektywy pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), składni alternatywnej pragma `__pragma(loop(hint_parallel(n)))` jest również obsługiwany.  
  
 Brak niektórych pętli, które kompilator nie parallelize, nawet jeśli ma być. Oto przykład:  
  
```cpp  
#pragma loop(hint_parallel(8))  
for (int i=0; i<upper_bound(); ++i)  
    A[i] = B[i] * C[i];  
```  
  
 Funkcja `upper_bound()` może zmieniać się za każdym razem, gdy jest ona wywoływana. Ponieważ górna granica nie może być znane, kompilator może emitować diagnostycznych komunikat, który wyjaśnia, dlaczego nie mogę parallelize pętlę. W poniższym przykładzie pokazano pętli, które mogą być zarządzana z przetwarzaniem, pętli, które nie może być zarządzana z przetwarzaniem kompilatora składni stosowanej w wierszu polecenia, a dane wyjściowe kompilatora, dla każdej opcji wiersza polecenia:  
  
```cpp  
int A[1000];  
void test() {  
#pragma loop(hint_parallel(0))  
    for (int i=0; i<1000; ++i) {  
        A[i] = A[i] + 1;  
    }  
  
    for (int i=1000; i<2000; ++i) {  
        A[i] = A[i] + 1;  
    }  
}  
  
```  
  
 Kompilacja za pomocą tego polecenia:  
  
 **Cl d:\myproject\mylooptest.cpp/O2 /Qpar /Qpar-report: 1**  
  
 daje w wyniku tego dane wyjściowe:  
  
 **---Analizowanie funkcji: void __cdecl test(void)**   
 **d:\myproject\mytest.cpp(4): zarządzana z przetwarzaniem pętli**  
  
 Kompilacja za pomocą tego polecenia:  
  
 **Cl d:\myproject\mylooptest.cpp/O2 /Qpar /Qpar-report: 2**  
  
 daje w wyniku tego dane wyjściowe:  
  
 **---Analizowanie funkcji: void __cdecl test(void)**   
 **d:\myproject\mytest.cpp(4): zarządzana z przetwarzaniem pętli**   
 **d:\myproject\mytest.cpp(4): pętli nie została zrównoleglona z powodu "1008"**  
  
 Zwróć uwagę, w danych wyjściowych różnicę dwóch różnych [/Qpar-report (poziom raportowania automatycznej Paralelizacji)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) opcje. **/ Qpar-report: 1** generuje paralelizatora tylko dla pętli, które są pomyślnie zarządzana z przetwarzaniem. **/ Qpar-report: 2** generuje paralelizatora dla obu parallelizations pętli zakończone powodzeniem i niepowodzeniem.  
  
 Aby uzyskać więcej informacji na temat Kody przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
## <a name="auto-vectorizer"></a>Wektoryzowania automatycznego  
 Wektoryzowania automatycznego analizuje pętli w kodzie i korzysta z rejestrów wektora i instrukcje na komputerze docelowym można wykonać, jeśli można go. Może to poprawić wydajność kodu. Kompilator jest przeznaczony dla instrukcji SSE2, AVX i AVX2 w procesorów Intel lub AMD lub instrukcji NEON procesorów ARM, zgodnie z [/arch](../build/reference/arch-minimum-cpu-architecture.md) przełącznika.  
  
 Wektoryzowania automatycznego może generować instrukcje inny niż określony w **/arch** przełącznika. Te instrukcje są chroniony przez sprawdzanie czasu wykonywania, aby upewnić się, że kod nadal działa poprawnie. Na przykład podczas kompilowania **SSE2**, mogą być wydane SSE4.2 instrukcje. Sprawdzanie czasu wykonywania sprawdza, czy SSE4.2 jest dostępna w docelowej procesora i przechodzi do wersji z systemem innym niż SSE4.2 pętli, jeśli procesor nie obsługują tych instrukcji.  
  
 Wektoryzowania automatycznego jest domyślnie włączone. Jeśli chcesz porównać wydajności kodu w obszarze vectorization, możesz użyć [#pragma loop(no_vector)](../preprocessor/loop.md) wyłączyć vectorization żadnych danego pętli.  
  
```  
  
      #pragma loop(no_vector)  
for (int i = 0; i < 1000; ++i)  
   A[i] = B[i] + C[i];  
  
```  
  
 Jak w przypadku wszystkich [dyrektywy pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), składni alternatywnej pragma `__pragma(loop(no_vector))` jest również obsługiwany.  
  
 Zgodnie z automatycznej Paralelizacji, można określić [/Qvec-report (poziom raportowania automatycznej Wektoryzacji)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) opcji wiersza polecenia, aby zgłosić albo pomyślnie Przekształcono pętli tylko —**/Qvec-report: 1**— lub pomyślnie i niepomyślnie Przekształcono pętli —**/Qvec-report: 2**).  
  
 Aby uzyskać więcej informacji na temat Kody przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
 Na przykład przedstawiający sposób działania wektoryzowania w praktyce, zobacz [projektu Austin część 2, 6: strony Curling](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)  
  
## <a name="see-also"></a>Zobacz też  
 [pętli](../preprocessor/loop.md)   
 [Programowanie równoległe w kodzie natywnym](http://go.microsoft.com/fwlink/p/?linkid=263662)   
 [/ Qpar (automatyczny Paralelizator)](../build/reference/qpar-auto-parallelizer.md)   
 [/ Qpar raport (automatyczny Paralelizator poziom raportowania)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [/ Qvec raport (raportowania automatycznej Wektoryzacji poziomu)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)   
 [Komunikaty wektoryzatora i paralelizatora](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)