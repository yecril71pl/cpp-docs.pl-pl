---
title: Bloki opisów
description: NMAKE używa bloków opisu do kojarzenia obiektów docelowych, zależności i poleceń w pliku reguł programu make.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: fb9cf4400c96b588e8704e972dd29ab27f41cae9
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144530"
---
# <a name="description-blocks"></a>Bloki opisów

Bloki opisu tworzą rdzeń pliku reguł programu make. Określają one *cele*lub pliki do utworzenia oraz ich *zależności*, pliki, które są konieczne do utworzenia obiektów docelowych. Blok opisu może zawierać *polecenia*, które opisują sposób tworzenia obiektów docelowych z zależności. Blok opisu jest linią zależności, opcjonalnie po którym następuje blok poleceń:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Linie zależności

*Linia zależności* określa co najmniej jeden element docelowy i zero lub więcej elementów zależnych. Jeśli obiekt docelowy nie istnieje lub ma wcześniejszą sygnaturę czasową niż zależna, NMAKE wykonuje polecenia w bloku poleceń. NMAKE wykonuje również blok poleceń, jeśli obiektem docelowym jest [pseudotarget](pseudotargets.md). Oto przykładowa linia zależności:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

W tej linii zależności `hi_bye.exe` jest elementem docelowym. Jego zależności są `hello.obj`, `goodbye.obj`i `helper.lib`. Linia zależności instruuje NMAKE, aby kompilować obiekt docelowy za każdym razem, gdy `hello.obj`, `goodbye.obj`lub `helper.lib` uległy zmianie ostatnio niż `hi_bye.exe`.

