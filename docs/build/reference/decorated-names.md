---
title: Nazwy ozdobione
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: e3950f79c4c88d031e04d0d145e0a03c9ebc0a37
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221795"
---
# <a name="decorated-names"></a>Nazwy ozdobione

Funkcje, dane i obiekty w ramach programów C i C++ są reprezentowane wewnętrznie przez ich nazwy dekoracyjne. A *nazwy ozdobionej* jest zakodowany ciąg utworzony przez kompilator podczas kompilowania obiektu, danych lub definicji funkcji. Rejestruje konwencji wywoływania, typów, parametrów funkcji i inne informacje wraz z nazwą. Ta dekorowania nazwy, nazywana również *dekorowanie nazw*pomaga konsolidatora Znajdź poprawną funkcje i obiekty, gdy łączenie pliku wykonywalnego.

Konwencje nazewnictwa ozdobione zostały zmienione w różnych wersjach programu Visual Studio i mogą być także różne w różnych docelowych architektur. Połączyć poprawnie przy użyciu plików źródłowych, utworzony przy użyciu programu Visual Studio C i C++ bibliotek DLL i bibliotek powinna być skompilowana przy użyciu tego samego zestawu narzędzi kompilatora, flag i Architektura docelowa. 

> [!NOTE]
> Biblioteki utworzonych za pomocą programu Visual Studio 2015, mogą być używane przez aplikacje utworzone przy użyciu programu Visual Studio 2017 lub Visual Studio 2019 r.

##  <a name="Using"></a> Za pomocą nazw ozdobionych

Zwykle nie trzeba znać nazwę uzupełnioną napisać kod, który kompiluje i łączy pomyślnie. Nazwy ozdobione są wewnętrzne kompilatora i konsolidatora szczegółowo opisuje implementacja. Narzędzia zazwyczaj może obsługiwać nazwy w postaci niedekorowanego. Jednak dekorowaną nazwę czasami jest wymagany po określeniu nazwy funkcji, program łączący i inne narzędzia. Na przykład aby dopasować przeciążonej funkcji języka C++, elementów członkowskich przestrzeni nazw, klasy konstruktorów, destruktorów i specjalnych funkcji Członkowskich, należy określić nazwę z atrybutami. Szczegółowe informacje na temat opcji flag i innych sytuacjach, które wymagają nazwy dekorowane, zobacz dokumentację narzędzia i opcje, które są używane.

Jeśli zmienisz nazwę funkcji, klasy, Konwencja wywoływania, typ zwracany lub żadnych parametrów, zmienia się również nazwę uzupełnioną W takim przypadku należy pobrać nowe nazwy dekoracyjne i użyć wszędzie tam, gdzie określono nazwę z atrybutami.

Nazwij dekorację ważne jest również podczas łączenia do kodu napisanego w innych językach programowania lub za pomocą innych kompilatorów. Różne kompilatory używają różnych konwencji dekorowania nazwy. Gdy plik wykonywalny łączy do kodu napisanego w innym języku, specjalne należy uważać, aby odpowiadać nazwom wyeksportowane i zaimportowane i Konwencje wywoływania. Kod języka zestawu musi być nazwy dekorowane MSVC i Konwencje wywoływania link do kodu źródłowego napisanego przy użyciu MSVC.

##  <a name="Format"></a> Format C++ nazwy ozdobionej

Dekorowaną nazwę dla funkcji języka C++ zawiera następujące informacje:

- Nazwa funkcji.

- Klasa, że funkcja ta jest członkiem, jeśli jest to funkcja elementu członkowskiego. To może zawierać klasę, która zawiera klasę, która zawiera funkcję i tak dalej.

- Przestrzeń nazw funkcji, do której należy, jeśli jest on częścią przestrzeni nazw.

- Typy parametrów funkcji.

- Konwencja wywoływania.

- Typ zwrotny funkcji.

Nazwy funkcji i klas są kodowane w również nazwę uzupełnioną. Pozostałe nazwa uzupełniona jest kod, który ma znaczenie wewnętrzny tylko dla kompilatora i konsolidatora. Poniżej przedstawiono przykłady niedekorowanego i ozdobione nazw języka C++.

|Nieozdobioną nazwę|Nazwy ozdobione|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

##  <a name="FormatC"></a> C format nazwy ozdobionej

Formularza dekorację funkcji C zależy od konwencji wywoływania, używany w jego deklaracji, jak pokazano w poniższej tabeli. Jest używany, gdy kod języka C++ jest zadeklarowany ma format dekoracji `extern "C"` powiązania. Wartość domyślna konwencja wywołania to `__cdecl`. Należy pamiętać, że w środowisku 64-bitowych, funkcje nie są oznaczone.

|Konwencja wywoływania|Dekoracja|
|------------------------|----------------|
|`__cdecl`|Wiodący znak podkreślenia (**_**)|
|`__stdcall`|Wiodący znak podkreślenia (**_**) i końcowe znakiem (**\@**) następuje liczba bajtów na liście parametrów w zapisie dziesiętnym|
|`__fastcall`|Początkowe i końcowe znaków (**\@**) następuje liczba dziesiętna reprezentujący liczbę bajtów na liście parametrów|
|`__vectorcall`|Końcowe znakami dwóch (**\@\@**) następuje dziesiętna liczba bajtów na liście parametrów|

##  <a name="Viewing"></a> Wyświetlanie dekorowane nazwy

Po skompilowaniu pliku źródłowego, który zawiera dane, obiekt lub definicji funkcji lub prototypu, możesz uzyskać ozdobione postaci nazwy symbolu. Aby zbadać nazwy dekorowane w swoim programie, można użyć jednej z następujących metod:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Użyj, aby wyświetlić listę nazw ozdobionych

1. Generowanie listy przez kompilowanie pliku źródłowego, który zawiera dane, obiekt lub definicji funkcji lub prototyp z [listę typu pliku](fa-fa-listing-file.md) — opcja kompilatora równa asembler z kodem źródłowym (**/FAS**).

   Na przykład, wprowadź `cl /c /FAs example.cpp` w wierszu polecenia dla deweloperów, aby wygenerować plik listingu example.asm.

2. W pliku wynikowego listy Znajdź wiersz, który rozpoczyna się od publicznego i kończy się średnikiem nieozdobioną nazwę danych lub funkcji. Symbol między publicznym i średnik jest również nazwę uzupełnioną.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Użycie DUMPBIN do wyświetlania nazw ozdobionych

1. Aby wyświetlić wyeksportowane symboli w pliku .obj lub .lib, wprowadź `dumpbin /symbols` `objfile` polecenie w wierszu polecenia dla deweloperów.

2. Aby znaleźć ozdobione formularz symbolu, poszukaj nieozdobioną nazwę zawartej w nawiasach. Nazwa uzupełniona jest w tym samym wierszu po potoku (&#124;) znak i przed nieozdobioną nazwę.

##  <a name="Undecorated"></a> Wyświetlanie bez nazwy

Undname.exe umożliwia konwertowanie dekorowaną nazwę do postaci niedekorowanego. Ten przykład pokazuje, jak to działa:

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Zobacz także

[MSVC dodatkowe narzędzia do kompilacji](c-cpp-build-tools.md)<br/>
[Użycie zewnętrznie w celu określenia powiązania](../../cpp/using-extern-to-specify-linkage.md)
