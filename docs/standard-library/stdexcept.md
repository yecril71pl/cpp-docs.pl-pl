---
title: "&lt;stdexcept —&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <stdexcept>
dev_langs:
- C++
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26cc6c5811819ffcb909e2e27ab90e7dad1f19fc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;
Definiuje kilka standardowych klasy służące do raportowania wyjątków. Klasy tworzą hierarchię pochodnym wszystkie pochodną klasy [wyjątek](../standard-library/exception-class.md) i obejmują dwa typy ogólne wyjątki: błędów logicznych i błędów czasu wykonywania. Błędy logiczne są spowodowane programisty błędów. Będą pochodzić od logic_error — klasa podstawowa i obejmują:  
  
-   `domain_error`  
  
-   `invalid_argument`  
  
-   `length_error`  
  
-   `out_of_range`  
  
 Błędy środowiska wykonawczego wystąpić z powodu błędów w funkcji biblioteki lub w systemie czasu wykonywania. Będą pochodzić od runtime_error — klasa podstawowa i obejmują:  
  
-   `overflow_error`  
  
-   `range_error`  
  
-   `underflow_error`  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[domain_error, klasa](../standard-library/domain-error-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych zgłosić błąd domeny.|  
|[invalid_argument, klasa](../standard-library/invalid-argument-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych do zgłaszania nieprawidłowy argument.|  
|[length_error, klasa](../standard-library/length-error-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych do zgłaszania próby generowania zbyt długi, aby określić obiekt.|  
|[logic_error, klasa](../standard-library/logic-error-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych może raportować błędy prawdopodobnie wykrywalny, przed wykonaniem programu, np. naruszenia logicznej warunki wstępne.|  
|[out_of_range, klasa](../standard-library/out-of-range-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych do zgłaszania argument, który jest poza prawidłowym zakresem.|  
|[overflow_error, klasa](../standard-library/overflow-error-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych do zgłaszania przepełnienie arytmetyczne.|  
|[range_error, klasa](../standard-library/range-error-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych zgłosić błąd zakresu.|  
|[runtime_error, klasa](../standard-library/runtime-error-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych może raportować błędy prawdopodobnie wykrywalny, tylko wtedy, gdy program jest wykonywana.|  
|[underflow_error, klasa](../standard-library/underflow-error-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych do zgłaszania arytmetycznego underflow.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

