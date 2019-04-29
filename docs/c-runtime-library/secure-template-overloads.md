---
title: Przeciążenia bezpiecznych szablonów
ms.date: 11/04/2016
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
ms.openlocfilehash: dfb13d5a48376efb72a845e2f5e2380407937f5b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364535"
---
# <a name="secure-template-overloads"></a>Przeciążenia bezpiecznych szablonów

Microsoft jest przestarzała wiele funkcji biblioteki (CRT) środowiska uruchomieniowego C na rzecz wersje rozszerzonymi zabezpieczeniami. Na przykład `strcpy_s` bezpieczniejsze zastępuje `strcpy`. Przestarzałe funkcje są wspólnych źródeł błędów zabezpieczeń, ponieważ nie uniemożliwiają operacje, które może spowodować zastąpienie pamięci. Domyślnie kompilator generuje ostrzeżenie o zakończeniu obsługi, korzystając z jednej z tych funkcji. CRT zapewnia przeciążenia szablonu języka C++ dla tych funkcji ułatwić przejście do bardziej bezpieczne wariantów.

Na przykład, następujący fragment kodu generuje ostrzeżenie, ponieważ `strcpy` jest przestarzała:

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Ostrzeżenie o zakończeniu obsługi jest informujące o tym, że Twój kod może być niebezpieczne. Jeśli sprawdzono, że Twój kod nie może zastąpić pamięci, masz kilka opcji. Możesz zignorować to ostrzeżenie, można zdefiniować symbol `_CRT_SECURE_NO_WARNINGS` przed instrukcje dołączania dla CRT nagłówki, aby pominąć to ostrzeżenie, lub można zaktualizować kodu, aby użyć `strcpy_s`:

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

Przeciążenia szablonu zapewniają dodatkowe możliwości. Jeśli zdefiniujesz `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 1, dzięki temu przeciążenia szablonu funkcji CRT standardowych, które automatycznie wywołują wariantów bardziej bezpieczne. Jeśli `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` wynosi 1, a następnie nie są wymagane żadne zmiany w kodzie. W tle wywołania `strcpy` jest zmieniana na wywołanie `strcpy_s` z argumentem rozmiaru określane automatycznie.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` nie ma wpływu na funkcje, których takie jak liczba `strncpy`. Aby włączyć przeciążenia szablonu funkcji count, zdefiniuj `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 1. Przedtem, jednak należy się upewnić, że kod przekazuje liczba znaków, nie rozmiar buforu (powszechnym). Ponadto kod, który jawnie zapisuje terminatora null na końcu bufor po wywołaniu funkcji nie jest konieczne, jeśli bezpieczne wariant jest wywoływana. Jeśli potrzebujesz obcięcie zachowanie, zobacz [_TRUNCATE](../c-runtime-library/truncate.md).

> [!NOTE]
>  Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` wymaga, aby `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` również jest zdefiniowana jako 1. Jeśli `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` jest zdefiniowana jako 1 i `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jest zdefiniowana jako 0, aplikacja nie będzie wykonywać wszystkie przeciążenia szablonu.

Podczas definiowania `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 1, umożliwia ona przeciążenia szablonu bezpiecznego wariantów (nazwy kończące się na "_s"). W takim przypadku `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` wynosi 1, a następnie jednego niewielkie zmiany muszą zostać wprowadzone oryginalny kod:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Tylko nazwa funkcji musi być zmienione (przez dodanie "_s"); przeciążenia szablonu zajmuje się związanych z udostępnianiem argumentu rozmiaru.

Domyślnie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` i `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` są definiowane jako 0 (wyłączone) i `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` jest zdefiniowana jako 1 (włączone).

Należy pamiętać, że tych szablonów przeciążenia działają tylko dla tablic statyczne. Bufory dynamicznie przydzielonej wymagać zmian w kodzie dodatkowe źródła. Ponowne spojrzenie na powyższych przykładach:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; you have to change it to
                       // strcpy_s(szBuf, 10, "test");
```

I to:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>Zobacz także

[Funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)
