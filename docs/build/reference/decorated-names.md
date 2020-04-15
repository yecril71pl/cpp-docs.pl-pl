---
title: Nazwy ozdobione
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: f6d81029d20d9aaca96ff184f48e94a9ce35d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320503"
---
# <a name="decorated-names"></a>Nazwy ozdobione

Funkcje, dane i obiekty w programach C i C++ są reprezentowane wewnętrznie przez ich nazwy dekoracyjne. Dekoracyjna *nazwa* jest zakodowanym ciągiem utworzonym przez kompilator podczas kompilacji obiektu, danych lub definicji funkcji. Rejestruje konwencje wywołujące, typy, parametry funkcji i inne informacje wraz z nazwą. Ta dekoracja nazwy, znana również jako *mangling nazw,* pomaga konsolidatorowi znaleźć poprawne funkcje i obiekty podczas łączenia pliku wykonywalnego.

Dekoracyjne konwencje nazewnictwa uległy zmianie w różnych wersjach programu Visual Studio i mogą być również różne w różnych architekturach docelowych. Aby poprawnie połączyć się z plikami źródłowymi utworzonymi przy użyciu programu Visual Studio, biblioteki DLL i biblioteki DLL w języku C i C++ i biblioteki powinny być kompilowane przy użyciu tego samego zestawu narzędzi kompilatora, flag i architektury docelowej.

> [!NOTE]
> Biblioteki utworzone za pomocą programu Visual Studio 2015 mogą być używane przez aplikacje utworzone za pomocą programu Visual Studio 2017 lub Visual Studio 2019.

## <a name="using-decorated-names"></a><a name="Using"></a>Używanie dekorowanych nazw

Zwykle nie trzeba znać dekoracyjną nazwę, aby napisać kod, który kompiluje i łączy pomyślnie. Dekoracyjne nazwy są szczegóły implementacji wewnętrzne do kompilatora i konsolidatora. Narzędzia zazwyczaj mogą obsługiwać nazwę w postaci niezrażonej. Jednak dekoracyjna nazwa jest czasami wymagana podczas określania nazwy funkcji konsolidatora i innych narzędzi. Na przykład, aby dopasować przeciążonych funkcji C++, członków obszarów nazw, konstruktorów klas, destruktorów i specjalnych funkcji członkowskich, należy określić nazwę dekoracyjną. Aby uzyskać szczegółowe informacje na temat flag opcji i innych sytuacji, które wymagają dekoracyjnych nazw, zobacz dokumentację narzędzi i opcji, których używasz.

Jeśli zmienisz nazwę funkcji, klasę, konwencję wywoływania, typ zwracany lub dowolny parametr, nazwa dekoracyjna również się zmieni. W takim przypadku należy uzyskać nową nazwę dekoracyjną i używać jej wszędzie tam, gdzie określono nazwę dekoracyjną.

Dekoracja nazwy jest również ważne podczas łączenia do kodu napisanego w innych językach programowania lub przy użyciu innych kompilatorów. Różne kompilatory używają różnych konwencji dekoracji nazw. Gdy można wykonywalne łącza do kodu napisanego w innym języku, należy zwrócić szczególną uwagę, aby dopasować eksportowane i importowane nazwy i konwencje wywoływania. Kod języka zestawu musi używać msvc dekoracyjne nazwy i konwencje wywoływania do łącza do kodu źródłowego napisanego przy użyciu MSVC.

## <a name="format-of-a-c-decorated-name"></a><a name="Format"></a>Format nazwy dekoracyjnej języka C++

Udekorowana nazwa funkcji Języka C++ zawiera następujące informacje:

- Nazwa funkcji.

- Klasa, do jakiej należy pełnić funkcję, jeśli jest to funkcja elementu członkowskiego. Może to obejmować klasę, która otacza klasę, która zawiera funkcję i tak dalej.

