---
title: '#include, dyrektywa (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 0792f522427e5658de992969745878894fbd454d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220248"
---
# <a name="include-directive-cc"></a>#include — dyrektywa (CC++/)

Nakazuje preprocesorowi traktować zawartość określonego pliku, tak jakby pojawił się w programie źródłowym w punkcie, gdzie pojawia się dyrektywa.

## <a name="syntax"></a>Składnia

> **#include** "*path-spec*" \
> **#include** *ścieżka — Specyfikacja* \<>

## <a name="remarks"></a>Uwagi

Możesz zorganizować definicje stałych i makr w pliki dołączane, a następnie użyć dyrektyw **#include** , aby dodać je do dowolnego pliku źródłowego. Pliki dołączane są również przydatne do dołączania deklaracji zmiennych zewnętrznych i złożonych typów danych. Typy mogą być zdefiniowane i nazwane tylko raz w pliku dołączanym utworzonym do tego celu.

Metoda *path-spec* to nazwa pliku, która opcjonalnie może być poprzedzona przez specyfikację katalogu. Nazwa pliku musi mieć nazwę istniejącego pliku. Składnia funkcji *path-spec* zależy od systemu operacyjnego, w którym program jest kompilowany.

Aby uzyskać informacje dotyczące sposobu odwoływania się do C++ zestawów w aplikacji, która jest skompilowana przy użyciu [/clr](../build/reference/clr-common-language-runtime-compilation.md), zobacz [#using](../preprocessor/hash-using-directive-cpp.md).

Obie formy składni powodują, że dyrektywa jest zastępowana przez całą zawartość określonego pliku dołączanego. Różnica między dwoma formularzami polega na kolejności, w której preprocesor wyszukuje pliki nagłówkowe w przypadku niekompletnego określenia ścieżki. W poniższej tabeli przedstawiono różnice między dwoma formami składni.

|Formularz składni|Akcja|
|---|------------|
|Formularz w cudzysłowie|Preprocesor wyszukuje pliki dołączane w następującej kolejności:<br/><br/> 1) w tym samym katalogu, w którym znajduje się plik, który zawiera instrukcję **#include** .<br/><br/> 2) w katalogach aktualnie otwartych plików dołączanych w kolejności odwrotnej, w której zostały otwarte. Wyszukiwanie rozpoczyna się w katalogu nadrzędnego pliku dołączanego i kontynuuje w górę przez katalogi dowolnych plików dołączania.<br/><br/> 3) wzdłuż ścieżki, która jest określona przez każdą opcję kompilatora **/i** .<br/><br/> 4) wzdłuż ścieżek określonych przez zmienną środowiskową INCLUDE.|
|Formularz z nawiasami ostrymi|Preprocesor wyszukuje pliki dołączane w następującej kolejności:<br/><br/> 1) wzdłuż ścieżki określonej przez każdą opcję kompilatora **/i** .<br/><br/> 2) Kompilowanie odbywa się w wierszu polecenia, wzdłuż ścieżek, które są określone przez zmienną środowiskową INCLUDE.|

Preprocesor przestaje wyszukiwać po znalezieniu pliku o danej nazwie. Jeśli zapełnisz kompletną, jednoznaczną specyfikację ścieżki dla pliku dołączanego między podwójnym cudzysłowem (`" "`), preprocesor przeszukuje tylko tę specyfikację ścieżki i ignoruje katalogi standardowe.

Jeśli nazwa pliku ujęta w znaki podwójnego cudzysłowu jest niekompletną specyfikacją ścieżki, preprocesor najpierw przeszukuje katalog "nadrzędny". Plik nadrzędny to plik zawierający dyrektywę **#include** . Na przykład jeśli w pliku o nazwie *plik1*zostanie uwzględniony plik o nazwie *plik2* , *plik1* jest plikiem nadrzędnym.

Pliki dołączane mogą być "zagnieżdżone": Dyrektywa **#include** może pojawić się w pliku, który jest nazwany przez inną dyrektywę **#include** . Na przykład *plik2* może zawierać *file3*. W tym przypadku, *plik1* nadal będzie elementem nadrzędnym elementu *plik2*, ale będzie to "dziadka" *file3*.

