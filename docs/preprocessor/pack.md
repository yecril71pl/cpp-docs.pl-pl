---
title: pack, pragma
ms.date: 11/11/2019
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 037c57a10b1de7dd00249ae60acaef0939e355eb
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765737"
---
# <a name="pack-pragma"></a>pack, pragma

Określa wyrównanie pakowania dla elementów członkowskich struktury, Unii i klasy.

## <a name="syntax"></a>Składnia

> **Pakiet #pragma (Pokaż)**\
> **#pragma Pack (wypychanie** [ **,** *Identyfikator* ] [ **,** *n* ] **)**\
> **#pragma Pack (pop** [ **,** { *Identyfikator* | *n* }] **)**\
> **pakiet #pragma (** [ *n* ] **)**

### <a name="parameters"></a>Parametry

**wskazują**\
Obowiązkowe Wyświetla bieżącą wartość bajtu na potrzeby wyrównania pakowania. Wartość jest wyświetlana przez komunikat ostrzegawczy.

**wydajności**\
Obowiązkowe Wypycha bieżącą wartość wyrównania pakowania na wewnętrznym stosie kompilatora i ustawia bieżącą wartość wyrównania pakowania na *n*. Jeśli *n* nie jest określony, bieżąca wartość wyrównania pakowania jest wypchnięcia.

**skakując**\
Obowiązkowe Usuwa rekord z góry wewnętrznego stosu kompilatora. Jeśli *n* nie jest określony za pomocą **pop**, wartość pakowania skojarzona z rekordem wyjściowym w górnej części stosu jest nową wartością wyrównania. Jeśli *n* jest określony, na przykład `#pragma pack(pop, 16)`, *n* zmienia wartość nowej wartości wyrównania. Jeśli używasz *identyfikatora*, na przykład `#pragma pack(pop, r1)`, wszystkie rekordy na stosie są zdjęte do momentu znalezienia rekordu o *identyfikatorze* . Ten rekord to zdjęte, a wartość pakowania skojarzona z rekordem wyjściowym w górnej części stosu jest nową wartością wyrównania. Jeśli używasz *identyfikatora* , który nie został znaleziony w żadnym rekordzie na stosie **, zostanie on** zignorowany.

Instrukcja `#pragma pack (pop, r1, 2)` jest równoznaczna z `#pragma pack (pop, r1)` operatorem `#pragma pack(2)`.

*identyfikatora*\
Obowiązkowe W przypadku użycia z opcją **push**przypisuje nazwę rekordu na wewnętrznym stosie kompilatora. Gdy jest używany z **pop**, pop rejestruje wewnętrzny stos do momentu usunięcia *identyfikatora* . Jeśli na stosie wewnętrznym nie znaleziono *identyfikatora* , nic nie jest zdjęte.

*Azotan*\
Obowiązkowe Określa wartość w bajtach, która ma być używana na potrzeby pakowania. Jeśli opcja kompilatora [/ZP](../build/reference/zp-struct-member-alignment.md) nie jest ustawiona dla modułu, wartość domyślna dla *n* to 8. Prawidłowe wartości to 1, 2, 4, 8 i 16. Wyrównanie elementu członkowskiego znajduje się na granicy, która jest wielokrotnością *n*lub wielokrotnością rozmiaru elementu członkowskiego, w zależności od tego, który jest mniejszy.

## <a name="remarks"></a>Uwagi

Do *spakowania* klasy jest umieszczanie jej elementów członkowskich bezpośrednio po sobie w pamięci. Może to oznaczać, że niektóre lub wszystkie elementy członkowskie mogą być wyrównane na granicy mniejszej niż domyślne wyrównanie architektury docelowej. **pakiet** daje kontrolę na poziomie deklaracji danych. Różni się od opcji kompilatora [/ZP](../build/reference/zp-struct-member-alignment.md), która zapewnia tylko kontrolę na poziomie modułu. **pakiet** zaczyna obowiązywać przy pierwszej deklaracji **struktury**, **Unii**lub **klasy** po napotkaniu dyrektywy pragma. **pakiet** nie ma wpływu na definicje. **Pakiet** wywołujący bez argumentów ustawia *n* do wartości ustawionej w opcji `/Zp`kompilatora. Jeśli opcja kompilatora nie jest ustawiona, wartość domyślna to 8 dla procesorów x86, ARM i ARM64. Wartość domyślna to 16 dla architektury x64 Native.

W przypadku zmiany wyrównania struktury nie można użyć ilości miejsca w pamięci, ale może zostać wyświetlony spadek wydajności lub nawet uzyskać wyjątek wygenerowany sprzętowo dla niewyrównanego dostępu.  To zachowanie wyjątku można zmodyfikować za pomocą polecenia [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode).

Aby uzyskać więcej informacji na temat modyfikowania wyrównania, zobacz następujące artykuły:

- [__alignof](../cpp/alignof-operator.md)

- [dostosowania](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specyficzne dla architektury x64)

   > [!WARNING]
   > W programie Visual Studio 2015 i nowszych można używać standardowych operatorów **alignas** i **alignof** , które są w `__alignof` przeciwieństwie `declspec( align )` do i są przenośne przez kompilatory. Standard C++ nie odwołuje się do pakowania, dlatego nadal trzeba używać **pakietu** (lub odpowiedniego rozszerzenia w innych kompilatorach), aby określić wyrównania mniejsze niż rozmiar słowa docelowego architektury docelowej.

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje, jak zmienić wyrównanie struktury przy użyciu dyrektywy pragma **Pack** .

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

Poniższy przykład pokazuje, jak używać składni *wypychania*, *pop*i *show* .

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810

// pop to the identifier and then set
// the value of the current packing alignment:
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
