---
title: pack, pragma
ms.date: 07/22/2020
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 72f94520516cce2ae36b70795fb29e3d4d8068df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219394"
---
# <a name="pack-pragma"></a>pack, pragma

Określa wyrównanie pakowania dla elementów członkowskich struktury, Unii i klasy.

## <a name="syntax"></a>Składnia

> **`#pragma pack( show )`**\
> **`#pragma pack( push`** [ **`,`** *`identifier`* ] [ **`,`** *`n`* ] **`)`**\
> **`#pragma pack( pop`** [ **`,`** { *`identifier`* | *`n`* } ] **`)`**\
> **`#pragma pack(`** [ *`n`* ] **`)`**

### <a name="parameters"></a>Parametry

**`show`**\
Obowiązkowe Wyświetla bieżącą wartość bajtu na potrzeby wyrównania pakowania. Wartość jest wyświetlana przez komunikat ostrzegawczy.

**`push`**\
Obowiązkowe Wypycha bieżącą wartość wyrównania pakowania na wewnętrznym stosie kompilatora i ustawia bieżącą wartość wyrównania pakowania na *n*. Jeśli *n* nie jest określony, bieżąca wartość wyrównania pakowania jest wypchnięcia.

**`pop`**\
Obowiązkowe Usuwa rekord z góry wewnętrznego stosu kompilatora. Jeśli *n* nie jest określony za pomocą **`pop`** , wartość pakowania skojarzona z rekordem wyjściowym w górnej części stosu jest nową wartością wyrównania. Jeśli *n* jest określony, na przykład, `#pragma pack(pop, 16)` *n* zmienia wartość nowej wartości wyrównania. Jeśli zostanie wyświetlona *`identifier`* wartość, na przykład, `#pragma pack(pop, r1)` wszystkie rekordy na stosie są zdjęte do momentu znalezienia rekordu, który *`identifier`* zostanie znaleziony. Ten rekord pobiera zdjęte, a wartość pakowania skojarzona z rekordem znalezionym w górnej części stosu staje się nową wartością wyrównania. Jeśli zostanie wyświetlona *`identifier`* wartość, która nie znajduje się w żadnym rekordzie na stosie, **`pop`** zostanie zignorowana.

Instrukcja `#pragma pack (pop, r1, 2)` jest równoznaczna z `#pragma pack (pop, r1)` operatorem `#pragma pack(2)` .

*`identifier`*\
Obowiązkowe Gdy jest używany z **`push`** , przypisuje nazwę do rekordu na wewnętrznym stosie kompilatora. Gdy jest używany z **`pop`** , pop rejestruje wewnętrzny stos do momentu *`identifier`* usunięcia. Jeśli *`identifier`* nie znaleziono na stosie wewnętrznym, nic nie jest zdjęte.

*`n`*\
Obowiązkowe Określa wartość w bajtach, która ma być używana na potrzeby pakowania. Jeśli opcja kompilatora [`/Zp`](../build/reference/zp-struct-member-alignment.md) nie jest ustawiona dla modułu, wartość domyślna *`n`* to 8. Prawidłowe wartości to 1, 2, 4, 8 i 16. Wyrównanie elementu członkowskiego znajduje się na granicy, która jest wielokrotnością *`n`* lub wielokrotnością rozmiaru elementu członkowskiego, w zależności od tego, który jest mniejszy.

## <a name="remarks"></a>Uwagi

Do *spakowania* klasy jest umieszczanie jej elementów członkowskich bezpośrednio po sobie w pamięci. Może to oznaczać, że niektóre lub wszystkie elementy członkowskie mogą być wyrównane na granicy mniejszej niż domyślne wyrównanie architektury docelowej. **`pack`** daje kontrolę na poziomie deklaracji danych. Różni się on od opcji kompilatora [`/Zp`](../build/reference/zp-struct-member-alignment.md) , która zapewnia tylko kontrolę na poziomie modułu. **pakiet** zaczyna obowiązywać **`struct`** po pierwszej, **`union`** lub **`class`** deklaracji po wystąpieniu dyrektywy pragma. **`pack`** nie ma wpływu na definicje. Wywoływanie **`pack`** bez argumentów ustawia *`n`* wartość ustawioną w opcji kompilatora **`/Zp`** . Jeśli opcja kompilatora nie jest ustawiona, wartość domyślna to 8 dla procesorów x86, ARM i ARM64. Wartość domyślna to 16 dla architektury x64 Native.

W przypadku zmiany wyrównania struktury nie może ona używać ilości miejsca w pamięci. Jednak może zostać wyświetlona utrata wydajności lub nawet wygenerowanie wyjątku generowanego sprzętowo dla niewyrównanych praw dostępu. Zachowanie tego wyjątku można zmienić za pomocą polecenia [`SetErrorMode`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) .

Aby uzyskać więcej informacji na temat modyfikowania wyrównania, zobacz następujące artykuły:

- [`alignof`](../cpp/alignof-operator.md)

- [`align`](../cpp/align-cpp.md)

- [`__unaligned`](../cpp/unaligned.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specyficzne dla architektury x64)

   > [!WARNING]
   > W programie Visual Studio 2015 i nowszych można używać standardowych **`alignas`** operatorów i **`alignof`** , które są w przeciwieństwie do **`__alignof`** i **`__declspec( align )`** są przenośne przez kompilatory. Standard C++ nie odwołuje się do pakowania, dlatego **`pack`** do określenia wyrównania mniejszego niż rozmiar wyrazu docelowej architektury należy używać (lub odpowiedniego rozszerzenia dla innych kompilatorów).

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje, jak używać **`pack`** dyrektywy pragma do zmiany wyrównania struktury.

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

[Dyrektywy pragma i `__pragma` słowo kluczowe](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
