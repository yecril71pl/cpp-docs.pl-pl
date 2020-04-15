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
ms.openlocfilehash: 6dba60b57616a1656b2791958e460f0268eaa7fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361124"
---
# <a name="secure-template-overloads"></a>Przeciążenia bezpiecznych szablonów

Firma Microsoft przestarzała wiele funkcji biblioteki C Runtime (CRT) na rzecz wersji z podwyższonymi zabezpieczeniami. Na przykład, `strcpy_s` jest bardziej `strcpy`bezpieczne zastąpienie . Przestarzałe funkcje są typowymi źródłami błędów zabezpieczeń, ponieważ nie uniemożliwiają operacji, które mogą zastąpić pamięć. Domyślnie kompilator generuje ostrzeżenie o deprecation podczas korzystania z jednej z tych funkcji. CRT zapewnia przeciążenia szablonu języka C++ dla tych funkcji, aby ułatwić przejście do bardziej bezpiecznych wariantów.

Na przykład ten fragment kodu generuje ostrzeżenie, `strcpy` ponieważ jest przestarzały:

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Ostrzeżenie o usunięciu jest tam, aby poinformować, że kod może być niebezpieczne. Jeśli masz zweryfikowane, że kod nie można zastąpić pamięci, masz kilka opcji. Można zignorować ostrzeżenie, można zdefiniować `_CRT_SECURE_NO_WARNINGS` symbol przed dołączanie instrukcji dla nagłówków CRT, aby pominąć `strcpy_s`ostrzeżenie, lub można zaktualizować kod do użycia:

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

Przeciążenia szablonu zapewniają dodatkowe opcje. Jeśli zdefiniujesz `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` do 1, to umożliwia przeciążenia szablonu standardowych funkcji CRT, które automatycznie wywołują bardziej bezpieczne warianty. Jeśli `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jest 1, to nie są wymagane żadne zmiany w kodzie. W tle wywołanie `strcpy` jest zmieniane na `strcpy_s` wywołanie z argumentem rozmiaru dostarczonym automatycznie.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` nie wpływa na funkcje, które `strncpy`przyjmują liczbę, takie jak . Aby włączyć przeciążenia szablonu dla `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` funkcji zliczania, zdefiniuj do 1. Zanim to jednak zrobić, upewnij się, że kod przekazuje liczbę znaków, a nie rozmiar buforu (częsty błąd). Ponadto kod, który jawnie zapisuje terminator zerowy na końcu buforu po wywołaniu funkcji jest niepotrzebne, jeśli wywoływany jest wariant secure. Jeśli potrzebujesz zachowania obcinania, zobacz [_TRUNCATE](../c-runtime-library/truncate.md).

> [!NOTE]
> Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` wymaga, `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` aby jest również zdefiniowany jako 1. Jeśli `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` jest zdefiniowany `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 i jest zdefiniowany jako 0, aplikacja nie będzie wykonywać żadnych przeciążeń szablonu.

Podczas definiowania `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` do 1, umożliwia przeciążenia szablonu bezpiecznych wariantów (nazwy kończące się na "_s"). W takim przypadku, jeśli `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` jest 1, należy dokonać jednej małej zmiany w oryginalnym kodzie:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Należy zmienić tylko nazwę funkcji (przez dodanie "_s"); przeciążenie szablonu zajmuje się dostarczaniem argumentu rozmiaru.

Domyślnie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` i `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` są zdefiniowane jako 0 (wyłączone) i `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` jest zdefiniowany jako 1 (włączone).

Należy zauważyć, że te przeciążenia szablonu działają tylko dla tablic statycznych. Bufory przydzielane dynamicznie wymagają dodatkowych zmian kodu źródłowego. Wracając do powyższych przykładów:

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

## <a name="see-also"></a>Zobacz też

[Funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
