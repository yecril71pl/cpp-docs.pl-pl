---
title: Bloki opisów
description: NMAKE używa bloków opisu do kojarzenia obiektów docelowych, zależności i poleceń w pliku makefile.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: e4e80b59d3d30b3b34c55b40d337ef5c078e6404
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322261"
---
# <a name="description-blocks"></a>Bloki opisów

Bloki opisu tworzą rdzeń pliku makefile. Opisują one *obiekty docelowe*lub pliki do utworzenia i ich *zależności*, pliki potrzebne do utworzenia obiektów docelowych. Blok opisu może zawierać *polecenia,* które opisują sposób tworzenia obiektów docelowych z zależności. Blok opisu jest wierszem zależności, po którym opcjonalnie następuje blok poleceń:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Linie zależności

*Wiersz zależności* określa jeden lub więcej obiektów docelowych i zero lub więcej osób zależnych. Jeśli obiekt docelowy nie istnieje lub ma wcześniejszą sygnaturę czasową niż zależna, NMAKE wykonuje polecenia w bloku poleceń. NMAKE wykonuje również blok poleceń, jeśli obiekt docelowy jest [pseudotargetem.](pseudotargets.md) Oto przykładowy wiersz zależności:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

W tym wierszu `hi_bye.exe` zależności jest obiekt docelowy. Jego zależności `hello.obj`to `goodbye.obj`, `helper.lib`i . Wiersz zależności mówi NMAKE do tworzenia `hello.obj`obiektu `goodbye.obj`docelowego, gdy , lub `helper.lib` zmienił się ostatnio niż `hi_bye.exe`.

