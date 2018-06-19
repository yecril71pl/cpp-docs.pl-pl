---
title: Wywołania z różną liczbą argumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- arguments [C++], variable number of
- VARARGS.H
- ellipses (...), variable number of arguments
- STDARGS.H
- function calls, arguments
- '... ellipsis'
- function calls, variable number of arguments
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bee194177acc9f2e63719b4ecd16593db7fe048f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383192"
---
# <a name="calls-with-a-variable-number-of-arguments"></a>Wywołania z różną liczbą argumentów
Listy parametrów z częściowa może zostać rozwiązana przez notacji wielokropka, to przecinek trzy kropki (**,...** ), aby wskazać, że może być więcej argumentów została przekazana do funkcji, ale nie więcej informacji znajduje się o nich. Kontrola typów nie jest wykonywana na takich argumentach. Co najmniej jeden parametr musi poprzedzać notację wielokropka, a notacja wielokropka musi stanowić ostatni token na liście parametrów. Bez notacji wielokropka zachowanie funkcji jest niezdefiniowane, jeżeli otrzyma parametry oprócz tych zadeklarowanych na liście parametrów.  
  
 Aby wywołać funkcję o zmiennej liczbie argumentów, wystarczy określić dowolną liczbę argumentów w wywołaniu funkcji. Przykładem jest funkcja `printf` z biblioteki wykonawczej C. Wywołanie funkcji musi zawierać jeden argument dla każdej nazwy typu zadeklarowanej w liście parametrów lub liście typów argumentów.  
  
 Wszystkie argumenty określone w wywołaniu funkcji są umieszczenie w stosie, chyba że określono konwencję wywoływania `__fastcall`. Liczba parametrów zadeklarowanych dla funkcji określa, ile argumentów pochodzi ze stosu i jest przypisanych do parametrów. Użytkownik jest odpowiedzialny za pobieranie dodatkowych argumentów ze stosu i określanie, ile argumentów jest obecne. Plik STDARG.H zawiera makra stylu ANSI do uzyskiwania dostępu do argumentów funkcji, które mają zmienną liczbę argumentów. Ponadto, makra stylu XENIX w VARARGS.H są nadal obsługiwane.  
  
 Ta przykładowa deklaracja dotyczy funkcji, która wywołuje zmienną liczbę argumentów:  
  
```  
int average( int first, ...);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołania funkcji](../c-language/function-calls.md)