- Obszar nazw, do którego należy funkcja, jeśli jest częścią obszaru nazw.

- Typy parametrów funkcji.

- Konwencja wywołująca.

- Zwracany typ funkcji.

Nazwy funkcji i klas są zakodowane w nazwie dekoracyjną. Reszta nazwy dekoracyjną to kod, który ma wewnętrzne znaczenie tylko dla kompilatora i konsolidatora. Poniżej przedstawiono przykłady niezrażonych i zdobionych nazw C++.

|Niezdrobniona nazwa|Nazwa zdobiona|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

## <a name="format-of-a-c-decorated-name"></a><a name="FormatC"></a>Format nazwy zdobionej c

Forma dekoracji dla funkcji C zależy od konwencji wywołującej używanej w jej deklaracji, jak pokazano w poniższej tabeli. Jest to również format dekoracji, który jest używany, `extern "C"` gdy kod C++ jest zadeklarowany jako mający powiązania. Domyślną konwencją `__cdecl`wywoływania jest . Należy zauważyć, że w środowisku 64-bitowym funkcje nie są dekorowane.

|Konwencja wywoływania|Dekoracji|
|------------------------|----------------|
|`__cdecl`|Podkreślenie wiodące (**_**)|
|`__stdcall`|Podkreślenie wiodące (**_**)**\@** i końcowe na znak ( ), po którym następuje liczba bajtów na liście parametrów w przecinku|
|`__fastcall`|Prowadzenie i końcowe znaki**\@**( ), po którym następuje liczba dziesiętna reprezentująca liczbę bajtów na liście parametrów|
|`__vectorcall`|Dwa końcowe znaki**\@**( ), po których na liście parametrów znajduje się liczba dziesiętnych bajtów|

## <a name="viewing-decorated-names"></a><a name="Viewing"></a>Wyświetlanie udekorowanych nazw

Po skompilowaniu pliku źródłowego zawierającego dane, obiekt lub definicję lub prototyp można uzyskać dekoracyjną formę nazwy symbolu. Aby sprawdzić dekoracyjne nazwy w programie, można użyć jednej z następujących metod:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Aby użyć aukcji do wyświetlania udekorowanych nazw

1. Generowanie listy przez kompilowanie pliku źródłowego zawierającego definicję danych, obiektu lub funkcji lub prototyp z opcją kompilatora [typu pliku aukcji](fa-fa-listing-file.md) ustawioną na Zestaw z kodem źródłowym (**/FAs**).

   Na przykład `cl /c /FAs example.cpp` wprowadź w wierszu polecenia dewelopera, aby wygenerować plik aukcji, example.asm.

2. W wynikowym pliku aukcji znajdź wiersz rozpoczynający się od PUBLIC i kończy średnik, po którym następuje niezrażonych danych lub nazwa funkcji. Symbolem między PUBLIC a średnikiem jest nazwa dekoracyjna.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Aby wyświetlić nazwy dekoracyjne, aby użyć funkcji DUMPBIN

1. Aby wyświetlić wyeksportowane symbole w pliku `dumpbin /symbols` `objfile` obj lub lib, wprowadź w wierszu polecenia dewelopera.

2. Aby znaleźć dekoracyjną formę symbolu, poszukaj nazwy niezdrobnionej w nawiasach. Nazwa dekoracyjna znajduje się w tym samym wierszu, po znaku potoku (&#124;) i przed nazwą niezrażoną.

## <a name="viewing-undecorated-names"></a><a name="Undecorated"></a>Wyświetlanie niezdrobnionych nazw

Za pomocą undname.exe można przekonwertować dekoracyjną nazwę na jej niezrażony formularz. W tym przykładzie pokazano, jak to działa:

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Zobacz też

[Dodatkowe narzędzia do budowania MSVC](c-cpp-build-tools.md)<br/>
[Użycie zewnętrznie w celu określenia powiązania](../../cpp/using-extern-to-specify-linkage.md)
