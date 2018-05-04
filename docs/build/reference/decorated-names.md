---
title: Nazwy ozdobione | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 794e7583158379f84c5ee20408fb784aca213669
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="decorated-names"></a>Nazwy ozdobione
Funkcje, danych i obiektów w programach C i C++ są reprezentowane wewnętrznie przez ich nazwy ozdobione. A *dekorowane nazwy* jest zakodowany ciąg utworzony przez kompilator podczas kompilowania obiektu, danych lub definicji funkcji. Rejestruje konwencji wywoływania, typy parametrów funkcji i inne informacje, łącznie z nazwą. Ta nazwij dekorację, nazywany również *przekręcona nazwa*, pomaga konsolidator Znajdź poprawne funkcje i obiekty podczas łączenia pliku wykonywalnego.  
  
 Ozdobione konwencje nazewnictwa zostały zmienione w różnych wersjach programu Visual C++, a także mogą być różne na inny element docelowy architektury. Aby połączyć poprawnie z plikami źródłowymi utworzone za pomocą języka Visual C++, C i C++ bibliotek DLL i biblioteki ma być kompilowana przy użyciu tego samego zestawu narzędzi kompilatora, flag i Architektura docelowa.  
  
 **Zawartość**  
  
-   [Przy użyciu nazwy ozdobione](#Using)  
  
-   [Nazwy ozdobione format C++](#Format)  
  
-   [Nazwy ozdobione format języka c](#FormatC)  
  
-   [Nazwy ozdobione wyświetlania](#Viewing)  
  
-   [Wyświetlanie bez nazwy](#Undecorated)  
  
##  <a name="Using"></a> Przy użyciu nazwy ozdobione  
 Zwykle nie trzeba znać nazwa napisać kod, który kompiluje i linki pomyślnie. Nazwy ozdobione są wewnętrzne kompilatorze i konsolidatorze szczegóły implementacji. Narzędzia zazwyczaj może obsługiwać nazwy w postaci bez. Jednak nazwy ozdobione czasami jest wymagany po określeniu nazwę funkcji, aby konsolidator i inne narzędzia. Na przykład aby dopasować przeciążonej funkcji języka C++, elementów członkowskich przestrzeni nazw, konstruktorów klas i destruktory specjalnych funkcji Członkowskich, należy określić nazwę dekorowany. Aby uzyskać więcej informacji dotyczących opcji flagi i w innych sytuacjach, które wymagają nazwy ozdobione, zobacz dokumentację narzędzia i opcje, które są używane.  
  
 Jeśli zmienisz nazwę funkcji, klasy, Konwencja wywoływania, zwracany typ lub żadnego parametru ozdobione zmienia się również nazwa. W takim przypadku należy pobrać nowe nazwy ozdobione i użyj wszędzie tam, gdzie nazwa jest określona.  
  
 Nazwij dekorację są też ważne podczas łączenia z kodu napisanego w innych językach programowania lub przy użyciu inne kompilatory. Kompilatory różnych Użyj różnych nazw decoration Konwencji. Jeśli pliku wykonywalnego zawiera łącza do kodu napisanego w innym języku, należy szczególną do dopasowania nazwy wyeksportowane i zaimportowane i konwencji wywoływania. Kod języka zestawu musi użyć Visual C++ dekorowane nazwy i Konwencje wywoływania, aby połączyć do kodu źródłowego napisane przy użyciu języka Visual C++.  
  
##  <a name="Format"></a> Nazwy ozdobione format C++  
 Ozdobione nazwę funkcji C++ zawiera następujące informacje:  
  
-   Nazwa funkcji.  
  
-   Klasa funkcja jest elementem członkowskim, jeśli jest to funkcja elementu członkowskiego. To może zawierać klasę, która obejmuje klasę, która zawiera funkcję i tak dalej.  
  
-   Przestrzeń nazw funkcji, do której należy, jeśli jest częścią przestrzeni nazw.  
  
-   Typy parametrów funkcji.  
  
-   Konwencja wywoływania.  
  
-   Zwracany typ funkcji.  
  
 Nazwy funkcji i klasy są kodowane w nazwa. Pozostała część nazwa jest kod, który ma znaczenie wewnętrzny tylko dla kompilatora i konsolidator. Poniżej przedstawiono przykłady bez i ozdobione nazw C++.  
  
|Bez nazwy|Nazwy ozdobione|  
|----------------------|--------------------|  
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|  
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|  
  
##  <a name="FormatC"></a> Nazwy ozdobione format języka c  
 Formę decoration dla funkcji C zależy od Konwencja wywoływania używany w jego deklaracji, jak pokazano w poniższej tabeli. Jest używany, gdy kod w języku C++ jest zadeklarowana, aby mieć format decoration `extern "C"` połączenie. Jest domyślną konwencję wywoływania `__cdecl`. Należy pamiętać, że w środowisku 64-bitowym, funkcje nie są oznaczone.  
  
|Konwencja wywoływania|Decoration|  
|------------------------|----------------|  
|`__cdecl`|Wiodący znak podkreślenia (**_**)|  
|`__stdcall`|Wiodący znak podkreślenia (**_**) i końcowe znak @ (@) następuje liczba bajtów na liście parametrów dziesiątkowo|  
|`__fastcall`|Spacji wiodących i końcowych znaków (@) następuje liczbą dziesiętną reprezentujący liczbę bajtów na liście parametrów|  
|`__vectorcall`|Końcowe dwóch znaków @@ następuje liczbą dziesiętną bajtów na liście parametrów|  
  
##  <a name="Viewing"></a> Nazwy ozdobione wyświetlania  
 Możesz uzyskać ozdobione formę nazwy symbolu Po skompilowaniu plik źródłowy, który zawiera dane, obiekt, lub definicji funkcji lub prototypu. Aby Sprawdź nazwy ozdobione w programie, można użyć jednej z następujących metod:  
  
-   #### <a name="to-use-a-listing-to-view-decorated-names"></a>Umożliwia wyświetlanie listy nazwy ozdobione  
  
    1.  Generowanie listy według kompilowanie pliku źródłowego, który zawiera dane, obiekt, lub definicji funkcji lub prototyp z [listę typów plików](../../build/reference/fa-fa-listing-file.md) ustawioną zestaw z kodem źródłowym — opcja kompilatora (**/FAS**).  
  
         Na przykład wprowadź `cl /c /FAs example.cpp` w wierszu polecenia dewelopera, aby wygenerować plik listy example.asm.  
  
    2.  W wynikowym pliku listy odnaleźć wiersza, który rozpoczyna się od publicznego i kończy się średnikiem następuje nazwa bez danych lub funkcji. Symbol między publicznym i średnik jest również nazwa.  
  
-   #### <a name="to-use-dumpbin-to-view-decorated-names"></a>Nazwy ozdobione wyświetlać za pomocą polecenia DUMPBIN  
  
    1.  Aby zobaczyć wyeksportowane symboli w pliku obj lub lib, wprowadź `dumpbin /symbols` `objfile` w wierszu polecenia dewelopera.  
  
    2.  Aby znaleźć ozdobione formularza symbolu, wyszukaj nazwę bez w nawiasach. Nazwa jest w tym samym wierszu, po kreski pionowej (&#124;) znaków i przed bez nazwy.  
  
##  <a name="Undecorated"></a> Wyświetlanie bez nazwy  
 Undname.exe służy do konwertowania nazwy ozdobione do postaci bez. Ten przykład przedstawia, jak to działa:  
  
```  
C:\>undname ?func1@a@@AAEXH@Z  
Microsoft (R) C++ Name Undecorator  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
Undecoration of :- "?func1@a@@AAEXH@Z"  
is :- "private: void __thiscall a::func1(int)"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)   
 [Użycie zewnętrznie w celu określenia powiązania](../../cpp/using-extern-to-specify-linkage.md)