Element docelowy musi znajdować się na początku wiersza. Nie można utworzyć wcięcia przy użyciu żadnych spacji ani tabulatorów. Użyj dwukropka (`:`), aby oddzielić elementy docelowe od elementów zależnych. Spacje lub tabulatory są dozwolone między elementami docelowymi, separatorem dwukropka (`:`) i elementami zależnymi. Aby podzielić linię zależności, użyj ukośnika odwrotnego (`\`) po elemencie docelowym lub zależnie.

Przed wykonaniem bloków poleceń NMAKE skanuje wszystkie zależności i stosowane reguły wnioskowania w celu utworzenia *drzewa zależności*. Drzewo zależności określa kroki wymagane do pełnej aktualizacji celu. NMAKE sprawdza rekursywnie, niezależnie od tego, czy zależny jest sam obiekt docelowy na innej liście zależności. Po skompilowaniu drzewa zależności NMAKE sprawdza sygnatury czasowe. Jeśli którykolwiek z elementów zależnych w drzewie jest nowszy niż docelowy, NMAKE kompiluje element docelowy.

## <a name="targets"></a>Celach

Sekcja targets linii zależności określa co najmniej jeden element docelowy. Obiektem docelowym może być dowolna prawidłowa nazwa pliku, katalog lub [pseudotarget](pseudotargets.md). Oddziel wiele obiektów docelowych przy użyciu co najmniej jednej spacji lub kart. W obiektach docelowych nie jest rozróżniana wielkość liter. Ścieżki są dozwolone z nazwami plików. Wartość docelowa i jej ścieżka nie mogą przekraczać 256 znaków. Jeśli obiekt docelowy poprzedzający dwukropek jest pojedynczym znakiem, Użyj spacji rozdzielającej. W przeciwnym razie NMAKE interpretuje kombinację dwukropka jako specyfikatora dysku.

### <a name="multiple-targets"></a>Wiele obiektów docelowych

NMAKE oblicza wiele obiektów docelowych w pojedynczej zależności, tak jak gdyby zostały określone w osobnym bloku opisu.

Na przykład ta reguła:

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

jest oceniane jako:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a>Zależności zbiorcze

Zależności są kumulowane w bloku opisu, jeśli element docelowy jest powtarzany.

Na przykład ten zestaw reguł,

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

jest oceniane jako:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Jeśli masz wiele obiektów docelowych w wielu wierszach zależności w jednym bloku opisu, NMAKE oblicza je tak, jakby zostały określone w osobnym bloku opisu. Jednak tylko obiekty docelowe w ostatnim wierszu zależności używają bloku poleceń. NMAKE próbuje użyć reguły wnioskowania dla innych celów.

Na przykład ten zestaw reguł,

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

jest oceniane jako:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a>Elementy docelowe w blokach z wieloma opisami

Aby zaktualizować element docelowy w więcej niż jednym bloku opisu przy użyciu różnych poleceń, określ dwa kolejne dwukropki (::) między elementami docelowymi i elementami zależnymi.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a>Efekty uboczne zależności

Można określić element docelowy z dwukropkiem (:) w dwóch wierszach zależności w różnych lokalizacjach. Jeśli polecenia pojawiają się po tylko jednym z wierszy, NMAKE interpretuje zależności tak, jakby linie były sąsiadujące lub połączone. Nie wywołuje reguły wnioskowania dla zależności, która nie ma poleceń. Zamiast tego, NMAKE zakłada, że zależności należą do jednego bloku opisu i wykonuje polecenia określone z inną zależnością. Należy wziąć pod uwagę ten zestaw reguł:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

jest oceniane jako:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Ten efekt nie występuje, gdy jest używany podwójny dwukropek (`::`). Na przykład ten zestaw reguł:

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

jest oceniane jako:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a>Pseudo cele

*Pseudotarget* to etykieta użyta zamiast nazwy pliku w wierszu zależności. Jest on interpretowany jako plik, który nie istnieje, a więc jest nieaktualny. NMAKE zakłada, że sygnatura czasowa pseudotarget jest taka sama jak Najnowsza z jej elementów zależnych. Jeśli nie ma żadnych zależności, założono bieżącą godzinę. Jeśli pseudotarget jest używany jako element docelowy, jego polecenia są zawsze wykonywane. Pseudotarget używany jako element zależny musi również występować jako obiekt docelowy w innej zależności. Jednak taka zależność nie musi mieć bloku poleceń.

Nazwy pseudotarget są zgodne z regułami składni nazw dla elementów docelowych. Jeśli jednak nazwa nie ma rozszerzenia, może przekroczyć limit 8 znaków dla nazw plików i może składać się z maksymalnie 256 znaków.

Pseudo cele są przydatne, gdy chcesz, aby NMAKE automatycznie kompilować więcej niż jeden element docelowy. NMAKE kompiluje tylko elementy docelowe określone w wierszu polecenia. Lub, jeśli nie określono elementu docelowego wiersza polecenia, kompiluje tylko pierwszy element docelowy w pierwszej zależności w pliku reguł programu make. Możesz powiedzieć NMAKE, aby kompilować wiele obiektów docelowych bez wyświetlania ich indywidualnie w wierszu polecenia. Napisz blok opisu z zależnością zawierającą element pseudotarget, a następnie utwórz listę obiektów docelowych, które chcesz skompilować jako zależne. Następnie umieść ten blok opisu jako pierwszy w pliku reguł programu make lub określ pseudotarget w wierszu polecenia NMAKE.

W tym przykładzie aktualizacja jest pseudotarget.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Gdy aktualizacja jest szacowana, NMAKE kopiuje wszystkie pliki w bieżącym katalogu do określonego dysku i katalogu.

W poniższym pliku reguł programu make pseudotarget `all` kompiluje `project1.exe` i `project2.exe`, jeśli w wierszu polecenia nie określono `all` lub żadnego elementu docelowego. Pseudotarget `setenv` zmienia zmienną środowiskową LIB przed zaktualizowaniem plików `.exe`:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a>Zależności

W wierszu zależności należy określić zero lub więcej zależności po dwukropku (`:`) lub podwójnym dwukropku (`::`), używając dowolnych prawidłowych nazw plików lub [pseudotarget](pseudotargets.md). Oddziel wiele zależności, używając co najmniej jednej spacji lub kart. Zależne nie są rozróżniane wielkości liter. Ścieżki są dozwolone z nazwami plików.

### <a name="inferred-dependents"></a>Zależności wywnioskowane

Wraz z zależnościami, które można jawnie wyświetlić w wierszu zależności, NMAKE może przyjmować *zależne zależności*. Zależne od wywnioskowanego elementu pochodzą z reguły wnioskowania i są oceniane przed jawnymi elementami zależnymi. Gdy wywnioskowane zależności są nieaktualne w porównaniu do ich celu, NMAKE wywołuje blok poleceń dla zależności. Jeśli wywnioskowane zależnie nie istnieje lub jest nieaktualne w porównaniu z własnymi zależnymi, NMAKE najpierw aktualizuje zależne zależności. Aby uzyskać więcej informacji o wnioskach zależnych, zobacz [reguły wnioskowania](inference-rules.md).

### <a name="search-paths-for-dependents"></a>Ścieżki wyszukiwania dla zależności

Możesz określić opcjonalną ścieżkę wyszukiwania dla każdego elementu zależnego. Oto składnia określająca zestaw katalogów do przeszukania:

> **{** _katalog_\[ **;** _katalog_...] **}** _zależne_

Nazwy katalogów należy ująć w nawiasy klamrowe (`{ }`). Rozdziel wiele katalogów średnikami (`;`). Nie są dozwolone żadne spacje ani karty. NMAKE szuka elementu zależnego najpierw w bieżącym katalogu, a następnie na liście katalogów w określonej kolejności. Możesz użyć makra, aby określić część lub wszystkie ścieżki wyszukiwania. Tylko określone zależne użycie tej ścieżki wyszukiwania.

#### <a name="directory-search-path-example"></a>Przykład ścieżki wyszukiwania w katalogu

Ten wiersz zależności pokazuje, jak utworzyć specyfikację katalogu dla wyszukiwania:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

`reverse.exe` docelowa ma jedną zależność, `retro.obj`. Lista ujęta w nawiasy klamrowe określa dwa katalogi. NMAKE wyszukuje najpierw `retro.obj` w bieżącym katalogu. Jeśli tak nie jest, NMAKE przeszukuje katalog `\src\omega`, a następnie katalog `e:\repo\backwards`.

## <a name="see-also"></a>Zobacz także

[NMAKE — dokumentacja](nmake-reference.md)
