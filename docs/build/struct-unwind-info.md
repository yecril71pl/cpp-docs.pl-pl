---
title: Struktura UNWIND_INFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c306e8920bb058b64133b7fec18f21a243e1f715
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="struct-unwindinfo"></a>struktura UNWIND_INFO
Struktury informacji o danych unwind służy do rejestrowania wpływ, jaki ma funkcji na wskaźnik stosu i którym nieulotnej rejestrów są zapisywane na stosie:  
  
|||  
|-|-|  
|UBYTE: 3|Wersja|  
|UBYTE: 5|Flagi|  
|UBYTE|Rozmiar prologu|  
|UBYTE|Liczba kodów unwind|  
|UBYTE: 4|Rejestr ramki|  
|UBYTE: 4|Przesunięcie rejestru ramki (skalowane)|  
|USHORT * n|Tablica kody unwind|  
|zmienna|Albo można formularza (1) lub (2) poniżej|  
  
 (1) Obsługa wyjątków  
  
|||  
|-|-|  
|ULONG|Adres obsługi wyjątków|  
|zmienna|Obsługa określonego języka danych (opcjonalnie)|  
  
 (2) łańcuchowej Unwind informacji  
  
|||  
|-|-|  
|ULONG|Adres początkowy — funkcja|  
|ULONG|Adres końcowy — funkcja|  
|ULONG|Informacje o adres unwind|  
  
 Struktura UNWIND_INFO musi być typu DWORD wyrównane w pamięci. Znaczenie każde pole jest następujący:  
  
 **Wersja**  
 Numer wersji dane odwinięcia aktualnie 1.  
  
 **Flagi**  
 Trzy flagi są obecnie zdefiniowane:  
  
 Funkcja UNW_FLAG_EHANDLER ma obsługi wyjątków, która powinna być wywoływana podczas wyszukiwania dla funkcji, które należy zbadać wyjątków.  
  
 UNW_FLAG_UHANDLER funkcja ma programu obsługi zakończenia, która powinna być wywoływana, gdy rozwinięcia Wystąpił wyjątek.  
  
 UNW_FLAG_CHAININFO unwind to struktura nie jest to podstawowy w procedurze informacji. Zamiast tego łańcuchowa unwind informacje, że wpis jest zawartość poprzedniego zapisu RUNTIME_FUNCTION. Zobacz następujący tekst, aby uzyskać informacje o łańcuchowej unwind struktury informacji o. Jeśli ta flaga jest ustawiona, flag UNW_FLAG_EHANDLER i UNW_FLAG_UHANDLER muszą zostać wyczyszczone. Ponadto pola ramki rejestru i stosu stałej alokacji musi mieć takie same wartości jak podstawowy unwind informacji.  
  
 **Rozmiar prologu**  
 Długość w bajtach prologu funkcji.  
  
 **Liczba kodów unwind**  
 Jest to liczba gniazd w tablicy kody unwind. Należy pamiętać, że niektóre unwind kody (na przykład UWOP_SAVE_NONVOL) wymagają więcej niż jednego miejsca w tablicy.  
  
 **Rejestr ramki**  
 Jeśli jest różna od zera, następnie funkcja wskaźnika ramki, a to pole jest to liczba nieulotnej rejestru używane jako wskaźnika ramki, przy użyciu tego samego kodowania w polu informacje o operacji UNWIND_CODE węzłów.  
  
 **Ramki zarejestrować przesunięcie (skalowane)**  
 Jeśli pole rejestru ramki jest różna od zera, to jest skalowana przesunięcie od źródło stosowany do rejestru FP po jego nawiązaniu. Rzeczywiste reg FP ustawiono źródło + 16 * ten numer, dzięki czemu przesunięcia od 0 do 240. Umożliwia wskazanie FP reg do środka alokacji stosu lokalnego ramek stosu dynamicznej, co lepiej gęstość kodu przy użyciu krótszej instrukcje (dodatkowe instrukcje formularz 8-bitową podpisem przesunięcia).  
  
 **Tablica kody unwind**  
 To jest tablica elementów opisano wpływ prologu w nieulotnej rejestrów i źródło. Zobacz sekcję dotyczącą UNWIND_CODE dla znaczenie poszczególnych elementów. Do celów wyrównanie tej tablicy zawsze będą mieć parzysta liczba wpisów wpisem końcowej potencjalnie nieużywane (w takim przypadku tablicy będzie być dłuższy niż określona według liczby unwind kody pól).  
  
 **Adres obsługi wyjątków**  
 Jest to wskaźnik względem obrazu do obsługi wyjątków specyficzne dla języka/zakończenia przez funkcję (Jeśli flaga UNW_FLAG_CHAININFO jest wyczyszczone i jest on flagi UNW_FLAG_EHANDLER lub UNW_FLAG_UHANDLER ustawiony).  
  
 **Dane specyficzne dla języka programu obsługi**  
 To są dane programu obsługi wyjątków specyficzne dla języka funkcji. Format tych danych jest nieokreślona i całkowicie określany przez program obsługi określony wyjątek w użyciu.  
  
 **Łańcuchowej Unwind informacji**  
 Jeśli jest ustawiona flaga UNW_FLAG_CHAININFO struktura UNWIND_INFO kończy się z trzech UWORDs.  Te UWORDs reprezentuje informacje RUNTIME_FUNCTION łańcuchowej unwind dla funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dane operacji unwind dla obsługi wyjątków, obsługa debugera](../build/unwind-data-for-exception-handling-debugger-support.md)