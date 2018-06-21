---
title: Formatowanie danych wyjściowych niestandardowego kroku budowania lub zdarzenia kompilacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7da71e6391d2d3223b47ba528686d2fec003ab3a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33321353"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Formatowanie danych wyjściowych niestandardowego kroku budowania lub zdarzenia kompilacji
Jeśli w danych wyjściowych niestandardowego kroku budowania lub zdarzenia kompilacji są poprawnie sformatowane, użytkownicy uzyskują następujące korzyści:  
  
-   Ostrzeżenia i błędy są zliczane **dane wyjściowe** okna.  
  
-   Zostaną wyświetlone dane wyjściowe w **listy zadań** okna.  
  
-   Kliknięcie w danych wyjściowych **dane wyjściowe** okno wyświetla odpowiedni temat.  
  
-   Operacje F1 są włączone w **listy zadań** okna lub **dane wyjściowe** okna.  
  
 Format danych wyjściowych powinny być:  
  
 {*filename* (*wiersza #* [, *kolumnę #*]) &#124; *toolname*} **:**  
  
 [*tekst*] {**błąd** &#124; **ostrzeżenie**} *kod ###***:*** Lokalizowalny ciągu*  
  
 [ *tekst* ]  
  
 Gdzie:  
  
-   {*a* &#124; *b*} jest wybór albo *a* lub *b*.  
  
-   [`ccc`] jest opcjonalny ciąg lub parametr.  
  
 Na przykład:  
  
 C:\\*sourcefile.cpp*(134): błąd C2143: błąd składni: Brak ";" przed "}"  
  
 ŁĄCZA: błąd krytyczny LNK1104: nie można otworzyć pliku "*somelib.lib*"  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](../ide/understanding-custom-build-steps-and-build-events.md)