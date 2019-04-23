---
title: '#include — dyrektywa (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 7ffccb34d52f8ffa1e6b9cc64a58d3471d02ac92
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038984"
---
# <a name="include-directive-cc"></a>#include — dyrektywa (C/C++)

Nakazuje preprocesorowi traktować zawartość określonego pliku, tak, jakby pojawiają się w programie źródłowym w punkcie, w którym pojawia się dyrektywa.

## <a name="syntax"></a>Składnia

```
#include  "path-spec"
#include  <path-spec>
```

## <a name="remarks"></a>Uwagi

Możesz zorganizować definicje stałych i makr w plikach dołączonych, a następnie użyć **#include** dyrektywy, aby dodać je do pliku źródłowego. Obejmują pliki są także przydatne przy dołączaniu deklaracje zmiennych zewnętrznych i złożonych typów danych. Typy może być zdefiniowane i nazwane tylko raz pomocą stworzonego w tym celu pliku.

*Path-spec* jest nazwą pliku, który opcjonalnie może być poprzedzona przez specyfikację katalogu. Nazwa pliku musi odnosić istniejącego pliku. Składnia *path-spec* zależy od systemu operacyjnego, w którym program jest skompilowany.

Aby uzyskać informacje dotyczące zestawów odwołań w języku C++ aplikacji, który jest kompilowany przy użyciu [/CLR](../build/reference/clr-common-language-runtime-compilation.md), zobacz [#using](../preprocessor/hash-using-directive-cpp.md).

Obie formy składni powodują tej dyrektywy, które mają zostać zastąpione przez całą zawartość określonegop dołączanego pliku. Różnica między dwoma formami polega na kolejności, w której preprocesor szuka plików nagłówkowych, jeśli ścieżka nie jest całkowicie określona. W poniższej tabeli przedstawiono różnice między dwoma formami składni.

|Forma składni|Akcja|
|---|------------|
|Cytowany formularz|Preprocesor wyszukuje pliki dołączane w następującej kolejności:<br/><br/> (1) w tym samym katalogu co plik, który zawiera **#include** instrukcji.<br/><br/> 2) w wszelkich aktualnie otwartych katalogów Dołącz pliki w odwrotnej kolejności, w jakiej zostały otwarte. Wyszukiwanie rozpoczyna się w katalogu nadrzędnego dołączyć plik i jest kontynuowane w górę przez katalogi stojących dołączyć pliki.<br/><br/> (3) na ścieżce określonej przez każdą **/I** — opcja kompilatora.<br/><br/> (4) wzdłuż ścieżek, które są określone przez zmienną środowiskową INCLUDE.|
|Formularz nawias kątowy|Preprocesor wyszukuje pliki dołączane w następującej kolejności:<br/><br/> (1) na ścieżce określonej przez każdą **/I** — opcja kompilatora.<br/><br/> (2) podczas kompilacji wykonywanej w wierszu polecenia, wzdłuż ścieżek które są określone przez zmienną środowiskową INCLUDE.|

Preprocesor przestaje wyszukiwać, natychmiast po odnalezieniu pliku o podanej nazwie. Jeśli uwzględnisz pełną, jednoznaczną specyfikację ścieżki do dołączanego pliku między znakami podwójnego cudzysłowu (**""**), preprocesor przeszukuje tylko tę specyfikację ścieżki i ignoruje katalogi standardowe.

Jeśli nazwa pliku ujęta w znaki podwójnego cudzysłowu jest niekompletnym opisem ścieżki, preprocesor najpierw przeszukuje katalog "rodzicielski". Plik, który zawiera plik jest plikiem nadrzędnym **#include** dyrektywy. Na przykład uwzględnisz plik o nazwie *plik2* w pliku o nazwie *plik1*, *plik1* jest plikiem nadrzędnym.

Dołącz pliki, które mogą być "zagnieżdżone"; oznacza to, że **#include** dyrektywy może znajdować się w pliku nazwanym przez inną **#include** dyrektywy. Na przykład *plik2* może obejmować *plik3*. W tym przypadku *plik1* nadal będzie nadrzędny *plik2*, ale będzie "dziadkiem" wobec *plik3*.

Gdy obejmują pliki są gnieżdżone i podczas kompilacji wykonywanej w wierszu polecenia, wyszukiwanie katalogów rozpoczyna się od katalogów pliku nadrzędnego i następnie przechodzi przez katalogi plików nadrzędnych wobec niego. Oznacza to wyszukiwanie rozpoczyna się względem katalogu zawierającego źródło obecnie przetwarzane. Jeśli plik nie zostanie znaleziony, wyszukiwanie przenosi się do katalogów określonych przez [/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md) — opcja kompilatora. Na koniec przeszukiwane są katalogi, które są określone przez zmienną środowiskową INCLUDE.

W środowisku programowania Visual Studio zmienna środowiskowa INCLUDE jest ignorowana. Aby uzyskać informacje o ustawianiu katalogów przeszukiwanych w poszukiwaniu plików dołączanych — dotyczy to również zmiennej środowiska LIB — zobacz [VC ++ Directories Property Page](../build/reference/vcpp-directories-property-page.md).

Ten przykład pokazuje włączenie pliku przy użyciu nawiasów:

```
#include <stdio.h>
```

Ten przykład dodaje zawartość pliku o nazwie stdio —. H do programu źródłowego. Nawiasy kątowe sprawiają, że preprocesor przeszukuje katalogi, które są określone przez zmienną środowiskową INCLUDE dla stdio —. Godz., po przeszukuje katalogi, które są określone przez **/I** — opcja kompilatora.

Następny przykład pokazuje włączenie pliku przy użyciu formy z cytatami:

```
#include "defs.h"
```

Ten przykład dodaje zawartość pliku, który jest określony przez DEFS. H do programu źródłowego. Podwójny cudzysłów oznacza, że preprocesor najpierw przeszukuje katalog zawierający nadrzędny plik źródłowy.

Zagnieżdżanie plików dołączanych można kontynuować do 10 poziomów. Gdy zagnieżdżony **#include** jest przetwarzany, preprocesor w dalszym ciągu Wstawia plik załączany do oryginalnego pliku źródłowego.

**Microsoft Specific**

Aby zlokalizować pliki źródłowe do zawarcia, preprocesor najpierw przeszukuje katalogi, które są określone przez **/I** — opcja kompilatora. Jeśli **/I** opcji nie istnieje lub nie powiedzie się, preprocesor wykorzysta zmienną środowiskową INCLUDE, aby znaleźć wszystkie pliki dołączane w nawiasach kątowych. Zmienna środowiskowa INCLUDE i **/I** — opcja kompilatora może zawierać wiele ścieżek oddzielonych średnikami (**;**). Jeśli więcej niż jeden katalog pojawia się jako część **/I** opcję lub w ramach zmienną środowiskową INCLUDE, preprocesor przeszukuje je w kolejności, w jakiej są wyświetlane.

Na przykład polecenie

```
CL /ID:\MSVC\INCLUDE MYPROG.C
```

powoduje, że preprocesor wyszukuje w katalogu D:\MSVC\INCLUDE\ pliki dołączane, takie jak stdio —. H. Polecenia

```
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

mają ten sam efekt. Jeśli oba zestawy wyszukiwań nie powiodą się, generowany jest błąd krytyczny kompilatora.

Jeśli nazwa pliku jest w pełni określona dla pliku dołączanego, który zawiera ścieżkę, która zawiera dwukropek (na przykład F:\MSVC\SPECIAL\INCL\TEST. Godz.), preprocesor postępuje zgodnie ze ścieżką.

Dla plików dołączanych, które są określone jako `#include "path-spec"`, wyszukiwanie katalogów rozpoczyna się od katalogu nadrzędnego pliku, a następnie przechodzi przez katalogi plików nadrzędnych wobec niego. Oznacza to, wyszukiwanie rozpoczyna się względem katalogu zawierającego plik źródłowy, który zawiera **#include** dyrektywę, który jest przetwarzany. Jeśli plik pokolenia nie istnieje, a plik nie został znaleziony, wyszukiwanie jest kontynuowane tak, jakby nazwa pliku została ujęta w nawiasy ostre.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)<br/>
[/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md)<br/>
