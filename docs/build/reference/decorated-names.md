---
title: Nazwy ozdobione
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: 3389b5466bf4a2a48c5e36b01da6818a523fec6f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077349"
---
# <a name="decorated-names"></a>Nazwy ozdobione

Funkcje, dane i obiekty w C i C++ programy są reprezentowane wewnętrznie przez ich nazwy dekoracyjne. *Nazwa dekoracyjna* to zakodowany ciąg utworzony przez kompilator podczas kompilowania definicji obiektu, danych lub funkcji. Rejestruje konwencje wywoływania, typy, parametry funkcji i inne informacje razem z nazwą. Ten dekoracja nazwy, znana także jako *Nazwa dekorowanie*, ułatwia konsolidatorowi znalezienie poprawnych funkcji i obiektów podczas łączenia pliku wykonywalnego.

Konwencje nazewnictwa dekoracyjne uległy zmianie w różnych wersjach programu Visual Studio i mogą być różne w różnych architekturach docelowych. Aby prawidłowo połączyć się z plikami źródłowymi utworzonymi za pomocą programu Visual Studio C++ , C i dll i biblioteki powinny być kompilowane przy użyciu tego samego zestawu narzędzi kompilatora, flag i architektury docelowej.

> [!NOTE]
> Biblioteki skompilowane z programem Visual Studio 2015 mogą być używane przez aplikacje skompilowane przy użyciu programu Visual Studio 2017 lub Visual Studio 2019.

##  <a name="using-decorated-names"></a><a name="Using"></a>Korzystanie z dekoracyjnych nazw

Zwykle nie trzeba znać nazwy dekoracyjnej, aby napisać kod, który pomyślnie kompiluje i łączy. Nazwy dekoracyjne to szczegóły implementacji wewnętrzne dla kompilatora i konsolidatora. Narzędzia mogą zazwyczaj obsługiwać nazwę w postaci niedekoracyjnej. Jednak nazwa dekoracyjna jest czasami wymagana w przypadku określenia nazwy funkcji dla konsolidatora i innych narzędzi. Na przykład aby dopasować przeciążone C++ funkcje, elementy członkowskie przestrzeni nazw, konstruktory klas, destruktory i specjalne funkcje członkowskie, należy określić nazwę dekoracyjną. Aby uzyskać szczegółowe informacje na temat flag opcji i innych sytuacji, które wymagają nazw dekoracyjnych, zapoznaj się z dokumentacją narzędzi i opcji, których używasz.

W przypadku zmiany nazwy funkcji, klasy, konwencji wywoływania, typu zwracanego lub dowolnego parametru, nazwa dekoracyjna również ulega zmianie. W takim przypadku należy uzyskać nową nazwę dekoracyjną i użyć jej wszędzie tam, gdzie jest określona nazwa dekoracyjna.

Dekoracja nazw jest również ważna w przypadku łączenia się z kodem zapisanym w innych językach programowania lub przy użyciu innych kompilatorów. Różne kompilatory używają różnych konwencji dekoracji nazw. Gdy plik wykonywalny łączy się z kodem zapisanym w innym języku, należy zwrócić szczególną uwagę na wyeksportowane i zaimportowane nazwy oraz konwencje wywoływania. Kod języka asemblera musi używać nazw dekoracyjnych MSVC i konwencji wywoływania do łączenia się z kodem źródłowym zapisanym przy użyciu MSVC.

##  <a name="format-of-a-c-decorated-name"></a><a name="Format"></a>Format nazwy C++ dekoracyjnej

Nazwa dekoracyjna C++ funkcji zawiera następujące informacje:

- Nazwa funkcji.

- Klasa, do której należy funkcja, jeśli jest to funkcja członkowska. Może to obejmować klasę, która zawiera klasę zawierającą funkcję i tak dalej.

- Przestrzeń nazw, do której należy funkcja, jeśli jest częścią przestrzeni nazw.

- Typy parametrów funkcji.

