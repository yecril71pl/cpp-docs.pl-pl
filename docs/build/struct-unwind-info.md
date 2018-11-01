---
title: struktura UNWIND_INFO
ms.date: 11/04/2016
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
ms.openlocfilehash: 0130d30c314a7736ffaf24753a2e6fdf9ad55b12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517042"
---
# <a name="struct-unwindinfo"></a>struktura UNWIND_INFO

Struktury informacji o danych unwind jest używana do rejestrowania efekty, które funkcja ma na wskaźnik stosu i gdzie nieulotnej rejestrów są zapisywane na stos:

|||
|-|-|
|UBYTE: 3|Wersja|
|UBYTE: 5|Flagi|
|UBYTE|Rozmiar prologu|
|UBYTE|Liczba kodów unwind|
|UBYTE: 4|Zarejestruj się ramki|
|UBYTE: 4|Przesunięcie rejestru ramki (skalowanie)|
|USHORT \* n|Operacja unwind kody tablicy|
|zmienna|Formularz (1) lub (2) poniżej albo być|

(1) Obsługa wyjątków

|||
|-|-|
|ULONG|Adres obsługi wyjątków|
|zmienna|Obsługa określonego języka danych (opcjonalnie)|

(2) łańcuchowej Unwind Info

|||
|-|-|
|ULONG|Adres początkowy — funkcja|
|ULONG|Adres końcowy — funkcja|
|ULONG|Operacja unwind info adresu|

Struktura UNWIND_INFO muszą być wyrównane w pamięci typu DWORD. Znaczenie każde pole jest następująca:

- **Wersja**

   Numer wersji dane odwinięcia aktualnie 1.

- **flagi**

   Trzy flagi są obecnie zdefiniowane:

   |Flaga|Opis|
   |-|-|
   |`UNW_FLAG_EHANDLER`| Funkcja ma obsługi wyjątków, która powinna być wywoływana podczas wyszukiwania dla funkcji, które są konieczne przeanalizowanie wyjątków.|
   |`UNW_FLAG_UHANDLER`| Funkcja ma powinna być wywoływana, gdy odwijanie wyjątków programu obsługi zakończenia.|
   |`UNW_FLAG_CHAININFO`| To unwind info, że struktura nie jest to podstawowy dla procedury. Zamiast tego łańcuchowych elementu unwind info wpis jest zawartość poprzedniego zapisu RUNTIME_FUNCTION. Zobacz poniższy tekst objaśnienia dotyczące łańcuchowej unwind info struktury. Jeśli ta flaga jest ustawiona, flagi UNW_FLAG_EHANDLER i UNW_FLAG_UHANDLER muszą zostać wyczyszczone. Ponadto ramki rejestr stosu stałej alokacji pola i musi mieć takie same wartości jak podstawowego elementu unwind info.|

- **Rozmiar prologu**

   Długość prologu funkcji w bajtach.

- **Liczba kodów unwind**

   Jest to liczba miejsc, w tablicy kody unwind. Należy pamiętać, że unwind niektóre kody (na przykład UWOP_SAVE_NONVOL) wymaga więcej niż jednego miejsca, w tablicy.

- **Zarejestruj się ramki**

   Jeśli wartość jest niezerowa, następnie funkcja używa wskaźnik ramki, a to pole jest to liczba nieulotnej rejestru używana jako wskaźnik ramki, przy użyciu tego samego kodowania dla pola informacje o operacji UNWIND_CODE węzłów.

- **Ramka zarejestrować przesunięcie (skalowanie)**

   Jeśli pola rejestru ramki jest różna od zera, to skalowany przesunięcie od RSP, która jest stosowana do FP reg, gdy zostanie stwierdzone. Rzeczywiste reg FP ustawiono RSP + 16 \* tę liczbę, dzięki czemu przesunięcia z zakresu od 0 do 240. Pozwala to na, wskazując FP reg do środka alokacji stosu lokalnego ramek stosu dynamiczne, umożliwiając lepsze gęstość kodu za pomocą krótszy instrukcje (więcej instrukcji użyć formularz przesunięcia podpisany 8-bitowa).

- **Operacja unwind kody tablicy**

   Jest to tablica elementów opisano wpływ prologu nieulotnej rejestrów i RSP. Zobacz sekcję dotyczącą UNWIND_CODE na znaczenie wybranych elementów. Ze względów wyrównanie tej tablicy jest parzysta liczba wpisów z ostatnim wpisem potencjalnie nieużywane (w którym to przypadku tablicy będzie być dłuższy niż określona przez liczbę unwind kodów pola).

- **Adres obsługi wyjątków**

   Jest to wskaźnik względem obrazu do obsługi wyjątków specyficzne dla języka/zakończeniem przez funkcję (jeśli UNW_FLAG_CHAININFO flaga jest wyczyszczona, i jest on flagi UNW_FLAG_EHANDLER lub UNW_FLAG_UHANDLER ustawiony).

- **Dane specyficzne dla języka programu obsługi**

   Jest to funkcja specyficzny dla języka programu obsługi wyjątku. Format danych nie zostanie podany, całkowicie jest określana przez program obsługi określonego wyjątku w użyciu.

- **Łańcuchowej Unwind Info**

   Jeśli jest ustawiona flaga UNW_FLAG_CHAININFO struktura UNWIND_INFO kończy się z trzech UWORDs.  Te UWORDs reprezentują informacje RUNTIME_FUNCTION funkcji łańcuchowej unwind.

## <a name="see-also"></a>Zobacz też

[Dane operacji Unwind dla obsługi wyjątków, obsługa debugera](../build/unwind-data-for-exception-handling-debugger-support.md)