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
ms.openlocfilehash: bf1ae81184d53dd271f63c26e8f9a52a6410b232
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038450"
---
# <a name="pack"></a>pakiet
Określa wyrównanie pakowania dla struktury, Unii i składowych klasy.

## <a name="syntax"></a>Składnia

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>Parametry

**Pokaż**<br/>
(Opcjonalnie) Wyświetla bieżącą wartość bajtu pakowania wyrównania. Wartość jest wyświetlana przez komunikat ostrzegawczy.

**push**<br/>
(Opcjonalnie) Wypchnięcia bieżącego wyrównania pakowania wartości na wewnętrznym stosie kompilatora i ustawia wartość bieżącej wyrównanie pakowania *n*. Jeśli *n* nie zostanie określony, bieżącą wartość wyrównania pakowania zostanie przypisany.

**POP**<br/>
(Opcjonalnie) Usuwa rekord z góry wewnętrznego stosu kompilatora. Jeśli *n* nie zostanie określony z **pop**, wartość pakowania skojarzone z wynikowego rekordu na górze stosu jest nową wartość wyrównania pakowania. Jeśli *n* jest określony, na przykład `#pragma pack(pop, 16)`, *n* staje się nowym pakowania wartością wyrównania. Jeśli pop z *identyfikator*, na przykład `#pragma pack(pop, r1)`, a następnie wszystkie rekordy na stosie są zdjęte ze stosu dopóki rekord, który ma *identyfikator* znajduje się. Że zdjęte ze stosu rekordu i wartość pakowania skojarzone z wynikowego rekordu w górnej części stosu nowe pakowania wartością wyrównania. Jeśli pop z *identyfikator* który nie znajduje się w każdy rekord w stosie, a następnie **pop** jest ignorowana.

*Identyfikator*<br/>
(Opcjonalnie) Gdy jest używane z *wypychania*, przypisuje nazwę rekordowi na wewnętrznym stosie kompilatora. Gdy jest używane z **pop**, zdejmuje rekordy z wewnętrznego stosu aż do usunięcia *identyfikator* zostanie usunięta; Jeśli *identyfikator* nie zostanie znaleziony na wewnętrznym stosie, nic nie zostanie zdjęte.

*n*<br/>
(Opcjonalnie) Określa wartość, w bajtach, służący do pakowania. Jeśli opcja kompilatora [/ZP](../build/reference/zp-struct-member-alignment.md) nie jest ustawiona dla modułu, wartością domyślną dla *n* wynosi 8. Prawidłowe wartości to 1, 2, 4, 8 i 16. Wyrównanie elementu członkowskiego będzie znajdować się na granicy, która jest wielokrotnością liczby *n* lub wielokrotność rozmiaru elementu członkowskiego, która kwota jest mniejsza.

`#pragma pack(pop, identifier, n)` jest niezdefiniowane.

## <a name="remarks"></a>Uwagi

Umieszczenie klasy jest umieszczenie jej elementy członkowskie bezpośrednio po sobie nawzajem w pamięci, co może oznaczać, że niektóre lub wszystkie elementy członkowskie można wyrównać na granicy mniejszy niż domyślne wyrównanie architektury docelowej. **pakiet** zapewnia kontrolę na poziomie deklaracji danych. To różni się od — opcja kompilatora [/ZP](../build/reference/zp-struct-member-alignment.md), który tylko można kontrolować poziom modułu. **pakiet** staje się skuteczny po pierwszym **struktury**, **Unii**, lub **klasy** deklaracji po pragmy jest widoczny. **pakiet** nie ma wpływu na definicje. Wywoływanie **pakiet** z zestawami nie argumentów *n* wartość ustawioną w — opcja kompilatora `/Zp`. Jeśli nie ustawiono opcję kompilatora, wartością domyślną jest 8.

Jeśli zmienisz Wyrównanie struktury, nie może używać dużej ilości miejsca w pamięci, ale może zobaczyć spadek wydajności lub nawet uzyskać wyjątek generowany sprzętu dla niewyrównany dostęp.  To zachowanie wyjątku można zmienić za pomocą [SetErrorMode](https://msdn.microsoft.com/library/windows/desktop/ms680621).

Aby uzyskać więcej informacji na temat sposobu modyfikowania wyrównania zobacz następujące tematy:

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Przykłady wyrównania struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) — x64 określonych 64

   > [!WARNING]
   > Należy pamiętać, że w programie Visual Studio 2015 i nowszych można użyć operatory alignof i alignas standardowa którego, w przeciwieństwie do `__alignof` i `declspec( align )` można przenosić między kompilatory. C++ standard nie opisano kwestii pakowania, dlatego należy nadal używać **pakiet** (lub odpowiedniego rozszerzenia na inne kompilatory) do określenia wyrównania jest mniejszy niż rozmiar word architektury docelowej.

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje sposób użycia **pakiet** pragma może zmienić wyrównanie struktury.

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

Poniższy przykład pokazuje sposób użycia *wypychania*, *pop*, i *Pokaż* składni.

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