- Konwencja wywoływania.

- Zwracany typ funkcji.

Nazwy funkcji i klas są zakodowane w nazwie dekoracyjnej. Pozostała część nazwy dekoracyjnej to kod, który ma wewnętrzne znaczenie tylko dla kompilatora i konsolidatora. Poniżej przedstawiono przykłady niedekoracyjnych i dekoracyjnych C++ nazw.

|Nazwa niedekoracyjna|Nazwa dekoracyjna|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

##  <a name="format-of-a-c-decorated-name"></a><a name="FormatC"></a>Format nazwy dekoracyjnej języka C

Forma dekoracji dla funkcji języka C zależy od konwencji wywoływania używanej w jej deklaracji, jak pokazano w poniższej tabeli. Jest to również format dekoracyjny, który jest używany C++ , gdy kod jest zadeklarowany do powiązania `extern "C"`. Domyślna konwencja wywoływania jest `__cdecl`. Należy pamiętać, że w środowisku 64-bitowym funkcje nie są dekoracyjne.

|Konwencja wywoływania|Dekorację|
|------------------------|----------------|
|`__cdecl`|Wiodący znak podkreślenia ( **_** )|
|`__stdcall`|Wiodący znak podkreślenia ( **_** ) i znak końcowy ( **\@** ), po którym następuje liczba bajtów na liście parametrów w wartości dziesiętnej|
|`__fastcall`|Wiodące i końcowe znaki ( **\@** ), po których następuje liczba dziesiętna reprezentująca liczbę bajtów na liście parametrów|
|`__vectorcall`|Dwa końcowe znaki ( **\@\@** ), po których następuje dziesiętna liczba bajtów na liście parametrów|

##  <a name="viewing-decorated-names"></a><a name="Viewing"></a>Wyświetlanie dekoracyjnych nazw

Po skompilowaniu pliku źródłowego, który zawiera dane, obiekt lub definicję funkcji lub prototyp, można uzyskać dekoracyjną postać nazwy symbolu. Aby przejrzeć dekoracyjne nazwy w programie, można użyć jednej z następujących metod:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Aby użyć listy do wyświetlania dekoracyjnych nazw

1. Wygeneruj listę, kompilując plik źródłowy, który zawiera definicję danych, obiektu lub funkcji albo prototyp z [listą typów plików](fa-fa-listing-file.md) z opcją kompilatora zestawu z kodem źródłowym ( **/FAS**).

   Na przykład wprowadź `cl /c /FAs example.cpp` w wierszu polecenia dewelopera, aby wygenerować plik listy, przykład. asm.

2. W wyszukiwanym pliku listy Znajdź wiersz, który rozpoczyna się od publicznego i kończy średnik, po którym następuje niedekoracyjne dane lub nazwa funkcji. Symbol między PUBLICZNą i średnikiem jest nazwą dekoracyjną.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Aby używać polecenia DUMPBIN do wyświetlania dekoracyjnych nazw

1. Aby wyświetlić eksportowane symbole w pliku obj lub lib, wpisz `dumpbin /symbols` `objfile` w wierszu polecenia dewelopera.

2. Aby znaleźć dekoracyjną postać symbolu, poszukaj niedekoracyjnej nazwy w nawiasach. Nazwa dekoracyjna znajduje się w tym samym wierszu, po znaku potoku (&#124;) i przed nazwą niedekoracyjną.

##  <a name="viewing-undecorated-names"></a><a name="Undecorated"></a>Wyświetlanie niedekoracyjnych nazw

Można użyć Undname. exe do przekonwertowania dekoracyjnej nazwy na postać niedekoracyjną. Ten przykład pokazuje, jak działa:

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Zobacz też

[Dodatkowe narzędzia do kompilacji MSVC](c-cpp-build-tools.md)<br/>
[Użycie zewnętrznie w celu określenia powiązania](../../cpp/using-extern-to-specify-linkage.md)