Gdy pliki dołączane są zagnieżdżane i kompilowanie odbywa się w wierszu polecenia, wyszukiwanie w katalogu rozpoczyna się w katalogach pliku nadrzędnego. Następnie przechodzi przez katalogi dowolnych plików nadrzędnych. Oznacza to, że wyszukiwanie rozpoczyna się względem katalogu zawierającego źródło, które jest aktualnie przetwarzane. Jeśli plik nie zostanie znaleziony, wyszukiwanie przechodzi do katalogów, które są określone przez [/i (Dodatkowe katalogi dołączane)](../build/reference/i-additional-include-directories.md) opcji kompilatora. Na koniec przeszukiwane są katalogi, które są określone przez zmienną środowiskową INCLUDE.

W środowisku deweloperskim programu Visual Studio zmienna środowiskowa INCLUDE jest ignorowana. Aby uzyskać informacje na temat sposobu ustawiania katalogów przeszukiwanych w poszukiwaniu plików i plików bibliotek, zobacz [stronę właściwości katalogów VC + +](../build/reference/vcpp-directories-property-page.md).

Ten przykład przedstawia dołączenie pliku przy użyciu nawiasów ostrych:

```C
#include <stdio.h>
```

Ten przykład dodaje zawartość pliku o nazwie STDIO. H do programu źródłowego. Nawiasy kątowe powodują, że preprocesor Przeszukuje katalogi, które są określone przez zmienną środowiskową INCLUDE dla STDIO. H, po przeszukaniu katalogów, które są określone przez **/i** opcję kompilatora.

W następnym przykładzie przedstawiono dołączenie pliku przy użyciu formularza w cudzysłowie:

```C
#include "defs.h"
```

Ten przykład dodaje zawartość pliku, który jest określony przez DEFS. H do programu źródłowego. Cudzysłów oznacza, że preprocesor najpierw przeszukuje katalog zawierający nadrzędny plik źródłowy.

Zagnieżdżanie plików dołączania może być kontynuowane do 10 poziomów. Po przetworzeniu zagnieżdżonej **#include** preprocesora kontynuuje Wstawianie otaczającego pliku dołączanego do oryginalnego pliku źródłowego.

**Microsoft Specific**

Aby zlokalizować pliki źródłowe zawarcia, preprocesor najpierw przeszukuje katalogi, które są określone przez **/i** opcję kompilatora. Jeśli opcja **/i** nie jest obecna lub nie powiedzie się, preprocesor używa zmiennej środowiskowej INCLUDE do znajdowania dowolnych plików dołączanych w nawiasach kątowych. Zmienna środowiskowa INCLUDE i opcja kompilatora **/i** mogą zawierać wiele ścieżek oddzielonych średnikami ( **;** ). Jeśli więcej niż jeden katalog jest wyświetlany jako część opcji **/i** lub w zmiennej środowiskowej INCLUDE, preprocesor przeszukuje je w kolejności, w jakiej są wyświetlane.

Na przykład polecenie

```cmd
CL /ID:\MSVC\INCLUDE MYPROG.C
```

powoduje, że preprocesor przeszukuje katalog D:\MSVC\INCLUDE\ pod kątem plików dołączanych, takich jak STDIO. C. Polecenia

```cmd
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

mieć ten sam efekt. Jeśli oba zestawy wyszukiwania zakończą się niepowodzeniem, generowany jest krytyczny błąd kompilatora.

Jeśli nazwa pliku jest w pełni określona dla pliku dołączanego, który ma ścieżkę, która zawiera dwukropek (na przykład F:\MSVC\SPECIAL\INCL\TEST. H) preprocesor postępuje zgodnie ze ścieżką.

W przypadku plików dołączanych, `#include "path-spec"`które są określone jako, wyszukiwanie w katalogu rozpoczyna się od katalogu pliku nadrzędnego, a następnie przechodzi przez katalogi dowolnych plików nadrzędnych. Oznacza to, że wyszukiwanie rozpoczyna się względem katalogu zawierającego plik źródłowy zawierający #includeową dyrektywę, która jest przetwarzana. Jeśli nie ma pliku nadrzędnego i nie znaleziono pliku, wyszukiwanie jest kontynuowane tak, jakby nazwa pliku została ujęta w nawiasy ostre.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)\
[/I (Dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md)
