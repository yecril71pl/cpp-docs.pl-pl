---
title: Omówienie x64 konwencji wywoływania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb4071cd3223ad2ab073f84418e641b515c05112
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374911"
---
# <a name="overview-of-x64-calling-conventions"></a>Przegląd konwencji wywoływania x64
Dwie ważne różnice między x86 i [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] są możliwości adresowania 64-bitowe i rejestruje płaski zestaw 16 64-bitowej do użytku ogólnego. Podany rozwinięte zarejestrować zestawu, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] używa [__fastcall](../cpp/fastcall.md) wywoływanie Konwencji i opartych na standardzie RISC model obsługi wyjątków. `__fastcall` Konwencji używa rejestruje pierwsze cztery argumenty i ramki stosu, aby przekazać dodatkowe argumenty.  
  
 Następująca opcja kompilatora pomaga zoptymalizować aplikacji dla [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]:  
  
-   [/favor (Optymalizacja pod kątem specyfiki architektury)](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## <a name="calling-convention"></a>Konwencja wywoływania  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] Aplikacji binarny interfejsu (ABI) domyślnie używa konwencji wywoływania wywołania fast cztery rejestru. Miejsce jest przydzielane w stosie wywołań jako magazyn cienia na potrzeby callees można zapisać tych rejestrów. Brak odpowiednika strict między argumentów dla wywołania funkcji i rejestruje używane dla tych argumentów. Któryś argument, który nie mieści się w 8 bajtów, lub nie jest 1, 2, 4 lub 8 bajtów, muszą być przekazywane przez odwołanie. Próba rozłożyć pojedynczy argument na wielu rejestrów nie istnieje. X87 stosu rejestru nie jest używana. Mogą być używane przez funkcję wywołującą, ale muszą być traktowane jako nietrwałe między wywołania funkcji. Zmiennoprzecinkowej wszystkie operacje są wykonywane przy użyciu 16 rejestruje XMM. Liczba całkowita argumenty są przekazywane w rejestrach RCX, RDX, R8 i R9. Liczba zmiennoprzecinkowa się, że argumenty są przekazywane w XMM0L, XMM1L XMM2L i XMM3L. 16-bajtowych argumenty są przekazywane przez odwołanie. Przekazywanie parametru opisano szczegółowo w [przekazywanie parametru](../build/parameter-passing.md). Oprócz tych rejestrów RAX, R10 R11, XMM4 i XMM5 są traktowane jako nietrwałe. Wszystkie inne rejestrów jest trwała. Rejestrowanie użycia jest zostały szczegółowo opisane w [rejestrowanie użycia](../build/register-usage.md) i [wywołujący/wywoływany zapisane rejestruje](../build/caller-callee-saved-registers.md).  
  
 Obiekt wywołujący jest odpowiedzialny za przydzielania miejsca dla parametrów do wywoływany i zawsze Przydziel wystarczającą ilość miejsca do przechowywania cztery parametry rejestru, nawet wtedy, gdy wywoływany nie przyjmuje to wiele parametrów. Upraszcza to obsługę funkcji języka C bez prototypu i w przypadku funkcji vararg C/C++. Dla funkcji vararg lub funkcji nieprototypowanych, wszelkie zmiennoprzecinkowych wartości musi być zduplikowany w odpowiednim rejestrze ogólnego przeznaczenia. Po pierwsze cztery parametry muszą być przechowywane na stosie, powyżej w tle sklepie pierwsze cztery przed wywołaniem. Szczegóły funkcji Vararg znajdują się w [Varargs](../build/varargs.md). Informacji o funkcji bez prototypu została szczegółowo opisana w [funkcje bez Pierwowzoru](../build/unprototyped-functions.md).  
  
## <a name="alignment"></a>Wyrównanie  
 Większość struktur są wyrównane do ich naturalnego wyrównania elementu. Podstawowe wyjątki są wskaźnik stosu i `malloc` lub `alloca` pamięci, które są wyrównane do 16 bajtów, aby pomóc wydajności. Wyrównanie powyżej 16 bajtów musi odbywać się ręcznie, ale ponieważ 16 bajtów jest typowy rozmiar wyrównania dla operacji XMM, powinno to działać dla większości kodu. Aby uzyskać więcej informacji o układzie struktury i wyrównanie zobacz [typy i magazyn](../build/types-and-storage.md). Informacje dotyczące układu stosu, zobacz [wykorzystanie stosu](../build/stack-usage.md).  
  
## <a name="unwindability"></a>Unwindability  
 Funkcje, które nie zmieniają się żadnych rejestrów trwałej są funkcje typu liść. Funkcja elementu członkowskiego typu liść może zmienić źródło trwałej, na przykład przez wywołanie funkcji lub przydzielenie miejsca na stosie dodatkowych dla zmiennych lokalnych. Aby odzyskać rejestrów trwałej, jeśli wyjątek jest obsługiwany, elementu członkowskiego typu liść funkcji musi być adnotowany przy dane statyczne, który opisuje sposób prawidłowo unwind funkcji w instrukcji dowolnego. Te dane są przechowywane jako *pdata*, lub procedury danych, który z kolei odwołuje się do *xdata*, danych obsługi wyjątków. Xdata odwijaniem informacjami i może wskazywać dodatkowe pdata lub funkcję obsługi wyjątków. Prologs i epilogs są zastrzeżonych, tak aby mogły być poprawnie opisanej w xdata. Wskaźnik stosu musi być wyrównany do 16 bajtów w dowolnym regionie kodu, który nie jest częścią epilogu lub prologu, z wyjątkiem w funkcjach typu liść. Funkcje liścia można odwinięty po prostu symulując zwracanym, więc pdata i xdata nie są wymagane. Aby uzyskać szczegółowe informacje o strukturze prawidłowego prologs funkcji i epilogs, zobacz [Prolog i Epilog](../build/prolog-and-epilog.md). Aby uzyskać więcej informacji na temat obsługi wyjątków i wyjątków, obsługa i odwijanie pdata i xdata, zobacz [(x64) obsługi wyjątków](../build/exception-handling-x64.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje kodowania x64](../build/x64-software-conventions.md)