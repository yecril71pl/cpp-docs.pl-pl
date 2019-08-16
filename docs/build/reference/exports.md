---
title: EKSPORTY
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 8338f27d35d3779a55b83b70c7a3eef285a91f46
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492881"
---
# <a name="exports"></a>EKSPORTY

Wprowadza sekcję zawierającą co najmniej jedną definicję eksportu, która określa wyeksportowane nazwy lub liczby porządkowe funkcji lub danych. Każda definicja musi znajdować się w osobnym wierszu.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Uwagi

Pierwsza *Definicja* może znajdować się w tym samym wierszu, `EXPORTS` co słowo kluczowe lub w kolejnym wierszu. Polu. Plik DEF może zawierać jedną lub więcej `EXPORTS` instrukcji.

Składnia *definicji* eksportu jest następująca:

> *entryname*\[ __=__ *internal_name*|*other_module.exported_name*] \[ **\@** _ordinal_ \[**NONAME**] ] \[ \[**PRIVATE**] | \[**DATA**] ]

*EntryName* to nazwa funkcji lub zmiennej, która ma zostać wyeksportowana. Jest to wymagane. Jeśli eksportowana nazwa różni się od nazwy w bibliotece DLL, należy określić nazwę eksportu w bibliotece DLL przy użyciu *internal_name*. Na przykład jeśli biblioteka DLL eksportuje funkcję `func1` i chcesz, aby obiekty wywołujące używały jej jako `func2`, należy określić:

```DEF
EXPORTS
   func2=func1
```

Jeśli eksportowana nazwa pochodzi z innego modułu, należy określić nazwę eksportu w bibliotece DLL za pomocą *other_module. exported_name*. Na przykład jeśli biblioteka DLL eksportuje funkcję `other_module.func1` i chcesz, aby obiekty wywołujące używały jej jako `func2`, należy określić:

```DEF
EXPORTS
   func2=other_module.func1
```

Jeśli eksportowana nazwa pochodzi z innego modułu, który eksportuje według liczby porządkowej, określ numer porządkowy eksportu w bibliotece DLL przy użyciu *other_module*. *numer porządkowy.* __#__ Na przykład jeśli biblioteka DLL eksportuje funkcję z innego modułu, gdzie jest porządkową 42, i chcesz, aby wywołujący używali go jako `func2`, należy określić:

```DEF
EXPORTS
   func2=other_module.#42
```

Ponieważ kompilator MSVC używa dekoracji nazw dla C++ funkcji, musisz użyć dekoracyjnej nazwy *internal_name* lub zdefiniować eksportowane funkcje przy użyciu `extern "C"` w kodzie źródłowym. Kompilator zdobi również funkcje języka C, które używają konwencji wywoływania [__stdcall](../../cpp/stdcall.md) z prefiksem podkreślenia\_() i sufiksem składającym się ze znaku (\@), po którym następuje liczba bajtów (w liczbie dziesiętnej) na liście argumentów.

Aby znaleźć dekoracyjne nazwy wytwarzane przez kompilator, użyj narzędzia [polecenia DUMPBIN](dumpbin-reference.md) lub konsolidatora [/map](map-generate-mapfile.md) . Nazwy dekoracyjne są specyficzne dla kompilatora. Jeśli eksportujesz dekoracyjne nazwy w. Plik DEF, pliki wykonywalne, które łączą się z biblioteką DLL, muszą być również skompilowane przy użyciu tej samej wersji kompilatora. Gwarantuje to, że nazwy dekoracyjne w obiekcie wywołującym są zgodne z wyeksportowanymi nazwami w. Plik DEF.

Można użyć \@liczby *porządkowej* , aby określić, że liczba, a nie nazwa funkcji, trafia do tabeli eksportu biblioteki DLL. Wiele porządkowych eksportu bibliotek DLL systemu Windows obsługuje kod starszej wersji. Często używamy liczb porządkowych w 16-bitowym kodzie systemu Windows, ponieważ może to pomóc zminimalizować rozmiar biblioteki DLL. Nie zalecamy eksportowania funkcji według liczby porządkowej, chyba że klienci biblioteki DLL potrzebują jej w celu uzyskania starszej obsługi. Ponieważ. Plik LIB będzie zawierać mapowanie między liczbą porządkową a funkcją, można użyć nazwy funkcji, jak zwykle w projektach korzystających z biblioteki DLL.

Za pomocą opcjonalnego słowa kluczowego **NoName** można eksportować według liczby porządkowej i zmniejszyć rozmiar tabeli eksportu w otrzymanej bibliotece DLL. Jeśli jednak chcesz użyć funkcji [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) dla biblioteki DLL, musisz znać numer porządkowy, ponieważ nazwa nie jest prawidłowa.

Opcjonalne słowo kluczowe **Private** uniemożliwia uwzględnienie wpisuname w bibliotece importu wygenerowanej przez link. Nie ma to wpływu na eksport w obrazie, który został również wygenerowany przez łącze.

Opcjonalne **dane** słowa kluczowego określa, że eksport to dane, a nie kod. Ten przykład pokazuje, jak można wyeksportować zmienną danych o nazwie `exported_global`:

```DEF
EXPORTS
   exported_global DATA
```

Istnieją cztery metody eksportowania definicji, wymienione w zalecanej kolejności:

1. Słowo kluczowe [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym

1. `EXPORTS` Instrukcja w. Plik DEF

1. Specyfikacja [/Export](export-exports-a-function.md) w POleceniu linku

1. Dyrektywa [komentarza](../../preprocessor/comment-c-cpp.md) w kodzie źródłowym formularza `#pragma comment(linker, "/export: definition ")`. W poniższym przykładzie przedstawiono dyrektywę komentarza #pragma przed deklaracją funkcji, gdzie `PlainFuncName` jest nazwą niedekoracyjną i `_PlainFuncName@4` jest nazwą dekoracyjną funkcji:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

Dyrektywa #pragma jest przydatna, jeśli trzeba wyeksportować niedekoracyjną nazwę funkcji i mieć różne Eksporty w zależności od konfiguracji kompilacji (na przykład w 32-bitowych lub 64-bitowych kompilacjach).

Wszystkie cztery metody mogą być używane w tym samym programie. Gdy LINK kompiluje program zawierający eksporty, tworzy również bibliotekę importu, chyba że. Plik EXP jest używany w kompilacji.

Oto przykład sekcji EKSPORTy:

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

Podczas eksportowania zmiennej z biblioteki DLL przy użyciu. Plik DEF, nie trzeba określać `__declspec(dllexport)` dla zmiennej. Jednak w każdym pliku, który korzysta z biblioteki DLL, należy nadal korzystać `__declspec(dllimport)` z deklaracji danych.

## <a name="see-also"></a>Zobacz także

[Zasady dla instrukcji definicji modułu](rules-for-module-definition-statements.md)
