---
title: Przegląd konwencji wywoływania x64
ms.date: 11/04/2016
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
ms.openlocfilehash: 37ba3c68310af938f382f88ab4f339166589b96b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444203"
---
# <a name="overview-of-x64-calling-conventions"></a>Przegląd konwencji wywoływania x64

Dwie ważne różnice między x86 i x64 są możliwości adresowania 64-bitowych i prostego zestawu 16 64-bitowych rejestrów do użytku ogólnego. Biorąc pod uwagę zestaw rejestru rozwinięty, używa x64 [__fastcall](../cpp/fastcall.md) wywoływania Konwencji i model obsługi wyjątków, na podstawie RISC. `__fastcall` Konwencji używa rejestrów, pierwsze cztery argumenty i ramki stosu do przekazywania dodatkowych argumentów.

Następująca opcja kompilatora pomaga zoptymalizować aplikację x64:

- [/favor (Optymalizacja pod kątem specyfiki architektury)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="calling-convention"></a>Konwencja wywoływania

X64 który binarnym interfejsem aplikacji (ABI) używa konwencji wywoływania wywołania fast cztery rejestru przez domyślne. Miejsce jest przydzielane w stosie wywołań jako magazynu w tle dla wywoływane zapisać te rejestrów. Ma rygorystyczne relację między argumenty do wywołania funkcji i rejestry, używany dla tych argumentów. Dowolny z argumentów, który nie mieści się w 8 bajtów lub nie jest 1, 2, 4 lub 8 bajtów, muszą być przekazywane przez odwołanie. Brak próba pojedynczy argument rozkłada się na wiele rejestrów. X87 rejestr stosu jest nieużywana. Mogą być używane przez obiekt wywoływany, ale należy rozważyć volatile dla wywołania funkcji. Wszystkie zmiennoprzecinkowej operacje są wykonywane przy użyciu 16 rejestrów XMM. Liczba całkowita argumenty są przekazywane w rejestrach RCX, RDX, R8 i R9. Zmiennoprzecinkowe argumenty są przekazywane do XMM0L, XMM1L, XMM2L i XMM3L. 16-bajtowy argumenty są przekazywane przez odwołanie. Przekazywanie parametru jest szczegółowo opisane w [przekazywania parametru](../build/parameter-passing.md). Oprócz tych rejestrów RAX R10, R11, XMM4 i XMM5 są traktowane jako nietrwałe. Wszystkie inne rejestrów jest trwała. Rejestrowanie użycia jest szczegółowo udokumentowano w [rejestrowanie użycia](../build/register-usage.md) i [rejestruje zapisać element wywołujący/wywoływany](../build/caller-callee-saved-registers.md).

Obiekt wywołujący jest odpowiedzialny za przydzielanie miejsca dla parametrów, aby obiekt wywoływany i zawsze należy przydzielić wystarczającej ilości miejsca do przechowywania czterech Parametry rejestru, nawet wtedy, gdy obiekt wywoływany nie przyjmuje parametrów tę liczbę. Upraszcza obsługę funkcje języka C bez pierwowzoru i funkcji języka C/C++ vararg. Dla funkcji vararg lub funkcji nieprototypowanych, wszelkie zmiennoprzecinkowej wartości muszą być zduplikowane w odpowiednim rejestrze ogólnego przeznaczenia. Wszelkie parametry poza pierwsze cztery muszą być przechowywane w stosie, powyżej magazynu w tle dla pierwsze cztery, przed wywołaniem. Szczegóły funkcji Vararg znajdują się w [Varargs](../build/varargs.md). Informacje o funkcji bez Pierwowzoru została szczegółowo opisana w [funkcje bez Pierwowzoru](../build/unprototyped-functions.md).

## <a name="alignment"></a>Wyrównanie

Większość struktury są wyrównane do ich naturalnego wyrównania składowej. Podstawowe wyjątki są wskaźnik stosu i `malloc` lub `alloca` pamięci, które są wyrównane do 16-bajtowy, aby pomóc wydajności. Wyrównanie powyżej 16 bajtów musi być wykonywane ręcznie, ale ponieważ 16 bajtów to typowy rozmiar wyrównania dla operacji XMM, powinno to działać dla większości kodu. Aby uzyskać więcej informacji na temat struktury układ i wyrównanie zobacz [typy i magazyn](../build/types-and-storage.md). Aby uzyskać informacji na temat układ stosu, zobacz [wykorzystanie stosu](../build/stack-usage.md).

## <a name="unwindability"></a>Unwindability

Funkcje typu liść są funkcje, które nie zmieniaj żadnych rejestrów trwałej. Funkcja elementu członkowskiego typu liść mogą ulec zmianie RSP trwałej, na przykład przez wywołanie funkcji lub przydzielenie miejsca na stosie dodatkowe dla zmiennych lokalnych. Aby można było odzyskać trwałej rejestrów, gdy wyjątek jest obsługiwany, funkcji elementu członkowskiego typu liść musi być oznaczona przy użyciu danych statycznych, który opisuje sposób prawidłowo unwind funkcji w dowolnych instrukcji. Te dane są przechowywane jako *pdata*, lub procedury danych, który z kolei odnosi się do *xdata*, wyjątków, Obsługa danych. Xdata odwijania informacjami i może wskazywać dodatkowe pdata lub funkcję obsługi wyjątków. Prologs i epilogs są zastrzeżonych, tak aby mogły być prawidłowo opisanych w xdata. Wskaźnik stosu muszą być dostosowane do 16 bajtów w dowolnym regionie kod, który nie jest częścią epilogu lub prologu, z wyjątkiem w funkcjach typu liść. Funkcje typu liść można odwinięty po prostu symulując zwrotu, dzięki czemu pdata i xdata nie są wymagane. Aby uzyskać szczegółowe informacje o strukturze odpowiednie prologs funkcji i epilogs, zobacz [prologu i epilogu](../build/prolog-and-epilog.md). Aby uzyskać więcej informacji na temat obsługi wyjątków i wyjątków, obsługa i odwinięcie pdata i xdata, zobacz [wyjątków (x64)](../build/exception-handling-x64.md).

## <a name="see-also"></a>Zobacz też

[Konwencje kodowania x64](../build/x64-software-conventions.md)