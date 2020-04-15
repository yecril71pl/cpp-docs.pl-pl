---
title: EKSPORTY
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 9ede0d3b53c975298dea3d1331bc0fb00ac246b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328255"
---
# <a name="exports"></a>EKSPORTY

Wprowadza sekcję jednej lub więcej definicji eksportu, które określają eksportowane nazwy lub porządki porządkowe funkcji lub danych. Każda definicja musi znajdować się w osobnym wierszu.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Uwagi

Pierwsza *definicja* może znajdować się `EXPORTS` w tym samym wierszu co słowo kluczowe lub w kolejnym wierszu. Tthe. Plik DEF może zawierać `EXPORTS` co najmniej jedną instrukcję.

Składnia *definicji* eksportu jest:

> *nazwa internal_name**other_module.exported_name* \[ **\@**] _nazwa porządkowa_ \[ **NONAME**] ] ] \[ \[ **PRYWATNE**] |*internal_name*\[__=__| \[ **DANE**] ]

*nazwa wpisu* jest nazwą funkcji lub zmiennej, którą chcesz wyeksportować. Jest to wymagane. Jeśli eksportowana nazwa różni się od nazwy biblioteki DLL, określ nazwę eksportu w dll, używając *internal_name*. Na przykład jeśli biblioteka DLL eksportuje funkcję `func1` i `func2`chcesz, aby wywołania używały jej jako , należy określić:

```DEF
EXPORTS
   func2=func1
```

Jeśli eksportowana nazwa pochodzi z innego modułu, określ nazwę eksportu w pliku DLL przy użyciu *other_module.exported_name*. Na przykład jeśli biblioteka DLL eksportuje funkcję `other_module.func1` i `func2`chcesz, aby wywołania używały jej jako , należy określić:

```DEF
EXPORTS
   func2=other_module.func1
```

Jeśli eksportowana nazwa pochodzi z innego modułu eksportowanego przez porządki porządkowe, określ liczba porządkowa eksportu w pliku DLL za pomocą *other_module*. __#__ *liczby porządkowej*. Na przykład jeśli biblioteka DLL eksportuje funkcję z innego modułu, w którym jest liczba `func2`porządkowa 42 i chcesz, aby wywołania używały jej jako , należy określić:

```DEF
EXPORTS
   func2=other_module.#42
```

Ponieważ kompilator MSVC używa dekoracji nazw dla funkcji Języka C++, należy użyć dekoracyjnej nazwy `extern "C"` *internal_name* lub zdefiniować eksportowane funkcje przy użyciu w kodzie źródłowym. Kompilator dekoruje również funkcje C, które używają konwencji\_wywoływania [__stdcall](../../cpp/stdcall.md) z prefiksem podkreślenia ( ) i sufiksem składającym się ze znaku at (\@), po którym następuje liczba bajtów (w przecinku) na liście argumentów.

Aby znaleźć dekoracyjne nazwy wywoływane przez kompilator, należy użyć narzędzia [DUMPBIN](dumpbin-reference.md) lub konsolidatora [/MAP.](map-generate-mapfile.md) Dekoracyjne nazwy są specyficzne dla kompilatora. Jeśli eksportujesz dekoracyjne nazwy w pliku . DEF, pliki wykonywalne, które łączą się z biblioteką DLL, muszą również być utworzone przy użyciu tej samej wersji kompilatora. Gwarantuje to, że dekoracyjne nazwy w wywołującym są zgodne z wyeksportowanymi nazwami w pliku . def.

Można użyć \@ *liczby porządkowej,* aby określić, że liczba, a nie nazwa funkcji, przechodzi do tabeli eksportu biblioteki DLL. Wiele bibliotek DLL systemu Windows eksportuje liczby porządkowe do obsługi starszego kodu. Często używane są liczby porządkowe w 16-bitowym kodzie systemu Windows, ponieważ może to pomóc zminimalizować rozmiar biblioteki DLL. Nie zaleca się eksportowania funkcji przez porządkowe, chyba że klienci biblioteki DLL potrzebują go do obsługi starszych. Ponieważ . Lib plik będzie zawierać mapowanie między porządkowe i funkcji, można użyć nazwy funkcji, jak zwykle w projektach, które używają biblioteki DLL.

Za pomocą opcjonalnego słowa kluczowego **NONAME,** można wyeksportować tylko przez porządkowe i zmniejszyć rozmiar tabeli eksportu w wynikowej biblioteki DLL. Jednak jeśli chcesz użyć [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) na dll, należy znać porządkowe, ponieważ nazwa nie będzie prawidłowa.

Opcjonalne słowo kluczowe **PRIVATE** zapobiega *uwzględnieniu nazwy wpisu* w bibliotece importu wygenerowanej przez LINK. Nie ma to wpływu na eksport na obrazie również generowany przez LINK.

Opcjonalne słowo kluczowe **DATA** określa, że eksport jest dane, a nie kod. W tym przykładzie pokazano, jak `exported_global`można wyeksportować zmienną danych o nazwie:

```DEF
EXPORTS
   exported_global DATA
```

Definicja jest wymieniona w zalecanej kolejności:

1. Słowo kluczowe [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym

1. Oświadczenie `EXPORTS` w . Plik DEF

1. Specyfikacja [/EXPORT](export-exports-a-function.md) w poleceniu LINK

1. Dyrektywa [komentarza](../../preprocessor/comment-c-cpp.md) w kodzie źródłowym `#pragma comment(linker, "/export: definition ")`formularza . Poniższy przykład przedstawia dyrektywę #pragma komentarz przed `PlainFuncName` deklaracją funkcji, gdzie jest `_PlainFuncName@4` niezrażona nazwa i jest dekoracyjną nazwą funkcji:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

#pragma dyrektywy jest przydatne, jeśli trzeba wyeksportować nazwę funkcji niezrażonej i mają różne eksportu w zależności od konfiguracji kompilacji (na przykład w kompilacji 32-bitowych lub 64-bitowych).

Wszystkie cztery metody mogą być używane w tym samym programie. Gdy funkcja LINK tworzy program zawierający eksport, tworzy również bibliotekę importu, chyba że program . Plik EXP jest używany w kompilacji.

Oto przykład sekcji EKSPORT:

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

Podczas eksportowania zmiennej z biblioteki DLL przy użyciu pliku . DEF, nie trzeba określać `__declspec(dllexport)` zmiennej. Jednak w każdym pliku, który używa biblioteki `__declspec(dllimport)` DLL, nadal należy używać na deklaracji danych.

## <a name="see-also"></a>Zobacz też

[Zasady dla instrukcji definicji modułu](rules-for-module-definition-statements.md)
