---
title: Występowanie wyjątków programowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fa925a01633d72f43b165b87c27e5203a143d1e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="raising-software-exceptions"></a>Występowanie wyjątków programowych
Niektóre z najczęstszych źródeł błędów programu nie są oflagowane jako wyjątki przez system. Na przykład, jeśli użytkownik spróbuje przydzielić blok pamięci, ale ilość pamięci jest niewystarczająca, czas wykonywania lub funkcja interfejsu API nie zgłosi wyjątku, ale zwróci kod błędu.  
  
 Jednak Traktuj wszystkie warunku jako wyjątek wykrywania tego warunku w kodzie i raportowania go przez wywołanie metody [raiseexception —](http://msdn.microsoft.com/library/windows/desktop/ms680552) funkcji. Flagowanie błędów w ten sposób może przynieść korzyści obsługi wyjątków strukturalnych do wszelkiego rodzaju błędów w czasie wykonywania.  
  
 Aby użyć obsługi wyjątków strukturalnych z błędami:  
  
-   Zdefiniuj własny kod wyjątku dla zdarzenia.  
  
-   Wywołanie **raiseexception —** podczas wykrycia problemu.  
  
-   Użyj filtrów obsługi wyjątków, aby przetestować zdefiniowany kod wyjątku.  
  
 \<Pliku winerror.h > pliku pokazuje format kodów wyjątków. Aby upewnić się, że nie zostanie zdefiniowany kod, który powoduje konflikt z istniejącym kodem wyjątku, należy ustawić trzeci najbardziej znaczący bit na 1. Cztery najbardziej znaczące bity powinny być ustawione, jak pokazano w poniższej tabeli.  
  
|Bity|Zalecane ustawienie binarne|Opis|  
|----------|--------------------------------|-----------------|  
|31-30|11|Te dwa bity opisują podstawowy stan kodu: 11 = błąd, 00 = sukces, 01 = informacyjny, 10 = ostrzeżenie.|  
|29|1|Bit klienta. Wartość 1 dla kodów zdefiniowanych przez użytkownika.|  
|28|0|Zarezerwowany bit. (Pozostawić ustawione na 0).|  
  
 Można ustawić pierwsze dwa bity na ustawienie inne niż 11 binarnie, mimo że ustawienie „błąd” jest odpowiednie dla większości wyjątków. Należy pamiętać o ustawieniu bitów 29 i 28, jak pokazano w poprzedniej tabeli.  
  
 Wynikowy kod błędu w związku z tym powinien mieć najwyższy bitów cztery szesnastkowe E. Na przykład następujące definicje zdefiniować kody wyjątków, które nie są w konflikcie z żadnych kodów wyjątek systemu Windows. (Jednak trzeba sprawdzić kody, które są używane przez biblioteki DLL innych firm).  
  
```  
#define STATUS_INSUFFICIENT_MEM       0xE0000001  
#define STATUS_FILE_BAD_FORMAT        0xE0000002  
```  
  
 Po zdefiniowaniu kodu wyjątku można go użyć, aby zgłosić wyjątek. Na przykład, poniższy kod zgłasza wyjątek STATUS_INSUFFICIENT_MEM w odpowiedzi na problem z alokacją pamięci:  
  
```  
lpstr = _malloc( nBufferSize );  
if (lpstr == NULL)  
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);  
```  
  
 Jeżeli wystarczy tylko zgłosić wyjątek, ostatnie trzy parametry można ustawić na 0. Trzy ostatnie parametry są przydatne do przekazywania informacji dodatkowych i ustawiania flagi, która uniemożliwia kontynuowanie wykonywania programów obsługi. Zobacz [raiseexception —](http://msdn.microsoft.com/library/windows/desktop/ms680552) działać w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] Aby uzyskać więcej informacji.  
  
 W filtrach obsługi wyjątków można przetestować zdefiniowane kody. Na przykład:  
  
```  
__try {  
    ...  
}  
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||  
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu do obsługi wyjątków](../cpp/writing-an-exception-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)