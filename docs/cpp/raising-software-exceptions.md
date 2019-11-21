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
ms.openlocfilehash: 7c58ae2e2b6635345a162d11d2b75a9865d37751
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246405"
---
# <a name="raising-software-exceptions"></a>Występowanie wyjątków programowych

Niektóre z najczęstszych źródeł błędów programu nie są oflagowane jako wyjątki przez system. Na przykład, jeśli użytkownik spróbuje przydzielić blok pamięci, ale ilość pamięci jest niewystarczająca, czas wykonywania lub funkcja interfejsu API nie zgłosi wyjątku, ale zwróci kod błędu.

However, you can treat any condition as an exception by detecting that condition in your code and then reporting it by calling the [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) function. Flagowanie błędów w ten sposób może przynieść korzyści obsługi wyjątków strukturalnych do wszelkiego rodzaju błędów w czasie wykonywania.

Aby użyć obsługi wyjątków strukturalnych z błędami:

- Zdefiniuj własny kod wyjątku dla zdarzenia.

- Call `RaiseException` when you detect a problem.

- Użyj filtrów obsługi wyjątków, aby przetestować zdefiniowany kod wyjątku.

The \<winerror.h> file shows the format for exception codes. Aby upewnić się, że nie zostanie zdefiniowany kod, który powoduje konflikt z istniejącym kodem wyjątku, należy ustawić trzeci najbardziej znaczący bit na 1. Cztery najbardziej znaczące bity powinny być ustawione, jak pokazano w poniższej tabeli.

|Bity|Zalecane ustawienie binarne|Opis|
|----------|--------------------------------|-----------------|
|31-30|11|Te dwa bity opisują podstawowy stan kodu: 11 = błąd, 00 = sukces, 01 = informacyjny, 10 = ostrzeżenie.|
|29|1|Bit klienta. Wartość 1 dla kodów zdefiniowanych przez użytkownika.|
|28|0|Zarezerwowany bit. (Pozostawić ustawione na 0).|

Można ustawić pierwsze dwa bity na ustawienie inne niż 11 binarnie, mimo że ustawienie „błąd” jest odpowiednie dla większości wyjątków. Należy pamiętać o ustawieniu bitów 29 i 28, jak pokazano w poprzedniej tabeli.

The resulting error code should therefore have the highest four bits set to hexadecimal E. For example, the following definitions define exception codes that do not conflict with any Windows exception codes. (Jednak trzeba sprawdzić kody, które są używane przez biblioteki DLL innych firm).

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Po zdefiniowaniu kodu wyjątku można go użyć, aby zgłosić wyjątek. For example, the following code raises the `STATUS_INSUFFICIENT_MEM` exception in response to a memory allocation problem:

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Jeżeli wystarczy tylko zgłosić wyjątek, ostatnie trzy parametry można ustawić na 0. Trzy ostatnie parametry są przydatne do przekazywania informacji dodatkowych i ustawiania flagi, która uniemożliwia kontynuowanie wykonywania programów obsługi. See the [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) function in the Windows SDK for more information.

W filtrach obsługi wyjątków można przetestować zdefiniowane kody. Na przykład:

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Zobacz także

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Structured exception handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)