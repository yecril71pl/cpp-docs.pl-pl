---
title: Przeciążenia bezpiecznych szablonów
description: Opis przeciążeń szablonów środowiska uruchomieniowego Microsoft C, które udostępniają funkcje ulepszone zabezpieczeniami.
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 5e795d4d68aaeb176ba0809a08310def23662028
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589643"
---
# <a name="secure-template-overloads"></a>Przeciążenia bezpiecznych szablonów

Firma Microsoft zakończyła działanie wielu funkcji biblioteki środowiska uruchomieniowego języka C (CRT) na korzyść wersji ulepszonych z zabezpieczeniami. Na przykład, `strcpy_s` jest bardziej bezpieczną wymianą `strcpy` . Przestarzałe funkcje są typowymi źródłami błędów zabezpieczeń, ponieważ nie uniemożliwiają operacji, które mogą zastąpić pamięć. Domyślnie kompilator generuje ostrzeżenie o zaniechaniu podczas korzystania z jednej z tych funkcji. CRT udostępnia przeciążenia szablonów języka C++ dla tych funkcji, aby ułatwić przechodzenie do bardziej bezpiecznych wariantów.

Na przykład ten fragment kodu generuje ostrzeżenie, ponieważ `strcpy` jest przestarzały:

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Ostrzeżenie o zaniechaniu informuje o tym, że kod może być niebezpieczny. Jeśli sprawdzono, że Twój kod nie może zastąpić pamięci, możesz wybrać kilka opcji. Możesz zignorować ostrzeżenie, można zdefiniować symbol `_CRT_SECURE_NO_WARNINGS` przed instrukcją include dla nagłówków CRT, aby pominąć ostrzeżenie, lub zaktualizować swój kod, aby użyć `strcpy_s` :

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

Przeciążenia szablonu zapewniają dodatkowe opcje. Jeśli zdefiniujesz `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` na 1, spowoduje to przeciążanie szablonu standardowych funkcji CRT, które automatycznie wywołują bezpieczniejsze warianty. Jeśli `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jest 1, nie są wymagane żadne zmiany w kodzie. W tle wywołanie `strcpy` jest zmieniane na wywołanie `strcpy_s` z argumentem o rozmiarze dostarczonym automatycznie.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` nie ma wpływu na funkcje, które przyjmują liczbę, na przykład `strncpy` . Aby włączyć przeciążenia szablonów dla funkcji count, zdefiniuj `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` na 1. Przed wykonaniem tej czynności należy jednak upewnić się, że kod przekazuje liczbę znaków, a nie rozmiar buforu (częsty błąd). Ponadto kod, który jawnie zapisuje terminator o wartości null na końcu buforu po wywołaniu funkcji jest zbędny, jeśli jest wywoływana bezpieczna zmienna. Jeśli konieczne jest zachowanie obcinania, zobacz [_TRUNCATE](../c-runtime-library/truncate.md).

> [!NOTE]
> Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` wymaga `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` również zdefiniowania 1. Jeśli `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` jest zdefiniowany jako 1 i `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jest zdefiniowany jako 0, aplikacja nie będzie wykonywać przeciążeń szablonu.

Po zdefiniowaniu wartości `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 1 włącza przeciążenia szablonu bezpiecznych wariantów (nazwy kończące się na "_s"). W takim przypadku, jeśli `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` ma wartość 1, należy wykonać jedną małą zmianę w oryginalnym kodzie:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Należy zmienić tylko nazwę funkcji (przez dodanie "_s"); Przeciążenie szablonu wymaga podania argumentu size.

Domyślnie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` i `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` są zdefiniowane jako 0 (wyłączone) i `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` zdefiniowane jako 1 (włączone).

Te przeciążenia szablonu działają tylko w przypadku tablic statycznych. Dynamicznie przydzielane bufory wymagają dodatkowych zmian w kodzie źródłowym. Ponowne odwiedzanie powyższych przykładów:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; change it to
                       // strcpy_s(szBuf, 10, "test");
```

I:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>Zobacz też

[Funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
