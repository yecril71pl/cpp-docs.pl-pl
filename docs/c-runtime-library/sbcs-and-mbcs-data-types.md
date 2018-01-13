---
title: "SBCS i MBCS — typy danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MBCS
- SBCS
dev_langs: C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c54b6e9716e7f0aee9a0b211148b76804d9520bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS i MBCS — Typy danych
Udostępnianych przez firmę Microsoft `MBCS` oczekuje procedury biblioteki wykonawczej, który obsługuje tylko znaków wielobajtowych jednego lub jeden bajt znaków wielobajtowych `unsigned int` argumentu (gdzie 0x00 < = wartość znaku < = 0xFFFF i 0x00 < = wartość bajtu < = 0xFF). `MBCS` Procedura obsługuje wielobajtowe bajtów lub znaków w kontekście ciąg spodziewa się ciągu znaków wielobajtowych może być reprezentowana jako `unsigned char` wskaźnika.  
  
> [!CAUTION]
>  Każdy bajt znaków wielobajtowych może być reprezentowany w 8-bitową `char`. Jednak `SBCS` lub `MBCS` znaków typu `char` o wartości większej niż 0x7F jest ujemna. Gdy taki znak jest konwertowany bezpośrednio do `int` lub `long`, wynik jest znakiem przez kompilator i w związku z tym może dać nieoczekiwane wyniki.  
  
 W związku z tym najlepiej do reprezentowania bajt znaków wielobajtowych jako 8-bitową `unsigned char`. Lub, w celu uniknięcia negatywnego wyniku, po prostu wykonać konwersji znaków typu `char` do `unsigned char` przed przekonwertowaniem go do `int` lub `long`.  
  
 Ponieważ niektóre `SBCS` funkcje obsługi ciągów wykonaj (ze znakiem) `char*` parametrów, spowoduje ostrzeżenia kompilatora niezgodność typów podczas `_MBCS` jest zdefiniowany. Istnieją trzy sposoby, aby uniknąć tego ostrzeżenia, wymienionych według wydajności:  
  
1.  Użyj funkcji śródwierszowych "bezpiecznej" w tchar —. H. Jest to zachowanie domyślne.  
  
2.  Użyj "bezpośrednie" makra w tchar —. H, definiując `_MB_MAP_DIRECT` w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typów. To jest najszybszy sposób, ale nie jest bezpieczne.  
  
3.  Użyj funkcji "bezpiecznej" statycznie połączone biblioteki w tchar —. H. Aby to zrobić, należy zdefiniować stała `_NO_INLINING` w wierszu polecenia. Jest to metoda najwolniejsze, ale najbardziej bezpieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Przystosowywanie do warunków międzynarodowych](../c-runtime-library/internationalization.md)   
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)