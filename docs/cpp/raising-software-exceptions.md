---
title: Występowanie wyjątków programowych
ms.date: 11/04/2016
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
ms.openlocfilehash: 49ee800bafff017c29b73c5f6fd64318009a140a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403467"
---
# <a name="raising-software-exceptions"></a>Występowanie wyjątków programowych

Niektóre z najczęstszych źródeł błędów programu nie są oflagowane jako wyjątki przez system. Na przykład, jeśli użytkownik spróbuje przydzielić blok pamięci, ale ilość pamięci jest niewystarczająca, czas wykonywania lub funkcja interfejsu API nie zgłosi wyjątku, ale zwróci kod błędu.

Jednak można traktować dowolny warunek jako wyjątek przez wykrycie tego warunku w kodzie i zgłoszenie go przez wywołanie [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552) funkcji. Flagowanie błędów w ten sposób może przynieść korzyści obsługi wyjątków strukturalnych do wszelkiego rodzaju błędów w czasie wykonywania.

Aby użyć obsługi wyjątków strukturalnych z błędami:

- Zdefiniuj własny kod wyjątku dla zdarzenia.

- Wywołaj `RaiseException` gdy problem zostanie wykryty.

- Użyj filtrów obsługi wyjątków, aby przetestować zdefiniowany kod wyjątku.

\<Winerror.h > plik pokazuje format kodów wyjątków. Aby upewnić się, że nie zostanie zdefiniowany kod, który powoduje konflikt z istniejącym kodem wyjątku, należy ustawić trzeci najbardziej znaczący bit na 1. Cztery najbardziej znaczące bity powinny być ustawione, jak pokazano w poniższej tabeli.

|Bity|Zalecane ustawienie binarne|Opis|
|----------|--------------------------------|-----------------|
|31-30|11|Te dwa bity opisują podstawowy stan kodu:  11 = błąd, 00 = sukces, 01 = informacyjny, 10 = ostrzeżenie.|
|29|1|Bit klienta. Wartość 1 dla kodów zdefiniowanych przez użytkownika.|
|28|0|Zarezerwowany bit. (Pozostawić ustawione na 0).|

Można ustawić pierwsze dwa bity na ustawienie inne niż 11 binarnie, mimo że ustawienie „błąd” jest odpowiednie dla większości wyjątków. Należy pamiętać o ustawieniu bitów 29 i 28, jak pokazano w poprzedniej tabeli.

Wynikowy kod błędu powinien zatem mieć najwyższe cztery bity ustawione na szesnastkowe E. Na przykład następujące definicje definiują kody wyjątków, które nie wchodzą w konflikt z dowolnym kody wyjątków Windows. (Jednak trzeba sprawdzić kody, które są używane przez biblioteki DLL innych firm).

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Po zdefiniowaniu kodu wyjątku można go użyć, aby zgłosić wyjątek. Na przykład, poniższy kod generuje `STATUS_INSUFFICIENT_MEM` wyjątek w odpowiedzi na problem z alokacją pamięci:

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Jeżeli wystarczy tylko zgłosić wyjątek, ostatnie trzy parametry można ustawić na 0. Trzy ostatnie parametry są przydatne do przekazywania informacji dodatkowych i ustawiania flagi, która uniemożliwia kontynuowanie wykonywania programów obsługi. Zobacz [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552) funkcji w zestawie Windows SDK, aby uzyskać więcej informacji.

W filtrach obsługi wyjątków można przetestować zdefiniowane kody. Na przykład:

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Zobacz także

[Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)