Cel musi znajdować się na początku wiersza. Nie można go wcięć żadnymi spacjami ani zakładkami. Użyj dwukropka (`:`), aby oddzielić obiekty docelowe od osób zależnych. Spacje lub karty są dozwolone między elementami`:`docelowymi, separatorem dwukropek ( ) i zależnymi. Aby podzielić linię zależności, użyj ukośnika odwrotnego (`\`) po docelowych lub zależnych.

Przed wykonaniem bloków poleceń, NMAKE skanuje wszystkie zależności i wszelkie odpowiednie *reguły*wnioskowania do tworzenia drzewa zależności . Drzewo zależności określa kroki wymagane do pełnej aktualizacji obiektu docelowego. NMAKE sprawdza rekurencyjnie, czy osoba zależna sama jest obiektem docelowym na innej liście zależności. Po zbudowaniu drzewa zależności NMAKE sprawdza sygnatury czasowe. Jeśli wszelkie zależności w drzewie są nowsze niż miejsce docelowe, NMAKE buduje miejsce docelowe.

## <a name="targets"></a><a name="targets"></a>Cele

Sekcja cele wiersza zależności określa jeden lub więcej obiektów docelowych. Celem może być dowolna prawidłowa nazwa pliku, nazwa katalogu lub [pseudotarget](pseudotargets.md). Oddziel wiele obiektów docelowych przy użyciu jednego lub większej liczby spacji lub kart. Obiekty docelowe nie są rozróżniane. Ścieżki są dozwolone za pomocą nazwy plików. Cel i jego ścieżka nie mogą przekraczać 256 znaków. Jeśli obiekt docelowy poprzedzający dwukropek jest pojedynczym znakiem, należy użyć odstępu oddzielającego. W przeciwnym razie NMAKE interpretuje kombinację dwukropek jako specyfikator dysku.

### <a name="multiple-targets"></a><a name="multiple-targets"></a>Wiele celów

NMAKE ocenia wiele obiektów docelowych w jednej zależności, tak jakby każdy z nich zostały określone w osobnym bloku opisu.

Na przykład ta reguła:

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

ocenia się jako:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a>Skumulowane zależności

Zależności są kumulatywne w bloku opisu, jeśli obiekt docelowy jest powtarzany.

Na przykład ten zestaw reguł,

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

ocenia się jako:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Jeśli masz wiele obiektów docelowych w wielu wierszach zależności w jednym bloku opisu, NMAKE ocenia je tak, jakby każdy z nich został określony w osobnym bloku opisu. Jednak tylko obiekty docelowe w ostatnim wierszu zależności używają bloku poleceń. NMAKE próbuje użyć reguły wnioskowania dla innych obiektów docelowych.

Na przykład ten zestaw reguł,

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

ocenia się jako:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a>Obiekty docelowe w wielu blokach opisu

Aby zaktualizować obiekt docelowy w więcej niż jednym bloku opisów przy użyciu różnych poleceń, określ dwa kolejne dwukropki (::) między celami a osobami pozostającymi na utrzymaniu.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a>Skutki uboczne zależności

Można określić obiekt docelowy z dwukropkiem (:) w dwóch wierszach zależności w różnych lokalizacjach. Jeśli polecenia pojawiają się tylko po jednym z wierszy, NMAKE interpretuje zależności tak, jakby wiersze były przylegające lub połączone. Nie wywołuje reguły wnioskowania dla zależności, która nie ma poleceń. Zamiast tego NMAKE zakłada, że zależności należą do jednego bloku opisu i wykonuje polecenia określone z innymi zależnościami. Należy wziąć pod uwagę ten zestaw reguł:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

ocenia się jako:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Efekt ten nie występuje, jeśli`::`używany jest podwójny dwukropek ( ). Na przykład ten zestaw reguł:

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

ocenia się jako:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a><a name="pseudotargets"></a>Pseudotargety

*Pseudotarget* jest etykietą używaną zamiast nazwy pliku w wierszu zależności. Jest interpretowany jako plik, który nie istnieje, a więc jest nieaktualny. NMAKE zakłada, że sygnatura czasowa pseudotargetu jest taka sama jak najnowsza ze wszystkich jego zależności. Jeśli nie ma zależności, zakłada się bieżący czas. Jeśli pseudotarget jest używany jako cel, jego polecenia są zawsze wykonywane. Pseudotarget używany jako zależny musi również pojawić się jako obiekt docelowy w innej zależności. Jednak ta zależność nie musi mieć bloku poleceń.

Nazwy pseudotargetów są zgodne z regułami składni nazwy pliku dla obiektów docelowych. Jeśli jednak nazwa nie ma rozszerzenia, może przekroczyć limit 8 znaków dla nazw plików i może mieć do 256 znaków.

Pseudotargets są przydatne, gdy chcesz NMAKE do tworzenia więcej niż jeden cel automatycznie. NMAKE tylko buduje cele określone w wierszu polecenia. Lub, jeśli nie określono celu wiersza polecenia, tworzy tylko pierwszy obiekt docelowy w pierwszej zależności w pliku makefile. Możesz powiedzieć NMAKE, aby zbudować wiele obiektów docelowych bez wyświetlania ich osobno w wierszu polecenia. Napisz blok opisu z zależnością zawierającą pseudotarget i wyświetl listę obiektów docelowych, które chcesz zbudować jako jego zależne. Następnie umieść ten blok opisu najpierw w pliku makefile lub określ pseudotarget w wierszu polecenia NMAKE.

W tym przykładzie UPDATE jest pseudotargetem.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Po ocenie update NMAKE kopiuje wszystkie pliki w bieżącym katalogu do określonego dysku i katalogu.

W poniższym pliku makefile `all` pseudotarget `project1.exe` `project2.exe` tworzy zarówno `all` i jeśli albo nie jest określony cel w wierszu polecenia. Pseudotarget `setenv` zmienia zmienną środowiskową `.exe` LIB przed zaktualizowaniem plików:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a>Zależności

W wierszu zależności określ zero lub więcej`:`zależności po dwukropku ( ) lub podwójnym dwukropku (`::`), używając dowolnej prawidłowej nazwy pliku lub [pseudotargetu](pseudotargets.md). Oddziel wiele zależności za pomocą jednego lub większej liczby spacji lub kart. Osoby pozostające na utrzymaniu nie są rozróżniane. Ścieżki są dozwolone za pomocą nazwy plików.

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a>Wywnioskować zależności

Wraz z zależnymi, które jawnie wymienisz w wierszu zależności, NMAKE może przyjąć *wywnioskowane zależne*. Wywnioskowane zależne pochodzi od reguły wnioskowania i jest oceniane przed jawnych zależności. Gdy wywnioskowane zależne jest nieaktualne w porównaniu do jego obiektu docelowego, NMAKE wywołuje blok poleceń dla zależności. Jeśli wywnioskowane zależne nie istnieje lub jest nieaktualne w porównaniu do własnych osób zależnych, NMAKE najpierw aktualizuje wywnioskowane zależne. Aby uzyskać więcej informacji na temat wywnioskować zależności, zobacz [Reguły wnioskowania](inference-rules.md).

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a>Szukaj ścieżek dla osób pozostających na utrzymaniu

Można określić opcjonalną ścieżkę wyszukiwania dla każdego zależnego. Oto składnia określająca zestaw katalogów do wyszukania:

> **{**_katalog_\[**;** _katalog ...]_ **}**_zależne_

Nazwy katalogów należy ująć w nawiasy klamrowe (`{ }`). Oddziel wiele katalogów średnikiem`;`( ). Miejsca ani karty nie są dozwolone. NMAKE szuka zależności najpierw w bieżącym katalogu, a następnie na liście katalogów w określonej kolejności. Za pomocą makra można określić część lub całość ścieżki wyszukiwania. Tylko określony zależny używa tej ścieżki wyszukiwania.

#### <a name="directory-search-path-example"></a>Przykład ścieżki wyszukiwania katalogu

Ten wiersz zależności pokazuje, jak utworzyć specyfikację katalogu dla wyszukiwania:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

Cel `reverse.exe` ma jeden `retro.obj`zależny, . Lista złącza klamrowa określa dwa katalogi. NMAKE najpierw `retro.obj` wyszukuje w bieżącym katalogu. Jeśli go nie ma, NMAKE `\src\omega` przeszukuje `e:\repo\backwards` katalog, a następnie katalog.

## <a name="see-also"></a>Zobacz też

[NMAKE — dokumentacja](nmake-reference.md)
