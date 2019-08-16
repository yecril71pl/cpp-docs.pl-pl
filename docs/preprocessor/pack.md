---
title: pakiet
ms.date: 12/17/2018
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: da4484ec86d39c8fa55a741eadd53a1d614b20dc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510178"
---
# <a name="pack"></a>pakiet
Określa wyrównanie pakowania dla elementów członkowskich struktury, Unii i klasy.

## <a name="syntax"></a>Składnia

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>Parametry

**wskazują**<br/>
Obowiązkowe Wyświetla bieżącą wartość bajtu na potrzeby wyrównania pakowania. Wartość jest wyświetlana przez komunikat ostrzegawczy.

**push**<br/>
Obowiązkowe Wypycha bieżącą wartość wyrównania pakowania na wewnętrznym stosie kompilatora i ustawia bieżącą wartość wyrównania pakowania na *n*. Jeśli *n* nie jest określony, bieżąca wartość wyrównania pakowania jest wypchnięcia.

**skakując**<br/>
Obowiązkowe Usuwa rekord z góry wewnętrznego stosu kompilatora. Jeśli *n* nie jest określony za pomocą **pop**, wartość pakowania skojarzona z rekordem wyjściowym w górnej części stosu jest nową wartością wyrównania. Jeśli *n* jest określony, na przykład `#pragma pack(pop, 16)`, *n* zmienia wartość nowej wartości wyrównania. Jeśli zostanie wyświetlona z identyfikatorem, `#pragma pack(pop, r1)`na przykład, wszystkie rekordy na stosie są zdjęte do momentu znalezienia rekordu o *identyfikatorze* . Ten rekord to zdjęte, a wartość pakowania skojarzona z rekordem wyjściowym w górnej części to stos nowej wartości wyrównania pakowania. Jeśli zostanie wyświetlony *Identyfikator* , który nie zostanie znaleziony w żadnym rekordzie na stosie, zostanie on zignorowany.

*identyfikatora*<br/>
Obowiązkowe W przypadku użycia z opcją *push*przypisuje nazwę rekordu na wewnętrznym stosie kompilatora. Gdy jest używany z **pop**, pop rejestruje wewnętrzny stos do momentu usunięcia *identyfikatora* ; Jeśli na stosie wewnętrznym nie znaleziono *identyfikatora* , nic nie jest zdjęte.

*n*<br/>
Obowiązkowe Określa wartość w bajtach, która ma być używana na potrzeby pakowania. Jeśli dla modułu nie ustawiono opcji kompilatora [/ZP](../build/reference/zp-struct-member-alignment.md) , wartością domyślną dla *n* jest 8. Prawidłowe wartości to 1, 2, 4, 8 i 16. Wyrównanie elementu członkowskiego będzie należeć do granicy, która jest wielokrotnością *n* lub wielokrotnością rozmiaru elementu członkowskiego, w zależności od tego, który jest mniejszy.

`#pragma pack(pop, identifier, n)`jest niezdefiniowany.

## <a name="remarks"></a>Uwagi

Do spakowania klasy jest umieszczenie jej elementów członkowskich bezpośrednio po sobie w pamięci, co może oznaczać, że niektóre lub wszystkie elementy członkowskie mogą być wyrównane na granicy mniejszej niż domyślne wyrównanie architektury docelowej. **pakiet** daje kontrolę na poziomie deklaracji danych. Różni się to od opcji kompilatora [/ZP](../build/reference/zp-struct-member-alignment.md), która zapewnia tylko kontrolę na poziomie modułu. **pakiet** zaczyna obowiązywać przy pierwszej deklaracji **struktury**, **Unii**lub **klasy** po napotkaniu dyrektywy pragma. **pakiet** nie ma wpływu na definicje. **Pakiet** wywołujący bez argumentów ustawia *n* do wartości ustawionej w opcji `/Zp`kompilatora. Jeśli opcja kompilatora nie jest ustawiona, wartością domyślną jest 8.

W przypadku zmiany wyrównania struktury nie można użyć ilości miejsca w pamięci, ale może zostać wyświetlony spadek wydajności lub nawet uzyskać wyjątek wygenerowany sprzętowo dla niewyrównanego dostępu.  To zachowanie wyjątku można zmodyfikować za pomocą polecenia [](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode)SetErrorMode.

Aby uzyskać więcej informacji na temat modyfikowania wyrównania, zobacz następujące tematy:

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specyficzne dla x64)

   > [!WARNING]
   > Należy pamiętać, że w programie Visual Studio 2015 i nowszych można używać standardowych operatorów alignas i alignof, które w `__alignof` przeciwieństwie do i `declspec( align )` są przenośne przez kompilatory. C++ Standard nie dotyczy pakowania, dlatego należy nadal używać **pakietu** (lub odpowiedniego rozszerzenia dla innych kompilatorów), aby określić wyrównania mniejsze niż rozmiar wyrazu w przypadku architektury docelowej.

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
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)